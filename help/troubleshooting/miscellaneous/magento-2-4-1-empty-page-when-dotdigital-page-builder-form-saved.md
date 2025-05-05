---
title: 「Adobe Commerce 2.4.1：儲存dotdigital Page Builder表單時顯示空白頁面」
description: 針對Adobe Commerce 2.4.1中的已知問題，本文提供因應措施，說明使用Safari瀏覽器時，在「管理面板」中儲存dotdigital Page Builder表單後，顯示空白網頁。
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1：儲存dotdigital Page Builder表單時顯示空白頁面

針對Adobe Commerce 2.4.1中的已知問題，本文提供因應措施，說明使用Safari瀏覽器時，在「管理面板」中儲存dotdigital Page Builder表單後，顯示空白網頁。

## 受影響的產品和版本

* Adobe Commerce內部部署2.4.1
* 雲端基礎結構上的Adobe Commerce 2.4.1

## 問題

<u>要再現的步驟</u>

1. 移至&#x200B;**管理面板** > **內容** > **頁面**，然後選取任何頁面的&#x200B;**編輯**。
1. 移至&#x200B;**內容**，然後按一下&#x200B;**使用頁面產生器編輯**&#x200B;按鈕。
1. 拖曳&#x200B;**dotdigital form**&#x200B;區塊並選取&#x200B;**編輯**。
1. 選取其中一個測試表單，然後選取&#x200B;**內嵌**&#x200B;模式並儲存表單。
1. 儲存頁面修改。

<u>預期結果：</u>

網頁應該會成功儲存。

<u>實際結果：</u>

網頁是空的。 重新載入網頁後，變更即會套用。

## 因應措施

因應措施是使用Safari的替代瀏覽器。 此問題已排定在2021年第一季的下一個版本Adobe Commerce 2.4.2中修正。

## 相關閱讀

* [什麼是頁面產生器？](https://developer.adobe.com/commerce/frontend-core/page-builder/)於我們的開發人員檔案。
* 在開發人員檔案中[頁面產生器設定](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html?lang=zh-Hant)。
* 使用手冊中的[頁面產生器](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/page-builder/introduction)。
* [頁面產生器 — 使用手冊中的元素](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/page-builder/workspace#elements)。
