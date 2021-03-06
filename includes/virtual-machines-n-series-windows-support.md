---
title: 包含檔案
description: 包含檔案
services: virtual-machines-windows
author: dlepow
ms.service: virtual-machines-windows
ms.topic: include
ms.date: 05/16/2018
ms.author: danlep
ms.custom: include file
ms.openlocfilehash: 9b36a8e90c20c8f0d08ca241e48e9306fb5b10f8
ms.sourcegitcommit: 96089449d17548263691d40e4f1e8f9557561197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34307500"
---
## <a name="supported-operating-systems-and-drivers"></a>支援的作業系統和驅動程式

### <a name="nc-ncv2-ncv3-and-nd-series---nvidia-tesla-cuda-drivers"></a>NC、NCv2、NCv3 和 ND 系列 - NVIDIA Tesla (CUDA) 驅動程式

下表提供的驅動程式下載連結，為發行當時的最新驅動程式。 如需最新的驅動程式，請瀏覽 [NVIDIA](http://www.nvidia.com/) 網站。

> [!TIP]
> 在 Windows Server VM 上手動安裝 CUDA 驅動程式的替代方案，就是部署 Azure [資料科學虛擬機器](../articles/machine-learning/data-science-virtual-machine/overview.md)映像。 適用於 Windows Server 2016 的 DSVM 版本會預先安裝 NVIDIA CUDA 驅動程式、CUDA 深度類神經網路程式庫和其他工具。


| 作業系統 | 驅動程式 |
| -------- |------------- |
| Windows Server 2016 | [391.29](http://us.download.nvidia.com/Windows/Quadro_Certified/391.29/391.29-tesla-desktop-winserver2016-international.exe) (.exe) |
| Windows Server 2012 R2 | [391.29](http://us.download.nvidia.com/Windows/Quadro_Certified/391.29/391.29-tesla-desktop-winserver2008-2012r2-64bit-international.exe) (.exe) |

### <a name="nv-series---nvidia-grid-drivers"></a>NV 系列 - NVIDIA GRID 驅動程式

Microsoft 會為 NV 虛擬機器重新發佈 NVIDIA GRID 驅動程式安裝程式。 僅可在 Azure NV 虛擬機器上安裝上述 GRID 驅動程式。 這些驅動程式包含在 Azure 的 GRID 虛擬 GPU 軟體的授權中。

| 作業系統 | 驅動程式 |
| -------- |------------- |
| Windows Server 2016<br/><br/>Windows 10 | [GRID 6.0 (391.03)](https://go.microsoft.com/fwlink/?linkid=836843) (.exe) |
| Windows Server 2012 R2 | [GRID 6.0 (391.03)](https://go.microsoft.com/fwlink/?linkid=836844) (.exe)  |