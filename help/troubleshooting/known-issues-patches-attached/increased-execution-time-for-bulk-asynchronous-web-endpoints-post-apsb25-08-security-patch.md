---
title: APSB25-08安全性修補程式之後，大量非同步Web端點的執行時間增加
description: 本文提供此問題的Hotfix：套用APSB25-08安全性修補程式後，1000多個專案的POST rest/all/async/bulk/V1/products要求執行時間大幅增加。
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# APSB25-08安全性修補程式之後，所有大量非同步Web端點的執行時間都有所增加

本文提供適用於所有大量非同步Web端點（例如`POST rest/all/async/bulk/V1/products`）的Hotfix，其中包含1000個以上的專案，在套用APSB25-08安全性修補程式後執行時間大幅延長。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11、2.4.4-p12

* Adobe Commerce （所有部署方法） 2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10、2.4.5-p11

* Adobe Commerce （所有部署方法） 2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8、2.4.6-p9

* Adobe Commerce （所有部署方法） 2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3、2.4.7-p4

* Adobe Commerce （所有部署方法） 2.4.8

## 問題

套用APSB25-08安全性修補程式後，具有1000+個專案的`POST rest/all/async/bulk/V1/products`個要求執行的時間明顯較長。

<u>要再現的步驟</u>：

1. 發出包含1000個以上專案（名稱、SKU和說明已足夠）的`POST rest/all/async/bulk/V1/products`請求。
1. 請注意請求所花費的時間。
1. 套用APSB25-08安全性修補程式，並使用`se:di:co`清除產生的資料和快取。
1. 執行`bin/magento c:f`。
1. 請前往storefront確認快取和產生的檔案已準備就緒。
1. 重複步驟1的要求。
1. 請注意請求所花費的時間增加。
1. 移除APSB25-08安全性修補程式、清除快取、重新產生程式碼，然後重複步驟1的要求以確認執行時間恢復正常。 （可選）

<u>預期結果</u>：

套用安全性修補程式後，`async/bulk`個要求的執行時間已大幅增加。

<u>實際結果</u>：

套用安全性修補程式後，`async/bulk`個要求的執行時間應該不會大幅增加，不過時間可能會增加。

## 解決方案

若要解決此問題，請套用[AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip)。

## 如何套用修補程式

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hant)提供的撰寫器修補程式，以取得指示。

## 相關閱讀

* [可用於Adobe Commerce的安全性更新 — APSB25-08](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-27149)
