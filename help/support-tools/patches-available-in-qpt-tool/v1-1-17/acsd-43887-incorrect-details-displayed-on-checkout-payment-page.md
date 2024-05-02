---
title: 「ACSD-43887：結帳付款頁面上顯示的詳細資料不正確」
description: ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887：結帳付款頁面上顯示的詳細資料不正確

ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.17。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用公司的採購單時，結帳付款頁面上會顯示不正確的詳細資料。

<u>必要條件</u>：

1. B2B模組已安裝。
1. 啟用公司已設為 _是_. 前往 **商店** > **設定** > **一般** > **B2B功能** > **啟用公司** > **是**.
1. 「啟用採購單」設為 _是_. 前往 **訂單核准設定** > **啟用採購單** > **是**.
1. PayPal Express已設定為付款方式。

<u>要再現的步驟</u>：

1. 建立虛擬產品。
1. 從前端向公司管理員註冊公司帳戶。
1. 從後端核准公司帳戶並設定 **啟用採購單** 作為 _是_ 核准公司時。
1. 前往前端，並使用在步驟二中建立的公司管理員帳戶登入。
1. 為公司建立「預設使用者」。 前往 **公司使用者** > **新增使用者**.
1. 為公司建立「核准規則」。 前往 **核准規則** > **新增規則**.

   * 規則型別：訂單總計
   * 訂單總計：大於或等於$1
   * 需要核准者：公司管理員

1. 登出並使用「預設使用者」帳戶登入。
1. 將在步驟一中建立的虛擬產品新增到購物車並繼續結帳。
1. 選取PayPal Express作為付款方式，然後按一下 **下採購單**.
1. 登出並使用公司管理員帳戶登入。
1. 前往 **我的採購單** 和從 **公司採購單**，按一下 **檢視** ，此專案適用於在步驟9中建立的訂單。
1. 核准採購單。 採購單狀態應為「已核准：暫緩付款」。
1. 登出並使用公司「預設使用者」帳戶登入。
1. 前往 **我的採購單** > **檢視** > **下單**.
1. 檢查 **訂單摘要**.

<u>預期結果</u>：

訂單摘要會顯示正確的非零值。

<u>實際結果</u>：

訂單摘要總計值為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
