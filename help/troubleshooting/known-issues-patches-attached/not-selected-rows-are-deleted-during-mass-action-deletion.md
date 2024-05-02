---
title: 在管理員中大量刪除期間，刪除的產品比初始的產品多
description: 針對雲端基礎結構2.2.3的已知AdobeсOmmerce修補程式，該問題與在Commerce管理員的網格中執行大量刪除時，未選取要刪除的記錄有關。
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 在管理員中大量刪除期間，刪除的產品比初始的產品多

針對雲端基礎結構2.2.3的已知AdobeсOmmerce修補程式，該問題與在Commerce管理員的網格中執行大量刪除時，未選取要刪除的記錄有關。

## 問題

在「管理員」中，如果您選取要刪除的客戶或使用者端記錄，請篩選網格，然後選取 **刪除** 動作，則會刪除所有記錄。

<u>要再現的步驟</u>：

1. 瀏覽至 **目錄** > **產品** 在Admin中。
1. 選取一或多個產品。
1. 從「動作」下拉式功能表中選取「刪除」 。

<u>預期結果</u>：

只會刪除選取的產品。

<u>實際結果</u>：

也會刪除其他產品。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-10600\_EE\_2.2.3\_v1.composer.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.3

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署2.1.8-2.1.14、2.2.0-2.2.2和2.2.4-2.2.5
* 雲端基礎結構上的Adobe Commerce 2.2.4-2.2.5

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得指示。
