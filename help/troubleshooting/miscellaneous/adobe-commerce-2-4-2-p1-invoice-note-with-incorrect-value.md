---
title: Adobe Commerce 2.4.2-p1：含錯誤值的發票備註
description: 本文會說明已知的Adobe Commerce 2.4.2-p1問題，其中在建立訂單時變更客戶群組時，會產生值不正確的發票備註。 此問題已在2.4.3版中修正。
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%
---
# Adobe Commerce 2.4.2-p1：含錯誤值的發票備註

本文會說明已知的Adobe Commerce 2.4.2-p1問題，其中在建立訂單時變更客戶群組時，會產生值不正確的發票備註。 此問題已在2.4.3版中修正。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.2-p1
* 雲端基礎結構上的Adobe Commerce 2.4.2-p1

## 問題

若在建立訂單時變更客戶群組，則會以不正確的商業發票備註產生商業發票。

<u>要再現的步驟</u>：

1. 建立&#x200B;**測試客戶帳戶**&#x200B;並將其新增至&#x200B;**零售客戶群組**。
1. 為測試客戶建立&#x200B;**新訂單**，新增&#x200B;**產品**&#x200B;和&#x200B;**地址**。
1. 選取&#x200B;**送貨方法**。
1. 在&#x200B;**帳戶資訊**&#x200B;區段中，將客戶群組從&#x200B;**Retailer**&#x200B;變更為&#x200B;**政府**。
1. 按一下&#x200B;**下訂單**。
1. 按一下&#x200B;**發票** > **提交發票**。

<u>預期結果</u>：

下列附註應出現在此訂單的&#x200B;**附註**&#x200B;區段下：「Vertex Invoice已成功傳送。 金額：$0.00。」

<u>實際結果</u>：

下列附註會出現在此訂單的&#x200B;**附註**&#x200B;區段下：「已成功傳送頂點發票。 金額：$3.23。」

## 解決方案

此問題已在2.4.3版中修正。
