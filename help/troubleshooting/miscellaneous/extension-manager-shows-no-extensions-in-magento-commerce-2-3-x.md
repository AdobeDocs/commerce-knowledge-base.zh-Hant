---
title: Extension Manager在Adobe Commerce 2.3.x中不會顯示擴充功能
description: 本文提供您透過Commerce Marketplace購買擴充功能後，Adobe Commerce 2.3.x管理員Extension Manager中缺少擴充功能的因應措施。
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager在Adobe Commerce 2.3.x中不會顯示擴充功能

本文提供您透過Commerce Marketplace購買擴充功能後，Adobe Commerce 2.3.x管理員Extension Manager中缺少擴充功能的因應措施。

## 受影響的產品和版本

* Adobe Commerce版本（所有部署方法） 2.3.x

## 問題

當您透過Commerce Marketplace購買擴充功能時，無法使用核心Adobe CommerceExtension Manager進行安裝。 當您新增存取金鑰並同步至Marketplace時，Extension Manager不會顯示任何擴充功能，

此問題的&#x200B;**因應措施**&#x200B;是使用命令列Adobe Commerce安裝，如開發人員檔案中的[一般CLI安裝](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)所示。

<u>要再現的步驟</u>：

1. 透過Commerce Marketplace購買擴充功能。
1. 新增擴充功能的存取金鑰，並同步至Marketplace。
1. 前往管理員的Extension Manager區段。

<u>預期結果</u>：

此擴充功能會顯示在「Commerce管理員」的「Extension Manager」區段上。

<u>實際結果</u>：

**Commerce管理員的Extension Manager區段上未出現任何擴充功能，類似於以下影像：**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## 因應措施

使用命令列Adobe Commerce安裝，如開發人員檔案中的[一般CLI安裝](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)所示。
