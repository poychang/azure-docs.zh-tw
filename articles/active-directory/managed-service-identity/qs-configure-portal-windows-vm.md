---
title: 如何使用 Azure 入口網站設定 Azure VM 上的 MSI
description: 使用 Azure 入口網站在 Azure VM 上設定「受控服務身分識別 (MSI)」的逐步指示。
services: active-directory
documentationcenter: ''
author: daveba
manager: mtillman
editor: ''
ms.service: active-directory
ms.component: msi
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 09/19/2017
ms.author: daveba
ms.openlocfilehash: 62b8504f5c10f338539d263bb231cf96eb405ba6
ms.sourcegitcommit: d98d99567d0383bb8d7cbe2d767ec15ebf2daeb2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33930335"
---
# <a name="configure-a-vm-managed-service-identity-msi-using-the-azure-portal"></a>使用 Azure 入口網站設定「VM 受控服務身分識別 (MSI)」

[!INCLUDE[preview-notice](../../../includes/active-directory-msi-preview-notice.md)]

在 Azure Active Directory 中，「受控服務身分識別」會提供自動受控身分給 Azure 服務。 您可以使用此身分識別來向任何支援 Azure AD 驗證的服務進行驗證，不需要任何您程式碼中的認證。 

在本文中，您將了解如何使用 Azure 入口網站啟用和停用 Azure VM 之系統指派的身分識別。 目前不支援透過 Azure 入口網站指派使用者指派身分識別，以及將其從 Azure VM 中移除。

> [!NOTE]
> 目前，不支援透過 Azure 入口網站的使用者指派身分識別作業。 請回來查看以取得更新資料。 

## <a name="prerequisites"></a>先決條件

- 如果您不熟悉受控服務識別，請參閱[概觀](overview.md)一節。
- 如果您還沒有 Azure 帳戶，請先[註冊免費帳戶](https://azure.microsoft.com/free/)，再繼續進行。

## <a name="managed-service-identity-during-creation-of-an-azure-vm"></a>在 Azure vm 建立期間的受控服務識別

目前，透過 Azure 入口網站建立虛擬機器不支援受控服務識別作業。 因此，請參閱下列 VM 建立快速入門文章之一，先建立 VM：

- [使用 Azure 入口網站建立 Windows 虛擬機器](../../virtual-machines/windows/quick-create-portal.md#create-virtual-machine)
- [使用 Azure 入口網站建立 Linux 虛擬機器](../../virtual-machines/linux/quick-create-portal.md#create-virtual-machine)  

然後進入下一節，取得在虛擬機器上啟用受控服務識別的詳細資料。

## <a name="enable-managed-service-identity-on-an-existing-azure-vm"></a>在現有的 Azure VM 上啟用受控服務識別

若要在原始佈建的虛擬機器 (沒有系統指派的身分識別) 上啟用該身分識別：

1. 使用與包含虛擬機器的 Azure 訂用帳戶相關聯的帳戶，登入 [Azure 入口網站](https://portal.azure.com)。 此外也請確定您的帳戶屬於在 VM 上具有寫入權限的角色，例如「虛擬機器參與者」。

2. 瀏覽至所需的虛擬機器，然後選取 [組態] 頁面。

3. 藉由在 [受控服務識別] 下選取 [是]，然後按一下 [儲存]，以在虛擬機器上啟用系統指派的身分識別。 此作業可能需要 60 秒以上才能完成：

    > [!NOTE]
    > 不支援透過 Azure 入口網站將使用者指派的身分識別新增至虛擬機器。

   ![組態頁面螢幕擷取畫面](../media/msi-qs-configure-portal-windows-vm/create-windows-vm-portal-configuration-blade.png)  

## <a name="remove-managed-service-identity-from-an-azure-vm"></a>將受控服務識別從 Azure VM 中移除

如果您的虛擬機器不再需要系統指派的身分識別：

1. 使用與包含虛擬機器的 Azure 訂用帳戶相關聯的帳戶，登入 [Azure 入口網站](https://portal.azure.com)。 此外也請確定您的帳戶屬於在 VM 上具有寫入權限的角色，例如「虛擬機器參與者」。

2. 瀏覽至所需的虛擬機器，然後選取 [組態] 頁面。

3. 藉由在 [受控服務識別] 下選取 [否]，然後按一下 [儲存]，以在虛擬機器上停用系統指派的身分識別。 此作業可能需要 60 秒以上才能完成：

    > [!NOTE]
    > 不支援透過 Azure 入口網站將使用者指派的身分識別新增至虛擬機器。

   ![組態頁面螢幕擷取畫面](../media/msi-qs-configure-portal-windows-vm/create-windows-vm-portal-configuration-blade-disable.png)  

## <a name="related-content"></a>相關內容

- 如需受控服務識別的概觀，請參閱[概觀](overview.md)。

## <a name="next-steps"></a>後續步驟

- 使用 Azure 入口網站，提供 Azure VM 的 MSI[ 存取權給另一個 Azure 資源](howto-assign-access-portal.md)。

