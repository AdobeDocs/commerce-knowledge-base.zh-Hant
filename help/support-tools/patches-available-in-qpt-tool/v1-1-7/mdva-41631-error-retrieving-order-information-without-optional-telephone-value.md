---
title: MDVA-41631：擷取不含可選「電話」值的訂單資訊時發生錯誤
description: MDVA-41631修補程式修正使用者透過GraphQL擷取訂單資訊（不含選擇性「電話」值）時發生錯誤。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631：擷取不含可選「電話」值的訂單資訊時發生錯誤

MDVA-41631修補程式修正使用者透過GraphQL擷取訂單資訊（不含選擇性「電話」值）時發生錯誤。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若未使用選用的「電話」值，使用者透過GraphQL擷取訂單資訊時發生錯誤。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **客戶** > **客戶設定** > **名稱和地址選項** > **顯示電話**&#x200B;並將電話號碼設定為選用。
1. 使用GraphQL API作為登入客戶下訂單。
   * 設定帳單和運送地址時不要設定電話號碼。 請依照開發人員檔案中的[GraphQL結帳教學課程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)指示操作。
1. 使用GraphQL [customerOrders查詢](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/)擷取訂單。

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>預期結果</u>：

使用者取得訂單資訊。

<u>實際結果</u>：

使用者收到下列錯誤： *&quot;message&quot;： &quot;Internal server error&quot;，*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
