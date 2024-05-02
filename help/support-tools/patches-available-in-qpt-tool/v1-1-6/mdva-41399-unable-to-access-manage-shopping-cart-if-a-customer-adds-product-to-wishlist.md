---
title: 「MDVA-41399：如果客戶將產品新增到願望清單，則無法存取管理購物車」
description: MDVA-41399修補程式解決如果客戶將產品新增至願望清單，管理員使用者無法存取「管理購物車」頁面的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-41399。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399：如果客戶將產品新增到願望清單，則無法存取管理購物車

MDVA-41399修補程式解決如果客戶將產品新增至願望清單，管理員使用者無法存取「管理購物車」頁面的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.6。 修補程式ID為MDVA-41399。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.3.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果客戶將產品新增到願望清單，則管理員使用者無法存取「管理購物車」頁面。

<u>必要條件</u>：

1. 建立兩個或多個產品。
1. 建立客戶。
1. 啟用開發人員模式。

<u>要再現的步驟</u>：

1. 前往Storefront，從先決條件以客戶身分登入。
1. 將產品新增至願望清單。
1. 前往管理員面板，導覽至已建立的客戶編輯頁面，然後按一下 **管理購物車** 按鈕。

<u>預期結果</u>：

管理員使用者能夠管理購物車。

<u>實際結果</u>：

管理員使用者收到錯誤訊息： *發生錯誤。 如需詳細資訊，請參閱錯誤記錄。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 區段。
