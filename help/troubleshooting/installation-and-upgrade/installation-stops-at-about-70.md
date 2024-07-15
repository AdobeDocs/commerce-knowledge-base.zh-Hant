---
title: 安裝大約停止70%
description: 本文提供安裝停止約70%時的修正。
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 安裝大約停止70%

本文提供安裝停止約70%時的修正。

## 問題

在使用安裝精靈進行安裝期間，流程會在大約70%停止（包含或不包含範例資料）。 畫面上不會顯示錯誤。

## 原因

此問題的常見原因包括：

* [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)的PHP設定
* nginx和Varnish的逾時值

## 解決方案：

視需要設定下列所有專案。

### 所有Web伺服器和Varnish {#all-web-servers-and-varnish}

1. 使用[`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo)檔案找出您的`php.ini`。
1. 以具有`root`許可權的使用者身分，在文字編輯器中開啟`php.ini`。
1. 找到`max_execution_time`設定。
1. 將其值變更為`18000` 。
1. 將變更儲存至`php.ini`並結束文字編輯器。
1. 重新啟動Apache：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`

   如果您使用nginx或Varnish，請繼續下列各節。

### 僅限nginx {#nginx-only}

如果您使用nginx，請使用我們隨附的`nginx.conf.sample`，或在nginx主機設定檔案中新增逾時設定至`location ~ ^/setup/index.php`區段，如下所示：

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

重新啟動nginx： `service nginx restart`

### 僅限上漆 {#varnish-only}

如果您使用Varnish，請編輯`default.vcl`並將逾時限制值新增至`backend`區段，如下所示：

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

重新啟動Varnish。

```php
service varnish restart
```
