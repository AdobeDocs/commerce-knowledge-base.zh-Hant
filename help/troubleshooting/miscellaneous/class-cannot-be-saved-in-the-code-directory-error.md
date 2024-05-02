---
title: 「類別無法儲存在程式碼目錄中」錯誤
description: 本文說明如何修正指定相依性的方式導致類別無法即時自動產生，以及收到*「類別無法儲存在產生的/程式碼目錄中」*錯誤訊息的問題。
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 「類別無法儲存在程式碼目錄中」錯誤

本文說明如何修正指定相依性的方式導致類別無法即時自動產生，且您收到 *「類別無法儲存在產生的/程式碼目錄中」* 錯誤訊息。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.2.0或更新版本

## 問題

<u>要再現的步驟</u>

1. 在您的本機環境中，撰寫與自動產生的類別相依的自訂類別。
1. 執行觸發自訂類別的案例，並檢視其是否正常運作。
1. 認可並將變更推送至整合環境。 這將觸發部署流程。 部署成功。
1. 在 [整合環境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)，執行觸發自訂類別的案例。

<u>預期結果</u>

一切皆正確運作，就像在本機環境中一樣。

<u>實際結果</u>

失敗並出現錯誤訊息，指出您的類別無法儲存在 `generated/code` 目錄。

## 原因

問題的原因是您有相依性的類別不會在部署期間產生，而且無法在稍後觸發類別時即時產生，因為 `generated/code` 部署完成後，目錄無法寫入。

發生此情形有兩個主要原因：

* 案例1：與自動產生的類別具有相依性的類別位於進入點(例如 `index.php` )，部署期間不會掃描相依性。
* 案例2：直接指定自動產生類別的相依性（與宣告相依性的建構函式的建議用法比較）。

## 解決方案

這兩種情況的常見解決方案之一，是建立真正的工廠，而不是自動產生的類別。

或者，每個案例都有特定的解決方案。

### 案例1特定解決方案

將類別代碼從進入點移至另一個模組，然後用於進入點。

<u>範例</u>

中的原始程式碼，例如， `index2.php` ：

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

您必須執行下列步驟：

1. 將類別定義移至 `app/code/YourVendor/YourModule`：

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. 編輯進入點 `my_api/index.php` 因此看起來像這樣：

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### 案例2特定解決方案

將相依性宣告移至建構函式。

<u>範例</u>

原始類別宣告：

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

您需要變更其建構函式，如下所示：

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## 相關閱讀

* [程式碼產生](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/code-generation.html) （位於我們的開發人員檔案中）。
