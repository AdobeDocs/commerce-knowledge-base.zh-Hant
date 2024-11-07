---
title: 'MDVA-39163：新註冊的使用者無法透過來賓工作階段的產品使用送貨方法'
description: MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163：新註冊的使用者無法從來賓工作階段取得產品的送貨方法

MDVA-39163修補程式可解決當新使用者註冊且購物車中的產品來自訪客工作階段時，無法使用送貨方法的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-39163。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

註冊新使用者時，無法使用送貨方法，且購物車中的產品來自訪客工作階段。

<u>要再現的步驟</u>：

1. 移至&#x200B;**管理員** > **商店** > **組態** > **銷售** > **傳遞方法**。 僅啟用&#x200B;**統一費率**&#x200B;送貨方法，並停用其他所有功能。
1. 在&#x200B;**統一運費**&#x200B;送貨方式中，選取&#x200B;**送貨至適用國家/地區**&#x200B;設定中可用的&#x200B;**特定**&#x200B;國家/地區選項，並從清單中選取一個國家/地區（例如，美國）。
1. 移至&#x200B;**管理員** > **商店** > **組態** > **客戶** > **客戶組態**，並將&#x200B;**要求電子郵件確認**&#x200B;設定為&#x200B;_是_。
1. 在&#x200B;**管理員** > **行銷** > **電子郵件範本**&#x200B;中建立新的電子郵件範本，並載入`Footer (magento/luma)`範本並將範本內容取代為CMS區塊。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. 移至&#x200B;**管理員** > **內容** > **設計** > **設定**，並選取與您的前端網站相關的主題。 將「頁尾範本」設定為已建立的新電子郵件範本。
1. 前往前端，將產品新增至購物車。
1. 建立客戶；您將收到確認電子郵件地址的電子郵件。 按一下驗證連結。 您將會登入網站。
1. 移至&#x200B;**我的帳戶**&#x200B;並新增地址。 將地址國家/地區設定為您先前在管理設定中設定的送貨國家/地區。
1. 前往結帳。

<u>預期結果</u>：

送貨方式可供使用，因為客戶的地址與送貨國家/地區相容。

<u>實際結果</u>：

無法使用送貨方法。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
