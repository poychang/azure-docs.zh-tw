---
title: Azure CLI 範例 - Azure SignalR Service | Microsoft Docs
description: Azure CLI 範例 - Azure SignalR Service
services: signalr
documentationcenter: signalr
author: wesmc7777
manager: cfowler
editor: ''
tags: azure-service-management
ms.service: signalr
ms.devlang: na
ms.topic: sample
ms.tgt_pltfrm: na
ms.workload: signalr
ms.date: 04/20/2018
ms.author: wesmc
ms.custom: mvc
ms.openlocfilehash: 6e76ee89160c84ff0f1033590d14c288f023f201
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="azure-cli-samples"></a>Azure CLI 範例

下表包含可針對 Azure SignalR Service 使用 Azure CLI 的 Bash 指令碼連結。

| | |
|-|-|
|**建立**||
| [建立新的 SignalR 服務和資源群組](scripts/signalr-cli-create-service.md) | 在資源群組中建立具有隨機名稱的新 Azure SignalR Service 資源。  |
|**整合**||
| [建立新 SignalR Service 和設定為使用 SignalR 的 Web 應用程式](scripts/signalr-cli-create-with-app-service.md) | 在資源群組中建立具有隨機名稱的新 Azure SignalR Service 資源。 並且新增 Web 應用程式和 App Service 方案來裝載 ASP.NET Core Web 應用程式，以使用 SignalR Service。 Web 應用程式會透過「應用程式設定」來設定，以連線至新的 SignalR 服務資源。 |
| [建立新 SignalR Service 和設定為使用 SignalR 與 GitHub OAuth 的 Web 應用程式](scripts/signalr-cli-create-with-app-service-github-oauth.md) | 在資源群組中建立具有隨機名稱的新 Azure SignalR Service 資源。 並且新增 Azure Web 應用程式和主控方案來裝載 ASP.NET Core Web 應用程式，以使用 SignalR Service。 Web 應用程式會透過應用程式設定來設定，以使用連接字串連線至新的 SignalR 服務資源，以及使用用戶端密碼來支援 [GitHub 驗證](https://developer.github.com/v3/guides/basics-of-authentication/)，如[驗證教學課程](signalr-authenticate-oauth.md)所述。 Web 應用程式也會設定為使用本機 Git 存放庫部署來源。 |
| | |
