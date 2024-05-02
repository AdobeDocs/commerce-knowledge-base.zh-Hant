---
title: 「ACSD-46581：在購物車中選取國家/地區後，預估稅捐總計未更新」
description: 套用ACSD-46581修補程式以解決在購物車中切換國家/地區後稅率未更新的Adobe Commerce問題。
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581：在購物車中選取國家/地區後，預估稅捐總計未更新

此ACSD-46581修補程式解決在購物車中切換國家/地區後稅率未更新的問題。 只有在選取送貨方法後才會更新。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.21。 修補程式ID為ACSD-46581。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在購物車中切換國家/地區後，稅率沒有更新。

<u>要再現的步驟</u>：

1. 在Adobe Commerce Admin中，前往 **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. 建立新的稅率 **[!UICONTROL Country]** = _美國_， **[!UICONTROL State]** = _*_， **[!UICONTROL Rate]** = _8.25_.
1. 建立新的稅率 **[!UICONTROL Country]** = _印度_， **[!UICONTROL State]** = _*_， **[!UICONTROL Rate]** = _10_.
1. 使用美國和印度的稅率建立稅捐規則。
1. 前往 **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** 並啟用多種送貨方法(_平準率_ 和 _免運費_ 例如)。
1. 使用建立簡單產品 **[!UICONTROL Taxable Goods]** 稅捐類別。
1. 將產品新增至商店前方的購物車。
1. 開啟購物車並檢查稅捐金額。
1. 系統會套用美國的預設稅捐設定，並根據8.25%的稅率計算稅捐。
1. 切換至印度。

<u>預期結果</u>：

將國家切換至印度時，稅捐金額變更為10%。

<u>實際結果</u>：

在購物車的總計區段中，稅捐金額保持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
