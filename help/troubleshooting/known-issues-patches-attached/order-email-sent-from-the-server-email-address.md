---
title: 從伺服器電子郵件地址排序傳送的電子郵件
description: 本文提供雲端基礎結構2.2.4上已知Adobe Commerce問題的修補程式，該問題與從伺服器電子郵件地址傳送的訂購電子郵件有關。
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 從伺服器電子郵件地址排序傳送的電子郵件

本文提供雲端基礎結構2.2.4上已知Adobe Commerce問題的修補程式，該問題與從伺服器電子郵件地址傳送的訂購電子郵件有關。

## 問題

從Apache伺服器電子郵件地址傳送訂單確認電子郵件。 其他電子郵件（忘記密碼等）會從已設定的電子郵件地址傳送。

<u>要再現的步驟</u>：

1. 使用以下專案下訂單： **傳送訂單確認** 方塊已核取。
1. 檢查電子郵件。

<u>預期結果</u>：

電子郵件是從Adobe Commerce設定的傳送地址傳送。

<u>實際結果</u>：

電子郵件是從所使用Apache伺服器中所設定的電子郵件地址傳送。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-10993\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.4

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.2.5
* 雲端基礎結構上的Adobe Commerce 2.2.6
* 雲端基礎結構上的Adobe Commerce 2.2.7
* 雲端基礎結構上的Adobe Commerce 2.2.8
* Adobe Commerce內部部署2.2.4
* Adobe Commerce內部部署2.2.5
* Adobe Commerce內部部署2.2.6
* Adobe Commerce內部部署2.2.7
* Adobe Commerce內部部署2.2.8
* Adobe Commerce內部部署2.3.0

## 如何套用修補程式

如需指示，請參閱 [如何套用Adobe提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中。

## 附加的檔案
