---
title: 'MDVA-39163：新註冊的使用者無法透過來賓工作階段的產品使用送貨方法'
description: MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163：新註冊的使用者無法從來賓工作階段取得產品的送貨方法

MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.9。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

註冊新使用者時，無法使用送貨方法，且購物車中的產品來自訪客工作階段。

<u>要再現的步驟</u>：

1. 前往 **管理員** > **商店** > **設定** > **銷售** > **傳遞方法**. 僅啟用 **平準率** 送貨方法，並停用其他所有功能。
1. 在 **平準率** 送貨方法，選取 **特定** 國家/地區選項可在 **送貨至適用國家/地區** 設定並從清單中選取一個國家/地區（例如，美國）。
1. 前往 **管理員** > **商店** > **設定** > **客戶** > **客戶組態** 並設定 **需要電子郵件確認** 至 _是_.
1. 在中建立新的電子郵件範本 **管理員** > **行銷** > **電子郵件範本** 和載入 `Footer (magento/luma)` 並以CMS區塊取代範本內容。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. 前往 **管理員** > **內容** > **設計** > **設定** 並選取與前端網站相關的主題。 將「頁尾範本」設定為已建立的新電子郵件範本。
1. 前往前端，將產品新增至購物車。
1. 建立客戶；您將收到確認電子郵件地址的電子郵件。 按一下驗證連結。 您將會登入網站。
1. 前往 **我的帳戶** 並新增地址。 將地址國家/地區設定為您先前在管理設定中設定的送貨國家/地區。
1. 前往結帳。

<u>預期結果</u>：

送貨方式可供使用，因為客戶的地址與送貨國家/地區相容。

<u>實際結果</u>：

無法使用送貨方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
