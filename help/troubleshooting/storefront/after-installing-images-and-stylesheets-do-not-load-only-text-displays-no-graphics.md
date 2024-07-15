---
title: 安裝後，影像和樣式表不會載入；只會顯示文字，不會顯示圖形
description: 本文介紹安裝Adobe Commerce後樣式表和影像未載入問題的可能原因和解決方案。
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# 安裝後，影像和樣式表不會載入；只會顯示文字，不會顯示圖形

本文介紹安裝Adobe Commerce後樣式表和影像未載入問題的可能原因和解決方案。

## 受影響的產品和版本

* Adobe Commerce 2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x

## 問題

<u>要再現的步驟</u>

1. 安裝Adobe Commerce。
1. 導覽至店面或管理員。

<u>預期結果</u>

套用樣式後，沒有UI元素看起來像是遺漏樣式。

<u>實際結果</u>

樣式未正確套用，圖形遺失。

## 原因

影像和樣式表的路徑不正確，可能是因為基底URL不正確，或伺服器重寫(CentOS、Ubuntu)未正確設定。

若要確認這點，請使用網頁瀏覽器檢查器來檢查靜態資產的路徑，並確認這些資產位於Adobe Commerce或Magento Open Source檔案系統上。

靜態資產位於`frontend`和`adminhtml`目錄中的`<magento_root>/pub/static/`下。

## 解決方案

根據您使用的軟體及問題原因，以下是可能的解決方案：

* 如果您使用Apache網頁伺服器，請確認您的[伺服器重寫了](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite)設定和Adobe Commerce/Magento Open Source伺服器的基底URL，然後再試一次。 如果您設定Apache `AllowOverride`指示詞不正確，則無法從正確的位置提供靜態檔案。
* 如果您使用nginx網頁伺服器，請務必[設定虛擬主機檔案](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu)。 nginx虛擬主機檔案必須符合下列條件：
   * `include`指示詞必須指向您Adobe Commerce/Magento Open Source安裝目錄中的nginx組態檔範例。 例如：    `include /var/www/html/magento2/nginx.conf.sample;`
   * `server_name`指示詞必須符合您在安裝Adobe Commerce/Magento Open Source時指定的基底URL。 例如： `server_name 192.186.33.10;`
* 如果應用程式處於[生產模式](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode)，請嘗試使用`magento setup:static-content:deploy`命令部署靜態檢視檔案。 如需有關部署靜態檔案的詳細資訊，請參閱我們的開發人員檔案中的[部署靜態檢視檔案](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html)。
