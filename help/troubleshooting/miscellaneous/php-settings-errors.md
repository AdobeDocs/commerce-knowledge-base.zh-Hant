---
title: PHP設定錯誤
description: 本文提供PHP設定錯誤的解決方案。
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# PHP設定錯誤

本文提供PHP設定錯誤的解決方案。

## PHP記憶體限制錯誤

整備檢查可確保您至少為PHP處理序預留了1GB的記憶體。 此設定對大部分的安裝而言應該已足夠，包括安裝選用的範例資料。 不過，我們建議至少使用2GB來進行偵錯。

若要增加PHP記憶體限制：

1. 登入您的Adobe Commerce伺服器。
1. 找出您的 `php.ini` 檔案，使用下列命令：

   ```
   bash    $ php --ini
   ```

1. 作為使用者，具有 `root` 許可權，使用文字編輯器開啟 `php.ini` 指定者 `Loaded Configuration File`.
1. 尋找 `memory_limit`.
1. 將其變更為值 `2GB` 以供正常使用和偵錯。
1. 將變更儲存至 `php.ini` 並退出文字編輯器。
1. 重新啟動您的網頁伺服器。 範例如下：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`
   * nginx （CentOS和Ubuntu）： `service nginx restart`

1. 請再次嘗試安裝。

## 大型表單導致max-input-vars錯誤

具有大量儲存稽核、產品、屬性或選項的組態可產生超過預設PHP限制的表單。 如果傳送的值數量超過 `max-input-vars` 限制設定於 `php.ini` （預設為1000），不會傳輸其餘資料，且不會更新這些資料庫值。 發生此情況時，PHP記錄檔中會出現警告：

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

「 」沒有「適當」值 `max-input-vars`；這取決於設定的大小和複雜性。 修改中的值 `php.ini` 檔案。 另請參閱 [必要的PHP設定](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## xdebug最大函式巢狀層級錯誤

另請參閱 [在安裝期間，xdebug最大函式巢狀層級錯誤](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## 存取PHTML範本時會顯示錯誤

錯誤文字通常是：

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### 解決方案：設定 `asp_tags = off` 在php.ini中

多個範本具有語法以支援包裝在範本上的抽象層級（使用不同的範本引擎，例如Twig） `<% %>` 類似以下的標籤 [範本](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) 若要顯示產品影像：

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

更多關於 [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

編輯 `php.ini` 並設定 `asp_tags = off`. 如需詳細資訊，請參閱 [必要的PHP設定](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
