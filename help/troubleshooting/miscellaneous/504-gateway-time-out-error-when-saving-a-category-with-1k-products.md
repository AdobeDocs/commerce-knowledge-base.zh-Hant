---
title: 使用1k+個產品儲存類別時發生504閘道逾時錯誤
description: 本文會針對您執行大類別(1k+ plus products)作業時可能遇到的逾時問題提供解決方案。
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

先決條件： **商店** > **組態** > **目錄** > **目錄** > **使用產品URL的類別路徑**&#x200B;選項已針對您的商店檢視設定為&#x200B;*是*。

<u>要再現的步驟</u>

1. 在Commerce Admin中，移至&#x200B;**目錄** > **類別**。
1. 開啟大型類別，像是超過1000項指派的產品。
1. 將產品新增至類別。
1. 按一下&#x200B;**儲存類別**。

<u>預期結果：</u>

類別已成功儲存。

<u>實際結果：</u>

儲存程式五分鐘後，會顯示504閘道逾時錯誤頁面。

## 原因

處理作業所需的時間比伺服器設定的逾時時間還長。

## 解決方案

停用&#x200B;**產生「類別/產品」URL重寫**&#x200B;選項將會從資料庫中移除所有類別/產品URL重寫，並大幅減少大型類別作業所需的時間。

>[!WARNING]
>
>關閉此選項將導致永久移除類別/產品URL重寫，而無法還原。

若要停用&#x200B;**產生「類別/產品」 URL重寫**&#x200B;選項：

1. 在Commerce管理員中，瀏覽至&#x200B;**商店** > **設定** > **目錄** > **目錄**。
1. 在設定頁面的左上角，在&#x200B;**範圍**&#x200B;欄位中，將您的設定範圍設定為&#x200B;*預設設定*。
1. 將&#x200B;**產生「類別/產品」URL重寫**&#x200B;設定為&#x200B;*否*。
1. 按一下&#x200B;**儲存設定**。
1. 執行以清除快取    ```bash    bin/magento cache:clean    ```    或在Commerce管理員中的&#x200B;**系統** > **工具** > **快取管理**&#x200B;下。

現在您可以繼續將產品新增至類別，或移動具有大量產品的類別，這些操作將花費更少時間，並且不會導致逾時。

## 相關閱讀

使用手冊中的[自動產品重新導向](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic)。
