---
title: 如果在「允許國家/地區」中未選取任何專案，則使用者無法將產品新增到購物車
description: 本文針對使用PHP 8.1的已知Adobe Commerce 2.4.4問題提供補丁，該問題導致如果未選取「允許國家/地區」，使用者無法將產品新增到購物車。
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 如果在「允許國家/地區」中未選取任何專案，則使用者無法將產品新增到購物車

本文針對使用PHP 8.1的已知Adobe Commerce 2.4.4問題提供補丁，該問題導致如果未選取「允許國家/地區」，使用者無法將產品新增到購物車。

## 受影響的產品和版本

Adobe Commerce 2.4.4與PHP 8.1

## 問題

如果未選取「允許國家/地區」，使用者無法將產品新增到購物車。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 移至&#x200B;**市集** > **組態** > **一般** > **國家選項**
1. 取消選取&#x200B;**允許國家**&#x200B;欄位中的所有選項。
1. 按一下&#x200B;**儲存設定**&#x200B;以儲存設定。
1. 前往店面，嘗試將產品新增到購物車。

<u>預期結果：</u>

您可以將產品新增到購物車。

<u>實際結果：</u>

您無法將產品新增至購物車。 您會收到下列主控台錯誤：

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## 原因

多選設定沒有任何選取的專案時，Adobe Commerce設定會擷取`null`。 如果在8.1之前的PHP版本中進一步成功處理此設定。然而，在PHP 8.1中，它無法正常運作，因為錯誤是由於「[Deprecate將null傳遞給PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)中內部函式的不可為空的引數」所造成。

## 解決方案

若要解決此問題，請套用下列修補程式：

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## 如何套用修補程式

請參閱我們的支援知識庫中的[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。

## 有用的連結

[在開發人員檔案中，將自訂修補程式套用至雲端基礎結構上的Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)。
