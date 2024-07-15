---
title: 結帳時重新整理頁面後未儲存送貨地址
description: 本文針對已知的Adobe Commerce 2.2.3問題提供修補程式，其中客戶在來賓結帳時重新整理瀏覽器頁面後，已填入的送貨地址表單再次空白。 啟用持續性購物車時發生問題。
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 結帳時重新整理頁面後未儲存送貨地址

本文針對已知的Adobe Commerce 2.2.3問題提供修補程式，其中客戶在來賓結帳時重新整理瀏覽器頁面後，已填入的送貨地址表單再次空白。 啟用持續性購物車時發生問題。

## 問題

客戶須完成訪客結帳及填寫所有表格，包括運送地址。 他們前往檢閱和付款區段並重新載入頁面。 表單是空的，他們需要重新輸入送貨地址。 已啟用持續性購物車功能。

<u>要再現的步驟</u> ：

**必要條件**：已啟用永久購物車功能。 根據您的Adobe Commerce版本，檢查是否在Admin中的&#x200B;**商店** > **設定** > **客戶**&#x200B;或&#x200B;**商店** > **設定** > **銷售，**&#x200B;下啟用它。

1. 前往店面。
1. 新增產品至購物車。
1. 以來賓身份繼續結帳。
1. 填寫送貨地址，選擇送貨選項，然後繼續確保付款安全。
1. 重新導向至結帳的「複查與付款」區段。
1. 仔細檢查您是否在「送貨地點」區段中看到送貨地址。
1. 重新整理頁面。

<u>預期結果</u>：

您可以繼續結帳，所有資料都會儲存。

<u>實際結果</u>：

運送地址是空的，您必須將它租用。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### 相容的Adobe Commerce版本

**已建立修補程式：**

* Adobe Commerce 2.2.3

**此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：**

* 雲端基礎結構上的Adobe Commerce 2.1.13 - 2.1.18
* 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.5
* Adobe Commerce內部部署2.0.X
* Adobe Commerce內部部署2.1.X
* Adobe Commerce內部部署2.2.0 - 2.2.2和2.2.4 - 2.2.5

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
