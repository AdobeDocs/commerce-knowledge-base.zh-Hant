---
title: 從Git推播時放入生產環境的新環境
description: 本文提供從Git版本控制系統推送新環境時，將新環境放置在雲端基礎結構上Adobe Commerce的生產環境底下的問題解決方案。
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# 從Git推播時放入生產環境的新環境

本文提供從Git版本控制系統推送新環境時，將新環境放置在雲端基礎結構上Adobe Commerce的生產環境底下的問題解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 問題

<u>必要條件</u>：

讓本機Git控制專案的複製。

<u>要再現的步驟</u>：

您必須從測試分支建立整合分支：

1. 在本機Shell中執行以下命令，以切換至臨時分支： `git checkout staging`
1. 在本機Shell中執行下列命令，從暫存分支建立整合分支： `git checkout -b <branch>`
1. 將分支推送到遠端存放庫，並在本機Shell中執行下列命令來設定上游分支： `git push --set-upstream origin <branch>`

<u>預期結果</u>：

新分支會在測試分支下建立。

<u>實際結果</u>：

新分支是在生產分支下建立的。

## 原因

這不是錯誤。 若要設定其他分支的父分支，商家應使用magento-cloud CLI。

## 解決方案

只有當商家推送新建立的分支並啟動它後，才能設定父分支。 請參閱我們的開發人員檔案中的[雲端基礎結構上的Adobe Commerce > Bitbucket整合](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/dev-tools/integrations/bitbucket#create-a-cloud-branch)。

若要更新伺服器上現有分支的父系，請使用magento-cloud CLI中的`magento-cloud environment:info`命令。

使用範例：

`magento-cloud environment:info parent Staging`

這會將目前出庫分支的父分支設定為「測試」。

## 相關閱讀

* 在開發人員檔案中，將[Adobe Commerce放在雲端基礎結構上> magento-cloud CLI](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)。
