---
title: robots.txt未更新或顯示預設設定
description: 文章提供已正確設定'robots.txt'時的解決方案，例如，根據[Adobe Commerce robots.txt的最佳實務](https://support.magento.com/hc/en-us/articles/360048754931)，但'robots.txt'未更新或顯示預設設定。
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt未更新或顯示預設設定

文章提供您正確設定`robots.txt`時的解決方案，例如根據[Adobe Commerce robots.txt的最佳實務](https://support.magento.com/hc/en-us/articles/360048754931)，但`robots.txt`未更新或顯示預設設定。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.3.x、2.4.x

## 問題

無法變更預設`robots.txt`設定。

<u>要再現的步驟：</u>

1. 存取「管理員」面板。
1. 新增內容至&#x200B;**內容** >設計> **組態** > **編輯`robots.txt`**&#x200B;檔案的自訂指示（例如「hello」文字）並儲存變更。
1. 瀏覽`robots.txt` URL。

<u>預期結果：</u>
`robots.txt`已儲存文字。

<u>實際結果：</u>

`robots.txt`檔案未變更。

## 原因

搜尋引擎的索引已關閉。

## 解決方案

依搜尋引擎啟用索引。 請參閱我們的開發人員檔案中的[依搜尋引擎設定索引](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine)。

## 相關閱讀

* [在開發人員檔案中新增網站地圖和搜尋引擎機器人](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。
