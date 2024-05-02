---
title: 未顯示在「管理員」中「訂單」網格中的訂單
description: 針對已知的Adobe Commerce 2.2.1問題，本文提供修補程式，這些問題與Commerce Admin中「訂單」格線中未顯示的訂單有關。
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# 未顯示在「管理員」中「訂單」網格中的訂單

針對已知的Adobe Commerce 2.2.1問題，本文提供修補程式，這些問題與Commerce Admin中「訂單」格線中未顯示的訂單有關。

## 問題

在已安裝B2B擴充功能的Adobe Commerce 2.2.1中，註冊客戶在店面建立的訂單不會顯示在Commerce管理員客戶帳戶的訂單清單中。 在偵錯記錄檔中(`./var/log/debug.log`)，則會記錄下列錯誤：

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>必要條件</u>：

您的商店目錄包含產品，而非Adobe Commerce範例資料，且已安裝B2B擴充功能。

<u>要再現的步驟</u>：

1. 導覽至店面並建立客戶帳戶。
1. 新增產品至購物車、完成結帳並提交訂單。
1. 登入管理員。
1. 瀏覽至 **客戶，** 然後選擇 **所有客戶**.
1. 對於新建立的客戶，按一下 **編輯**.
1. 按一下 **訂購** 在左側的面板中。

<u>預期結果</u>：

最近提交的訂單會列在格線中。

<u>實際結果</u>：

不會顯示「訂單」格線。 畫面改為顯示空白頁面。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-7868\_EE\_2.2.1\_v1\_composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce內部部署2.2.1

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce從2.2.0到2.2.3
* Adobe Commerce內部部署2.2.0和2.2.2至2.2.3

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我們的支援知識庫中取得指示。

## 附加的檔案
