---
title: 在沙箱指令碼中BootstrapAdobe Commerce 2
description: 若要在範例沙箱指令碼中初始化Adobe Commerce 2應用程式，請從Adobe Commerce根目錄執行以下指令碼：
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# 在沙箱指令碼中BootstrapAdobe Commerce 2

若要在範例沙箱指令碼中初始化Adobe Commerce 2應用程式，請從Adobe Commerce根目錄執行以下指令碼：

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
