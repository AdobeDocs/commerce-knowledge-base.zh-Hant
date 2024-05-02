---
title: 'MDVA-28409修補程式：Adobe Commerce網頁伺服器當機 — 記憶體不足'
description: MDVA-28409修補程式可解決移除報價的cron工作因必須處理大量專案而停止的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5時，即可使用此修補程式。
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409修補程式：Adobe Commerce網頁伺服器當機 — 記憶體不足

MDVA-28409修補程式可解決移除報價的cron工作因必須處理大量專案而停止的問題。 此修補程式適用於 [品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安裝v.1.0.5。

## 受影響的產品和版本

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5、 2.4.0

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

問題是由於工作嘗試處理的資料量，cron工作已用盡記憶體。 此問題的症狀包括MySQL的高磁碟使用率以及Web伺服器記憶體不足，導致效能緩慢。

<u>要再現的步驟：</u>

若要檢查是否有無法移除過期引號的cron作業，請執行以下查詢：

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>預期結果：</u>

的狀態 `sales_clean_quotes` cron工作應為 `success`.

<u>實際結果：</u>

的狀態 `sales_clean_quotes` cron工作是 `running` 或 `error`.

確認是否有無法移除過期引號的cron作業另一種方法是從對應查詢的輸出 **步驟1** (`executed_at`)的時間戳記，而非中任何記憶體錯誤的時間戳記。 `/var/log/cron.log`. 如果有一個cron作業無法處理資料量，您可能會看到類似以下的訊息：

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
