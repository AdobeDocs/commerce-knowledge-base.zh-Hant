---
title: 'ACSD-52786：目錄規則*[!UICONTROL SKU is]*適用於以SKU開頭的所有產品'
description: 套用ACSD-52786修補程式，修正目錄規則條件為*的Adobe Commerce問題[!UICONTROL SKU is]*適用於從指定SKU開始的所有產品。
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786：目錄規則»*[!UICONTROL SKU is]*&quot;適用於所有從SKU開始的產品

ACSD-52786修補程式修正了目錄規則條件的問題 *[!UICONTROL SKU is]* 適用於從特定SKU開始的所有產品。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.35。 修補程式ID為ACSD-52786。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

目錄規則條件 *[!UICONTROL SKU is]* 適用於從特定SKU開始的所有產品。

<u>要再現的步驟</u>：

1. 建立兩個產品，一個使用SKU「24」，另一個使用SKU「24-MB01」。
1. 瀏覽至 **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. 套用下列條件：
   * *[!UICONTROL If **&#x200B;全部&#x200B;**這些條件中有** TRUE **]*： *[!UICONTROL SKU is 24]*
1. 設定動作中的任何折扣金額。
1. 按一下 **[!UICONTROL Save and Apply]**.
1. 排清快取。
1. 前往店面，檢視24-MB01的價格。

<u>預期結果</u>：

目錄規則僅套用至SKU等於24的單一產品。

<u>實際結果</u>：

目錄規則條件 *[!UICONTROL SKU is]* 適用於從特定SKU開始的所有產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
