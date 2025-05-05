---
title: 如果Cloud UI有「記錄片段」錯誤，則檢查部署記錄
description: 本文針對下列問題提供解決方案：嘗試在雲端專案UI上檢視部署記錄檔時，雲端基礎結構上的Adobe Commerce會顯示*記錄檔片段因為太長*錯誤訊息。
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 846df05668b357b9088bcaf605a75c45ab10f1ae
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 正在檢查Cloud UI是否有&#x200B;*記錄檔片段*&#x200B;錯誤

本文針對雲端基礎結構UI上的Adobe Commerce顯示&#x200B;*記錄檔片段的問題，提供解決方案，因為嘗試在雲端專案UI上檢視部署記錄檔時，記錄檔片段太長*&#x200B;錯誤訊息。 (不適用於[Adobe Commerce Cloud主控台](https://console.adobecommerce.com/)。)

## 受影響的產品

雲端基礎結構上的Adobe Commerce （所有支援的版本）

## 問題

嘗試在雲端專案UI上檢視部署記錄檔時，雲端基礎結構UI上的Adobe Commerce會顯示下列錯誤訊息： *記錄檔片段因為太長*。

## 要再現的步驟

1. 前往專案URL，然後按一下相關部署的&#x200B;**狀態**。
1. 如果記錄檔太長，無法在UI中顯示，則會顯示錯誤訊息： *記錄檔片段太長*。

## 原因

請注意，UI中顯示的記錄不應被視為真實來源，尤其是如果您在部署列為「成功」狀態後發現網站未回應或無法正常運作。 您也應該使用伺服器上的記錄進行驗證。 請參閱我們的開發人員檔案中的[檢視及管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hant)。

## 解決方案

1. 請確定您已在本機環境中安裝[Magento雲端CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=zh-Hant)。
1. 您可以執行下列任一命令：

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. 這類變數會傳回類似下列的輸出：

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

* 雲端基礎結構上的[Adobe Commerce >建置和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=zh-Hant)
* 雲端基礎結構上的[Adobe Commerce >檢視及管理記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hant)
