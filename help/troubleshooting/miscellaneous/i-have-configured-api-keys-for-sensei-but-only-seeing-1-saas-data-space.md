---
title: 設定Adobe AI API金鑰後無法檢視多個SaaS資料空間
description: 針對Adobe AI的API金鑰設定完成後，您只看到一個SaaS資料空間的問題，本文提供解決方案。
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d3b92bef-63fa-5031-a925-d04d9362d616
    internal-label: Saas
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%
---
# 設定Adobe AI API金鑰後無法檢視多個SaaS資料空間

為Commerce服務(例如Adobe AI服務（產品建議或Live Search）或Adobe Commerce的支付服務)設定API金鑰後，您可能會在Commerce服務聯結器中看到多個SaaS資料空間。 根據產品權益和部署型別，聯結器只會顯示一個SaaS資料空間，這是預期行為。

## 受影響的產品和版本

* Adobe Commerce （所有部署方法）：所有版本
* Magento Open Source：所有版本
* 擴充功能或技術（Fastly、New Relic等）、Adobe AI （產品推薦/即時搜尋）

## 問題

設定Adobe AI API金鑰後，系統只會顯示一個SaaS資料空間。

## 原因

可用的SaaS資料空間數量取決於與Commerce帳戶相連結的產品權益以及所使用的服務型別。

## 解決方案

一般而言，可用的SaaS資料空間數量取決於Commerce授權：

* Adobe Commerce：一個生產資料空間和兩個測試資料空間
* Magento Open Source：一個生產資料空間，沒有測試資料空間

對於付款服務，預設行為是：

* Adobe Commerce （*雲端或內部部署*）上的付款服務預設有三個資料空間：
* 一個生產資料空間
* 兩個測試資料空間
* Magento Open Source上的支付服務預設有一個資料空間

擁有多個Cloud專案或內部部署（*即時/生產*）安裝的客戶，也可以透過提交支援要求來要求每個專案或執行個體的其他生產和測試資料空間。

使用Adobe支付服務的Magento Open Source客戶也可以請求額外的資料空間。 在提交支援請求以新增測試資料空間之前，請聯絡付款團隊以取得事先核准。

>[!NOTE]
> * 請勿在多個環境中同時使用相同的SaaS資料空間。 如果跨環境重複使用生產或測試資料空間，資料可能會變得混合併需要清理。
> * Adobe Commerce （*雲端/內部部署*）上的付款服務預設有三個資料空間。
> * Magento Open Source上的支付服務預設有一個資料空間。
> 若要請求其他資料空間：
> * 使用Adobe支付服務的Magento Open Source客戶可請求額外的資料空間。 在提交支援要求以取得測試資料空間之前，請聯絡付款團隊以取得事先核准。
> * 擁有多個Cloud專案或內部部署（*即時/生產*）安裝的客戶，也可以透過提交支援要求來要求每個專案或執行個體的其他生產和測試資料空間。

## 重新關聯的閱讀

[SaaS資料空間布建](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
