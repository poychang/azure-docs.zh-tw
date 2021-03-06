---
title: Azure 資訊安全中心的自適性應用程式控制 | Microsoft Docs
description: 本文件協助您了解如何使用 Azure 資訊安全中心的自適性應用程式控制，將在 Azure VM 中執行的應用程式列入允許清單。
services: security-center
documentationcenter: na
author: terrylan
manager: mbaldwin
editor: ''
ms.assetid: 9268b8dd-a327-4e36-918e-0c0b711e99d2
ms.service: security-center
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/15/2018
ms.author: yurid
ms.openlocfilehash: 841dbbf97a7fa25aa001636ba92cc2a966be4908
ms.sourcegitcommit: ca05dd10784c0651da12c4d58fb9ad40fdcd9b10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="adaptive-application-controls-in-azure-security-center-preview"></a>Azure 資訊安全中心的自適性應用程式控制 (預覽)
了解如何利用此逐步解說，在 Azure 資訊安全中心設定應用程式控制。

## <a name="what-are-adaptive-application-controls-in-security-center"></a>什麼是 Azure 資訊安全中心的自適性應用程式控制？
自適性應用程式控制有助於控制哪些應用程式可以在 Azure 中的 VM 上執行，而且有助於強化您的 VM 來抵禦惡意程式碼。 資訊安全中心會利用機器學習服務來分析在 VM 中執行的應用程式，並協助您利用此情報來套用列入允許清單規則。 這項功能可大幅簡化設定和維護應用程式允許清單的程序，可讓您：

- 封鎖執行惡意應用程式的嘗試或提出警示，包括反惡意程式碼解決方案可能遺漏的嘗試。
- 符合您組織規定只能使用授權軟體的安全性原則。
- 避免在您的環境中使用不必要的軟體。
- 避免執行舊版和不支援的應用程式。
- 阻止您的組織不允許的特定軟體工具。
- 讓 IT 能夠透過應用程式使用量來控制敏感性資料的存取。

## <a name="how-to-enable-adaptive-application-controls"></a>如何啟用自適性應用程式控制？
自適性應用程式控制可協助您定義一組可以在設定之資源群組上執行的應用程式。 這項功能只適用於 Windows 電腦 (所有版本，傳統或 Azure Resource Manager)。 可以使用下列步驟在資訊安全中心設定應用程式允許清單：

1. 開啟 [資訊安全中心] 儀表板。
2. 在左側窗格中，選取位於 [進階雲端防禦] 之下的 [自適性應用程式控制]。

    ![防禦](./media/security-center-adaptive-application/security-center-adaptive-application-fig1-new.png)

[自適性應用程式控制] 頁面隨即出現。

![controls](./media/security-center-adaptive-application/security-center-adaptive-application-fig2.png)

[VM 群組] 區段包含三個索引標籤：

* **已設定**：內含已設定應用程式控制之 VM 的群組清單。
* **建議**：建議採用應用程式控制的群組清單。 資訊安全中心會使用機器學習服務，根據 VM 是否以一致的方式執行相同的應用程式來識別適合採用應用程式控制的 VM。
* **無建議**：內含無任何應用程式控制建議之 VM 的群組清單。 例如，其上的應用程式一直改變且尚未達到穩定狀態的 VM。

> [!NOTE]
> 資訊安全中心會使用專屬群集演算法來建立 VM 群組，以確保類似的 VM 取得最佳建議應用程式控制原則。
>
>

### <a name="configure-a-new-application-control-policy"></a>設定新的應用程式控制原則
1. 針對具有應用程式控制建議的群組清單，按一下 [建議] 索引標籤：

  ![建議](./media/security-center-adaptive-application/security-center-adaptive-application-fig3.png)

  此清單包括：

  - **名稱**：訂用帳戶和群組的名稱
  - **VM**：群組中的虛擬機器數目
  - **狀態**：建議的狀態，在大部分的情況會是「開啟」
  - **嚴重性**：建議的嚴重性層級

2. 選取群組以開啟 [建立應用程式控制規則] 選項。

  ![應用程式控制規則](./media/security-center-adaptive-application/security-center-adaptive-application-fig4.png)

