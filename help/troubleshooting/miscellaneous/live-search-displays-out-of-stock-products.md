---
title: '[!DNL Live Search]顯示無庫存的產品，無論管理員中的庫存狀態設定為何'
description: 本文提供產品清單頁面(PLP)顯示*我們找不到符合選取範圍的產品*錯誤，而搜尋彈出視窗傳回部分專案的已知問題相關資訊。
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 無論admin中的庫存狀態設定為何，[!DNL Live Search]都會顯示無庫存產品

>[!IMPORTANT]
>
>已在[[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html)中修正此問題。 若要安裝最新版本，請參閱使用手冊中的[更新 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update)。

本文提供產品清單頁面(PLP)顯示&#x200B;*找不到符合選取專案*&#x200B;的產品，而搜尋彈出視窗傳回部分專案的已知問題相關資訊。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.x

## 問題

無論Adobe Commerce管理員中的庫存狀態設定為何，[!DNL Live Search]都會顯示搜尋結果。 即使&#x200B;**[!UICONTROL Display Out-of-Stock Products]**&#x200B;設定為&#x200B;*否*，也會顯示產品。 這會導致PLP錯誤&#x200B;*找不到符合選取專案*&#x200B;的產品。

<u>要再現的步驟</u>：

1. 建立類別、新增產品。 （範例：類別= _牛仔褲_，產品1 = _藍色牛仔褲_，產品2 = _黑色牛仔褲_）
1. 讓類別中的所有產品無庫存。
1. 將&#x200B;**[!UICONTROL Display Out-of-Stock Products]**&#x200B;設為&#x200B;*否*。
1. 在店面，在搜尋欄位中輸入&#x200B;*牛仔褲*。
1. 在快顯視窗中按一下&#x200B;**[!UICONTROL View All]**。

<u>預期結果</u>：

您看到&#x200B;*我們在PLP上找不到符合選取專案*&#x200B;訊息的產品，而且搜尋快顯視窗中未顯示任何產品。

<u>實際結果</u>：

您看到&#x200B;*我們在PLP上找不到符合選取專案*&#x200B;訊息的產品，而且這兩個產品都會顯示在搜尋快顯視窗中。

## 解決方案

此問題目前尚無解決方案。 我們的[!DNL Live Search]團隊很快將提供設定，以設定[!DNL Live Search]正確顯示產品。

## 相關閱讀

在我們的使用手冊中[安裝 [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html)。
