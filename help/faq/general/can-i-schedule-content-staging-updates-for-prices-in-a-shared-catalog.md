---
title: 我可以針對共用目錄中的價格排程內容測試更新嗎？
description: Adobe Commerce不提供針對共用目錄中的一或多個產品排程價格更新([內容分段](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html))的功能。
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 我可以針對共用目錄中的價格排程內容測試更新嗎？

Adobe Commerce不提供排程價格更新的功能([內容分段](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html))中，一或多個產品的資訊。

也就是說，您不能直接從 **設定訂價與結構** Commerce管理面板的功能表(沒有 **排程新更新** 按鈕)。

不過，您仍可使用其他方法，並針對下列專案排程價格更新：

* 客戶群組
* 產品基本價格

## 客戶群組的排程價格更新

1. 開始 [排程新產品更新](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. 向下捲動至 **價格** 欄位並按一下 **進階定價**.

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. 在 **客戶群組價格區段**，選取所需的「客戶群組」並設定更新後的價格。

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. 照常完成排程更新。

在此工作流程中，您只能更新單一產品的價格；無法使用大量價格更新。

請記住：共用目錄會運用客戶群組定價。

**相關檔案**

* [排程更新（內容分段）](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) 在我們的使用手冊中。
* [進階定價](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) 在我們的使用手冊中。

## 基準價格的排程價格更新

請參閱相關文章： [基礎價格變更對共用型錄價格有何影響？](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) 在我們的支援知識庫中。
