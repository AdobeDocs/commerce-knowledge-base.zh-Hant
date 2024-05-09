---
title: 如果Cloud UI有「記錄片段」錯誤，則檢查部署記錄
description: 本文針對下列問題提供解決方案：嘗試在雲端專案UI上檢視部署記錄檔時，雲端基礎結構上的Adobe Commerce會顯示*記錄檔片段因為太長*錯誤訊息。
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 71bec5b99063d771982f6dcab111b9e5a4aaec69
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 如果雲端UI有，則檢查部署記錄 *記錄已剪取* 錯誤

本文提供雲端基礎結構UI上Adobe Commerce顯示的問題 *記錄已剪取，因為太長* 嘗試在雲端專案UI上檢視部署記錄檔時出現錯誤訊息。 (不適用於 [Adobe Commerce Cloud Console](https://console.adobecommerce.com/).)

## 受影響的產品

雲端基礎結構上的Adobe Commerce （所有支援的版本）

## 問題

嘗試在雲端專案UI上檢視部署記錄時，雲端基礎結構上的Adobe Commerce UI會顯示下列錯誤訊息： *記錄已剪取，因為太長*.

## 要再現的步驟

1. 前往專案URL，然後按一下 **狀態** 有問題的部署的。
1. 如果記錄太長而無法顯示在UI中，則會顯示錯誤訊息： *記錄已剪取，因為太長*.

## 原因

請注意，UI中顯示的記錄不應被視為真實來源，尤其是如果您在部署列為「成功」狀態後發現網站未回應或無法正常運作。 您也應該使用伺服器上的記錄進行驗證。 請參閱 [檢視和管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) （位於我們的開發人員檔案中）。

## 解決方案

1. 確定您擁有 [Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) 已安裝在您的本機環境中。
1. 執行以下命令：

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. 它會傳回類似以下內容的輸出：

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. 複製受影響部署的活動ID，然後執行命令：

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   檢查失敗部署記錄的範例：

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## 開發人員檔案中的相關閱讀：

* [雲端基礎結構上的Adobe Commerce >建置和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [雲端基礎結構上的Adobe Commerce >檢視和管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
