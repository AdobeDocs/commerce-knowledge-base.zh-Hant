---
title: 'MDVA-35286：將多個位址切換至Onepage簽出時發生錯誤'
description: MDVA-35286修補程式修正了客戶在購物車中捆綁產品，並從多個地址結帳切換至單一頁面結帳時出現錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18後，即可使用此修補程式。 修補程式ID為MDVA-35286。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 40c98735-6054-4b25-9882-e274424b203f
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-35286：將多個位址切換至Onepage簽出時發生錯誤

MDVA-35286修補程式修正了客戶在購物車中捆綁產品，並從多個地址結帳切換至單一頁面結帳時出現錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18時，即可使用此修補程式。 修補程式ID為MDVA-35286。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果購物車中有套件組合產品，而使用者在放棄「多送貨結帳」後嘗試使用「內嵌結帳」，系統會顯示錯誤。

<u>要再現的步驟</u>：

1. 登入客戶帳戶並將多個套件組合產品新增到購物車。
1. 按一下連結以檢視並編輯購物車。
1. 按一下&#x200B;**使用多個地址簽出**&#x200B;連結。
1. 針對新增至購物車的產品，選取不同的地址。
1. 按一下&#x200B;**返回購物車**。
1. 在購物車中，按一下&#x200B;**繼續結帳**。

<u>預期結果</u>：

系統會將您重新導向至「結帳」頁面。

<u>實際結果</u>：

顯示錯誤訊息： *處理您的請求時發生錯誤*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