3. 在 [選取 VM] 中，檢閱建議的 VM 清單，並取消選取任何不想套用應用程式控制的 VM。 接下來，您會看到兩份清單：

  - **建議應用程式**：此群組中 VM 上經常使用的應用程式清單，因此資訊安全中心建議用於應用程式控制規則。
  - **更多應用程式**：此群組中 VM 上較不常使用或稱為「易受利用」(詳情請參閱下面內容) 的應用程式清單，建議在套用規則前先進行檢閱。

4. 檢閱每份清單中的應用程式，並取消選取您不想套用的應用程式。 每份清單都包括：

  - **名稱**：應用程式或其完整應用程式路徑的憑證資訊
  - **檔案類型**：應用程式檔案類型。 這可以是 EXE、指令碼或 MSI。
  - **易受利用**：警告圖示將會指出攻擊者是否可能使用應用程式來略過應用程式允許清單。 建議您在核准之前檢閱這些應用程式。
  - **使用者**：允許執行應用程式的建議使用者

5. 一旦完成您的選擇，請選取 [建立]。

根據預設，資訊安全中心一律在「稽核」模式啟用應用程式控制。 驗證允許清單對您的工作負載沒有任何不良影響之後，即可變更為「強制」模式。

資訊安全中心會依賴至少兩週的資料，以建立基準，並且在每個虛擬機器群組填入唯一建議。 資訊安全中心標準層的新客戶預期會有標準行為，也就是他們的虛擬機器群組一開始會出現在 [不推薦] 索引標籤底下。

> [!NOTE]
> 最佳的安全性作法就是，資訊安全中心一律嘗試為應列入允許清單的應用程式建立發行者規則，且只有在應用程式沒有發行者資訊 (也就是未簽署) 時，才會針對特定 EXE 的完整路徑建立路徑規則。
>   

### <a name="editing-and-monitoring-a-group-configured-with-application-control"></a>編輯和監視已設定應用程式控制的群組

1. 若要編輯和監視已設定應用程式控制的群組，請回到 [自適性應用程式控制] 頁面，然後選取 [VM 群組] 下的 [已設定]：

  ![群組](./media/security-center-adaptive-application/security-center-adaptive-application-fig5.png)

  此清單包括：

  - **名稱**：訂用帳戶和群組的名稱
  - **VM**：群組中的虛擬機器數目
  - **模式**：稽核模式會記錄執行非允許清單應用程式的嘗試；「強制」模式則不允許非允許清單的應用程式執行
  - **問題**：目前所有的違規情形

2. 選取群組以在 [編輯應用程式控制規則] 頁面中進行變更。

  ![保護](./media/security-center-adaptive-application/security-center-adaptive-application-fig6.png)

