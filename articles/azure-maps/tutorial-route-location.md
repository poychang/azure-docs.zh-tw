---
title: 使用 Azure 地圖服務尋找路線 | Microsoft Docs
description: 使用 Azure 地圖服務的景點路線
services: azure-maps
keywords: ''
author: kgremban
ms.author: kgremban
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: azure-maps
documentationcenter: ''
manager: timlt
ms.devlang: na
ms.custom: mvc
ms.openlocfilehash: 73ca61140f05a65ca75cd703ed226773b9a43dfa
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="route-to-a-point-of-interest-using-azure-maps"></a>使用 Azure 地圖服務的景點路線

本教學課程說明如何使用 Azure 地圖服務帳戶和路線規劃服務 SDK，來尋找景點路線。 在本教學課程中，您了解如何：

> [!div class="checklist"]
> * 使用地圖控制項 API 建立新的網頁
> * 設定地址座標
> * 查詢路線規劃服務，以了解如何前往景點

## <a name="prerequisites"></a>先決條件

在繼續之前，請遵循上一個教學課程中的步驟來[建立 Azure 地圖服務帳戶](./tutorial-search-location.md#createaccount)，並[取得帳戶的訂用帳戶金鑰](./tutorial-search-location.md#getkey)。 

<a id="getcoordinates"></a>

## <a name="create-a-new-map"></a>建立新的地圖 
下列步驟顯示如何建立內嵌地圖控制項 API 的靜態 HTML 網頁。 

1. 在您的本機機器上建立新檔案，並將其命名為 **MapRoute.html**。 
2. 在檔案中新增下列 HTML 元件：

    ```HTML
    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, user-scalable=no" />
        <title>Map Route</title>
        <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/css/atlas.min.css?api-version=1.0" type="text/css" />
        <script src="https://atlas.microsoft.com/sdk/js/atlas.min.js?api-version=1.0"></script>
        <style>
            html,
            body {
                width: 100%;
                height: 100%;
                padding: 0;
                margin: 0;
            }

            #map {
                width: 100%;
                height: 100%;
            }
        </style>
    </head>

    <body>
        <div id="map"></div>
        <script>
            // Embed Map Control JavaScript code here
        </script>
    </body>

    </html>
    ```
    HTML 標頭會內嵌 CSS 的資源位置和 Azure 地圖服務程式庫的 JavaScript 檔案。 HTML 檔案主體中的 script 區段將會包含用來存取 Azure 地圖服務 API 的內嵌 JavaScript 程式碼。

3. 在 HTML 檔案的 script 區塊中新增下列 JavaScript 程式碼。 將字串 **\<您的帳戶金鑰\>** 取代為您從地圖服務帳戶所複製的主要金鑰。

    ```JavaScript
    // Instantiate map to the div with id "map"
    var MapsAccountKey = "<your account key>";
    var map = new atlas.Map("map", {
        "subscription-key": MapsAccountKey
    });
    ```
    **atlas.Map** 是 Azure 地圖控制項 API 的元件，可供控制視覺化互動式網路地圖。

4. 儲存檔案並在瀏覽器中將其開啟。 至此，您已擁有可以進一步發展的基本地圖了。 

   ![檢視基本地圖](./media/tutorial-route-location/basic-map.png)

## <a name="set-start-and-end-points"></a>設定起點和終點

在此教學課程中，將起點設在 Microsoft，並將終點設在西雅圖的加油站。 

1. 在 **MapRoute.html** 檔案的同一個 script 區塊中，新增下列 JavaScript 程式碼以建立路線的起點和終點：

    ```JavaScript
    // Create the GeoJSON objects which represent the start and end point of the route
    var startPoint = new atlas.data.Point([-122.130137, 47.644702]);
    var startPin = new atlas.data.Feature(startPoint, {
        title: "Microsoft",
        icon: "pin-round-blue"
    });

    var destinationPoint = new atlas.data.Point([-122.3352, 47.61397]);
    var destinationPin = new atlas.data.Feature(destinationPoint, {
        title: "Contoso Oil & Gas",
        icon: "pin-blue"
    });
    ```
    此程式碼會建立兩個 [GeoJSON 物件](https://en.wikipedia.org/wiki/GeoJSON)，代表路線的起點和終點。 

2. 新增下列 JavaScript 程式碼，以在地圖中新增起點和終點的標示：

    ```JavaScript
    // Fit the map window to the bounding box defined by the start and destination points
    var swLon = Math.min(startPoint.coordinates[0], destinationPoint.coordinates[0]);
    var swLat = Math.min(startPoint.coordinates[1], destinationPoint.coordinates[1]);
    var neLon = Math.max(startPoint.coordinates[0], destinationPoint.coordinates[0]);
    var neLat = Math.max(startPoint.coordinates[1], destinationPoint.coordinates[1]);
    map.setCameraBounds({
        bounds: [swLon, swLat, neLon, neLat],
        padding: 50
    });

    // Add pins to the map for the start and end point of the route
    map.addPins([startPin, destinationPin], {
        name: "route-pins",
        textFont: "SegoeUi-Regular",
        textOffset: [0, -20]
    });
    ``` 
    **map.setCameraBounds** 會根據起點和終點座標來調整地圖視窗。 **map.addPins** API 會在地圖控制項中以視覺化元件的形式新增景點。

7. 儲存 **MapRoute.html** 檔案並重新整理瀏覽器。 現在地圖會以西雅圖作為中心，而且您會看到以圓形藍色圖釘標示的起點，和以藍色圖釘標示的終點。

   ![檢視標有起點和終點的地圖](./media/tutorial-route-location/map-pins.png)

<a id="getroute"></a>

## <a name="get-directions"></a>取得指示

本節說明如何使用地圖服務的路線規劃服務 API，尋找從給定起點到終點的路線。 路線規劃服務會提供 API 來規劃兩個位置之間「最快速」、「最短」、「最環保」或「驚心動魄」的路線。 它也可讓使用者使用 Azure 廣泛的歷史路況資料庫，並預測任何日期和時間的路線時間，以規劃日後的路線。 如需詳細資訊，請參閱[取得路線指示](https://docs.microsoft.com/rest/api/maps/route/getroutedirections)。


1. 首先，在地圖上新增一個圖層來顯示路線路徑 (亦即 linestring)。 在 script 區塊中新增下列 JavaScript 程式碼：

    ```JavaScript
    // Initialize the linestring layer for routes on the map
    var routeLinesLayerName = "routes";
    map.addLinestrings([], {
        name: routeLinesLayerName,
        color: "#2272B9",
        width: 5,
        cap: "round",
        join: "round",
        before: "labels"
    });
    ```

2. 建立 [XMLHttpRequest](https://xhr.spec.whatwg.org/)，並新增事件處理常式以剖析地圖服務的路線規劃服務所傳送的 JSON 回應。 此程式碼會建構路線線段的座標陣列，然後將一組座標新增至地圖的 linestrings 圖層。 

    ```JavaScript
    // Perform a request to the route service and draw the resulting route on the map
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function () {
        if (this.readyState == 4 && this.status == 200) {
            var response = JSON.parse(xhttp.responseText);

            var route = response.routes[0];
            var routeCoordinates = [];
            for (var leg of route.legs) {
                var legCoordinates = leg.points.map((point) => [point.longitude, point.latitude]);
                routeCoordinates = routeCoordinates.concat(legCoordinates);
            }

            var routeLinestring = new atlas.data.LineString(routeCoordinates);
            map.addLinestrings([new atlas.data.Feature(routeLinestring)], { name: routeLinesLayerName });
        }
    };
    ```

3. 新增下列程式碼，以建置查詢並將 XMLHttpRequest 傳送至地圖服務的路線規劃服務：

    ```JavaScript
    var url = "https://atlas.microsoft.com/route/directions/json?";
    url += "api-version=1.0";
    url += "&subscription-key=" + MapsAccountKey;
    url += "&query=" + startPoint.coordinates[1] + "," + startPoint.coordinates[0] + ":" +
        destinationPoint.coordinates[1] + "," + destinationPoint.coordinates[0];

    xhttp.open("GET", url, true);
    xhttp.send();
    ```

3. 儲存 **MapRoute.html** 檔案並重新整理網頁瀏覽器。 如果您成功連線到地圖服務的 API，您應該會看到類似下面的地圖。 

    ![Azure 地圖控制項和路線規劃服務](./media/tutorial-route-location/map-route.png)


## <a name="next-steps"></a>後續步驟
在本教學課程中，您已了解如何：

> [!div class="checklist"]
> * 使用地圖控制項 API 建立新的網頁
> * 設定地址座標
> * 查詢路線規劃服務以了解如何前往景點

下一個教學課程會示範如何建立具有限制 (例如，行進模式或貨物類型) 的路線查詢 ，然後在同一個地圖上顯示多條路線。 

> [!div class="nextstepaction"]
> [尋找不同行進模式的路線](./tutorial-prioritized-routes.md)
