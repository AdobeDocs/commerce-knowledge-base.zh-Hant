---
title: 提交不正確的檔案時發生部署錯誤
description: 當您收到因不正確認可不應新增的檔案/資料夾存放庫所導致的部署錯誤時，本文提供此問題的解決方案。
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# 提交不正確的檔案時發生部署錯誤

本文修正了因不正確認可不應新增的檔案/資料夾存放庫而導致部署錯誤的問題。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce （所有版本）

## 問題

當您認可至檔案/資料夾的存放庫時，會發生部署錯誤。 例如，下列錯誤是由於嘗試在[建置階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase)期間無法使用資料庫時連線至資料庫所造成：

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## 原因

某些檔案/資料夾不應認可至存放庫，因為它們會造成[部署工作流程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html)中斷。

## 解決方案

移除存放庫中的這些檔案/資料夾（如果存在）：

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
