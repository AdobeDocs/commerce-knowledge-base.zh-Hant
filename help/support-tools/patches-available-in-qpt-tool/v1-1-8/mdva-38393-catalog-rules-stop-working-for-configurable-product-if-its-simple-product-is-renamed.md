---
title: 'MDVA-38393：如果簡單產品重新命名，目錄規則會停止用於可設定的產品'
description: MDVA-38393修補程式修正重新命名簡單產品時，目錄規則無法對可設定產品運作的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-38393。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393：如果簡單產品重新命名，目錄規則會停止對可設定產品運作

MDVA-38393修補程式修正重新命名簡單產品時，目錄規則無法對可設定產品運作的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8時，即可使用此修補程式。 修補程式ID為MDVA-38393。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果簡單產品重新命名，目錄規則會停止用於可設定產品。

<u>要再現的步驟</u>：

1. 使用相關聯的簡單產品建立可設定的產品。
1. 建立類別。
1. 僅將可設定的產品指派給新類別。
1. 建立新目錄規則：
   * 條件=類別包含\&lt;新類別識別碼>
   * 動作= 50%折扣
   * 使用中=是
1. 執行重新索引。
1. 檢查前端的可設定產品（應套用折扣）。
1. 檢查`catalogrule_product`表格（簡單產品應該有折扣）。
1. 前往「管理員」並變更簡單產品的名稱。 這會將記錄新增至`catalogrule_product_cl`資料表。
1. 執行cron或`bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`命令。
1. 檢查`catalogrule_product`資料表。

<u>預期結果</u>：

可設定的產品有折扣。

<u>實際結果</u>：

* `catalogrule_product`表格中遺漏為簡單產品建立的折扣記錄。
* 前端的可設定產品具有完整的原始價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
