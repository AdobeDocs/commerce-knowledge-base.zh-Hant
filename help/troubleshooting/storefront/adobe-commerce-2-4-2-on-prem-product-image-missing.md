---
title: 'Adobe Commerce內部部署2.4.2：缺少產品影像'
description: 本文會說明一個已知的Adobe Commerce內部部署2.4.2問題，此問題導致產品影像未上傳至產品頁面。 此問題排程在2.4.3版之後的未來版本中解決。目前沒有可用的解決方案，但做為解決辦法，您可以停用Nginx來調整影像大小。
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce內部部署2.4.2：缺少產品影像

本文會說明一個已知的Adobe Commerce內部部署2.4.2問題，此問題導致產品影像未上傳至產品頁面。 此問題排程在2.4.3版之後的未來版本中解決。目前沒有可用的解決方案，但做為解決辦法，您可以停用Nginx來調整影像大小。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.2

## 問題

產品影像會儲存在 `s3` 貯體，但未同步回 `pub/media` 目錄。 只有同時使用兩者時，才會發生此問題：

* 啟用網站的Nginx可調整影像大小
* AWS `s3` 作為媒體儲存空間

<u>必要條件</u>：

Adobe Commerce已與Nginx一併安裝。

<u>要再現的步驟</u>：

1. 設定Adobe Commerce以使用AWS `s3` 作為媒體儲存空間。
1. 使用設定Nginx `nginx.conf.sample` Adobe Commerce安裝目錄中提供的設定檔及Nginx虛擬主機。 另請參閱 [設定Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) （位於我們的開發人員檔案中）。
1. 使用單一產品影像建立簡單產品。
1. Nginx在中調整影像大小的組態尚未註解 `nginx.conf.sample` 與以下內容類似：

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
