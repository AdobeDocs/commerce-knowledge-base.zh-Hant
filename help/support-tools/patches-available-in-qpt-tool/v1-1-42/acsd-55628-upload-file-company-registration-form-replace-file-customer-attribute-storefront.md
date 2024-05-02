---
title: 'ACSD-55628：在公司登錄檔單上傳檔案；取代店面中客戶屬性的檔案'
description: 套用ACSD-55628修補程式，修正上傳公司登錄檔格中的檔案並取代店面中客戶屬性的檔案時，所發生的Adobe Commerce問題。
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: ca85b459-f72b-4663-85af-1f793935fe7e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-55628：在公司登錄檔單上上傳檔案；取代店面中客戶屬性的檔案

>[!NOTE]
>
>此修補程式會取代 [ACSD-51240](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

ACSD-55628修補程式修正了在公司登錄檔單上上傳檔案，以及在店面取代客戶屬性檔案的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.42。 修補程式ID為ACSD-55628。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p2 &lt; 2.4.5和2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

無法取代店面中客戶屬性的檔案。

<u>要再現的步驟</u>：

1. 使用下列值建立新的客戶屬性：

   * *[!UICONTROL Input Type]*： *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*： *是*
   * *[!UICONTROL Forms to Use In]*： *所有可用選項*

1. 以客戶身分登入店面並開啟 **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. 上傳新影像並儲存。
1. 重新整理頁面。 刪除舊影像並上傳新影像。 儲存變更。

<u>預期結果</u>：

新影像即會儲存。

<u>實際結果</u>：

仍會顯示舊影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
