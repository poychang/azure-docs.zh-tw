---
title: 遠端監視解決方案中的裝置管理 - Azure | Microsoft Docs
description: 本教學課程會示範如何管理連線到遠端監視解決方案的裝置。
services: iot-suite
suite: iot-suite
author: dominicbetts
manager: timlt
ms.author: dobett
ms.service: iot-suite
ms.date: 05/01/2018
ms.topic: article
ms.devlang: NA
ms.tgt_pltfrm: NA
ms.workload: NA
ms.openlocfilehash: 3ad6de2a0ebcd257ca90ea3c5c69988d4c1afd7a
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2018
---
# <a name="manage-and-configure-your-devices"></a>管理及設定您的裝置

本教學課程會示範遠端監視解決方案的裝置管理功能。 為介紹這些功能，本教學課程會使用 Contoso IoT 應用程式中的情節。

Contoso 已排序新的機制，延伸其中一個設備來增加輸出。 當您等待傳遞新的機制時，您需要執行模擬來驗證您解決方案的行為。 身為操作員，您需要管理和設定遠端監視解決方案中的裝置。

為提供可延伸的方式來管理和設定裝置，遠端監視解決方案會使用 IoT 中樞功能，例如[作業](../iot-hub/iot-hub-devguide-jobs.md)和[直接方法](../iot-hub/iot-hub-devguide-direct-methods.md)。 若要了解裝置開發人員如何在實體裝置上實作方法，請參閱[自訂遠端監視解決方案加速器](iot-accelerators-remote-monitoring-customize.md)。

在本教學課程中，您了解如何：

>[!div class="checklist"]
> * 佈建模擬的裝置。
> * 測試模擬的裝置。
> * 從解決方案中呼叫裝置方法。
> * 重新設定裝置。

## <a name="prerequisites"></a>先決條件

若要依循本教學課程進行操作，您需要在 Azure 訂用帳戶中有一個已部署的遠端監視解決方案執行個體。

如果您尚未部署遠端監視解決方案，應該先完成[部署遠端監視解決方案加速器](iot-accelerators-remote-monitoring-deploy.md)教學課程。

## <a name="add-a-simulated-device"></a>新增模擬裝置

瀏覽至解決方案中的 [裝置] 頁面，然後選擇 [+ 新增裝置]。 在 [新增裝置] 面板中，選擇 [模擬]：

![佈建模擬的裝置](./media/iot-accelerators-remote-monitoring-manage/devicesprovision.png)

將要佈建的裝置數目設定保留為 **1**。 選擇 [故障引擎] 裝置型號，然後選擇 [套用]以建立模擬裝置：

![佈建模擬的引擎裝置](./media/iot-accelerators-remote-monitoring-manage/devicesprovisionengine.png)

若要了解如何佈建「實體」裝置，請參閱[將裝置連線到遠端監視解決方案加速器](iot-accelerators-connecting-devices-node.md)。

## <a name="test-the-simulated-device"></a>測試模擬的裝置

若要檢視新模擬裝置的詳細資料，請在 [裝置] 頁面的裝置清單中加以選取。 您裝置的相關資訊會顯示在 [裝置詳細資料] 面板中：

![檢視新的模擬引擎裝置](./media/iot-accelerators-remote-monitoring-manage/devicesviewnew.png)

在 [裝置詳細資料] 中，確認新的裝置正在傳送遙測。 若要從您裝置檢視不同的遙測串流，請選擇遙測名稱，例如 **震動**：

![選取要檢視的遙測串流](./media/iot-accelerators-remote-monitoring-manage/devicesvibration.png)

[裝置詳細資料] 面板會顯示關於裝置的其他資訊 (例如標記值)、它支援的方法，以及裝置所報告的屬性。

若要檢視詳細的診斷，請向下捲動以檢視 [診斷]。

## <a name="act-on-a-device"></a>在裝置上採取行動

若要在一或多個裝置上採取行動，請在裝置清單中進行選取，然後選擇 [作業]。 **引擎**裝置型號會指定裝置必須支援的三種方法：

![引擎方法](./media/iot-accelerators-remote-monitoring-manage/devicesmethods.png)

選擇 [FillTank]、將作業名稱設定為 **FillEngineTank**，然後選擇 [套用]：

![排程重新啟動方法](./media/iot-accelerators-remote-monitoring-manage/devicesrestartengine.png)

若要在 [維護] 頁面上追蹤作業的狀態，請選擇 [作業]：

![監視排程作業](./media/iot-accelerators-remote-monitoring-manage/maintenancerestart.png)

### <a name="methods-in-other-devices"></a>其他裝置中的方法

當您探索不同的模擬裝置類型時，會看到其他裝置類型支援不同的方法。 在使用實體裝置的部署中，裝置型號會指定裝置應該支援的方法。 一般而言，裝置開發人員會負責開發程式碼，讓裝置採取動作來回應方法呼叫。

若要排程可在多個裝置上執行的方法，您可以在 [裝置] 頁面的清單中選取多個裝置。 [作業] 面板會顯示所有選取裝置通用的方法類型。

## <a name="reconfigure-a-device"></a>重新設定裝置

若要變更裝置的設定，可在 [裝置] 頁面的裝置清單中選取它，接著選擇 [作業]，然後選擇 [重新設定]。 [作業] 面板會顯示您可以變更的所選裝置屬性值：

![重新設定裝置](./media/iot-accelerators-remote-monitoring-manage/devicesreconfigure.png)

若要進行變更，請新增作業的名稱、更新屬性值，然後選擇 [套用]：

![更新裝置屬性值](./media/iot-accelerators-remote-monitoring-manage/devicesreconfigurephysical.png)

若要在 [維護] 頁面上追蹤作業的狀態，請選擇 [作業]。

## <a name="next-steps"></a>後續步驟

本教學課程已示範如何：

<!-- Repeat task list from intro -->
>[!div class="checklist"]
> * 佈建模擬的裝置。
> * 測試模擬的裝置。
> * 從解決方案中呼叫裝置方法。
> * 重新設定裝置。

既然您已了解如何管理裝置，建議的後續步驟是了解如何：

* [針對裝置問題進行疑難排解和補救](iot-accelerators-remote-monitoring-maintain.md)。
* [使用模擬裝置來測試您的解決方案](iot-accelerators-remote-monitoring-test.md)。
* [將裝置連線到遠端監視解決方案加速器](iot-accelerators-connecting-devices-node.md)。

<!-- Next tutorials in the sequence -->