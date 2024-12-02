---
title: Adobe Commerce內部部署2.4.2：缺少產品影像
description: 本文會說明一個已知的Adobe Commerce內部部署2.4.2問題，此問題導致產品影像未上傳至產品頁面。 此問題排程在2.4.3版之後的未來版本中解決。目前沒有可用的解決方案，但做為解決辦法，您可以停用Nginx來調整影像大小。
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce內部部署2.4.2：缺少產品影像

本文會說明一個已知的Adobe Commerce內部部署2.4.2問題，此問題導致產品影像未上傳至產品頁面。 此問題排程在2.4.3版之後的未來版本中解決。目前沒有可用的解決方案，但做為解決辦法，您可以停用Nginx來調整影像大小。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.2

## 問題

產品影像已儲存在`s3`儲存貯體，但未同步回`pub/media`目錄。 只有同時使用兩者時，才會發生此問題：

* 啟用網站的Nginx可調整影像大小
* AWS `s3`作為媒體儲存空間

<u>必要條件</u>：

Adobe Commerce已與Nginx一併安裝。

<u>要再現的步驟</u>：

1. 設定Adobe Commerce以使用AWS `s3`作為媒體儲存空間。
1. 使用Adobe Commerce安裝目錄中提供的`nginx.conf.sample`設定檔和Nginx虛擬主機來設定Nginx。 請參閱我們的開發人員檔案中的[設定Nginx](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/nginx)。
1. 使用單一產品影像建立簡單產品。
1. Nginx在`nginx.conf.sample`中調整影像大小的組態未加註解，類似於：

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>預期結果</u>：

產品影像會上傳至產品頁面。

<u>實際結果</u>：

產品影像未上傳至產品頁面。

## 因應措施

停用Nginx以調整影像大小。
