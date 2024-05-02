---
title: 店面未顯示產品
description: 本文提供當產品未顯示在店面時的解決方案。
exl-id: 454eca5b-4722-46e0-8e5d-3daf8e3e675a
feature: Cache, Categories, Console, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '344'
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
1. 前往 **目錄** > **產品**.

   ![open_product_page_magento_2.4.1.png](assets/open_product_page_magento_2.4.1.png)

1. 按一下 **新增產品** 並完成產品建立流程。 或是從CSV檔案匯入產品。

<u>預期結果</u>：

產品會顯示在店面上。

<u>實際結果</u>：

產品未顯示。

## 原因

這可能是由許多原因造成的。 請依照下列步驟檢查有助於識別和解決問題的要點。

## 解決方案

下列各點都可能解決此問題。

* 檢查「管理員」中的產品設定。 前往 **目錄** > **產品**，開啟產品頁面，並確認下列欄位已正確設定：
   * **啟用產品** = *是。*
   * **庫存狀態**： *有貨*. 或者 *無庫存* 是正確的值，請確定 **顯示無庫存產品** (**商店** > **設定** > **設定** > **目錄** > **詳細目錄** > **股票期權** > **顯示無庫存產品**)設為 *是* （已在全域層級設定）。
   * **類別**：如果您嘗試在類別頁面上尋找產品，請確認已將產品指派給類別。 若要簡化疑難排解，請從目前頁面建立新類別，並為其指派產品。
   * **可見度** = *目錄，搜尋。*
   * 在 **網站中的產品** 區段，確定產品已指派至正確的網站。
   * 將範圍選擇器切換到商店檢視，您會嘗試在商店尋找產品，並驗證相同的設定。
* 透過執行來執行完整重新索引 `bin/magento indexer:reindex` ，並排清「管理員」中 **系統** > **工具** > **快取管理**，或從主控台執行 `bin/magento cache:clean`.
* 如果上述方法沒有幫助，您可以透過檢視中的記錄來開始進一步調查 `var/log` 目錄。

## 我們的支援知識庫中的相關閱讀

* [記錄Pro架構的位置（目錄）](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)
* [記錄入門架構的位置（目錄）](/help/how-to/general/log-locations-directories-for-starter-plan.md)
