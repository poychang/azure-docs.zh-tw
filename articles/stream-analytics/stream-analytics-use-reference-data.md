---
title: 使用參考資料在 Azure 串流分析中進行查閱
description: 本文說明如何在 Azure 串流分析作業的查詢設計中使用參考資料來查閱或相互關聯資料。
services: stream-analytics
author: jseb225
ms.author: jeanb
manager: kfile
ms.reviewer: jasonh
ms.service: stream-analytics
ms.topic: conceptual
ms.date: 04/25/2018
ms.openlocfilehash: 6dd96ee96201b05e4b272214983e955fcc5b9125
ms.sourcegitcommit: e2adef58c03b0a780173df2d988907b5cb809c82
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="using-reference-data-for-lookups-in-stream-analytics"></a>使用參考資料在串流分析中進行查閱
參考資料 (也稱為查詢資料表) 基本上是靜態或不常變更的有限資料集，可用來執行查閱或與資料流相互關聯。 若要使用 Azure 串流分析作業中的參考資料，您通常會在查詢中使用[參考資料聯結](https://msdn.microsoft.com/library/azure/dn949258.aspx)。 串流分析會使用 Azure Blob 儲存體做為參考資料的儲存層，且可和 Azure Data Factory 參考資料一起轉換和/或複製到來自 [任意數目的雲端架構和內部部署資料存放區](../data-factory/copy-activity-overview.md)的 Azure Blob 儲存體，做為參考資料。 參考資料會依 Blob 名稱中指定之日期/時間的遞增順序，以 Blob 序列的形式建立模型 (在輸入組態中定義)。 它「只」支援使用比序列中最後一個 Blob 指定之日期/時間「大」的日期/時間來新增到序列的結尾。

串流分析具有**每個 Bolb 100 MB 的限制**，但作業可以使用**路徑模式**屬性來存取多個參考 Blob。

支援壓縮無法用於參考資料。 

## <a name="configuring-reference-data"></a>設定參考資料
若要設定參考資料，您必須先建立屬於「 **參考資料**」類型的輸入。 下表說明您在建立參考資料輸入及其描述時必須提供的每個屬性：


<table>
<tbody>
<tr>
<td>屬性名稱</td>
<td>說明</td>
</tr>
<tr>
<td>輸入別名</td>
<td>在工作查詢中將用來參考這個輸入的易記名稱。</td>
</tr>
<tr>
<td>儲存體帳戶</td>
<td>您 blob 所在的儲存體帳戶名稱。 如果它與您的串流分析工作位於相同的訂用帳戶，您就可以從下拉式清單中選取它。</td>
</tr>
<tr>
<td>儲存體帳戶金鑰</td>
<td>與儲存體帳戶相關聯的密碼金鑰。 如果儲存體帳戶與您的「串流分析」工作位於相同的訂用帳戶，就會自動填入此資訊。</td>
</tr>
<tr>
<td>儲存體容器</td>
<td>容器提供邏輯分組給儲存在 Microsoft Azure Blob 服務中的 blob。 當您將 blob 上傳至 Blob 服務時，您必須指定該 blob 的容器。</td>
</tr>
<tr>
<td>路徑格式</td>
<td>用來在指定容器中找出 blob 的路徑。 在該路徑內，您也可以指定下列 2 個變數的一個或多個執行個體：<BR>{date}、{time}<BR>範例 1：products/{date}/{time}/product-list.csv<BR>範例 2：products/{date}/product-list.csv
</tr>
<tr>
<td>日期格式 [選用]</td>
<td>如果您已在指定的路徑模式內使用 {date}，則您可以從支援格式的下拉式清單中選取組織 Blob 所使用的日期格式。<BR>範例︰YYYY/MM/DD、MM/DD/YYYY 等。</td>
</tr>
<tr>
<td>時間格式 [選用]</td>
<td>如果您已在指定的路徑模式內使用 {time}，則您可以從支援格式的下拉式清單中選取組織 Blob 所使用的時間格式。<BR>範例︰HH、HH/mm 或 HH-mm</td>
</tr>
<tr>
<td>事件序列化格式</td>
<td>為了確定您的查詢運作如預期，串流分析需要知道您的內送資料流使用哪一種序列化格式。 參考資料的支援格式為 CSV 和 JSON。</td>
</tr>
<tr>
<td>編碼</td>
<td>UTF-8 是目前唯一支援的編碼格式</td>
</tr>
</tbody>
</table>

## <a name="generating-reference-data-on-a-schedule"></a>產生排程上的參考資料
如果您的參考資料是不常變更的資料集，可以啟用重新整理參考資料的支援，方法是使用 {date} 與 {time} 替代權杖指定輸入設定內的路徑模式。 串流分析會根據此路徑模式採用更新的參考資料定義。 例如，日期格式為 **“YYYY-MM-DD”** 且時間格式為 **“HH:mm”** 的模式 `sample/{date}/{time}/products.csv`，會指示串流分析在 UTC 時區 2015 年 4 月 16 日的下午 5:30 採用更新的 Blob `sample/2015-04-16/17-30/products.csv`。

> [!NOTE]
> 目前串流分析作業只有在機器時間朝向 Blob 名稱中編碼的時間時，才會尋求 Blob 重新整理。 例如，作業會儘速尋找 `sample/2015-04-16/17-30/products.csv` ，但不早於 UTC 時區 2015 年 4 月 16 日的下午 5:30。 它「決不會」尋找編碼時間早於最後一個探索到的 blob。
> 
> 例如 一旦作業找到 Blob `sample/2015-04-16/17-30/products.csv`，就會忽略任何編碼日期早於 2015 年 4 月 16 日下午 5:30 的檔案，所以如果在相同的容器中建立晚到的 `sample/2015-04-16/17-25/products.csv` Blob，作業便不會使用它。
> 
> 同樣地，如果 `sample/2015-04-16/17-30/products.csv` 只會在 2015 年 4 月 16 日下午 10:03 產生，但容器中沒有日期較早的 Blob，則作業會從 2015 年 4 月 16 日下午 10:03 開始使用這個檔案，並在那之前使用先前的參考資料。
> 
> 此情況有例外，就是當工作需要回到之前來重新處理資料，或當工作第一次啟動的時候。 啟動時，作業會尋找在指定作業啟動時間之前產生的最新 Blob。 這是為了確保在作業啟動時，會有 **非空白** 的參考資料集。 如果無法找到，作業會顯示下列診斷： `Initializing input without a valid reference data blob for UTC time <start time>`。
> 
> 

[Azure Data Factory](https://azure.microsoft.com/documentation/services/data-factory/) 可用來針對串流分析更新參考資料定義時所需的已更新 Blob，協調建立這些 Blob 的工作。 Data Factory 是雲端架構資料整合服務，用來協調以及自動移動和轉換資料。 Data Factory 可 [連線到大量雲端式和內部部署的資料存放區](../data-factory/copy-activity-overview.md) ，也可根據您指定的定期排程輕鬆移動資料。 如需詳細資訊及逐步解說指南，瞭解該如何設定 Data Factory 管線才能產生依預先定義排程重新整理的「串流分析」參考資料，請查看此 [GitHub 範例](https://github.com/Azure/Azure-DataFactory/tree/master/Samples/ReferenceDataRefreshForASAJobs)。

## <a name="tips-on-refreshing-your-reference-data"></a>重新整理參考資料的秘訣
1. 覆寫參考資料 Blob 並不會造成「串流分析」重新載入 Blob，並且在某些情況下，它可能會造成工作失敗。 若要變更參考資料，建議的方式是藉由使用工作輸入中定義的相同容器和路徑格式，並使用比序列中最後一個 Blob 指定之日期/時間「大」  的日期/時間，加入新的 Blob。
2. 參考資料 Blob **不是**依 Blob 的「上次修改日期」時間排序，而是只依 Blob 名稱中使用 {date} 和 {time} 替代來指定的時間和日期排序。
3. 若要避免必須列出大量 Blob，請考慮刪除再也不會進行處理且非常舊的 Blob。 請注意，ASA 在某些案例 (例如重新啟動) 中可能需要重新處理很少數舊的 Blob。

## <a name="next-steps"></a>後續步驟
> [!div class="nextstepaction"]
> [快速入門：使用 Azure 入口網站建立串流分析作業](stream-analytics-quick-create-portal.md)

<!--Link references-->
[stream.analytics.developer.guide]: ../stream-analytics-developer-guide.md
[stream.analytics.scale.jobs]: stream-analytics-scale-jobs.md
[stream.analytics.introduction]: stream-analytics-real-time-fraud-detection.md
[stream.analytics.get.started]: stream-analytics-get-started.md
[stream.analytics.query.language.reference]: http://go.microsoft.com/fwlink/?LinkID=513299
[stream.analytics.rest.api.reference]: http://go.microsoft.com/fwlink/?LinkId=517301
