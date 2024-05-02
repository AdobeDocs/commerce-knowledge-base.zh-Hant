---
title: '''ACSD-48313： [!UICONTROL configurable_variations] 如果屬性值包含逗號''，則不剖析欄'
description: 套用ACSD-48313修補程式以修正Adobe Commerce問題，其中 [!UICONTROL configurable_variations] 如果屬性值包含逗號，則不會剖析欄。
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313： **[!UICONTROL configurable_variations]** 如果屬性值包含逗號，則不剖析欄

ACSD-48313修補程式可解決 **[!UICONTROL configurable_variations]** 如果屬性值包含逗號，則不會剖析欄。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.25。 修補程式ID為ACSD-48313。 尚未提供將修正此問題的版本。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯出可設定產品後，由於的格式問題，無法再次匯入產生的檔案 **[!UICONTROL configurable_variations]** 屬性。 當屬性選項包含逗號時，就會發生這種情況。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 並建立新屬性 _大小_：
1. 存放區所有者的目錄輸入型別： **[!UICONTROL Dropdown]**.
1. 建立包含逗號在內的選項，例如：
   * 10,2公分
   * 15,5公分
1. **[!UICONTROL Advanced Attribute Properties]**  — 範圍： _全域_.
1. 使用「建立組態」功能建立新的可設定產品。
1. 選取上述屬性 _大小_ 以及包含逗號的兩個選項。
1. 前往 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** 並建立新的產品匯出（執行cron以觸發CSV檔案的產生）。
1. 前往 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** 並嘗試重新匯入上述建立的相同CSV檔案。

<u>預期結果</u>：

使用者應該能夠匯入檔案。

<u>實際結果</u>：

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。


## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
