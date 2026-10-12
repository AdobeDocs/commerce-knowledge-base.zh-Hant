---
title: 店面未顯示產品
description: 本文提供當產品未顯示在店面時的解決方案。
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%
---
# 店面未顯示產品

本文提供當產品未顯示在店面時的解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署X.X.X
* 雲端基礎結構X.X.X上的Adobe Commerce

## 問題

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 移至&#x200B;**目錄** > **產品**。

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. 按一下&#x200B;**新增產品**&#x200B;並完成產品建立程式。 或是從CSV檔案匯入產品。

<u>預期結果</u>：

產品會顯示在店面上。

<u>實際結果</u>：

產品未顯示。

## 原因

這可能是由許多原因造成的。 請依照下列步驟檢查有助於識別和解決問題的要點。

## 解決方案

下列各點都可能解決此問題。

* 檢查「管理員」中的產品設定。 移至&#x200B;**目錄** > **產品**，開啟產品頁面，並確定下列欄位已正確設定：
  * **啟用產品** = *是。*
  * **庫存狀態**： *庫存*。 或者，如果&#x200B;*缺貨*&#x200B;為正確的值，請確定&#x200B;**顯示缺貨產品** （**商店** > **設定** > **組態** > **目錄** > **庫存** > **庫存選項** > **顯示缺貨產品**）設定為&#x200B;*是* （已在全域層級設定）。
  * **類別**：如果您嘗試在類別頁面上尋找產品，請確認已將產品指派給類別。 若要簡化疑難排解，請從目前頁面建立新類別，並為其指派產品。
  * **可見度** = *目錄，搜尋。*
  * 在網站&#x200B;**的**&#x200B;產品區段中，確定已將產品指派給正確的網站。
  * 將範圍選擇器切換到商店檢視，您會嘗試在商店尋找產品，並驗證相同的設定。
* 從主控台執行`bin/magento indexer:reindex`，並在&#x200B;**系統** > **工具** > **快取管理**&#x200B;底下清除Admin中的所有快取，或從主控台執行`bin/magento cache:clean`，以執行完整重新索引。
* 如果上述方法沒有幫助，您可以檢查`var/log`目錄中的記錄以開始進一步調查。



