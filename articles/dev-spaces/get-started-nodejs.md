---
title: 使用 VS Code 在雲端建立 Kubernetes Node.js 開發環境 | Microsoft Docs
titleSuffix: Azure Dev Spaces
services: azure-dev-spaces
ms.service: azure-dev-spaces
ms.component: azds-kubernetes
author: ghogen
ms.author: ghogen
ms.date: 05/11/2018
ms.topic: tutorial
description: 在 Azure 上使用容器和微服務快速進行 Kubernetes 開發
keywords: Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, 容器
manager: douge
ms.openlocfilehash: deb651170b0fd58f8c89b591f3e42b5b629f4095
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2018
ms.locfileid: "34361466"
---
# <a name="get-started-on-azure-dev-spaces-with-nodejs"></a>在使用 Node.js 的 Azure 開發人員空間上開始使用

[!INCLUDE[](includes/learning-objectives.md)]

[!INCLUDE[](includes/see-troubleshooting.md)]

您現在可以在 Azure 中建立以 Kubernetes 為基礎的開發環境。

[!INCLUDE[](includes/portal-aks-cluster.md)]

## <a name="install-the-azure-cli"></a>安裝 Azure CLI
Azure 開發人員空間需要基本的本機電腦設定。 大部分開發環境的組態都會儲存在雲端，而且可與其他使用者共用。 從下載和執行 [Azure CLI](/cli/azure/install-azure-cli?view=azure-cli-latest) 著手。

> [!IMPORTANT]
> 如果您已安裝 Azure CLI，請確定您使用的是 2.0.32 版或更高版本。

[!INCLUDE[](includes/sign-into-azure.md)]

[!INCLUDE[](includes/use-dev-spaces.md)]

[!INCLUDE[](includes/install-vscode-extension.md)]

在您等候建立叢集時，您可以開始撰寫程式碼。

## <a name="create-a-nodejs-container-in-kubernetes"></a>在 Kubernetes 中建立 Node.js 容器

在這一節中，您會建立 Node.js Web 應用程式，並使其在 Kubernetes 的容器中執行。

### <a name="create-a-nodejs-web-app"></a>建立 Node.js Web 應用程式
瀏覽至 https://github.com/Azure/dev-spaces 以從 GitHub 下載程式碼，然後選取 [複製或下載]，將 GitHub 存放庫下載到您的本機環境。 本指南的程式碼位於 `samples/nodejs/getting-started/webfrontend`。

[!INCLUDE[](includes/azds-prep.md)]

[!INCLUDE[](includes/build-run-k8s-cli.md)]

### <a name="update-a-content-file"></a>更新內容檔案
Azure 開發人員空間不只讓程式碼中在 Kubernetes 中執行 - 還可讓您快速地反覆查看您的程式碼變更是否在雲端 Kubernetes 環境中生效。

1. 找出檔案 `./public/index.html` 並進行 HTML 編輯。 例如，將網頁的背景色彩變更為藍色陰影：

    ```html
    <body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
    ```

2. 儲存檔案。 稍後，您會在終端機視窗中看到一則訊息，指出執行中容器中的檔案已更新。
1. 移至您的瀏覽器並重新整理頁面。 您應會看到您的色彩更新。

發生什麼情形？ 編輯內容檔案 (例如 HTML 和 CSS) 時，不需要重新啟動 Node.js 程序，所以作用中 `azds up` 命令會自動將任何修改過的內容檔案，直接同步處理到 Azure 中的執行中容器，進而提供查看內容編輯的快速方法。

### <a name="test-from-a-mobile-device"></a>從行動裝置測試
如果您在行動裝置上開啟 Web 應用程式，您會發現 UI 無法正確顯示在小型裝置上。

為了修正此問題，您會新增 `viewport` 中繼標記：
1. 開啟 `./public/index.html` 檔案
1. 在現有的 `head` 元素中，新增 `viewport` 中繼標記：

    ```html
    <head>
        <!-- Add this line -->
        <meta name="viewport" content="width=device-width, initial-scale=1">
    </head>
    ```

1. 儲存檔案。
1. 重新整理您裝置的瀏覽器。 您現在應會看到正確呈現的 Web 應用程式。 

這是一個範例：您在打算使用應用程式的裝置上進行測試前，為何就是找不到某些問題。 使用 Azure 開發人員空間，您可以快速地逐一查看您的程式碼，並且在目標裝置上驗證任何變更。

### <a name="update-a-code-file"></a>更新程式碼檔案
更新伺服器端程式碼檔案時，需要執行更一點的工作，因為必須重新啟動 Node.js 應用程式。

