---
title: ACSD-48417：建立排程變更後發生SQL錯誤
description: 套用ACSD-48417修補程式來修正Adobe Commerce問題，建立產品的排程變更並儲存另一個產品後，出現SQL錯誤。
exl-id: 2bbf3bb5-dec8-43b3-81f1-be0dc53d1f46
feature: Storage
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417：建立排程變更後發生SQL錯誤

ACSD-48417修補程式修正建立產品的排程變更並儲存另一個產品後出現SQL錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48417。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立產品的排程變更並儲存另一個產品後，會出現SQL錯誤。

<u>要再現的步驟</u>：

1. 安裝Magento 2.4 — 開發EE +範例資料。
1. 前往管理面板> **[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 編輯任何產品（例如Joust Duffle Bag [SKU： 24-MB01]）。
1. 排程新的更新：
   * 選取&#x200B;**[!UICONTROL Save as a New Update]**
   * 更新名稱： &quot;Update 1&quot;
   * 開始日期：目前時間+1分鐘
   * 結束日期：目前時間+1小時
   * 將產品名稱修改為：「Joust Duffle Bag 2」
   * 儲存產品。
1. 前往CLI並執行cron，然後等待套用排程。

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. 再次移至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;並編輯任何可設定的產品（例如Chaz Kangeroo Hoodie [SKU： MH01]）。

   * 停用所有變體。 移至[動作]欄> **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**。
   * 儲存可設定的。

<u>預期結果</u>：

儲存產品時沒有錯誤。

<u>實際結果</u>：

發生下列錯誤：

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：我們的支援知識庫提供自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
