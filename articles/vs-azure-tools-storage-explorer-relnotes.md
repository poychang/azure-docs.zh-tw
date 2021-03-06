---
title: Microsoft Azure 儲存體總管版本資訊
description: Microsoft Azure 儲存體總管版本資訊
services: storage
documentationcenter: na
author: cawa
manager: paulyuk
editor: ''
ms.assetid: ''
ms.service: storage
ms.devlang: multiple
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/31/2017
ms.author: cawa
ms.openlocfilehash: 7e290b3bbe3fa70522533f23febe587fbb873e35
ms.sourcegitcommit: ca05dd10784c0651da12c4d58fb9ad40fdcd9b10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32779000"
---
# <a name="microsoft-azure-storage-explorer-release-notes"></a>Microsoft Azure 儲存體總管版本資訊

本文包含 Microsoft Azure 儲存體總管 1.0.0 版和先前版本的版本資訊。

[Microsoft Azure 儲存體總管](./vs-azure-tools-storage-manage-with-storage-explorer.md) 是一個獨立應用程式，可讓您在 Windows、macOS 和 Linux 上輕鬆使用 Azure 儲存體資料。

## <a name="version-100"></a>1.0.0 版
04/16/2018

### <a name="download-azure-storage-explorer-100"></a>下載 Azure 儲存體總管 1.0.0
- [適用於 Windows 的 Azure 儲存體總管 1.0.0](https://go.microsoft.com/fwlink/?LinkId=708343)
- [適用於 Mac 的 Azure 儲存體總管 1.0.0](https://go.microsoft.com/fwlink/?LinkId=708342)
- [適用於 Linux 的 Azure 儲存體總管 1.0.0](https://go.microsoft.com/fwlink/?LinkId=722418)

### <a name="new"></a>新增
* 增強式驗證，可讓儲存體總管使用與 Visual Studio 2017 相同的帳戶存放區。 若要使用這項功能，您必須重新登入您的帳戶，並重新設定已篩選的訂用帳戶。
* 對於 AAD 所支援的 Azure Stack 帳戶，如果已啟用 [目標 Azure Stack]，則儲存體總管現在會擷取 Azure Stack 訂用帳戶。 您不再需要建立自訂登入環境。
* 已新增數個捷徑，以便進行更快速的導覽。 這些包括切換各種面板並在編輯器之間移動。 如需詳細資訊，請參閱 [檢視] 功能表。
* GitHub 上現在提供儲存體總管意見反應。 按一下左下方的 [意見反應] 按鈕或移至 [https://github.com/Microsoft/AzureStorageExplorer/issues](https://github.com/Microsoft/AzureStorageExplorer/issues)，即可抵達我們的問題頁面。 請隨意提出建議、回報問題、詢問問題，或留下任何其他形式的意見反應。
* 如果您遇到 SSL 憑證問題，而且找不到引起問題的憑證，現在可以使用 `--ignore-certificate-errors` 旗標從命令列啟動儲存體總管。 使用這個旗標啟動時，儲存體總管會忽略 SSL 憑證錯誤。
* Blob 和檔案項目的內容功能表中現在有 [下載] 選項。
* 已改善協助工具和畫面讀取器支援。 如果您需依賴協助工具功能，請參閱[協助工具文件](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-accessibility)以取得詳細資訊。
* 儲存體總管現在使用 Electron 1.8.3

### <a name="breaking-changes"></a>重大變更
* 儲存體總管已切換到新的驗證程式庫。 切換到此程式庫時，您必須重新登入您的帳戶，並重新設定已篩選的訂用帳戶。
* 用來加密敏感性資料的方法已變更。 這可能會導致必須重新新增部分的快速存取項目及/或必須重新連結部分已連結的資源。

### <a name="fixes"></a>修正
* 位於 Proxy 後方的某些使用者會有因為「無法解析」錯誤訊息而中斷的群組 blob 上傳或下載。 已修正此問題。
* 如果使用直接連結時需要登入，按一下 [登入] 提示就會顯示空白的對話方塊。 已修正此問題。
* 在 Linux 上，如果儲存體總管因為 GPU 程序損毀而無法啟動，您現在會獲知損毀、得知要使用 '--disable-gpu' 參數，而儲存體總管會接著在已啟用此參數的情況下自動重新啟動。
* 在 [存取原則] 對話方塊中難以識別無效的存取原則。 無效的存取原則識別碼現在會以紅色標示，讓您更容易辨識。
* 活動記錄有時在活動的不同部分之間會有大量空白區域。 已修正此問題。
* 在表格查詢編輯器中，如果您讓時間戳記子句處於無效狀態，然後嘗試修改另一個子句，則編輯器會凍結。 如果偵測到另一個子句變更，編輯器現在會將時間戳記子句還原到其前次有效的狀態。
* 如果您在樹狀檢視中輸入搜尋查詢時暫停，則搜尋會開始並且從文字方塊竊取焦點。 現在，您必須按 'Enter' 鍵，或按一下 [開始搜尋] 按鈕，明確地開始搜尋。
* 在檔案共用中的檔案上按一下滑鼠右鍵時，有時會停用 [取得共用存取簽章] 命令。 已修正此問題。
* 如果在搜尋期間已篩選掉具有焦點的資源樹狀節點，您就無法用 Tab 鍵移入資源樹狀結構並使用方向鍵來瀏覽資源樹狀結構。 現在，如果取得焦點的資源樹狀節點隱藏起來，則資源樹狀結構中的第一個節點會自動取得焦點。
* 在編輯器工具列中有時可看到額外的分隔符號。 已修正此問題。
* 階層連結文字方塊有時會溢位。 已修正此問題。
* 一次上傳許多檔案時，有時會經常重新整理 Blob 和檔案共用編輯器。 已修正此問題。
* 在檔案共用快照集管理檢視中，[資料夾統計資料] 功能沒有任何用途。 它現在已停用。
* 在 Linux 上，[檔案] 功能表不會出現。 已修正此問題。
* 將資料夾上傳至檔案共用時，預設只會上傳資料夾的內容。 現在，預設行為是將資料夾的內容上傳到檔案共用中的相符資料夾。
* 數個對話方塊中的按鈕順序已反轉。 已修正此問題。
* 各種安全性相關修正程式。

### <a name="known-issues"></a>已知問題
* 在少數情況下，樹狀焦點可能會固定在快速存取上。 若要取消固定焦點，您可以 [全部重新整理]。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用此處所述的取消篩選器因應措施。 
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：

```
./StorageExplorer.exe --disable-gpu
```

* 對於 Linux 使用者，您必須安裝 [.NET Core 2.0](https://docs.microsoft.com/en-us/dotnet/core/linux-prerequisites?tabs=netcore2x)。
* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="previous-releases"></a>舊版

* [0.9.6 版](#version-096)
* [0.9.5 版](#version-095)
* [0.9.4 和 0.9.3 版](#version-094-and-093)
* [0.9.2 版](#version-092)
* [0.9.1 和 0.9.0 版](#version-091-and-090)
* [0.8.16 版](#version-0816)
* [版本 0.8.14](#version-0814)
* [0.8.13 版](#version-0813)
* [0.8.12、0.8.11 和 0.8.10 版](#version-0812-and-0811-and-0810)
* [0.8.9 和 0.8.8 版](#version-089-and-088)
* [0.8.7 版](#version-087)
* [0.8.6 版](#version-086)
* [0.8.5 版](#version-085)
* [0.8.4 版](#version-084)
* [0.8.3 版](#version-083)
* [0.8.2 版](#version-082)
* [0.8.0 版](#version-080)
* [0.7.20160509.0 版](#version-07201605090)
* [0.7.20160325.0 版](#version-07201603250)
* [0.7.20160129.1 版](#version-07201601291)
* [0.7.20160105.0 版](#version-07201601050)
* [0.7.20151116.0 版](#version-07201511160)

## <a name="version-096"></a>0.9.6 版
02/28/2018

### <a name="download-azure-storage-explorer-096-preview"></a>下載 Azure 儲存體總管 0.9.6 (預覽)
- [適用於 Windows 的 Azure 儲存體總管 0.9.6 (預覽)](https://go.microsoft.com/fwlink/?LinkId=708343)
- [適用於 Mac 的 Azure 儲存體總管 0.9.6 (預覽)](https://go.microsoft.com/fwlink/?LinkId=708342)
- [適用於 Linux 的 Azure 儲存體總管 0.9.6 (預覽)](https://go.microsoft.com/fwlink/?LinkId=722418)

### <a name="fixes"></a>修正
* 導致預期的 blob/檔案無法列在編輯器中的問題。 已修正此問題。
* 導致快照集檢視之間的切換無法正確顯示項目的問題。 已修正此問題。

### <a name="known-issues"></a>已知問題
* 儲存體總管不支援 ADFS 帳戶。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用[此處](https://github.com/Azure/azure-storage-node/issues/317)所述的取消篩選器因應措施。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：

```
./StorageExplorer.exe --disable-gpu
```

* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="version-095"></a>0.9.5 版
02/06/2018

### <a name="download-azure-storage-explorer-095-preview"></a>下載 Azure 儲存體總管 0.9.5 (預覽)
- [適用於 Windows 的 Azure 儲存體總管 0.9.5 (預覽)](https://go.microsoft.com/fwlink/?LinkId=708343)
- [適用於 Mac 的 Azure 儲存體總管 0.9.5 (預覽)](https://go.microsoft.com/fwlink/?LinkId=708342)
- [適用於 Linux 的 Azure 儲存體總管 0.9.5 (預覽)](https://go.microsoft.com/fwlink/?LinkId=722418)

### <a name="new"></a>新增

* 檔案共用快照集的支援：
    * 建立和管理檔案共用的快照集。
    * 在瀏覽時輕易地在檔案共用快照集之間切換檢視。
    * 還原檔案的先前版本。
* Azure Data Lake Store 的預覽支援：
    * 連線到跨多個帳戶的 ADLS 資源。
    * 使用 ADL URI 連線並共用 ADLS 資源。
    * 以遞迴方式執行基本的檔案/資料夾作業。
    * 將個別資料夾釘選到快速存取。
    * 顯示資料夾統計資料。

### <a name="fixes"></a>修正
* 啟動效能改進。
* 各種 Bug 修正。

### <a name="known-issues"></a>已知問題
* 儲存體總管不支援 ADFS 帳戶。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用此處所述的取消篩選器因應措施。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：

```
./StorageExplorer.exe --disable-gpu
```

* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="version-094-and-093"></a>0.9.4 和 0.9.3 版
01/21/2018

### <a name="download-azure-storage-explorer-094-preview"></a>下載 Azure 儲存體總管 0.9.4 (預覽)
* [下載適用於 Windows 的 Azure 儲存體總管 0.9.4 (預覽)](https://go.microsoft.com/fwlink/?LinkId=809306)
* [下載適用於 Mac 的 Azure 儲存體總管 0.9.4 (預覽)](https://go.microsoft.com/fwlink/?LinkId=809307)
* [下載適用於 Linux 的 Azure 儲存體總管 0.9.4 (預覽)](https://go.microsoft.com/fwlink/?LinkId=809308)

### <a name="new"></a>新增
* 在下列情況下，將會重新使用您的現有儲存體總管視窗：
    * 開啟儲存體總管中所產生的直接連結。
    * 從入口網站開啟儲存體總管。
    * 從 Azure 儲存體 VS Code 延伸模組 (即將推出) 開啟儲存體總管。
* 已新增從儲存體總管內開啟新儲存體總管視窗的功能。
    * 針對 Windows，在 [檔案] 功能表下方以及工作列的操作功能表中會有 [開新視窗] 選項。
    * 針對 Mac，[應用程式功能表] 下方會有 [開新視窗] 選項。

### <a name="fixes"></a>修正
* 已修正安全性問題。 請盡早升級至 0.9.4 版。
* 舊的活動不適合進行清理。 這會影響長期執行作業的效能。 現在，會將它們正確地清除。
* 涉及大量檔案和目錄的動作偶而會導致儲存體總管凍結。 現在會對 Azure for File Shares 要求進行節流控制，以限制系統資源使用。

### <a name="known-issues"></a>已知問題
* 儲存體總管不支援 ADFS 帳戶。
* 用於「檢視總管」及「檢視帳戶管理」的快速鍵應該分別是 Ctrl/Cmd+Shift+E 和 Ctrl/Cmd+Shift+A。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用此處所述的取消篩選器因應措施。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：
```
./StorageExplorer --disable-gpu
```
* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="version-092"></a>0.9.2 版
11/01/2017

### <a name="hotfixes"></a>Hotfix
* 端視當地時區而定，編輯資料表實體的 Edm.DateTime 值時，可能出現未預期的資料變更。 編輯器目前使用純文字方塊，對於 Edm.DateTime 值提供精確、一致的控制。
* 無法在連接到名稱和金鑰時開始上傳/下載一組 Blob。 已修正此問題。
* 在過去，如果已選取一或多個帳戶的訂用帳戶，儲存體總管只會提示您重新驗證過期的帳戶。 而現在，即使完全篩選排除帳戶，儲存體總管也會提示您。
* Azure 美國政府的端點網域不正確。 已修正此問題。
* [管理帳戶] 面板的 [套用] 按鈕有時不容易按。 這應該不會再發生。

### <a name="new"></a>新增
* Azure Cosmos DB 預覽支援：
    * [線上文件](./cosmos-db/storage-explorer.md)
    * 建立資料庫和集合
    * 操作資料
    * 查詢、建立或刪除文件
    * 更新預存程序、使用者定義函式或觸發程序
    * 使用連接字串來連接和管理您的資料庫
* 改善上傳/下載許多小 Blob 的效能。
* 新增 Blob 上傳群組或 Blob 下載群組發生失敗時的「全部重試」動作。
* 如果儲存體總管偵測到您的網路連線已遺失，現在將在 Blob 上傳/下載期間暫停反覆項目。 然後在網路連線重新建立後，您可以繼續反覆項目。
* 新增透過捷徑功能表「全部關閉」、「關閉其他」和「關閉」索引標籤的能力。
* 儲存體總管現在會使用原生對話方塊和原生捷徑功能表。
* 儲存體總管現在更容易存取。 改善項目包括：
    * 改善的螢幕讀取器支援，Windows 上的 NVDA，以及 Mac 上的 VoiceOver
    * 改良的高對比佈景主題
    * 修正鍵盤定位停駐點和鍵盤焦點

### <a name="fixes"></a>修正
* 如果您嘗試使用無效的 Windows 檔案名稱開啟或下載 Blob，作業會失敗。 儲存體總管現在會偵測 Blob 名稱是否無效，並詢問您是否要加以編碼或略過該 Blob。 儲存體總管也會偵測檔案名稱是否已經過編碼，並詢問您是否要在上傳之前將它解碼。
* Blob 上傳期間，目標 Blob 容器的編輯器會有時不正確地重新整理。 已修正此問題。
* 數種形式的連接字串和 SAS URI 支援已回歸。 我們已經處理所有已知的問題，但如果您遇到其他問題，請傳送意見反應。
* 0.9.0 中有些使用者的更新通知已中斷。 已修正此問題，以及對於受此錯誤影響的使用者，可以在[這裡](https://azure.microsoft.com/features/storage-explorer/)手動下載最新版的儲存體總管。

### <a name="known-issues"></a>已知問題
* 儲存體總管不支援 ADFS 帳戶。
* 用於「檢視總管」及「檢視帳戶管理」的快速鍵應該分別是 Ctrl/Cmd+Shift+E 和 Ctrl/Cmd+Shift+A。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用此處所述的取消篩選器因應措施。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：
```
./StorageExplorer --disable-gpu
```
* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="version-091-and-090"></a>0.9.1 和 0.9.0 版
10/20/2017
### <a name="new"></a>新增
* Azure Cosmos DB 預覽支援：
    * [線上文件](./cosmos-db/storage-explorer.md)
    * 建立資料庫和集合
    * 操作資料
    * 查詢、建立或刪除文件
    * 更新預存程序、使用者定義函式或觸發程序
    * 使用連接字串來連接和管理您的資料庫
* 改善上傳/下載許多小 Blob 的效能。
* 新增 Blob 上傳群組或 Blob 下載群組發生失敗時的「全部重試」動作。
* 如果儲存體總管偵測到您的網路連線已遺失，現在將在 Blob 上傳/下載期間暫停反覆項目。 然後在網路連線重新建立後，您可以繼續反覆項目。
* 新增透過捷徑功能表「全部關閉」、「關閉其他」和「關閉」索引標籤的能力。
* 儲存體總管現在會使用原生對話方塊和原生捷徑功能表。
* 儲存體總管現在更容易存取。 改善項目包括：
    * 改善的螢幕讀取器支援，Windows 上的 NVDA，以及 Mac 上的 VoiceOver
    * 改良的高對比佈景主題
    * 修正鍵盤定位停駐點和鍵盤焦點

### <a name="fixes"></a>修正
* 如果您嘗試使用無效的 Windows 檔案名稱開啟或下載 Blob，作業會失敗。 儲存體總管現在會偵測 Blob 名稱是否無效，並詢問您是否要加以編碼或略過該 Blob。 儲存體總管也會偵測檔案名稱是否已經過編碼，並詢問您是否要在上傳之前將它解碼。
* Blob 上傳期間，目標 Blob 容器的編輯器會有時不正確地重新整理。 已修正此問題。
* 數種形式的連接字串和 SAS URI 支援已回歸。 我們已經處理所有已知的問題，但如果您遇到其他問題，請傳送意見反應。
* 0.9.0 中有些使用者的更新通知已中斷。 已修正此問題，以及對於受此錯誤影響的使用者，可以在[這裡](https://azure.microsoft.com/features/storage-explorer/)手動下載最新版的儲存體總管

### <a name="known-issues"></a>已知問題
* 儲存體總管不支援 ADFS 帳戶。
* 用於「檢視總管」及「檢視帳戶管理」的快速鍵應該分別是 Ctrl/Cmd+Shift+E 和 Ctrl/Cmd+Shift+A。
* 當目標為 Azure Stack，以附加 Blob 方式上傳特定檔案會失敗。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 這是因為我們使用此處所述的取消篩選器因應措施。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 儲存體總管使用的 Electron 殼層具有一些 GPU (圖形處理單元) 硬體加速的問題。 如果儲存體總管顯示空白 (空的) 主視窗，您可以嘗試從命令列啟動儲存體總管並透過新增 `--disable-gpu` 切換停用 GPU 加速：
```
./StorageExplorer --disable-gpu
```
* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

## <a name="version-0816"></a>0.8.16 版
8/21/2017

### <a name="new"></a>新增
* 您開啟 blob 時，如果偵測到變更，儲存體總管將提示您上傳已下載的檔案
* 增強的 Azure Stack 登入體驗
* 改善同時上傳/下載許多小檔案的效能


### <a name="fixes"></a>修正
* 對於某些 blob 類型，在上傳衝突時選擇取代有時會導致重新啟動上傳。
* 在 0.8.15 版中，上傳有時會延滯在 99%。
* 將檔案上傳到檔案共用時，如果您選擇上傳到尚未存在的目錄，上傳會失敗。
* 儲存體總管未正確產生共用存取簽章和資料表查詢的時間戳記。


### <a name="known-issues"></a>已知問題
* 目前無法使用名稱和金鑰連接字串。 這將在下一版中予以修正。 在此之前，您可以使用名稱和金鑰附加。
* 如果您嘗試開啟無效 Windows 檔案名稱的檔案，下載會導致找不到檔案的錯誤。
* 按一下工作上的 [取消] 之後，該工作可能需要經過一段時間才會取消。 此為 Microsoft Azure 儲存體節點程式庫的限制。
* 完成 Blob 上傳之後，系統會重新整理起始該上傳的索引標籤。 這和先前的行為不同，且會導致您返回所在容器的根。
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* 使用 Ubuntu 14.04 的使用者必須確定 GCC 編譯器集合是最新版本，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

* 使用 Ubuntu 17.04 的使用者必須安裝 GConf，這可以透過執行下列命令並重新啟動電腦來完成：

    ```
    sudo apt-get install libgconf-2-4
    ```

### <a name="version-0814"></a>版本 0.8.14
06/22/2017

### <a name="new"></a>新增

* 將 Electron 版本更新至 1.7.2 以利用數個重要安全性更新
* 現已可從 [說明] 功能表快速存取線上疑難排解指南
* 儲存體總管疑難排解[指南][2]
* 連線至 Azure Stack 訂用帳戶的[指示][3]

### <a name="known-issues"></a>已知問題

* 在 Linux 上，刪除資料夾確認對話方塊上的按鈕不會註冊滑鼠點選。 因應措施為使用 Enter 鍵
* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* Ubuntu 14.04 安裝需要更新或升級 gcc 版本，升級步驟如下：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```

### <a name="version-0813"></a>0.8.13 版
05/12/2017

#### <a name="new"></a>新增

* 儲存體總管疑難排解[指南][2]
* 連線至 Azure Stack 訂用帳戶的[指示][3]

#### <a name="fixes"></a>修正

* 已修正︰檔案上傳先前很容易造成記憶體不足錯誤
* 已修正：您現在可以使用 PIN/智慧卡登入
* 已修正：[在入口網站中開啟] 現已可以搭配 Azure 中國、Azure 德國、Azure 美國政府及 Azure Stack 運作
* 已修正：先前將資料夾上傳至 Blob 容器時，有時候會發生「作業不合法」錯誤
* 已修正：先前在管理快照集時會停用 [全選]
* 已修正：在檢視基底 Blob 的快照集屬性後，可能會覆寫該基底 Blob 的中繼資料

#### <a name="known-issues"></a>已知問題

* 如果您選擇錯誤的 PIN/智慧卡憑證，則必須重新啟動，才能使儲存體總管忘記該決定
* 在放大或縮小期間，縮放層級可能會暫時重設為預設層級
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* Ubuntu 14.04 安裝需要更新或升級 gcc 版本，升級步驟如下：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```


### <a name="version-0812-and-0811-and-0810"></a>0.8.12、0.8.11 和 0.8.10 版
04/07/2017

#### <a name="new"></a>新增

* 儲存體總管現在會在您從更新通知安裝更新之後自動關閉
* 就地快速存取能針對您經常存取的資源提供加強的使用體驗
* 在 Blob 容器編輯器中，您現在可以查看租用 Blob 所屬的虛擬機器
* 現已能摺疊左側面板
* 探索現在會和下載同時執行
* 使用 Blob 容器、檔案共用及資料表編輯器中的 [統計資料] 來查看您資源或選取項目的大小
* 現已能登入以 Azure Active Directory (AAD) 為基礎的 Azure Stack 帳戶。
* 現已能將大小超過 32MB 的封存檔案上傳至進階儲存體帳戶
* 改善協助工具支援
* 現已能移至 [編輯] -&gt; [SSL 憑證] -&gt; [匯入憑證] 來新增受信任的 Base-64 編碼 X.509 SSL 憑證

#### <a name="fixes"></a>修正

* 已修正：先前在重新整理帳戶的認證之後，樹狀檢視有時候不會自動重新整理
* 已修正：先前針對模擬器佇列和資料表產生 SAS 會導致無效的 URL
* 已修正：進階儲存體帳戶現在可以在啟用 Proxy 時展開
* 已修正：先前在選取 1 或 0 個帳戶的情況下，帳戶管理頁面的 [套用] 按鈕會無法運作
* 已修正：上傳需要衝突解決的 Blob 可能會失敗 - 已在 0.8.11 中修正
* 已修正：傳送意見反應的功能在 0.8.11 中無法運作 - 已在 0.8.12 中修正

#### <a name="known-issues"></a>已知問題

* 升級至 0.8.10 之後，您必須重新整理所有認證。
* 在放大或縮小期間，縮放層級可能會暫時重設為預設層級。
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤。
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶。
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留。
* 雖然 Azure Stack 目前並不支援檔案共用，檔案共用節點仍然會出現在附加的 Azure Stack 儲存體帳戶之下。
* Ubuntu 14.04 安裝需要更新或升級 gcc 版本，升級步驟如下：

    ```
    sudo add-apt-repository ppa:ubuntu-toolchain-r/test
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get dist-upgrade
    ```


### <a name="version-089-and-088"></a>0.8.9 和 0.8.8 版
02/23/2017

>[!VIDEO https://www.youtube.com/embed/R6gonK3cYAc?ecver=1]

>[!VIDEO https://www.youtube.com/embed/SrRPCm94mfE?ecver=1]


#### <a name="new"></a>新增

* 儲存體總管 0.8.9 將會自動下載最新版本的更新。
* Hotfix：先前使用由入口網站所產生的 SAS URI 來附加儲存體帳戶將會導致錯誤。
* 現已能針對 Blob 快照集進行建立、管理及升階。
* 現已能登入 Azure 中國、Azure 德國及 Azure 美國政府帳戶。
* 現已能變更縮放層級。 使用 [檢視] 功能表中的選項來放大、縮小及重設縮放。
* Blob 和檔案的使用者中繼資料現已支援 Unicode 字元。
* 協助工具改進。
* 可從更新通知中檢視下個版本的版本資訊。 您也可以從 [說明] 功能表檢視目前版本的資訊。

#### <a name="fixes"></a>修正

* 已修正：版本號碼現在已會正確顯示於 Windows 上的 [控制台] 中
* 已修正：搜尋已不再具有 50,000 個節點的限制
* 已修正：在目的地目錄不存在的情況下，上傳至檔案共用會卡在無限的迴圈之中
* 已修正：改善較長上傳及下載的穩定性

#### <a name="known-issues"></a>已知問題

* 在放大或縮小期間，縮放層級可能會暫時重設為預設層級。
* 快速存取僅適用於以訂用帳戶為基礎的項目。 此版本不支援透過金鑰或 SAS 權杖附加的本機資源或資源。
* 視您擁有的資源數量而定，快速存取可能需要幾秒鐘才能瀏覽至目標資源。
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤。

12/16/2016
### <a name="version-087"></a>0.8.7 版

>[!VIDEO https://www.youtube.com/embed/Me4Y4jxoer8?ecver=1]

#### <a name="new"></a>新增

* 在剛開始更新、下載或複製工作階段時，您可以在 [活動] 視窗中選擇如何解決衝突
* 將游標暫留在索引標籤上可以看到儲存體資源的完整路徑
* 按一下索引標籤之後，它會與左側導覽窗格中的位置同步

#### <a name="fixes"></a>修正

* 已修正：儲存體總管在 Mac 上現已是受信任的應用程式
* 已修正：再次支援 Ubuntu 14.04
* 已修正：「新增帳戶」UI 在載入訂用帳戶時有時會閃爍
* 已修正：左側導覽窗格中有時不會列出所有儲存體資源
* 已修正：[動作] 窗格有時會顯示空白動作
* 已修正：現已會保留上次工作階段關閉時的視窗大小
* 已修正：可以使用內容選單針對相同資源開啟多個索引標籤

#### <a name="known-issues"></a>已知問題

* 快速存取僅適用於以訂用帳戶為基礎的項目。 此版本不支援透過金鑰或 SAS 權杖附加的本機資源或資源
* 視您擁有的資源數量而定，快速存取可能需要幾秒鐘才能瀏覽至目標資源
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤
* 搜尋功能在處理超過大約 50,000 個節點的搜尋作業之後，可能會影響效能或造成未處理的例外狀況
* 在 macOS 上第一次使用儲存體總管時，系統可能會多次要求使用者的許可，以存取鑰匙圈。 建議您選取 [一律允許] 來使系統不會再次顯示該提示

11/18/2016
### <a name="version-086"></a>0.8.6 版

#### <a name="new"></a>新增

* 現已可將常用的服務釘選到 Quick Access 以便瀏覽
* 現已可在多個索引標籤開啟多個編輯器。 按一下以開啟暫時索引標籤；按兩下以開啟永久索引標籤。您也可以按一下暫時索引標籤來將它設為永久索引標籤
* 我們已大幅改善上傳及下載的效能和穩定性，尤其是在高效能機器上處理大型檔案的情況
* 現可在 Blob 容器內建立空白的「虛擬」資料夾
* 我們已重新推出範圍搜尋，並搭配全新增強的子字串搜尋，因此您現在將會有兩種搜尋的選項：
    * 全域搜尋：請直接在搜尋文字方塊中輸入搜尋字詞
    * 範圍搜尋：按一下位於節點旁邊的放大鏡圖示，然後將搜尋字詞新增至路徑末端，或是以滑鼠右鍵按一下並選取 [從這裡搜尋]
* 已新增多種佈景主題：淺色 (預設)、深色、黑色高對比和白色高對比。 移至 [編輯] -&gt; [佈景主題] 來變更佈景主題喜好設定
* 您可以修改 Blob 和檔案的屬性
* 我們現已支援編碼 (base64) 及未編碼的佇列訊息
* 若使用 Linux，必須為 64 位元作業系統。 針對此版本，我們僅支援 64 位元的 Ubuntu 16.04.1 LTS
* 已更新我們的標誌！

#### <a name="fixes"></a>修正

* 已修正︰畫面凍結的問題
* 已修正：增強安全性
* 已修正：有時候可能會出現重複的附加帳戶
* 已修正：具有未定義內容類型的 Blob 可能會產生例外狀況
* 已修正：先前並無法在空白資料表上開啟 [查詢] 面板
* 已修正：數個搜尋功能中的錯誤
* 已修正：按一下 [載入更多] 時所載入資源的數目已從 50 提升至 100
* 已修正：首次執行時，如果已登入某個帳戶，現在預設會選取該帳戶的所有定用帳戶

#### <a name="known-issues"></a>已知問題

* 此版本的儲存體總管並無法在 Ubuntu 14.04 上執行
* 若要針對相同資源開啟多個索引標籤，請不要持續點選相同的資源。 請先按一下其他資源，然後再返回按一下原始資源，以在另一個索引標籤上再次開啟它
* 快速存取僅適用於以訂用帳戶為基礎的項目。 此版本不支援透過金鑰或 SAS 權杖附加的本機資源或資源
* 視您擁有的資源數量而定，快速存取可能需要幾秒鐘才能瀏覽至目標資源
* 同時上傳超過 3 個 Blob 或檔案群組可能會造成錯誤
* 搜尋功能在處理超過大約 50,000 個節點的搜尋作業之後，可能會影響效能或造成未處理的例外狀況

10/03/2016
### <a name="version-085"></a>0.8.5 版

#### <a name="new"></a>新增

* 現已能使用由入口網站所產生的 SAS 金鑰來附加儲存體帳戶和資源

#### <a name="fixes"></a>修正

* 已修正：先前在搜尋期間的競爭條件有時候會使節點無法展開
* 已修正：在以帳戶名稱和金鑰連線至儲存體帳戶時，[使用 HTTP] 會無法運作
* 已修正：SAS 金鑰 (特別是由入口網站所產生的 SAS 金鑰) 會傳回「結尾斜線」錯誤
* 已修正：資料表匯入問題
    * 資料分割索引鍵和列索引鍵有時候會反轉
    * 無法讀取 "null" 資料分割索引鍵

#### <a name="known-issues"></a>已知問題

* 搜尋功能在處理超過大約 50,000 個節點的搜尋作業之後，可能會影響效能
* Azure Stack 目前不支援 [檔案]，因此嘗試展開 [檔案] 將會顯示錯誤

09/12/2016
### <a name="version-084"></a>0.8.4 版

>[!VIDEO https://www.youtube.com/embed/cr5tOGyGrIQ?ecver=1]

#### <a name="new"></a>新增

* 產生針對儲存體帳戶、容器、佇列、資料表或檔案共用的直接連結，以便共用及輕鬆存取資源 - Windows 與 Mac 作業系統支援
* 從搜尋方塊搜尋 Blob 容器、資料表、佇列、檔案共用或儲存體帳戶
* 現已能在資料表查詢建立器中對子句進行群組
* 從 SAS 附加帳戶及容器內對 Blob 容器、檔案共用、資料表、Blob、Blob 資料夾、檔案及目錄進行重新命名和複製/貼上
* 對 Blob 容器和檔案共用進行重新命名和複製時，現在會保留屬性和中繼資料

#### <a name="fixes"></a>修正

* 已修正：無法編輯包含布林值或二進位屬性的資料表實體

#### <a name="known-issues"></a>已知問題

* 搜尋功能在處理超過大約 50,000 個節點的搜尋作業之後，可能會影響效能

08/03/2016
### <a name="version-083"></a>0.8.3 版

>[!VIDEO https://www.youtube.com/embed/HeGW-jkSd9Y?ecver=1]

#### <a name="new"></a>新增

* 對容器、資料表、檔案共用進行重新命名
* 改善查詢建立器體驗
* 能夠儲存及載入查詢
* 針對儲存體帳戶或容器、佇列、資料表或檔案共用的直接連結，可用來進行共用及輕鬆存取資源 (僅限 Windows，macOS 支援即將推出！)
* 能夠管理及設定 CORS 規則

#### <a name="fixes"></a>修正

* 已修正：Microsoft 帳戶每 8 至 12 小時便需要重新驗證

#### <a name="known-issues"></a>已知問題

* UI 有時候會呈現為凍結的情況，將視窗最大化能協助解決此問題
* macOS 安裝可能會需要較高的權限
* 帳戶設定面板可能會提示您需要重新輸入認證以篩選訂用帳戶
* 對檔案共用、Blob 容器及資料表進行重新命名，並不會保留中繼資料或容器上的其他屬性，例如檔案共用配額、公用存取層級或存取原則
* 重新命名 Blob (個別執行或在重新命名的 Blob 容器內) 不會保留快照集。 Blob、檔案和實體的所有其他屬性和中繼資料都會在重新命名期間保留
* 在 SAS 附加帳戶內並無法對資源進行複製或重新命名

07/07/2016
### <a name="version-082"></a>0.8.2 版

>[!VIDEO https://www.youtube.com/embed/nYgKbRUNYZA?ecver=1]

#### <a name="new"></a>新增

* 儲存體帳戶是依訂用帳戶進行群組。透過金鑰或 SAS 附加的開發儲存體和資源會顯示在 (本機和附加的) 節點之下
* 在 [Azure 帳戶設定] 面板中登出帳戶
* 設定 Proxy 設定以啟用並管理登入
* 建立和中斷 Blob 租用
* 按一下便能開啟 Blob 容器、佇列、資料表及檔案

#### <a name="fixes"></a>修正

* 已修正：使用 .NET 或 Java 程式庫插入的佇列訊息沒有從 base64 正確解碼
* 已修正：$metrics 資料表不會針對 Blob 儲存體帳戶顯示
* 已修正：資料表節點無法用於本機 (開發) 儲存體

#### <a name="known-issues"></a>已知問題

* macOS 安裝可能會需要較高的權限

06/15/2016
### <a name="version-080"></a>0.8.0 版

>[!VIDEO https://www.youtube.com/embed/ycfQhKztSIY?ecver=1]

>[!VIDEO https://www.youtube.com/embed/k4_kOUCZ0WA?ecver=1]

>[!VIDEO https://www.youtube.com/embed/3zEXJcGdl_k?ecver=1]

#### <a name="new"></a>新增

* 檔案共用支援：檢視、上傳、下載、複製檔案和目錄、SAS URI (建立和連線)
* 改善透過 SAS URI 或帳戶金鑰連線至儲存體的使用者體驗
* 匯出資料表查詢結果
* 針對資料表資料行的重新排列和自訂
* 搭配啟用的計量檢視儲存體帳戶的 $logs Blob 容器和 $metrics 資料表
* 改善匯出和匯入行為，現已包含屬性值類型

#### <a name="fixes"></a>修正

* 已修正：上傳或下載大型 Blob 可能會導致不完整的上傳/下載
* 已修正：編輯、新增或匯入具有數值字串值 ("1") 的實體會將它轉換為 double
* 已修正：無法在本機開發環境中展開資料表節點

#### <a name="known-issues"></a>已知問題

* $metrics 資料表不會針對 Blob 儲存體帳戶顯示
* 如果以程式設計方式新增的佇列訊息是使用 Base64 編碼方式進行編碼，則該訊息可能會無法正確顯示

05/17/2016
### <a name="version-07201605090"></a>0.7.20160509.0 版

#### <a name="new"></a>新增

* 改善應用程式當機的錯誤處理

#### <a name="fixes"></a>修正

* 已修正在需要登入認證時，InfoBar 訊息有時候不會顯示的錯誤

#### <a name="known-issues"></a>已知問題

* 資料表：新增、編輯或匯入具有不明確數值 (例如 "1" 或 "1.0") 的實體，且使用者嘗試將它傳送為 `Edm.String` 時，該值將會透過用戶端 API 以 Edm.Double 的形式傳回

03/31/2016

### <a name="version-07201603250"></a>0.7.20160325.0 版

>[!VIDEO https://www.youtube.com/embed/imbgBRHX65A?ecver=1]

>[!VIDEO https://www.youtube.com/embed/ceX-P8XZ-s8?ecver=1]

#### <a name="new"></a>新增

* 資料表支援：針對實體的檢視、查詢、匯出、匯入及 CRUD 作業
* 佇列支援：針對訊息進行檢視、新增、清除佇列
* 針對儲存體帳戶產生 SAS URI
* 透過 SAS URI 連線至儲存體帳戶
* 針對儲存體總管未來更新的更新通知
* 更新外觀與風格

#### <a name="fixes"></a>修正

* 改善效能和可靠性

### <a name="known-issues-amp-mitigations"></a>已知問題 &amp; 緩解方式

* 下載大型 Blob 檔案並無法正確運作。在我們解決此問題的期間，建議您使用 AzCopy
* 如果找不到主資料夾，或是無法寫入該資料夾，則不會擷取或快取帳戶認證
* 在新增、編輯或匯入具有不明確數值 (例如 "1" 或 "1.0") 的實體，且使用者嘗試將它傳送為 `Edm.String` 時，該值將會透過用戶端 API 以 Edm.Double 的形式傳回
* 匯入具有多行記錄的 CSV 檔案時，資料可能會變得破碎或變成亂碼

02/03/2016

### <a name="version-07201601291"></a>0.7.20160129.1 版

#### <a name="fixes"></a>修正

* 改善上傳、下載及複製 Blob 的整體效能

01/14/2016

### <a name="version-07201601050"></a>0.7.20160105.0 版

#### <a name="new"></a>新增

* Linux 支援 (和 OSX 相同的功能)
* 新增具有共用存取簽章 (SAS) 金鑰的 Blob 容器
* 新增 Azure 中國的儲存體帳戶
* 新增具有自訂端點的儲存體帳戶
* 開啟及檢視內容文字和圖片 Blob
* 檢視及編輯 Blob 屬性和中繼資料

#### <a name="fixes"></a>修正

* 已修正：上傳或下載大量的 Blob (超過 500 個) 時，有時候可能會導致應用程式出現白色畫面
* 已修正：設定 Blob 容器公用存取層級時，在您重新將焦點設定在容器上之前，新的值將不會更新。 此外，對話方塊預設一律會顯示「無公用存取」，而非目前實際的值。
* 更佳的整體鍵盤/協助工具及 UI 支援
* 階層連結記錄在因大量空白字元而變得過長時便會自動換行
* SAS 對話方塊支援輸入驗證
* 本機存放區在使用者認證過期後仍會持續可用
* 刪除已開啟的 Blob 容器時，便會關閉位於右側的 Blob 總管

#### <a name="known-issues"></a>已知問題

* Linux 安裝需要更新或升級 gcc 版本，升級步驟如下：
    * `sudo add-apt-repository ppa:ubuntu-toolchain-r/test`
    * `sudo apt-get update`
    * `sudo apt-get upgrade`
    * `sudo apt-get dist-upgrade`

11/18/2015
### <a name="version-07201511160"></a>0.7.20151116.0 版

#### <a name="new"></a>新增

* macOS 及 Windows 版本
* 登入以檢視儲存體帳戶，使用您的組織帳戶、Microsoft 帳戶、2FA 等等。
* 本機開發儲存體 (使用儲存體模擬器，僅限 Windows)
* Azure Resource Manager 和傳統資源支援
* 建立及刪除 Blob、佇列或資料表
* 搜尋特定的 Blob、佇列或資料表
* 瀏覽 Blob 容器的內容
* 檢視並瀏覽目錄
* 上傳、下載及刪除 Blob 和資料夾
* 檢視及編輯 Blob 屬性和中繼資料
* 產生 SAS 金鑰
* 管理及建立儲存的存取原則 (SAP)
* 使用前置詞搜尋 Blob
* 拖放檔案以上傳或下載

#### <a name="known-issues"></a>已知問題

* 設定 Blob 容器公用存取層級時，在您重新將焦點設定在容器上之前，新的值將不會更新
* 當您開啟對話方塊以設定公用存取層級時，該對話方塊預設一律會顯示「無公用存取」，而非目前實際的值
* 無法對已下載的 Blob 進行重新命名
* 發生錯誤時，活動記錄項目有時候會卡在進行中的狀態，且該錯誤不會顯示
* 嘗試上傳或下載大量的 Blob 時，有時候會當機或是出現白色畫面
* 取消複製作業有時候會無法運作
* 在建立容器 (Blob/佇列/資料表) 的期間，如果您輸入無效的名稱，並繼續以不同的容器類型建立另一個容器，將無法把焦點設定在新的類型上
* 無法建立新資料夾或對資料夾進行重新命名




[2]: https://support.microsoft.com/en-us/help/4021389/storage-explorer-troubleshooting-guide
[3]: vs-azure-tools-storage-manage-with-storage-explorer.md
