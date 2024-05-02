---
title: 「ACSD-46618：產品清單Widget針對登入的客戶顯示不正確的快取價格」
description: 套用修補程式，修正Adobe Commerce產品清單Widget對登入客戶顯示錯誤快取價格的問題。
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618：產品清單Widget針對登入的客戶顯示不正確的快取價格

ACSD-46618修補程式解決產品清單Widget針對登入客戶顯示不正確快取價格的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 已安裝1.1.21。 修補程式ID為ACSD-46618。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**
* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

ACSD-46618修補程式解決產品清單Widget針對登入客戶顯示不正確快取價格的問題。

<u>要再現的步驟</u>：

1. 在「Adobe Commerce管理員」中，選取 **[!UICONTROL Stores]**，然後 **[!UICONTROL Configuration]**，展開 **[!UICONTROL Sales]**，並選取 **[!UICONTROL Tax]**. 更新稅捐設定以顯示含稅與不含稅的價格。
1. 設定 **[!UICONTROL Enable Cross Border Trade]** = _是_.
1. 建立只適用於美國的稅捐規則。
1. 將Widget新增至包含多項產品的首頁。
1. 建立兩個具有美國地址和非美國地址的客戶。
1. 從店面使用美國客戶登入。 請確定已快取頁面。
1. 觀察首頁Widget中顯示的價格。
1. 登出並使用非美國客戶登入。

<u>預期結果</u>：

首頁Widget中顯示的價格會與客戶地址相對應。

<u>實際結果</u>：

首頁Widget會顯示非美國客戶使用稅捐的價格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
