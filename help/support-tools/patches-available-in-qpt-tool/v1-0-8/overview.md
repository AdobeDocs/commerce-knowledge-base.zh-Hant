---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.0.8中可用修補程式所修正問題的詳細說明。
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8概覽

此小節提供[!DNL Quality Patches Tool] (QPT) v1.0.8中可用修補程式所修正問題的詳細說明。

QPT v1.0.8包含下列修補程式：

1. **MDVA-28357**：以自訂分析器取代標準分析器，並針對[!DNL ElasticSearch]索引中的SKU欄位使用關鍵字Tokenizer，讓萬用字元搜尋查詢可搭配包含連字型大小(「 — 」)的SKU運作。
1. **MDVA-29954**：修正&#x200B;*新公司註冊要求*&#x200B;與&#x200B;*您已連結至公司*&#x200B;電子郵件傳送錯誤地址的問題。
1. **MDVA-30112**：修正若訂購數量超過&#x200B;*bunch-size*&#x200B;值的問題，Adobe Commerce會將狀態為&#x200B;*擱置中*&#x200B;的訂購視為不一致。
1. **MDVA-30963**：修正產品篩選結果設為僅包含為Admin中的&#x200B;*所有存放區檢視*&#x200B;範圍指定的值，包含已在存放區檢視層級上覆寫值的產品的問題。
1. **MDVA-31150**：修正當商業發票以Rest API呼叫過帳且訂單部份由商店信用卡與禮品卡帳戶付款時，GETInvoice Rest API呼叫未傳回商店信用卡與禮品卡餘額的問題。
1. **MDVA-31242**：修正[!UICONTROL Credit Memo]格線中顯示錯誤貨幣符號的問題。
1. **MDVA-31295**：修正部分訂單完成且專案徵稅時未計算獎勵點數的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
