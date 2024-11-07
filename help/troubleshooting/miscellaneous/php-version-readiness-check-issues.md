---
title: PHP版本整備檢查問題
description: 本文介紹使用Web安裝精靈在內部部署Adobe Commerce安裝/升級時，可能遇到的PHP版本問題解決方案。
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# PHP版本整備檢查問題

本文介紹使用Web安裝精靈在內部部署Adobe Commerce安裝/升級時，可能遇到的PHP版本問題解決方案。

>[!WARNING]
>
>在雲端基礎結構上的Adobe Commerce上，請注意，服務升級無法在未提前48個營業時間通知我們的基礎結構團隊的情況下推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 不支援的PHP版本

### 問題

檢查失敗，因為您使用的是不受支援的PHP版本。

### 解決方案

若要解決此問題，請使用開發人員檔案[2.3.x系統需求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)和[2.2.x系統需求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)中列出的支援版本之一。

## PHP整備檢查不顯示

### 問題

PHP整備檢查不會顯示PHP版本，如下圖所示。
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### 解決方案

這是cron作業設定不正確的症狀。 如需詳細資訊，請參閱我們的開發人員檔案中的[設定cron工作](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration)。

## PHP版本不正確

### 問題

檢查報告不正確的PHP版本。 通常，只有安裝了多個PHP版本的進階使用者才會發生這種情況。 在某些情況下，整備檢查會失敗；在其他情況下，可能會通過。

如果整備檢查報告的PHP版本不正確，則是PHP CLI和Web伺服器外掛程式之間PHP版本不符的結果。 Adobe Commerce需要您針對CLI （執行cron）和Web伺服器(執行Commerce管理、元件管理員和系統升級)使用&#x200B;*一個PHP版本*。

### 解決方案

如果您有此問題，我們假設您是進階使用者，可能在您的系統上安裝了多個版本的PHP。

若要解決此問題，請嘗試下列步驟：

* 重新啟動Web伺服器或php-fm。
* 檢查`$PATH`環境變數以取得多個PHP路徑。
* 使用`which php`命令找出您路徑中的第一個PHP可執行檔；如果不正確，請移除它或建立指向正確PHP版本的符號連結。
* 使用[`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software)頁面來收集更多資訊。
* 請根據我們的系統需求，在我們的開發人員檔案中確定您執行的是支援的PHP版本：
   * [Adobe Commerce系統需求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
* 為PHP命令列和PHP Web伺服器外掛程式設定相同的PHP設定，如開發人員檔案中的[PHP組態選項](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#php-settings)中所述。
