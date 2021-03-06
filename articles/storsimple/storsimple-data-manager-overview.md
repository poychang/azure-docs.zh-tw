---
title: Microsoft Azure StorSimple Data Manager 概觀 | Microsoft Docs
description: 提供 StorSimple 資料管理員服務的概觀
services: storsimple
documentationcenter: NA
author: vidarmsft
manager: syadav
editor: ''
ms.assetid: ''
ms.service: storsimple
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: TBD
ms.date: 02/26/2018
ms.author: vidarmsft
ms.openlocfilehash: 429f1edae15a98b3c38ae4980a630f23b3a85d23
ms.sourcegitcommit: 96089449d17548263691d40e4f1e8f9557561197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34271899"
---
# <a name="storsimple-data-manager-solution-overview"></a>StorSimple 資料管理員解決方案概觀

## <a name="overview"></a>概觀

Microsoft Azure StorSimple 使用雲端儲存體作為內部部署解決方案的擴充功能，並且會跨內部部署儲存體和雲端自動將資料分層。 資料儲存在雲端時會採用已啟用重複資料刪除功能的壓縮格式，以獲得最大效率並降低成本。 當資料以 StorSimple 格式儲存時，無法立即供您要使用的其他雲端應用程式取用。

StorSimple 資料管理員可讓您順暢地存取及使用雲端中的 StorSimple 格式資料。 原因是它會將 StorSimple 格式轉換成原生的 blob 和檔案，以供您搭配 Azure 媒體服務、Azure HDInsights 和 Azure Machine Learning 等其他服務使用。

本文會提供 StorSimple 資料管理員解決方案的概觀。 也說明如何使用這項服務來撰寫應用程式，以使用 StorSimple 資料和雲端中的其他 Azure 服務。

## <a name="how-it-works"></a>運作方式

StorSimple 資料管理員服務可從 StorSimple 8000 系列的內部部署裝置識別雲端中的 StorSimple 資料。 雲端中的 StorSimple 資料會採用已啟用重複資料刪除功能的 StorSimple 壓縮格式。 資料管理員服務會提供 API，以便擷取 StorSimple 格式資料並將它轉換成其他格式，例如 Azure blob 和 Azure 檔案。 這個經過轉換的資料隨後便可供 Azure HDInsight 和 Azure 媒體服務立即取用。 因此，資料轉換可讓這些服務從 StorSimple 8000 系列的內部部署裝置操作經過轉換的 StorSimple 資料。 下圖可說明此流程。

![高階圖表](./media/storsimple-data-manager-overview/storsimple-data-manager-overview2.png)


## <a name="data-manager-use-cases"></a>資料管理員使用案例

資料管理員可以搭配 Azure Functions、Azure 自動化和 Azure Data Factory 使用，而讓這些工作流程在處理資料時，就和資料進入 StorSimple 時的處理方式相同。 建議您使用 Azure 媒體服務來處理您儲存在 StorSimple 上的媒體內容、對該資料執行機器學習演算法，或啟動 Hadoop 叢集來分析您儲存在 StorSimple 上的資料。 結合 Azure 所提供的各式各樣服務與 StorSimple 上的資料，您可以釋放資料的威力。


## <a name="region-availability"></a>區域可用性

StorSimple 資料管理員適用於下列 7 個區域：

 - 東南亞
 - 美國東部
 - 美國西部
 - 美國西部 2
 - 美國中西部
 - 北歐
 - 西歐

不過，您可以使用 StorSimple 資料管理員在下列區域轉換資料。 

![資料的適用區域](./media/storsimple-data-manager-overview/data-manager-job-definition-different-regions-m.png)

這組區域較大，因為任何上述區域中的資源部署都能夠在下列區域中啟動轉換程序。 因此，只要您的資料位於這 19 個區域中的任何一個，您就可以使用此服務來轉換資料。


## <a name="choosing-a-region"></a>選擇區域

我們的建議如下：
 - 讓來源儲存體帳戶 (與 StorSimple 裝置相關聯的帳戶) 和目標儲存體帳戶 (要讓資料採用原生格式的帳戶) 位於相同的 Azure 區域。
 - 在包含 StorSimple 儲存體帳戶的區域中啟動您的資料管理員與作業定義。 如果無法這麼做，則在最接近的 Azure 區域中啟動資料管理員，然後在與 StorSimple 儲存體帳戶相同的區域中建立作業定義。 

    如果 StorSimple 儲存體帳戶不是位於支援建立作業定義的 26 個區域，則建議您不要執行 StorSimple 資料管理員，否則您會發現延遲時間很久，而且輸出費用可能會很高。

## <a name="security-considerations"></a>安全性考量

StorSimple 資料管理員必須有服務資料加密金鑰，才能從 StorSimple 格式轉換為原生格式。 當第一個裝置向 StorSimple 服務進行註冊時，系統就會產生服務資料加密金鑰。 如需這個金鑰的詳細資訊，請移至 [StorSimple 安全性](storsimple-8000-security.md)。

提供作為輸入的服務資料加密金鑰，會儲存在您建立資料管理員時所建立的金鑰保存庫中。 此保存庫位於與 StorSimple 資料管理員相同的 Azure 區域中。 當您刪除資料管理員服務時，此金鑰會隨之刪除。

計算資源會使用此金鑰來執行轉換。 這些計算資源位於與作業定義相同的 Azure 區域中。 此區域不一定會與您啟動資料管理員的區域相同。

如果資料管理員所在的區域與作業定義所在的區域不同，請務必了解這些區域中各自擁有哪些資料/中繼資料。 下圖說明資料管理員與作業定義位於不同區域時的效果。

![位於不同區域的服務和作業定義](./media/storsimple-data-manager-overview/data-manager-job-different-regions.png)

## <a name="gdpr-compliance"></a>GDPR 合規性

[一般資料保護規定 (GDPR)](http://ec.europa.eu/justice/data-protection/reform/index_en.htm) 是歐盟 (EU) 所制定的資料保護和隱私權法律。 GDPR 包含許多有關如何收集、儲存和使用個人資訊的需求。 GDPR 規則強制實行於 EU 內營運，並且收集、分析 EU 居民相關之資料的公司、政府機關和其他組織。 StorSimple 資料管理員符合 GDPR。 資料管理員服務不會收集個人資料。
如需詳細資訊，請在[信任中心](https://www.microsoft.com/trustcenter)檢閱 Microsoft 隱私權原則。

## <a name="next-steps"></a>後續步驟

[使用 StorSimple Data Manager UI 來轉換資料](storsimple-data-manager-ui.md)。
