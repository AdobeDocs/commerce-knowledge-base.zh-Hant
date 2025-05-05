---
title: 疑難排解cron
description: 本文針對Adobe Commerce內部部署產品中的cron問題，提供疑難排解解決方案。
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# 疑難排解cron

本文針對Adobe Commerce內部部署產品中的cron問題，提供疑難排解解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 問題

## 以下是cron問題的症狀：

* 您的更新或升級永遠不會執行；它保持在`pending`狀態。
* 即使已正確設定PHP設定`$HTTP_RAW_POST_DATA`，也會顯示錯誤訊息。
* cron整備檢查失敗。 可能的錯誤包括不可寫入的路徑以及未設定的cron。 範例如下：

  ![upgr-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* PHP整備檢查不會顯示PHP版本，如下圖所示。

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* Commerce管理員中會顯示下列錯誤：

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

若要檢視錯誤，您可能需要按一下視窗頂端的&#x200B;**系統訊息**，如下所示：

![compman_sys-messages.png](assets/compman_sys-messages.png)

## 調查以找出原因 {#check-your-existing-crontab}

本節探討如何檢視cron目前是否正在執行，以及驗證其設定是否正確。

若要確認您的crontab是否已設定，請執行下列步驟：

1. 以[Magento檔案系統擁有者](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)身分登入或切換至您的Magento伺服器。
1. 檢視下列檔案是否存在：    `bash    ls -al <magento_root>/var/.setup_cronjob_status`。 如果檔案存在，則cron過去已順利執行。 如果檔案&#x200B;*不存在*，表示您尚未安裝Magento或沒有執行cron。 無論是上述哪一種情況，請繼續進行下一個步驟。
1. 取得有關cron的更多詳細資料。 以具有`root`許可權的使用者身分，輸入下列命令：    `bash    crontab -u <Magento file system owner name> -l`。 例如，在CentOS `bash    crontab -u magento_user -l`上。  如果尚未為使用者設定crontab，則會顯示以下訊息：    `terminal    no crontab for magento_user`。 您的crontab會告訴您下列內容：

   * 您正在使用的PHP二進位檔（在某些情況下，您有多個）
   * 您正在執行哪些Magentocron指令碼（尤其是這些指令碼的路徑）
   * cron記錄檔的位置

請參閱下列其中一個章節，以取得問題的解決方案。

## 解決方案

### 未設定crontab的解決方案 {#solution-crontab-not-set-up}

若要確認您的cron工作已正確設定，請參閱[設定cron工作](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/next-steps/configuration)。

### 從不正確的PHP二進位檔案執行cron的解決方案 {#solution-cron-running-from-incorrect-php-binary}

如果您的cron作業使用與Web伺服器外掛程式不同的PHP二進位檔，則可能會顯示PHP設定錯誤。 若要解決此問題，請為PHP命令列和PHP Web伺服器外掛程式設定相同的PHP設定。

如需有關PHP設定的詳細資訊，請參閱我們的開發人員檔案中的[必要的PHP設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/php-settings)。

### cron執行時發生錯誤的解決方案 {#solution-cron-running-with-errors}

嘗試手動執行每個命令，因為命令可能會顯示有用的錯誤訊息。 請參閱[設定cron工作](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/next-steps/configuration)。

>[!NOTE]
>
>您必須執行cron至少&#x200B;*兩次*，才能執行工作；第一次將工作排入佇列，第二次執行工作。
