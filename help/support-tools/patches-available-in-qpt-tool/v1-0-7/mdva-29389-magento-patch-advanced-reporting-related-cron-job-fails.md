---
title: 'MDVA-29389：進階報告相關cron工作失敗'
description: 「MDVA-29389修補程式修正進階報表中，『analytics_collect_data』 cronjob指出：「*Port必須在主機引數中設定（如localhost：3306）*」的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 修補程式ID為MDVA-29389。 Adobe Commerce 2.4.2已修正問題。
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389：進階報告相關cron工作失敗

MDVA-29389修補程式修正進階報告的問題，其中 `analytics_collect_data` cronjob說：「*連線埠必須在主機引數（如localhost：3306）中設定*「。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.7。 修補程式ID為MDVA-29389。 Adobe Commerce 2.4.2已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.3.4。

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 在您的Adobe Commerce執行個體中，啟用進階報告。
1. 執行以下查詢，以在DB中插入analytics/general/token值：

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. 開啟您的env.php，並以下列格式在DB組態中將連線埠加入主機引數： `'host' => 'hostname:port',`
1. 清除快取。
1. 執行 `analytics_collect_data` cron工作。

<u>預期結果</u>：

此 `analytics_collect_data` 使用預設或非預設連線埠連線至env.php中的MySQL時，工作會順利執行。

<u>實際結果</u>：

此 `analytics_collect_data` 工作擲回錯誤»*連線埠必須在主機引數（如localhost：3306）中設定*&#39;&#39;使用非預設連線埠連線到env.php中的MySQL時。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
