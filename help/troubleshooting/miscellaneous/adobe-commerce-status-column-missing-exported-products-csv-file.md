---
title: Adobe Commerce狀態列缺少匯出的產品CSV檔案
description: 當您在包含已匯出產品的CSV檔案中找不到狀態列時，本文提供此問題的解決方案。
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%
---
# Adobe Commerce狀態列缺少匯出的產品CSV檔案

當您在包含已匯出產品的CSV檔案中找不到狀態列（即表示產品已啟用或已停用）時，本文提供此問題的解決方案。 [!UICONTROL product_online]欄表示產品的狀態。

## 受影響的產品和版本

Adobe Commerce （所有部署方法）所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 問題

您在包含已匯出產品的CSV檔案中找不到[!UICONTROL status]欄。 舉例來說，您匯出所有SKU的CSV及其狀態，但表格似乎遺失[!UICONTROL status]欄。

<u>要再現的步驟：</u>

1. 在「Adobe Commerce管理員」中，選取「**[!UICONTROL System]**」，在「**[!UICONTROL Data Transfer]**」下選取「**[!UICONTROL Export]**」。
1. 在&#x200B;**[!UICONTROL Export Settings]**&#x200B;區段中，選取&#x200B;**[!UICONTROL Entity Type]**&#x200B;下拉式清單&#x200B;**[!UICONTROL Products]**&#x200B;上的。
1. 搜尋&#x200B;**[!UICONTROL status]**，列在&#x200B;**[!UICONTROL Attribute Code]**&#x200B;下。 您會在可用屬性(**[!UICONTROL Enable Product]**)清單中看到該屬性代碼。
1. 按一下&#x200B;**[!UICONTROL Export]**。

<u>預期結果：</u>

在您剛匯出的CSV檔案中，您會看到標示為[!UICONTROL status]的欄。

<u>實際結果：</u>

您未在匯出的CSV檔案中看到標示為[!UICONTROL status]的欄。

## 原因

CSV檔案中的產品狀態屬性已重新命名。 現在是[!UICONTROL product_online]欄。

## 解決方案

1. 選取&#x200B;**[!UICONTROL System]**，在&#x200B;**[!UICONTROL Data Transfer]**&#x200B;下選取&#x200B;**[!UICONTROL Import]**。
1. 按一下&#x200B;**[!UICONTROL Download Sample File]**。
1. 您可以在CSV檔案中看到[!UICONTROL product_online]欄。

## 相關閱讀

* [使用我們的使用手冊中的CSV檔案](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/data-transfer/data-csv)。
* 使用手冊中的[產品匯出屬性參考](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/data-transfer/data-attributes-product)。
