---
title: 「Adobe Commerce上的撰寫器更新失敗：不相容的引數型別」
description: 本文提供因程式碼編譯問題而卡住部署的解決方案。 此問題是由新版本的symfony/主控台相依性(4.4.27、4.4.28)所導致。
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Adobe Commerce上的撰寫器更新失敗：不相容的引數型別

>[!NOTE]
>
>此問題現在已在最新的Symfony 4.4.29版本中修正。

本文提供因程式碼編譯問題而卡住部署的解決方案。 此問題是由新版本的symfony/主控台相依性(4.4.27、4.4.28)所導致。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）和Magento Open Source：
   * 2.4.0、2.4.0-p1、2.4.1、2.4.1-p1、2.4.2、2.4.2-p1、2.4.2-p2、2.4.3
   * 2.3.5、2.3.5-p1、2.3.5-p2、2.3.6、2.3.6-p1、2.3.7、2.3.7-p1
* symfony/主控台相依性(4.4.27、4.4.28)。

## 問題

新版symfony/主控台相依性(4.4.27、4.4.28)導致相依性編譯程式失敗。

<u>要再現的步驟</u>：

當您安裝或升級Adobe Commerce或執行撰寫器更新時，執行會失敗，並出現下列錯誤訊息：
*不相容的引數型別：必要的型別： int。 實際型別：字串*

## 原因

此問題是由於Adobe Commerce核心程式碼與4.4.27和4.4.28版中發行的最新「symfony/console」相依性不相容。

## 解決方案

在新的symfony/console 4.2.29版（預計於2021年8月）發行後，問題將自動解決。

**如何在Adobe Commerce內部部署修正：**

Adobe Commerce內部部署2.4.x

在CLI/終端機中執行以下命令：

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

所有2.3.5以上的Adobe Commerce內部部署商家都應執行下列CLI命令：

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**如何在雲端基礎結構上修正Adobe Commerce：**

執行上述命令或升級至最新的ECE工具版本(ece-tools：2002.1.7)，將於7月29日（星期四）提供。 如需相關步驟，請參閱 [適用於Adobe Commerce的Cloud >更新ece-tools版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html) （位於我們的開發人員檔案中）。

完整修正將在Adobe Commerce （所有部署方法） 2.4.4中發佈。

## 相關閱讀

* Github： [2021-07-27 Composer更新不相容的引數型別：必要型別： int。 實際型別：字串](https://github.com/magento/magento2/issues/33595)
