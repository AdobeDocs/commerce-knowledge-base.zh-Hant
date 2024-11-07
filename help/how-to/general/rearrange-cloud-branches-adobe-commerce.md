---
title: 在Adobe Commerce上重新排列雲端分支
description: 本文提供在Adobe Commerce上重新排列雲端分支的步驟（如果它們未根據正確的階層進行組織）。 如果您沒有將分支組織在正確的階層中，您將無法合併到正確的父分支 — 它將轉到現有的父分支。
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 在Adobe Commerce上重新排列雲端分支

本文提供在Adobe Commerce上重新排列雲端分支的步驟（如果它們未根據正確的階層進行組織）。 如果您沒有將分支組織在正確的階層中，您將無法合併到正確的父分支 — 它將轉到現有的父分支。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce， 2.3.0-2.3.7-p2， 2.4.0-2.4.3-p1

## 雲端分支組織

分支的正確階層組織為：

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## 不正確的雲端分支組織的解決方案

若要重新排列雲端分支：

1. 您必須擁有[[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)角色。
1. 安裝magento-cloud [!DNL CLI] （如果尚未安裝）。
1. 為需要移動的分支執行以下命令：
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

附註：建立新分支時，您可以指定父分支。 如需相關步驟，請參閱開發人員檔案中的[建立分支](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches)快速入門。

您可以使用`branch <environment-name> <parent-environment-ID>` magento-cloud environment命令建立新的環境分支。

建立及啟用新環境分支可能需要一些額外的時間。

## 相關閱讀

在我們的開發人員檔案中[使用 [!DNL CLI]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches)管理分支。
