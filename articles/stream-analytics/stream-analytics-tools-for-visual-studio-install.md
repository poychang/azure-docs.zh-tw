---
title: 安裝適用於 Visual Studio 的 Azure 串流分析工具
description: 本文說明安裝需求，以及如何設定適用於 Visual Studio 的 Azure 串流分析工具。
services: stream-analytics
author: su-jie
ms.author: sujie
manager: kfile
ms.reviewer: jasonh
ms.service: stream-analytics
ms.topic: conceptual
ms.date: 09/19/2017
ms.openlocfilehash: 511658fc0e2b480987455007dac5f55cd7850feb
ms.sourcegitcommit: 5b2ac9e6d8539c11ab0891b686b8afa12441a8f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2018
---
# <a name="install-azure-stream-analytics-tools-for-visual-studio"></a>安裝適用於 Visual Studio 的 Azure 串流分析工具
Azure 串流分析工具現在支援 Visual Studio 2017、2015 和 2013。 本文件說明如何安裝和解除安裝這些工具。

如需使用工具的詳細資訊，請參閱[適用於 Visual Studio 的串流分析工具](https://docs.microsoft.com/azure/stream-analytics/stream-analytics-tools-for-visual-studio)。

## <a name="install"></a>Install
### <a name="visual-studio-2017"></a>Visual Studio 2017
* 下載 [Visual Studio 2017 (15.3 或更新版本)](https://www.visualstudio.com/)。 支援 Enterprise (Ultimate/Premium)、Professional 和 Community 版本。 不支援 Express 版本。 
* 串流分析工具在 Visual Studio 2017 中，屬於 **Azure 開發**與**資料儲存和處理**工作負載的一部分。 安裝 Visual Studio 時，請啟用其中一個工作負載。

啟用**資料儲存和處理**工作負載，如下所示：

![資料儲存和處理工作負載](./media/stream-analytics-tools-for-vs/stream-analytics-tools-for-vs-2017-install-01.png)

啟用 **Azure 開發**工作負載，如下所示：

![Azure 開發工作負載](./media/stream-analytics-tools-for-vs/stream-analytics-tools-for-vs-2017-install-02.png)


### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
* 安裝 Visual Studio 2015 或 Visual Studio 2013 Update 4。 支援 Enterprise (Ultimate/Premium)、Professional 和 Community 版本。 不支援 Express 版本。 
* 使用 [Web Platform Installer](http://www.microsoft.com/web/downloads/platform.aspx) 安裝 Microsoft Azure SDK for .NET 2.7.1 版或更新版本。
* 安裝 [Visual Studio 適用的 Azure 串流分析工具](http://aka.ms/asatoolsvs)。



## <a name="update"></a>更新

### <a name="visual-studio-2017"></a>Visual Studio 2017
新版本提醒會顯示在 Visual Studio 通知中。 

### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
已安裝之 Visual Studio 適用的串流分析工具會自動檢查新版本。 請依照快顯視窗中的指示來安裝最新的版本。 


## <a name="uninstall"></a>解除安裝

### <a name="visual-studio-2017"></a>Visual Studio 2017
按兩下 Visual Studio 安裝程式，然後選取 [修改]。 從 [資料儲存和處理] 或 [Azure 開發] 工作負載取消核取 [Azure Data Lake 和串流分析工作] 核取方塊。

### <a name="visual-studio-2013-2015"></a>Visual Studio 2013、2015
移至控制台，並解除安裝 **Visual Studio 適用的 Microsoft Azure Data Lake 和串流分析工具**。





