---
title: PHP版本整備檢查問題
description: 本文介紹使用Web安裝精靈在內部部署Adobe Commerce安裝/升級時，可能遇到的PHP版本問題解決方案。
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# PHP版本整備檢查問題

本文介紹使用Web安裝精靈在內部部署Adobe Commerce安裝/升級時，可能遇到的PHP版本問題解決方案。

>[!WARNING]
>
>在雲端基礎結構上的Adobe Commerce上，請注意，服務升級無法在未提前48個營業時間通知我們的基礎結構團隊的情況下推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，必須在變更需要投入生產前48小時 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 詳細說明您需要的服務升級，並說明您想要啟動升級程式的時間。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 不支援的PHP版本

### 問題

檢查失敗，因為您使用的是不受支援的PHP版本。

### 解決方案

若要解決此問題，請使用開發人員檔案中列出的其中一個支援版本 [2.3.x系統需求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) 和 [2.2.x系統需求](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## PHP整備檢查不顯示

### 問題

PHP整備檢查不會顯示PHP版本，如下圖所示。
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### 解決方案

這是cron作業設定不正確的症狀。 如需詳細資訊，請參閱 [設定cron工作](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) （位於我們的開發人員檔案中）。

## PHP版本不正確

### 問題

檢查報告不正確的PHP版本。 通常，只有安裝了多個PHP版本的進階使用者才會發生這種情況。 在某些情況下，整備檢查會失敗；在其他情況下，可能會通過。

如果整備檢查報告的PHP版本不正確，則是PHP CLI和Web伺服器外掛程式之間PHP版本不符的結果。 Adobe Commerce會要求您使用 *一個版本* PHP的CLI （執行cron）和Web伺服器(執行Commerce管理員、元件管理員和系統升級)。

### 解決方案

如果您有此問題，我們假設您是進階使用者，可能在您的系統上安裝了多個版本的PHP。

若要解決此問題，請嘗試下列步驟：

* 重新啟動Web伺服器或php-fm。
* 檢查 `$PATH` PHP的多個路徑的環境變數。
* 使用 `which php` 命令以找出路徑中的第一個PHP可執行檔；如果不正確，請將其移除或建立指向正確PHP版本的符號連結。
* 使用 [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) 頁面以收集更多資訊。
* 請根據我們的系統需求，在我們的開發人員檔案中確定您執行的是支援的PHP版本：
   * [Adobe Commerce 2.3.x系統需求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Adobe Commerce 2.2.x系統需求](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* 為PHP命令列和PHP Web伺服器外掛程式設定相同的PHP設定，如中所述 [PHP組態選項](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) （位於我們的開發人員檔案中）。
