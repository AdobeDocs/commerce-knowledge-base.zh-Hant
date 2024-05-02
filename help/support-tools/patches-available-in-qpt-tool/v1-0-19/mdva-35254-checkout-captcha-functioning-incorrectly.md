---
title: 'MDVA-35254：簽出CAPTCHA運作不正確'
description: MDVA-35254修補程式修正嘗試結帳取得第三方付款失敗後，驗證碼欄位無法顯示的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19後，即可使用此修補程式。 修補程式ID為MDVA-35254。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254：簽出CAPTCHA運作不正確

MDVA-35254修補程式修正嘗試結帳取得第三方付款失敗後，驗證碼欄位無法顯示的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.19。 修補程式ID為MDVA-35254。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.1-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

設定驗證碼：

1. 安裝並設定第三方付款提供者(範例：Braintree)。
1. 前往 **儲存>設定>客戶>客戶設定>驗證碼> Forms**.
1. 選取 **結帳/下訂單**.
1. 保留 **登入嘗試失敗的次數** 預設值(預設= *3*)。
1. 以客戶身分登入。
1. 新增任何產品至購物車。
1. 前往結帳中的付款區段。
1. 選取 **信用卡** 付款方式(範例：Braintree)。
1. 嘗試三次失敗的付款。

<u>預期結果</u>：

達到失敗嘗試次數時，會顯示驗證碼欄位。

<u>實際結果</u>：

驗證碼欄位不會顯示，只會顯示錯誤訊息： *請提供驗證碼並重試。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
