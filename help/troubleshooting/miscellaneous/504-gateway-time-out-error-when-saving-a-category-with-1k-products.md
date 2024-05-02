---
title: 使用1k+個產品儲存類別時發生504閘道逾時錯誤
description: 本文會針對您執行大類別(1k+ plus products)作業時可能遇到的逾時問題提供解決方案。
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 使用1k+個產品儲存類別時發生504閘道逾時錯誤

本文會針對您執行大類別(1k+ plus products)作業時可能遇到的逾時問題提供解決方案。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.3.3
* Adobe Commerce內部部署2.3.3
* Magento Open Source2.3.3

## 問題

先決條件：此 **商店** > **設定** > **目錄** > **目錄** > **使用產品URL的類別路徑** 選項已設為 *是* 以取得商店檢視。

<u>要再現的步驟</u>

1. 在Commerce Admin中，前往 **目錄** > **類別**.
1. 開啟大型類別，像是超過1000項指派的產品。
1. 將產品新增至類別。
1. 按一下 **儲存類別**.

<u>預期結果：</u>

類別已成功儲存。

<u>實際結果：</u>

儲存程式五分鐘後，會顯示504閘道逾時錯誤頁面。

## 原因

處理作業所需的時間比伺服器設定的逾時時間還長。

## 解決方案

停用 **產生「類別/產品」URL重寫** 選項會從資料庫中移除所有類別/產品URL重新寫入，大幅減少大型類別作業所需的時間。

>[!WARNING]
>
>關閉此選項將導致永久移除類別/產品URL重寫，而無法還原。

若要停用 **產生「類別/產品」URL重寫** 選項：

1. 在Commerce管理員中，導覽至 **商店** > **設定** > **目錄** > **目錄**.
1. 在設定頁面的左上角、 **範圍** 欄位，將您的設定範圍設為 *預設設定*.
1. 設定 **產生「類別/產品」URL重寫** 至 *否*.
1. 按一下 **儲存設定**.
1. 執行以清除快取    ```bash    bin/magento cache:clean    ```    或在「Commerce管理員」中的 **系統** > **工具** > **快取管理**.

現在您可以繼續將產品新增至類別，或移動具有大量產品的類別，這些操作將花費更少時間，並且不會導致逾時。

## 相關閱讀

[自動產品重新導向](https://docs.magento.com/user-guide/v2.3/marketing/url-redirect-product-automatic.html) 在我們的使用手冊中。
