---
title: 影響xdebug安裝的已知問題
description: 本文提供在使用選用的PHP擴充功能'xdebug'時發生例外狀況錯誤時的解決方案。
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# 影響xdebug安裝的已知問題

本文提供在使用選用的PHP擴充功能`xdebug`時發生例外狀況錯誤時的解決方案。

* 安裝期間
* 成功安裝後存取Commerce管理員或店面

例外狀況範例：

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

若要解決此問題，您可以：

* 停用`xdebug`延伸。
* 將`xdebug.max_nesting_level`的值設定為200或以上的值。 如需詳細資訊，請參閱[xdebug檔案](http://xdebug.org/docs/basic#max_nesting_level)。

在您變更或停用`xdebug`的設定後，請重新啟動Apache：

* CentOS： `sudo service httpd restart`
* Ubuntu： `sudo service apache2 restart`
