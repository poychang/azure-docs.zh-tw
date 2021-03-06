---
title: 安裝 Visual Studio 並連線至 Azure Stack | Microsoft Docs
description: 了解安裝 Visual Studio 並連線至 Azure Stack 的必要逐步執行
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
ms.assetid: 2022dbe5-47fd-457d-9af3-6c01688171d7
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/15/2018
ms.author: mabrigg
ms.openlocfilehash: 3eaefbe011c4d98fe9a76d4f277a76a2f167b191
ms.sourcegitcommit: 688a394c4901590bbcf5351f9afdf9e8f0c89505
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
ms.locfileid: "34301888"
---
# <a name="install-visual-studio-and-connect-to-azure-stack"></a>安裝 Visual Studio 並連線至 Azure Stack

*適用於：Azure Stack 整合系統和 Azure Stack 開發套件*

使用 Visual Studio 建立並將 Azure Resource Manager [範本](azure-stack-arm-templates.md)部署至 Azure Stack 中。 您可以使用此文章所述的逐步執行，來從 [Azure Stack 開發套件](azure-stack-connect-azure-stack.md#connect-to-azure-stack-with-remote-desktop)，或如果您透過 [VPN](azure-stack-connect-azure-stack.md#connect-to-azure-stack-with-vpn)連線，從以 Windows 為基礎的外部用戶端安裝 Visual Studio。 本文中的這些步驟適用於全新安裝 Visual Studio 2015 Community 版本。 深入了解關於其他 Visual Studio 版本的[共存](https://msdn.microsoft.com/library/ms246609.aspx)。

## <a name="install-visual-studio"></a>安裝 Visual Studio

1. 下載並執行 [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)。
2. 搜尋**Visual Studio Community 2015 與 Microsoft Azure SDK - 2.9.6**，選取 [新增]，然後選取 [安裝]。

    ![WebPI 安裝步驟的螢幕擷取畫面](./media/azure-stack-install-visual-studio/image1.png)

3. 解除安裝作為 Azure SDK 安裝一部分的 **Microsoft Azure PowerShell**。

    ![Azure PowerShell 新增/移除程式介面的螢幕擷取畫面](./media/azure-stack-install-visual-studio/image2.png)

4. [安裝 Azure Stack 適用的 PowerShell](azure-stack-powershell-install.md)

5. 在安裝完成之後，請重新啟動作業系統。

## <a name="connect-to-azure-stack"></a>連線至 Azure Stack

1. 啟動 Visual Studio。

2. 從 [檢視] 功能表選取 [Cloud Explorer]。

3. 在新的窗格中，選取 [新增帳戶] 並以您的 Azure Active Directory 認證登入。
    ![登入 Cloud Explorer 後並連線到 Azure Stack 的螢幕擷取畫面](./media/azure-stack-install-visual-studio/image6.png)

登入之後，您可以[部署範本](azure-stack-deploy-template-visual-studio.md)，或瀏覽可用的資源型別和資源群組來建立您自己的範本。

## <a name="next-steps"></a>後續步驟

* [開發適用於 Azure Stack 的範本](azure-stack-develop-templates.md)