3. 在 [保護模式] 之下，您可以選取下列選項：

  - **稽核**：在此模式中，應用程式控制解決方案不會強制執行規則，而只會稽核受保護虛擬機器上的活動。 此模式建議用於下列情況：您想在封鎖要在目標 VM 中執行的應用程式之前，先觀察整體行為。
  - **強制**：在此模式中，應用程式控制解決方案會強制執行規則，並確定不得執行的應用程式會遭到封鎖。

  如先前所述，根據預設，新的應用程式控制原則一律設定為「稽核」模式。 在 [原則擴充功能] 之下，您可以將自己的應用程式路徑新增至允許清單。 新增這些路徑後，除了已採用的規則以外，資訊安全中心會為這些應用程式建立適當的規則。

  [最近的問題] 區段會列出目前所有的違規情形。

  ![問題](./media/security-center-adaptive-application/security-center-adaptive-application-fig7.png)

  此清單包括：
  - **問題**：任何已記錄的違規，其中包括下列項目：

      - **ViolationsBlocked**：當解決方案開啟 [強制] 模式時，嘗試執行未列入白名單的應用程式。
      - **ViolationsAudited**：當解決方案開啟 [稽核] 模式時，執行未列入允許清單的應用程式。

 - **VM 數目**：具有此問題類型的虛擬機器數目。

  如果您按一下每一行，系統會將您重新導向至 [Azure 活動記錄](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs)頁面，您可以在其中查看具有此類違規的所有虛擬機器資訊。 如果您按一下每一行結尾的三個點，您就能夠刪除該特定項目。 [已設定的虛擬機器] 區段會列出套用這些規則的 VM。

  ![已設定的虛擬機器](./media/security-center-adaptive-application/security-center-adaptive-application-fig8.png)

  在 [發行者允許清單規則] 下，此清單包含：

  - **規則**：根據每個應用程式的憑證資訊，建立發行者規則的應用程式
  - **檔案類型**：特定發行者規則所涵蓋的檔案類型。 這可以是下列任何一項：EXE、指令碼或 MSI。
  - **使用者**：允許執行每個應用程式的使用者數目

  如需詳細資訊，請參閱[了解 Applocker 中的發行者規則](https://docs.microsoft.com/windows/device-security/applocker/understanding-the-publisher-rule-condition-in-applocker)。

  ![列入允許清單規則](./media/security-center-adaptive-application/security-center-adaptive-application-fig9.png)

  如果您按一下每一行結尾的三個點，就可以刪除該特定規則或編輯允許的使用者。

  [路徑列入允許清單規則] 區段會列出未使用數位憑證簽署，但目前仍在列入允許清單規則中之應用程式的整個應用程式路徑 (包括特定檔案類型)。

  > [!NOTE]
  > 根據預設，最佳的安全性作法就是，資訊安全中心一律嘗試為應列入允許清單的 EXE 建立發行者規則，且只有在 EXE 沒有發行者資訊 (也就是未簽署) 時，才會針對特定 EXE 的完整路徑建立路徑規則。

  ![路徑列入白名單規則](./media/security-center-adaptive-application/security-center-adaptive-application-fig10.png)

  此清單包含：
  - **名稱**：可執行檔的完整修補程式
  - **檔案類型**：特定路徑規則所涵蓋的檔案類型。 這可以是下列任何一項：EXE、指令碼或 MSI。
  - **使用者**：允許執行每個應用程式的使用者數目

  如果您按一下每一行結尾的三個點，就可以刪除該特定規則或編輯允許的使用者。

4. 在 [自適性應用程式控制] 頁面上進行變更後，按一下 [儲存] 按鈕。 如果您決定不套用變更，則按一下 [捨棄]。

### <a name="not-recommended-list"></a>不建議使用的清單

資訊安全中心只會針對執行一組穩定應用程式的虛擬機器，建議應用程式允許清單。 如果相關 VM 上的應用程式一直變更，則不會產生建議。

![建議](./media/security-center-adaptive-application/security-center-adaptive-application-fig11.png)

此清單包含：
- **名稱**：訂用帳戶和群組的名稱
- **VM**：群組中的虛擬機器數目

## <a name="next-steps"></a>後續步驟
在本文件中，您已了解如何使用 Azure 資訊安全中心的自適性應用程式控制，將在 Azure VM 中執行的應用程式列入允許清單。 若要深入了解「Azure 資訊安全中心」，請參閱下列主題：

* [管理及回應 Azure 資訊安全中心的安全性警示](https://docs.microsoft.com/azure/security-center/security-center-managing-and-responding-alerts)。 了解如何在資訊安全中心管理警示，以及回應安全性事件。
* [Azure 資訊安全中心的安全性健全狀況監視](security-center-monitoring.md)。 了解如何監視 Azure 資源的健全狀況。
* [了解 Azure 資訊安全中心的安全性警示](https://docs.microsoft.com/azure/security-center/security-center-alerts-type)。 了解不同類型的安全性警示。
* [Azure 資訊安全中心疑難排解指南](https://docs.microsoft.com/azure/security-center/security-center-troubleshooting-guide)。 了解如何針對資訊安全中心的常見問題進行疑難排解。
* [Azure 資訊安全中心常見問題集](security-center-faq.md)。 尋找有關使用服務的常見問題。
* [Azure 安全性部落格](http://blogs.msdn.com/b/azuresecurity/)。 尋找有關 Azure 安全性與相容性的部落格文章。
