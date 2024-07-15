---
title: 將資料和檔案生產同步至測試環境，或將測試環境同步至整合環境
description: 本文說明如何在雲端基礎結構上同步化您的生產環境到Adobe Commerce上的中繼環境；這是不可能的。
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: ef294ddc9c4a12b06ce7738cb4702253dd892f3b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 將資料和檔案生產同步至測試環境，或將測試環境同步至整合環境

本文說明如何同步化您的生產環境，直到雲端基礎結構上的Adobe Commerce上的中繼環境；這是無法透過使用者介面或Magento雲端CLI完成。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.x、2.4.x

## 將資料從一個環境同步到另一個環境

若要同步資料，您必須手動從來源環境傾印資料庫。 若要將資料傳輸至另一個環境，您必須將來源傾印上傳至目標環境並匯入它。 如需詳細資訊，請參閱我們的開發人員檔案中的[將Adobe Commerce程式碼匯入雲端專案>匯入Adobe Commerce資料庫](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html)。

對於雲端基礎結構上的Adobe Commerce Pro計畫架構，您還可以從測試和生產同步到您的整合主分支。 此同步僅提取和推送程式碼，不會提取資料。 若要同步資料，您必須傾印資料庫資料，並將其推送到另一個環境的資料庫。

>[!WARNING]
>
>無法在Pro Staging和Production叢集中同步資料庫。

## 將檔案從一個環境同步到另一個環境

若要將檔案從一個環境同步到另一個環境，請使用`rsync`命令。 如需詳細資訊，請參閱開發人員檔案中的[部署程式碼並移轉靜態檔案與資料>使用rsync](https://devdocs.magento.com/cloud/live/stage-prod-migrate.html#migrate-files-using-rsync)移轉檔案。

>[!NOTE]
>
>如果您想要將程式碼從整合約步到測試環境，您必須從整合分支執行此作業。 如需相關步驟，請參閱我們的開發人員檔案中的[從環境的父系](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment)同步。
