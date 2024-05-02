---
title: 類別變更未儲存
description: 本文修正透過「Commerce管理員」更新產品類別時，管理員和店面不會顯示變更的問題。 問題是由於'catalog_category_entity'表格中的資料損毀所造成。 若要解決此問題，請修正或移除表格中有問題的類別更新記錄。 之後，您應該能夠使用管理員更新產品類別。
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# 類別變更未儲存

本文修正透過「Commerce管理員」更新產品類別時，管理員和店面不會顯示變更的問題。 問題是由於 `catalog_category_entity` 表格。 若要解決此問題，請修正或移除表格中有問題的類別更新記錄。 之後，您應該能夠使用管理員更新產品類別。

## 問題

在管理員中變更產品類別並儲存後，新的更新既不會儲存也不會顯示在管理員和店面中。

### 要再現的步驟

1. 前往 **目錄** > **類別**.
1. 選取類別。
1. 進行變更，然後按一下 **儲存**.
1. 隨即顯示訊息： *您已儲存類別*.
1. 請注意，您所做的變更尚未儲存。

## 可能的原因： `catalog_category_entity` 表格

此問題是由於 `created_in` 資料庫(DB)中受影響類別記錄的欄。

![catalog_category_entity表格中的資料已損毀](assets/catalog_category_entity.png)

詳細資料：

* 此 `catalog_category_entity` DB表格有兩個或多個受影響類別的記錄(這些記錄具有相同的 `entity_id` 值)。
* 這些類別記錄具有 **中的相同值 `created_in` 欄**.

### 第二個資料庫專案（以及所有後續專案）如何出現在相同類別的DB中？

受影響類別的第二個DB記錄（可能還有下一個記錄）表示已使用Magento\_Staging模組排程類別更新。 模組會為中的類別進行額外記錄 `catalog_category_entity` 這是預期的應用程式行為；問題是這些記錄的 `created_in` 欄。

### 相同的值如何顯示？

我們無法確切說明資料損毀的原因。 可能的原因包括：

* 自訂（程式碼、主題等）
* 不正確的資料移轉
* 從備份還原的資料不正確

就我們所知，這類資料損毀不適用於「乾淨」（現成）Adobe Commerce執行個體，而且無法在沒有自訂功能的Adobe Commerce安裝上重現。

### 如何確認這是您的問題

此 `catalog_category_entity` 表格應有多個受影響類別的記錄(記錄應具有相同的 `entity_id` 值)，且這些記錄中至少應有兩個相同 `created_in` 值。 如此一來，Commerce管理員中就不會顯示測試排程更新；您只會看到空白的「已排程變更」區塊。

#### 驗證步驟

1. 存取資料庫中的catalog\_category\_entity表格。
1. 依entity\_id篩選實體，使用entity\_id識別受影響的類別。
1. 如果created\_in欄中的值對於具有相同entity\_id的不同專案是相同的，即是這種情況。 通常情況下， `created_in` 每個記錄的值都不同。

![catalog_category_entity表格中的資料已損毀](assets/catalog_category_entity.png)

## 解決方案

您可以選擇下列其中一種解決方案：

1. **刪除** 有問題的類別更新記錄
1. **修復** 有問題的類別更新記錄

### 刪除有問題的類別更新記錄

在此解決方案中，您需要將 `updated_in` 初始類別記錄的值，並刪除此類別的所有其他記錄。 這會移除所有已排程的類別更新。

請依照下列步驟執行：

1. 使用尋找資料庫記錄 `entity_id` 受影響的類別。
1. 選取中整數最大的記錄 `updated_in` 欄。
1. 複製 `updated_in` 所選記錄的值。
1. 選取記錄 `row_id` = `entity_id` （初始類別記錄）並將複製的值貼到 `updated_in` 此記錄的欄。
1. 刪除列，使用 `row_id` 不等於 `entity_id` .

### 修復有問題的類別更新記錄

1. 尋找具有相同的類別記錄 `entity_id` 和相同 `created_in` 值。
1. 選取記錄，其中 `row_id` = `entity_id` 並複製 `updated_in` 值。
1. 選取記錄，其中 `row_id` 不等於 `entity_id` 並貼上複製的 `updated_in` 值作為 `created_in` 值。 請參閱下方的熒幕擷圖以作圖例。    ![複製created_in value.png](assets/copy_created-in_value.png)
1. 確認類別更新記錄、 `created_in` （在步驟3中）中您更新過的值，已存在於 `staging_update` 表格。 *例如：* 若已複製 `created_in` 值為1509281953，然後為實體 `row_id` =1509281953必須存在於 `staging_update` 表格
