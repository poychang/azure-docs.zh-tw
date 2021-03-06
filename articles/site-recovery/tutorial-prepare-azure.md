---
title: 建立要搭配 Azure Site Recovery 使用的資源 | Microsoft Docs
description: 了解如何準備 Azure，以使用 Azure Site Recovery 來進行內部部署電腦的複寫。
services: site-recovery
author: rayne-wiselman
ms.service: site-recovery
ms.topic: tutorial
ms.date: 05/02/2018
ms.author: raynew
ms.custom: MVC
ms.openlocfilehash: 852c854de9feb9bcc98fc89aa9340b93f2c4e8d3
ms.sourcegitcommit: 870d372785ffa8ca46346f4dfe215f245931dae1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="prepare-azure-resources-for-replication-of-on-premises-machines"></a>準備 Azure 資源以進行內部部署機器的複寫

 [Azure Site Recovery](site-recovery-overview.md) 藉由確保您的商務應用程式可在計劃性與非計劃性中斷期間持續啟動並執行，來提供商務持續性和災害復原 (BCDR) 策略。 Site Recovery 會管理並協調內部部署機器和 Azure 虛擬機器 (VM) 的災害復原，包括複寫、容錯移轉和復原。

本教學課程說明如何在您想要將內部部署 VM (Hyper-V 或 VMware) 或 Windows/Linux 實體伺服器複寫至 Azure 時，準備好 Azure 元件。 在本教學課程中，您了解如何：

> [!div class="checklist"]
> * 確認您的 Azure 帳戶具有複寫權限。
> * 建立 Azure 儲存體帳戶。 複寫的資料會儲存在此。
> * 建立復原服務保存庫。
> * 設定 Azure 網路。 當 Azure VM 在容錯移轉後建立時，會加入此 Azure 網路。

如果您沒有 Azure 訂用帳戶，請在開始前建立 [免費帳戶](https://azure.microsoft.com/pricing/free-trial/) 。

## <a name="sign-in-to-azure"></a>登入 Azure

登入 [Azure 入口網站](http://portal.azure.com)。

## <a name="verify-account-permissions"></a>確認帳戶權限

如果您剛建立免費的 Azure 帳戶，您就是您的訂用帳戶管理員。 如果您不是訂用帳戶管理員，請與系統管理員合作以指派您所需的權限。 若要啟用新虛擬機器的複寫，您必須具有權限才能：

- 在所選的資源群組中建立 VM。
- 在所選的虛擬網路中建立 VM。
- 寫入所選取的儲存體帳戶。

若要完成這些工作，應將虛擬機器參與者內建角色指派至您的帳戶。 此外，若要管理保存庫中的 Site Recovery 作業，應將 Site Recovery 參與者內建角色指派至您的帳戶。

## <a name="create-a-storage-account"></a>建立儲存體帳戶

複寫機器的映像會保留在 Azure 儲存體中。 當您從內部部署容錯移轉至 Azure 時，會從儲存體建立 Azure VM。

1. 在 [Azure 入口網站](https://portal.azure.com)功能表上，選取 [新增] > [儲存體] > [儲存體帳戶]。
2. 在 [建立儲存體帳戶] 上，輸入帳戶的名稱。 在這些教學課程中，使用名稱 **contosovmsacct1910171607**。 此名稱必須是 Azure 中的唯一名稱，並介於 3 到 24 個字元，而且只能包含數字和小寫字母。
3. 在 [部署模型] 中選取 [Resource Manager]。
4. 在 [帳戶種類] 中選取 [一般用途]。 在 [效能] 中選取 [標準]。 請勿選取 Blob 儲存體。
5. 在 [複寫] 中，針對儲存體備援選取預設的 [讀取權限異地備援儲存體]。
6. 在 [訂用帳戶] 中，選取您要在其中建立新儲存體帳戶的訂用帳戶。
7. 在 [資源群組] 中，輸入新的資源群組。 Azure 資源群組是在其中部署與管理 Azure 資源的邏輯容器。 在這些教學課程中，使用名稱 **ContosoRG**。
8. 在 [位置] 中，選取儲存體帳戶的地理位置。 儲存體帳戶與復原服務保存庫必須位於相同的區域。 在這些教學課程中，使用 [西歐] 區域。

   ![建立儲存體帳戶](media/tutorial-prepare-azure/create-storageacct.png)

9. 選取 [建立]  以建立儲存體帳戶。

## <a name="create-a-vault"></a>建立保存庫

1. 在 Azure 入口網站中，選取 [建立群組] > [監視 + 管理] > [備份和 Site Recovery]。
2. 在 [ **名稱**] 中，輸入保存庫的易記識別名稱。 在此教學課程中，使用 **ContosoVMVault**。
3. 在 [資源群組] 中，選取名為 **contosoRG** 的現有資源群組。
4. 在 [位置] 中，輸入這套教學課程中使用的 Azure 區域 [西歐]。
5. 若要從儀表板快速存取保存庫，請按一下 [釘選到儀表板] > [建立]。

   ![建立新保存庫](./media/tutorial-prepare-azure/new-vault-settings.png)

   新的保存庫會出現在 [儀表板] > [所有資源] 上，以及 [復原服務保存庫] 主頁面上。

## <a name="set-up-an-azure-network"></a>設定 Azure 網路

當 Azure VM 在容錯移轉後從儲存體建立時，會加入此網路。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [建立資源] > [網路] > [虛擬網路]。
2. 保持選取 [Resource Manager] 作為部署模型。 Resource Manager 是慣用的部署模型。 然後採取下列步驟：

   a. 在 [名稱] 中，輸入網路名稱。 此名稱必須是 Azure 資源群組中的唯一名稱。 使用名稱 **ContosoASRnet**。

   b. 在 [資源群組] 中，使用現有的資源群組 **contosoRG**。

   c. 在 [位址範圍] 中，輸入網路位址範圍 **10.0.0.0/24**。

   d. 在此教學課程中，您不需要子網路。

   e. 在 [訂用帳戶] 中，選取要在其中建立網路的訂用帳戶。

   f. 在 [位置] 中，選取 [西歐]。 此網路必須位於與復原服務保存庫相同的區域中。

3. 選取 [建立] 。

   ![建立虛擬網路](media/tutorial-prepare-azure/create-network.png)

   虛擬網路的建立會耗用幾秒鐘時間。 建立後，您會在 Azure 入口網站儀表板中看到它。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [準備內部部署 VMware 基礎結構以進行 Azure 的災害復原](tutorial-prepare-on-premises-vmware.md)
