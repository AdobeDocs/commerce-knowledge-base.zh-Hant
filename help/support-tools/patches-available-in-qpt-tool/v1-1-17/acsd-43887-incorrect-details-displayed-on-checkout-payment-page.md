---
title: 「ACSD-43887：結帳付款頁面上顯示的詳細資料不正確」
description: ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887：結帳付款頁面上顯示的詳細資料不正確

ACSD-43887修補程式修正啟用「公司採購單」時，結帳付款頁面上顯示不正確詳細資料的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-43887。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用公司的採購單時，結帳付款頁面上會顯示不正確的詳細資料。

<u>必要條件</u>：

1. B2B模組已安裝。
1. 啟用公司設定為&#x200B;_是_。 移至&#x200B;**商店** > **設定** > **一般** > **B2B功能** > **啟用公司** > **是**。
1. 啟用採購單設定為&#x200B;_是_。 移至&#x200B;**訂單核准設定** > **啟用採購單** > **是**。
1. PayPal Express已設定為付款方式。

<u>要再現的步驟</u>：

1. 建立虛擬產品。
1. 從前端向公司管理員註冊公司帳戶。
1. 從後端核准公司帳戶，並在核准公司時將&#x200B;**啟用採購單**&#x200B;設定為&#x200B;_是_。
1. 前往前端，並使用在步驟二中建立的公司管理員帳戶登入。
1. 為公司建立「預設使用者」。 移至&#x200B;**公司使用者** > **新增使用者**。
1. 為公司建立「核准規則」。 移至&#x200B;**核准規則** > **新增規則**。

   * 規則型別：訂單總計
   * 訂單總計：大於或等於$1
   * 需要核准者：公司管理員

1. 登出並使用「預設使用者」帳戶登入。
1. 將在步驟一中建立的虛擬產品新增到購物車並繼續結帳。
1. 選取PayPal Express作為付款方式，然後按一下&#x200B;**下採購單**。
1. 登出並使用公司管理員帳戶登入。
1. 移至&#x200B;**我的採購單**，並從&#x200B;**公司採購單**，針對在步驟9中建立的訂單，按一下&#x200B;**檢視**。
1. 核准採購單。 採購單狀態應為「已核准：暫緩付款」。
1. 登出並使用公司「預設使用者」帳戶登入。
1. 移至&#x200B;**我的採購單** > **檢視** > **下訂單**。
1. 檢查&#x200B;**訂單摘要**。

<u>預期結果</u>：

訂單摘要會顯示正確的非零值。

<u>實際結果</u>：

訂單摘要總計值為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
