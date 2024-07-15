---
title: Github代號問題和撰寫器金鑰程式
description: 本文提供解決方案，解決因過時撰寫器金鑰而導致Github權杖失敗的相關部署失敗問題。
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Github代號問題和撰寫器金鑰程式

本文提供解決方案，解決因過時撰寫器金鑰而導致Github權杖失敗的相關部署失敗問題。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer 1.10.20版及更低版本

>[!NOTE]
>
>由於Git匯入的權杖格式變更，Adobe Commerce內部部署商家應洽詢其主機提供者，以確保他們使用Composer 1.10.21版或更新版本。

## 問題

部署失敗，且部署記錄檔包含類似下列的資訊：

*嚴重錯誤：未攔截到UnexpectedValueException：您的github.com的github oauth權杖包含無效字元： /app/vendor/composer/composer/src/Composer/IO/BaseIO.php：129*&#x200B;中的「ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx」

## 原因

過時的撰寫器金鑰會導致Github權杖失敗，進而導致部署失敗。

## 解決方案

若要解決此問題，請將您的Composer版本更新為1.10.22：

1. 在您的本機環境中，執行`composer require “composer/composer”:”>1.10.21`。
1. 這為該撰寫器套件版本新增了需求。 檢查鎖定檔案 — `composer/composer`版本必須為1.0.22或更高版本。
1. 認可`composer.json`和`composer.lock`並推播部署。

如果此方法無法運作，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

## 相關閱讀

* [Github部落格： GitHub的新驗證權杖格式背後](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com新聞文章： GitHub變更Token格式以改善識別能力、秘密掃描和平均資訊量](https://www.infoq.com/news/2021/04/github-new-token-format/)
