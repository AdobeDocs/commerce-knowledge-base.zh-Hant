---
title: 影響xdebug安裝的已知問題
description: 本文提供在使用選用的PHP擴充功能'xdebug'時發生例外狀況錯誤時的解決方案。
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# 影響xdebug安裝的已知問題

本文提供在使用選用的PHP擴充功能時發生例外錯誤時的解決方案 `xdebug`.

* 安裝期間
* 成功安裝後存取Commerce管理員或店面

例外狀況範例：

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

若要解決此問題，您可以：

* 停用 `xdebug` 副檔名。
* 設定值 `xdebug.max_nesting_level` 值增加至200或更多。 如需詳細資訊，請參閱 [xdebug檔案](http://xdebug.org/docs/basic#max_nesting_level).

變更或停用的設定後 `xdebug`，重新啟動Apache：

* CentOS： `sudo service httpd restart`
* Ubuntu： `sudo service apache2 restart`
