---
title: 'MDVA-31007：顯示自訂位址屬性'
description: MDVA-31007修補程式可解決「我的帳戶」區域與後端(在**Sales &amp；gt； Orders**位置)的訂單詳細資訊頁面中，未正確顯示自訂地址屬性的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007：自訂地址屬性顯示

MDVA-31007修補程式可解決「我的帳戶」區域與後端（**銷售>訂單**&#x200B;位置）的訂單詳細資料頁面中，未正確顯示自訂地址屬性的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 登入管理員後端。
1. 導覽至&#x200B;**商店** > **屬性** > **客戶地址**。
1. 建立兩個屬性：

   * 設定輸入型別： *下拉式清單*。
   * 設定輸入型別： *文字*。

1. 瀏覽至&#x200B;**商店** > **設定** > **客戶** > **客戶設定**。
1. 選取&#x200B;*領域*&#x200B;作為&#x200B;**預設存放區**&#x200B;檢視。
1. 展開&#x200B;**地址範本**&#x200B;區段。 更新&#x200B;*Text*、*Text One Line*&#x200B;和&#x200B;*HTML*&#x200B;以包含上述兩個自訂屬性：

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. 開啟店面。
1. 建立和使用者登入。
1. 移至&#x200B;**我的帳戶** > **通訊錄**，然後新增地址（填入兩個自訂屬性）。
1. 將產品加入購物車並下訂單。
1. 在訂單成功頁面上，按一下&#x200B;**訂單編號**&#x200B;連結。
1. 在訂單詳細資訊頁面上，觀察&#x200B;**訂單資訊**&#x200B;區段。
1. 移至&#x200B;**後端** > **銷售** > **訂單**，按一下上述訂單，並觀察&#x200B;**地址資訊**&#x200B;區段。

<u>預期結果</u>：

在前端和後端，帳單和送貨地址都會如預期顯示。

<u>實際結果</u>：

在前端和後端，帳單地址未正確顯示。 下拉式清單屬性的選取選項遺失，且輸入屬性的值包含屬性代碼。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
