---
title: 部署後.magento.env.yaml變更未顯示在env.php中
description: 本文針對.magento.env.yaml檔案的變更在部署後未反映在app/etc/env.php中的問題提供解決方案。
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 部署後.magento.env.yaml變更未顯示在env.php中

>[!NOTE]
>
>如果您有此問題，請升級至ece-tools 2002.1.5進行修正。 2002.1.5可在每次部署時重設opcache，因此永遠不需要變更設定 `opcache.enable_cli=1`. 如果您不想升級，則必須按照解決方案中所述進行因應步驟。

本文提供問題的解決方案，其中變更 `.magento.env.yaml` 檔案未反映在 `app/etc/env.php` 部署後。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce (全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf))。

## 問題

在中進行的變更 `.magento.env.yaml` 檔案不會影響 `app/etc/env.php` 已產生。

<u>要再現的步驟：</u>

變更中的任何值 `.magento.env.yaml` 並推送至伺服器，其應定義目前取出環境的組態（和部署設定）。 如需相關步驟，請參閱 [環境變數>部署變數](https://devdocs.magento.com/cloud/env/variables-deploy.html) （位於我們的開發人員檔案中）。

<u>預期結果：</u>

在中進行的變更 `.magento.env.yaml` 檔案影響 `app/etc/env.php` 已產生。

<u>實際結果：</u>

這些變更對 `app/etc/env.php` 部署後的變數。

## 原因

問題的原因可能是 `opcache.enable_cli` 中的引數 `php.ini` 檔案。

## 解決方案

1. 檢查系統是否根據 [Adobe Commerce效能最佳實務>軟體建議](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. 檢查情況 `opcache.enable_cli` 中的指示詞 `php.ini` 設為 `0` 透過執行： `php -i | grep opcache.enable_cli`
1. 如果輸出結果類似於 `opcache.enable_cli=1` ，編輯 `php.ini` 檔案及變更 `opcache.enable_cli=1` 至 `opcache.enable_cli=0`
1. 重新部署專案。

## 相關閱讀

* [適用於Adobe Commerce的Cloud >建置和部署](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
