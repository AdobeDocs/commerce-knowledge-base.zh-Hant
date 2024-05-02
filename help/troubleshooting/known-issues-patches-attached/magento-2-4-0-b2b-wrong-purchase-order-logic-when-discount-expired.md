---
title: 「Adobe Commerce 2.4.0 B2B：折扣過期時採購單邏輯錯誤」
description: 本文針對Adobe Commerce 2.4.0 B2B中未套用的採購單(PO)折扣已知問題提供修補程式。 如果採購單在核准處理時具有過期的折扣代碼，則核准的訂單不會反映折扣。
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B：折扣過期時採購單邏輯錯誤

本文針對Adobe Commerce 2.4.0 B2B中未套用的採購單(PO)折扣已知問題提供修補程式。 如果採購單在核准處理時具有過期的折扣代碼，則核准的訂單不會反映折扣。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>必要條件</u>：已建立折扣券，且存在無法自動處理採購單的核准規則。

<u>要再現的步驟：</u>

1. 套用折扣的採購單。
1. 停用折扣優惠券。
1. 核准採購單為經理。
1. 檢查因此建立的訂單。

<u>預期結果：</u>

訂單是以折扣總計建立。

<u>實際結果：</u>

已建立全額的訂單。

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

修補程式也可在以下兩種版本中下載： `.git` 和 `.composer` ，格式於 [Adobe Commerce下載內容](https://magento.com/tech-resources/download) 頁面，下 **修補程式** 在左側欄導覽中。 搜尋XXX修補程式。

## 如何套用修補程式

另請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。
