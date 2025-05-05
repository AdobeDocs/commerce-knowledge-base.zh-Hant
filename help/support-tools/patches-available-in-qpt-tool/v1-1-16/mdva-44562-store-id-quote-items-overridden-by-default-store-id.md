---
title: 'MDVA-44562：預設商店ID已覆寫報價專案的商店ID'
description: MDVA-44562修補程式修正了預設商店ID會覆寫GraphQL要求之報價專案的商店ID的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16後，即可使用此修補程式。 修補程式ID為MDVA-44562。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562：預設商店ID已覆寫報價專案的商店ID

MDVA-44562修補程式修正了預設商店ID會覆寫GraphQL要求之報價專案的商店ID的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16時，即可使用此修補程式。 修補程式ID為MDVA-44562。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL要求的預設商店ID會覆寫報價專案的商店ID。

<u>要再現的步驟</u>：

1. 建立新的存放區檢視。
1. 為每個商店檢視建立具有不同名稱的新簡單產品。
1. 建立新客戶。
1. 取得客戶授權權杖。

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 使用授權權杖為客戶建立新報價。

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 新增產品至購物車。

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 取得預設商店檢視的購物車內容。

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 取得新商店檢視的購物車內容。

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>預期結果</u>：

來自新商店檢視的回應會顯示來自新商店檢視的產品名稱。

<u>實際結果</u>：

來自新商店檢視的回應會在預設商店檢視下顯示產品名稱設定。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
