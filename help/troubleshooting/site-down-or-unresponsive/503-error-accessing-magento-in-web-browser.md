---
title: 在網頁瀏覽器中存取Adobe Commerce時出現503錯誤
description: 針對嘗試存取Adobe Commerce店面和/或管理員時出現503錯誤的問題，本文提供可能的解決方案。
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 在網頁瀏覽器中存取Adobe Commerce時出現503錯誤

針對嘗試存取Adobe Commerce店面和/或管理員時出現503錯誤的問題，本文提供可能的解決方案。

## 受影響的產品和版本

Adobe Commerce 2.3.x

## 問題 {#symptoms}

<u>要再現的步驟</u>

(先決條件：確認存放區不在 [維護模式](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-mode.html#config-mode-show))。

在網頁瀏覽器中導覽至您的Commerce管理員或店面。

<u>預期結果</u>

頁面載入。

<u>實際結果</u>

您收到HTTP 503 （服務無法使用）錯誤。 Apache `error.log` 包含下列訊息：

*無效的命令&#39;Order&#39;，可能拼寫錯誤或是由未包含在伺服器設定中的模組定義。*

## 原因 {#details}

Apache 2.4相容性模組 `mod_access_compat` 會導致Adobe Commerce URL重寫無法正常運作。

## 解決方案 {#suggested-solution}

啟用 `mod_access_compat` Apache模組並重新啟動Apache，方式為以具有「root」許可權的使用者身分執行以下命令：

```bash
a2enmod access_compat
service <name> restart
```

在CentOS上，

```bash
<name>
```

是

```bash
httpd
```

。在Ubuntu，

```bash
<name>
```

是

```bash
apache2
```

.

## 相關閱讀 {#additional-resources}

* [有關mod\_access\_compat的Apache檔案](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [有關mod\_authz\_host的Apache檔案](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Apache Definitive指南中的Order、Allow、Deny](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
