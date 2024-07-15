---
title: 'MDVA-34847：customer_grid_flat資料表緩慢查詢'
description: MDVA-34847修補程式可解決「customer_grid_flat」表格中發生緩慢查詢的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16後，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847：customer_grid_flat資料表緩慢查詢

MDVA-34847修補程式解決在`customer_grid_flat`資料表上發生緩慢查詢的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.3

**與Adobe版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在`customer_grid_flat`資料表上發生緩慢的查詢。

<u>要再現的步驟</u>：

1. 建立具有自訂範圍的管理員使用者（範例：設定&#x200B;**GWS** = *0，*，然後選擇具有&#x200B;**ID** = *1*&#x200B;的現有預設網站）。
1. 建立任何產品和類別專案。
1. 從前端下訂單。
1. 以新使用者身分登入「管理員」。
1. 移至[銷售]網格（**銷售>訂單**）。
1. 檢查SQL查詢是否已傳送至DB （資料庫）。

<u>預期結果</u>：

Admin GWS擴充功能應使用

```sql
int
```

值

```sql
website_id
```

在SQL條件中，如預期，例如：

```sql
main_table.website_id IN (1)
```

<u>實際結果</u>：

Admin GWS擴充功能新增條件，其中包含

```sql
website_id
```

值為

```sql
string
```

，例如：

```sql
main_table.website_id IN ('1')
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
