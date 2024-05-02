---
title: 「B2B：公司無法存取店面中的設定檔頁面」
description: 針對已註冊公司在店面的「帳戶」頁面上出現錯誤的相關已知Adobe Commerce 2.2.4 B2B問題，本文提供相關修補程式。
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B：公司無法存取店面中的設定檔頁面

針對已註冊公司在店面的「帳戶」頁面上出現錯誤的相關已知Adobe Commerce 2.2.4 B2B問題，本文提供相關修補程式。

## 問題

客戶（公司）可以在網站上成功建立公司帳戶，但取得 *「沒有具有customerId = 」的這類實體」* 和 *「您還沒有公司帳戶」* 錯誤訊息。 他們可能也會取得 *「500內部伺服器錯誤」* 嘗試存取「公司設定檔」頁面時。

## 修補

若要下載含有修補程式的封存，請按一下以下連結：

[下載MDVA-9013\_EE\_2.2.2\_composer.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### 相容的Adobe Commerce版本

已建立下列專案的修正程式：

* Adobe Commerce內部部署2.2.2

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce從2.2.0到2.2.4
* 從2.2.0到2.2.1以及從2.2.3到2.2.4的Adobe Commerce內部部署

## 如何套用修補程式

另請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得指示。
