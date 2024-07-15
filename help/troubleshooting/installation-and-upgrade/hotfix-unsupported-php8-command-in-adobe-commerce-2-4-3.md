---
title: Adobe Commerce升級2.4.3、2.3.7-p1 PHP嚴重錯誤Hotfix
description: 「本文修正了商家嘗試升級至Adobe Commerce （所有部署方法）或Magento Open Source2.4.3或2.3.7-p1時看到以下錯誤的問題：」
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce升級2.4.3、2.3.7-p1 PHP嚴重錯誤Hotfix

本文提供當商家嘗試升級至Adobe Commerce （所有部署方法）或Magento Open Source2.4.3或2.3.7-p1時，他們看到以下錯誤的修正：

*PHP嚴重錯誤：未攔截錯誤：呼叫&lt;...>Magento\Framework\Filesystem\Directory\str_contains：74*&#x200B;中的未定義函式/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php()

此問題將在2.4.4、2.4.3-p1和2.3.7-p2版本的範圍內修正。

## 受影響的版本和產品

* 升級至2.3.7-p1或2.4.3時，使用Adobe Commerce （所有部署方法）。
* 升級至2.3.7-p1或2.4.3時出現Magento Open Source。

## 問題

此問題是由使用PHP 8的新Adobe Commerce 2.4.3和2.3.7-p1版本僅功能`str_contains`所造成。 Adobe Commerce 2.4.3和2.3.7-p1僅與PHP 7.4相容，因此無法使用此函式。

<u>要再現的步驟</u> ：

嘗試升級至Adobe Commerce 2.4.3或2.3.7-p1。

<u>預期結果：</u>

升級成功。

<u>實際結果：</u>

php嚴重錯誤。

## 解決方案

作為因應措施，您可以在CLI/終端機中執行下列命令：從Magento根資料夾執行`composer require symfony/polyfill-php80`或安裝撰寫器修補程式。

為了修正2.4.3的問題，Adobe Commerce （所有部署方法）和Magento Open Source商家應套用修補程式：

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

為了修正2.3.7-p1的問題，Adobe Commerce （所有部署方法）和Magento Open Source商家應套用修補程式：

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## 如何套用修正程式

如需指示，請參閱[如何套用Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 相關閱讀

GitHub [Magento2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)中不支援的PHP 8命令
