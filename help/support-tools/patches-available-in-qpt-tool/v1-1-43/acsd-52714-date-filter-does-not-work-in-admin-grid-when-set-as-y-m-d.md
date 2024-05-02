---
title: 「ACSD-52714：日期篩選器設定為y-m-d時無法在管理格線中運作」
description: 套用ACSD-52714修補程式，修正日期格式設為y-m-d時，日期篩選器在管理格線中無法運作的Adobe Commerce問題。
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714：設定為y-m-d時，日期篩選器在管理格線中無法運作

ACSD-52714修補程式修正日期格式設為y-m-d時，日期篩選器在管理格線中無法運作的問題。此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.43。 修補程式ID為ACSD-52714。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

日期格式設為y-m-d時，日期篩選器無法在管理網格中運作。

<u>要再現的步驟</u>：

1. 安裝乾淨的Adobe Commerce。
1. 編輯
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
檔案並新增
   `<dateFormat>Y-MM-dd</dateFormat>`
至
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
在標籤下
   `<dataType>date</dataType>`

1. 排清快取 `bin/magento c:f`.
1. 登入管理員並從建立新客戶 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * 起始：目前日期減1天
   * 至：目前日期

1. 按一下 **[!UICONTROL Apply Filters]**.

<u>預期結果</u>：

格線的日期篩選器不論地區設定為何，皆可正常運作。

<u>實際結果</u>：

系統會顯示下列訊息： *找不到任何記錄*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
