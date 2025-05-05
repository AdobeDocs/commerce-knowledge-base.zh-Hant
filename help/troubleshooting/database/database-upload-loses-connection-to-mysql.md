---
title: 資料庫上載遺失與MySQL的連線
description: 本文提供當資料庫上載失去與MySQL的連線時的解決方案。
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 資料庫上載遺失與MySQL的連線

本文提供當資料庫上載失去與MySQL的連線時的解決方案。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce 2.2.x.、2.3.x

## 問題

資料庫沒有上傳到雲端基礎結構上Adobe Commerce的主要/整合分支Pro規劃架構或雲端基礎結構上Adobe Commerce的任何分支入門規劃架構，症狀是無法連線。 您在CLI中看到此錯誤。

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## 原因

這通常是因為缺少匯入資料庫的磁碟空間。

## 解決方案

檢查磁碟空間是否不足。 若要這麼做，請針對資料庫連線埠3306在CLI中執行`netcat`命令；如果磁碟已滿，則會出現磁碟已滿訊息：

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

您必須在`services.yaml`中配置更多空間給資料庫，而且如果您有未使用的空間，則需部署。 如需相關步驟，請參閱[服務磁碟空間](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space)。

注意：在Pro架構計畫上，您可以執行下列命令來檢查磁碟分割上配置的空間： `df -h`

預期輸出與以下輸出類似。 在此範例中，已使用10GB的25GB配置，而未使用15GB的MySQL空間。

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## 相關閱讀

在開發人員檔案中[管理磁碟空間](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