1. 在終端機視窗中，按 `Ctrl+C` (以停止 `azds up`)。
1. 開啟名為 `server.js` 的程式碼檔案，然後編輯服務的 hello 訊息： 

    ```javascript
    res.send('Hello from webfrontend running in Azure!');
    ```

3. 儲存檔案。
1. 在終端機視窗中執行 `azds up`。 

這會重建容器映像，並重新部署 Helm 圖表。 重新載入瀏覽器頁面，以查看您的程式碼變更是否生效。

但是還有「更加快速的方法」可開發程式碼，您將在下一節中加以探索。 

## <a name="debug-a-container-in-kubernetes"></a>在 Kubernetes 中進行容器偵錯

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]

### <a name="select-the-azds-debug-configuration"></a>選取 AZDS 偵錯組態
1. 若要開啟 [偵錯] 檢視，請按一下 VS Code 側邊的 [活動列] 中的 [偵錯] 圖示。
1. 選取 [啟動程式 (AZDS)] 作為作用中偵錯組態。

![](media/get-started-node/debug-configuration-nodejs.png)

> [!Note]
> 如果您未在 [命令選擇區] 中看到任何 Azure 開發人員空間命令，請確定您已安裝適用於 [Azure 開發人員空間的 VS Code ](get-started-nodejs.md#get-kubernetes-debugging-for-vs-code)擴充功能。

### <a name="debug-the-container-in-kubernetes"></a>在 Kubernetes 中進行容器偵錯
按 **F5** 可在 Kubernetes 中進行程式碼偵錯！

類似於 `up` 命令，程式碼會在您開始偵錯時同步處理到開發環境，而且容器會建置並部署到 Kubernetes。 此時，偵錯工具會連結至遠端容器。

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

在伺服器端程式碼檔案中設定中斷點，例如在 `server.js` 中的 `app.get('/api'...` 內。 重新整理瀏覽器頁面，或按 [再說一次] 按鈕，而且您應叫用中斷點，才能逐步執行程式碼。

就如同已在本機執行程式碼一樣，您擁有偵錯資訊的完整存取權，例如呼叫堆疊、區域變數、例外狀況資訊等等。

### <a name="edit-code-and-refresh-the-debug-session"></a>編輯程式碼並重新整理偵錯工作階段
當偵錯工具作用中時，進行程式碼編輯；例如，再次修改 hello 訊息：

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

儲存檔案，然後在 [偵錯動作] 窗格中，按一下 [重新整理] 按鈕。 

![](media/get-started-node/debug-action-refresh-nodejs.png)

Azure 開發人員空間會在偵錯工作階段之間重新啟動 Node.js 程序，以提供更快的編輯/偵錯迴圈，而不是在每次進行程式碼編輯時重新建置及重新部署新的容器映像 (這通常要花費相當長的時間)。

在瀏覽器中重新整理 Web 應用程式，或按 [再說一次] 按鈕。 您應會看到自訂訊息出現在 UI 中。

### <a name="use-nodemon-to-develop-even-faster"></a>使用 NodeMon 更快速地開發
Nodemon 是 Node.js 開發人員用來快速開發的工具。 開發人員通常會將其 Node 專案設定為讓 nodemon 監視檔案變更並自動重新啟動伺服器程序，而不是在每次進行伺服器端程式碼編輯時，以手動方式重新啟動 Node 程序。 以此方式運作，開發人員只會在進行程式碼編輯之後重新整理其瀏覽器。

透過 Azure 開發人員空間，您可以在本機開發時使用許多相同的開發工作流程。 為了說明這點，已將範例 `webfrontend` 專案設定為使用 nodemon (它已在 `package.json` 中設定為開發相依性)。

請嘗試下列步驟：
1. 停止 VS Code 偵錯工具。
1. 按一下 VS Code 側邊的 [活動列] 中的 [偵錯] 圖示。 
1. 選取 [連結 (AZDS)] 作為作用中偵錯組態。
1. 按 F5。

在此組態中，容器已設定為要啟動 nodemon。 進行伺服器程式碼編輯時，nodemon 會自動重新啟動 Node 程序，就如同您在本機開發時一樣。 
1. 在 `server.js` 中再次編輯 hello 訊息，然後儲存檔案。
1. 重新整理瀏覽器，或按一下 [再說一次] 按鈕，以查看您的變更是否生效！

**您現在有辦法在 Kubernetes 中快速逐一查看程式碼及直接進行偵錯！** 接下來，您將了解如何建立和呼叫第二個容器。

## <a name="call-a-service-running-in-a-separate-container"></a>呼叫在個別容器中執行的服務

在本節中，您會建立第二個服務 `mywebapi`，並由 `webfrontend` 加以呼叫。 每個服務都會在個別的容器中執行。 然後，您將在這兩個容器間進行偵錯。

![](media/common/multi-container.png)

### <a name="open-sample-code-for-mywebapi"></a>開啟 *mywebapi* 的範例程式碼
您在名為 `samples` 的資料夾下應該已有本指南的 `mywebapi` 適用的範例程式碼 (如果沒有，請移至 https://github.com/Azure/dev-spaces 並選取 [複製或下載]，以從 GitHub 存放庫進行下載。)本節的程式碼位於 `samples/nodejs/getting-started/mywebapi`。

### <a name="run-mywebapi"></a>執行 *mywebapi*
1. 在個別的 VS Code 視窗中開啟資料夾 `mywebapi`。
1. 按 F5，並等候服務進行建置和部署。 當 VS Code 偵錯列出現時，表示已就緒。
1. 記下端點 URL，它看起來會像是 http://localhost:\<portnumber\>。 **提示：VS Code 狀態列會顯示可點按的 URL。** 容器可能看起來像在本機執行，但實際是在 Azure 的開發環境中執行的。 localhost 位址的原因是因為 `mywebapi` 並未定義任何公用端點，而只能從 Kubernetes 執行個體中存取。 為了方便您操作以及與本機電腦上的私人服務互動，Azure 開發人員空間會建立暫存的 SSH 通道，連到在 Azure 中執行的容器。
1. 當 `mywebapi` 就緒時，請開啟瀏覽器並進入 localhost 位址。 您應該會看到 `mywebapi` 服務的回應 (「來自 mywebapi 的 Hello」)。


### <a name="make-a-request-from-webfrontend-to-mywebapi"></a>從 webfrontend 發出對 mywebapi 的要求
我們現在要在 `webfrontend` 中撰寫對 `mywebapi` 發出要求的程式碼。
1. 切換至 `webfrontend` 的 VS Code 視窗。
1. 在 `server.js` 的最上方加入下列幾行程式碼：
    ```javascript
    var request = require('request');
    var propagateHeaders = require('./propagateHeaders');
    ```

3. 取代 `/api` 處理常式的程式碼。 在處理要求時，接著會呼叫 `mywebapi`，然後從這兩項服務傳回結果。

    ```javascript
    app.get('/api', function (req, res) {
        request({
            uri: 'http://mywebapi',
            headers: propagateHeaders.from(req) // propagate headers to outgoing requests
        }, function (error, response, body) {
            res.send('Hello from webfrontend and ' + body);
        });
    });
    ```

請留意系統如何使用 Kubernetes 的 DNS 服務探索將服務參照為 `http://mywebapi`。 **開發環境中的程式碼會以後續在生產環境中執行的相同方式執行**。

上述程式碼範例會使用名為 `propagateHeaders` 的協助程式模組。 此協助程式已在您執行 `azds prep` 時新增至程式碼資料夾。 `propagateHeaders.from()` 函式會將特定標頭從現有的 http.IncomingMessage 物件傳播到傳出要求的標頭物件中。 您稍後將了解這對小組的共同開發有何幫助。

### <a name="debug-across-multiple-services"></a>在多個服務間進行偵錯
1. 此時，`mywebapi` 仍應使用附加的偵錯工具執行中。 如果不是，在 `mywebapi` 專案中按 F5。
1. 在預設的 GET `/` 處理常式中設定中斷點。
1. 在 `webfrontend` 專案中，請將中斷點設定在傳送 GET 要求給 `http://mywebapi` 的前一刻。
1. 在 `webfrontend` 專案中按 F5。
1. 開啟 Web 應用程式，並在這兩項服務中逐步執行程式碼。 Web 應用程式應會顯示由兩項服務串連的訊息：「來自 webfrontend 的 Hello 和來自 mywebapi 的 Hello」。

做得好！ 現在，您已有每個容器可以個別開發和部署的多容器應用程式。

## <a name="learn-about-team-development"></a>了解小組開發

[!INCLUDE[](includes/team-development-1.md)]

現在，請了解它是如何運作的：
1. 請移至 `mywebapi` 的 VS Code 視窗，並對 GET `/` 處理常式進行程式碼編輯，例如：

    ```javascript
    app.get('/', function (req, res) {
        res.send('mywebapi now says something new');
    });
    ```

[!INCLUDE[](includes/team-development-2.md)]

[!INCLUDE[](includes/well-done.md)]

[!INCLUDE[](includes/clean-up.md)]




