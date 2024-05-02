---
title: 'ACSD-47937：由於應用程式層級的快取，未傳送價格下降通知'
description: 套用ACSD-47937修補程式，修正Adobe Commerce因應用程式層級的快取而不一定傳送降價通知的問題。
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937：由於應用程式層級的快取，未傳送降價通知

ACSD-47937修補程式修正了因應用程式層級的快取而未一定傳送降價通知的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.26。 修補程式ID為ACSD-47937。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.4和2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4、2.4.5和2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶不會因為後續產品價格變更而收到產品價格下降電子郵件。

<u>要再現的步驟</u>：

1. 啟用 **[!UICONTROL Product Alert]** 針對兩者 *[!UICONTROL Price Changes]* 和 *[!UICONTROL Back in Stock]* 在 **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. 啟用 **[!UICONTROL Display Out of Stock Products]**.
1. 建立數量= 0的簡單產品(ABC)。
1. 從店面建立客戶並訂閱上述產品，以取得價格下降的產品警示。
1. 開始向客戶發出產品警示。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. 卸除ABC產品的價格。
1. 觸發產品警報確認。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 再次降低ABC產品的價格。
1. 觸發產品警報確認。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>如果您不熟悉 [!DNL n98] 工具，然後您可以 `bin/magento cron:run command` 照常操作並監視 `cron_schedule` 表格以確定 `catalog_product_alert` 工作取得成功狀態。

<u>預期結果</u>：

已傳送第二個降價電子郵件。

<u>實際結果</u>：

第二個降價電子郵件未傳送。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
