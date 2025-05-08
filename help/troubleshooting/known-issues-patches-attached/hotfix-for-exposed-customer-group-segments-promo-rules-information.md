---
title: 透過 [!DNL GraphQL]公開的客戶群組名稱、區段和促銷規則資訊
description: 本文提供Hotfix，防止透過 [!DNL GraphQL]洩露客戶群組名稱、客戶區段和促銷規則資訊。
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# 透過[!DNL GraphQL]公開的客戶群組名稱、區段和促銷規則資訊

本文提供Hotfix，以防止透過[!DNL GraphQL]公開客戶群組名稱、客戶區段和促銷規則資訊。 此問題已排程在Adobe Commerce 2.4.8-p1中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.8

## 問題

已針對[!UICONTROL Storefront Personalization Drop-ins]引入新的[!DNL GraphQL]變動，以顯示客戶群組名稱、區段、購物車及目錄規則等基本資訊。 但是，如果名稱中包含選件詳細資料或優惠券代碼，這可能會公開敏感資料。

### 要再現的步驟

#### 案例I： [!UICONTROL Catalog Rule]

1. 在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 定義規則條件（例如產品屬性或類別）。
1. 儲存並套用規則。
1. 確保產品符合規則條件。
1. 執行下列[!DNL GraphQL]查詢以擷取所有規則：

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. 查詢產品以驗證規則是否適用：

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### 案例II： [!UICONTROL Cart Rule]

1. 在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 設定條件，例如最小購物車值和客戶群組。
1. 儲存並套用規則。
1. 將產品新增到購物車以觸發規則。
1. 使用[!DNL GraphQL]驗證所有的購物車規則：

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. 檢查規則是否已套用至作用中的購物車：

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### 案例III： [!UICONTROL Customer Group]

1. 在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**。
1. 驗證預期的群組是否存在。
1. 使用[!DNL GraphQL]擷取所有群組：

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. 驗證客戶/來賓的群組：

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### 案例IV： [!UICONTROL Customer Segment] (僅適用於Adobe Commerce)

1. 在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**。
1. 定義以客戶為基礎的條件（例如，訂單、購物車內容）。
1. 指派適用的範圍： *[!UICONTROL Visitor]*、*[!UICONTROL Registered]*&#x200B;或兩者。
1. 確保條件符合測試客戶。
1. 使用[!DNL GraphQL]檢查所有區段：

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. 驗證套用至購物車的區段：

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>預期結果</u>：

客戶群組、區段和促銷規則資訊的名稱不會透過[!DNL GraphQL]公開。

<u>實際結果</u>：

透過[!DNL GraphQL]公開客戶群組、區段和促銷規則資訊的名稱。

## 解決方案

根據您的Adobe Commerce版本套用附加的修補程式：

* 若為Adobe Commerce 2.4.8版：

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* 針對[!DNL Magento]，請開啟Source 2.4.8版：

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
