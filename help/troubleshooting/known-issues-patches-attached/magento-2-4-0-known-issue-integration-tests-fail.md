---
title: 「Adobe Commerce 2.4.0已知問題：整合測試失敗」
description: 本文針對Adobe Commerce 2.4.0問題提供修補程式，該問題導致整合測試失敗，因為「Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest：：setup()」的宣告與用於2.4.0的PHPUnit 9不相容。
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知問題：整合測試失敗

本文針對Adobe Commerce 2.4.0問題提供修補程式，該問題導致整合測試失敗，因為`Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()`的宣告與用於2.4.0的PHPUnit 9不相容。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 問題

<u>要再現的步驟</u>

執行2.4.0整合測試。

<u>預期結果</u>

測試通過。

<u>實際結果</u>

*PHP嚴重錯誤： Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest：：setup()的宣告必須與PHPUnit\\Framework\\TestCase：：setup()： /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php第36*&#x200B;行中的void相容

## 解決方案

套用本文提供的修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.4.0
* Adobe Commerce內部部署2.4.0

## 如何套用修補程式

請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得指示。

## 附加的檔案
