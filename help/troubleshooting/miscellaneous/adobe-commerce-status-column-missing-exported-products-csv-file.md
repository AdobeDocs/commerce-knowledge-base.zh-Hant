---
title: Adobe Commerce狀態列缺少匯出的產品CSV檔案
description: 當您在包含已匯出產品的CSV檔案中找不到狀態列時，本文提供此問題的解決方案。
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce狀態列缺少匯出的產品CSV檔案

當您在包含已匯出產品的CSV檔案中找不到狀態列（即表示產品已啟用或已停用）時，本文提供此問題的解決方案。 產品的狀態會由 [!UICONTROL product_online] 欄。

## 受影響的產品和版本

Adobe Commerce （所有部署方法）全部 [支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

您找不到 [!UICONTROL status] 欄（在包含已匯出產品的CSV檔案中）。 舉例來說，您匯出所有SKU的CSV及其狀態，但表格似乎遺失 [!UICONTROL status] 欄。

<u>要再現的步驟：</u>

1. 在「Adobe Commerce管理員」中，選取 **[!UICONTROL System]**，下 **[!UICONTROL Data Transfer]** 選取 **[!UICONTROL Export]**.
1. 在 **[!UICONTROL Export Settings]** 區段，選取 **[!UICONTROL Entity Type]** 下拉式清單 **[!UICONTROL Products]**.
1. 搜尋 **[!UICONTROL status]**，列於下 **[!UICONTROL Attribute Code]**. 您會在可用屬性清單中看到該屬性代碼(**[!UICONTROL Enable Product]**)。
1. 按一下 **[!UICONTROL Export]**.

<u>預期結果：</u>

在您剛匯出的CSV檔案中，您會看到一欄標示為 [!UICONTROL status].

<u>實際結果：</u>

您沒有看到標示為 [!UICONTROL status] 在匯出的csv檔案中。

## 原因

CSV檔案中的產品狀態屬性已重新命名。 現在是 [!UICONTROL product_online] 欄。

## 解決方案

1. 選取 **[!UICONTROL System]**，下 **[!UICONTROL Data Transfer]** 選取 **[!UICONTROL Import]**.
1. 按一下 **[!UICONTROL Download Sample File]**.
1. 您可以看到 [!UICONTROL product_online] 欄。

## 相關閱讀

* [使用CSV檔案](https://docs.magento.com/user-guide/system/data-csv.html) 在我們的使用手冊中。
* [產品匯出屬性參考](https://docs.magento.com/user-guide/system/data-attributes-product.html) 在我們的使用手冊中。
