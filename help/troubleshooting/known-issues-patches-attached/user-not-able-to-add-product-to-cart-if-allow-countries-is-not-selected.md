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
1. 前往 **儲存** > **設定** > **一般** > **國家/地區選項**
1. 取消選取中的所有選項 **允許國家/地區** 欄位。
1. 按一下 **儲存設定** 以儲存組態。
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

Adobe Commerce設定會擷取 `null` 如果多選組態沒有任何選取的專案。 如果在8.1之前的PHP版本中進一步成功處理此設定。但是在PHP 8.1中，由於「[在PHP 8.1中，不要將null傳遞至內部函式的不可為空引數](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)「。

## 解決方案

若要解決此問題，請套用下列修補程式：

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。

## 有用的連結

[在雲端基礎結構上套用自訂修補程式至Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。
