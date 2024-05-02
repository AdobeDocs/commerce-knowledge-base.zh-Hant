---
title: 'MDVA-12304：商店前端出現503錯誤和Cookie錯誤'
description: 此MDVA-12304 Adobe Commerce修補程式解決商店前端的503個錯誤，其中*無法傳送Cookie。 將超過Cookie的最大數量。*記錄檔中的錯誤訊息。 這是已知的Adobe Commerce 2.2.5問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12後，即可使用此修補程式。
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304：商店前端出現503錯誤和Cookie錯誤

此MDVA-12304 Adobe Commerce修補程式解決商店前端的503個錯誤，具有 *無法傳送Cookie。 將超過Cookie的最大數量。* 記錄檔中的錯誤訊息。 這是已知的Adobe Commerce 2.2.5問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.0.12。

## 受影響的產品和版本

* **此修補程式是針對Adobe Commerce版本建立的：** Adobe Commerce內部部署2.2.5。
* **與Adobe Commerce版本相容：** Adobe Commerce （所有部署方法） 2.x.x。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶瀏覽商店前方時會收到503錯誤。 在 `var/log/exception.log` 檔案出現下列錯誤訊息 *無法傳送Cookie。 將超過Cookie的最大數量。*

發生此問題的原因是Adobe Commerce預設Cookie限制設為50，而如果使用者端的瀏覽器達到限制，Commerce會擲回例外狀況。 修補程式中提供的解決方案將Cookie上限提高至200。

<u>要再現的步驟：</u>

客戶嘗試登入並檢視其購物車時，隨時都會顯示503錯誤。

在 `var/log/exception.log` 檔案出現下列錯誤訊息 *無法傳送Cookie。 將超過Cookie的最大數量。*

<u>實際結果：</u> 客戶無法檢查購物車或完成訂單。

<u>預期結果：</u> 客戶可以檢查其購物車並完成訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。


## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
