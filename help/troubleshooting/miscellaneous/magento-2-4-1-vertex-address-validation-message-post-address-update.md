---
title: Adobe Commerce 2.4.1頂點位址驗證訊息張貼位址更新
description: 本文會說明一個已知的Adobe Commerce 2.4.1問題，其中在使用與帳單地址不同的送貨地址時，Vertex地址驗證在付款步驟中無法運作。 此問題已排程在Adobe Commerce 2.4.2中修正。
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Adobe Commerce 2.4.1頂點位址驗證訊息張貼位址更新

本文會說明一個已知的Adobe Commerce 2.4.1問題，其中在使用與帳單地址不同的送貨地址時，Vertex地址驗證在付款步驟中無法運作。 此問題已排程在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.1，已啟用頂點整合
* 雲端基礎結構2.4.1上的Adobe Commerce已啟用頂點整合

## 問題

先決條件：

啟用&#x200B;**頂點位址清除**。 如需相關步驟，請參閱使用手冊中的[設定店面位址清理](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html?lang=zh-Hant)。

<u>要再現的步驟：</u>

1. 建立帳戶並登入。
1. 按一下&#x200B;**[加入購物車]**，將專案加入購物車。 按一下「購物車」圖示，然後按一下「**繼續結帳**」。
1. 在&#x200B;**送貨地址**&#x200B;欄位中輸入有效的地址。
1. 檢查&#x200B;**送貨方法**&#x200B;下的其中一個選項。 然後按一下&#x200B;**下一步**。
1. 如果位址驗證建議不同的位址資訊，請按一下&#x200B;**更新位址**，然後按一下&#x200B;**下一步**。
1. 取消勾選「**我的帳單和運送地址相同**」核取方塊。

<u>第一個情境：</u>

請依照上述六個步驟[&#128279;](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)中的進行，然後：

1. 輸入新的有效帳單地址。
1. 按一下&#x200B;**更新**&#x200B;按鈕。 它會顯示類似下列的訊息/建議： *地址無效。*&#x200B;這將會接著提供地址建議，例如： *郵遞區號： XXXXX- XXXX Street ： XXX City Street XXX*
1. 按一下&#x200B;**更新**&#x200B;按鈕（請勿按頂點位址建議的&#x200B;**更新位址**&#x200B;按鈕）。
1. 按一下已更新帳單地址的&#x200B;**編輯**&#x200B;按鈕。
1. 從地址下拉式清單中選取地址。
1. 按一下&#x200B;**更新**&#x200B;按鈕。

<u>預期結果：</u>

舊的驗證訊息/建議訊息已移除。

<u>實際結果：</u>

驗證訊息/建議&#x200B;*「我們找不到有效的地址郵遞區號： XXXXX-XXXX Street ： XXX City street XXX」*&#x200B;訊息為&#x200B;**未移除**。 如果您在表單中輸入的地址無效，也會發生相同的問題。

<u>第二個情境：</u>

請依照上述六個步驟[&#128279;](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)中的進行，然後：

1. 使用有效地址填寫地址表單。
1. 按一下&#x200B;**更新**&#x200B;按鈕。 它會顯示類似下列的訊息/建議： *地址無效。*&#x200B;這將會接著提供地址建議，例如： *郵遞區號： XXXXX-XXXX Street ： XXX City Street XXX*。
1. 按一下&#x200B;**更新**&#x200B;按鈕（請勿按頂點地址建議的&#x200B;**更新地址**&#x200B;按鈕）。
1. 檢查&#x200B;***我的帳單和運送地址相同***&#x200B;下拉式清單。

<u>預期結果：</u>

舊的驗證訊息/建議訊息已移除。

<u>實際結果：</u>

驗證訊息/建議&#x200B;*「我們找不到有效的地址郵遞區號： XXXXX-XXXX Street XXX City street XXX」*&#x200B;訊息為&#x200B;**未移除**。 如果您在表單中輸入的地址無效，也會發生相同的問題。

## 我們的支援知識庫中的相關閱讀：

[Adobe Commerce 2.3.6、2.4.0-p1和2.4.1已知問題：啟用帳戶時無法登入dotdigital](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
