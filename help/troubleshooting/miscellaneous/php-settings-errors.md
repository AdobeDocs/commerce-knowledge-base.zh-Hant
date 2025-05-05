---
title: PHP設定錯誤
description: 本文提供PHP設定錯誤的解決方案。
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. 使用下列命令找出您的`php.ini`檔案：

   ```
   bash    $ php --ini
   ```

1. 以具有`root`許可權的使用者身分，使用文字編輯器開啟`Loaded Configuration File`所指定的`php.ini`。
1. 找到`memory_limit`。
1. 將其變更為值`2GB`，以供正常使用和偵錯。
1. 將變更儲存至`php.ini`並結束文字編輯器。
1. 重新啟動您的網頁伺服器。 範例如下：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`
   * nginx （CentOS和Ubuntu）： `service nginx restart`

1. 請再次嘗試安裝。

## 大型表單導致max-input-vars錯誤

具有大量儲存稽核、產品、屬性或選項的組態可產生超過預設PHP限制的表單。 如果傳送的值數目超過`php.ini`內設定的`max-input-vars`限制（預設為1000），則不會傳輸剩餘的資料，也不會更新這些資料庫值。 發生此情況時，PHP記錄檔中會出現警告：

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

`max-input-vars`沒有「適當的」值；這取決於您設定的大小和複雜性。 視需要修改`php.ini`檔案中的值。 請參閱[必要的PHP設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/php-settings)。

## xdebug最大函式巢狀層級錯誤

請參閱[在安裝期間，xdebug最大函式巢狀層級錯誤](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md)。

## 存取PHTML範本時會顯示錯誤

錯誤文字通常是：

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### 解決方案：在php.ini中設定`asp_tags = off`

多個範本具有語法以支援包裝在`<% %>`標籤中的範本抽象層級（使用不同的範本引擎，例如Twig），例如這個[範本](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml)用於顯示產品影像：

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

有關[asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags)的詳細資訊。

編輯`php.ini`並設定`asp_tags = off`。 如需詳細資訊，請參閱[必要的PHP設定](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/installation-guide/prerequisites/php-settings)。
