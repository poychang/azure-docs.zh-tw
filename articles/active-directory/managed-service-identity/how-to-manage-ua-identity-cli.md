---
title: 如何使用 Azure CLI 管理使用者指派的受控服務識別 (MSI)
description: 如何使用 Azure CLI 建立、列出和刪除使用者指派之受控服務識別的逐步說明。
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
ms.date: 04/16/2018
ms.author: daveba
ms.openlocfilehash: 5262914e469bdc07921c3b82e990d544349b5fd4
ms.sourcegitcommit: d98d99567d0383bb8d7cbe2d767ec15ebf2daeb2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33930661"
---
# <a name="create-list-or-delete-a-user-assigned-identity-using-the-azure-cli"></a>使用 Azure CLI 建立、列出和刪除使用者指派的身分識別

[!INCLUDE[preview-notice](~/includes/active-directory-msi-preview-notice-ua.md)]

在 Azure Active Directory 中，「受控服務識別」會提供受控身分識別給 Azure 服務。 您可以使用此身分識別來向支援 Azure AD 驗證的服務進行驗證，而不需要您程式碼中的認證。 

在本文中，您會了解如何使用 Azure CLI 建立、列出和刪除使用者指派的身分識別。

## <a name="prerequisites"></a>先決條件

- 如果您不熟悉受控服務識別，請參閱[概觀](overview.md)一節。 **請務必檢閱[已指派系統和使用者指派之身分識別其間的差異](overview.md#how-does-it-work)**。
- 如果您還沒有 Azure 帳戶，請先[註冊免費帳戶](https://azure.microsoft.com/free/)，再繼續進行。

- 若要執行 CLI 指令碼範例，您有三個選項：

    - 從 Azure 入口網站使用 [Azure Cloud Shell](../../cloud-shell/overview.md) (請參閱下一節)。
    - 請透過每個程式碼區塊右上角的 [立即試用] 按鈕，使用內嵌的 Azure Cloud Shell。
    - 如果您想要使用本機的 CLI 主控台，請[安裝最新版的 CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli) (2.0.13 或更新版本)。 使用 `az login` 登入 Azure，使用與 Azure 訂用帳戶相關聯的帳戶，而您要以此帳戶部署使用者指派身分識別。

[!INCLUDE [cloud-shell-try-it.md](../../../includes/cloud-shell-try-it.md)]

## <a name="create-a-user-assigned-managed-identity"></a>建立使用者指派的受控身分識別 

若要建立使用者指派的身分識別，請使用 [az identity create](/cli/azure/identity#az-identity-create) 命令。 `-g` 參數會指定要建立使用者指派之身分識別的資源群組，而 `-n` 參數則指定其名稱。 將 `<RESOURCE GROUP>` 和 `<USER ASSIGNED IDENTITY NAME>` 參數取代為您自己的值：

> [!IMPORTANT]
> 建立使用者指派的身分識別僅支援英數字元和連字號 (0-9 或 a-z 或 A-Z 或 -) 字元。 此外，指派至 VM/VMSS 的名稱應該限制為 24 個字元長度，才能正常運作。 請回來查看以取得更新資料。 如需詳細資訊，請參閱[常見問題集和已知問題](known-issues.md)

 ```azurecli-interactive
az identity create -g <RESOURCE GROUP> -n <USER ASSIGNED IDENTITY NAME>
```
## <a name="list-user-assigned-identities"></a>列出使用者指派的身分識別

若要列出使用者指派的身分識別，請使用 [az identity list](/cli/azure/identity#az-identity-list) 命令。  `-g` 參數會指定建立使用者指派之身分識別所在的資源群組。  將 `<RESOURCE GROUP>` 取代為您自己的值：

```azurecli-interactive
az identity list -g <RESOURCE GROUP>
```
在 json 回應中，使用者身分識別具備`"Microsoft.ManagedIdentity/userAssignedIdentities"`為索引鍵傳回的值`type`。

`"type": "Microsoft.ManagedIdentity/userAssignedIdentities"`

## <a name="delete-a-user-assigned-identity"></a>刪除使用者指派的身分識別

若要刪除使用者指派的身分識別，請使用 [az identity delete](/cli/azure/identity#az-identity-delete) 命令。  -n 參數會指定其名稱，而 -g 參數會指定建立使用者指派之身分識別所在的資源群組。  將 `<USER ASSIGNED IDENTITY NAME>` 和 `<RESOURCE GROUP>` 參數取代為您自己的值：

 ```azurecli-interactive
az identity delete -n <USER ASSIGNED IDENTITY NAME> -g <RESOURCE GROUP>
```
> [!NOTE]
> 將使用者指派的身分識別從受指派的任何資源中刪除，並不會移除參考。 請使用 `az vm/vmss identity remove` 命令將其從 VM/VMSS 中移除

## <a name="related-content"></a>相關內容

如需 Azure CLI 身分識別命令的完整清單，請參閱 [az identity](/cli/azure/identity)。

如需如何將使用者指派之身分識別指派至 Azure VM 的相關資訊，請參閱[使用 Azure CLI 設定受控服務識別 (MSI)](qs-configure-cli-windows-vm.md#user-assigned-identity)


 
