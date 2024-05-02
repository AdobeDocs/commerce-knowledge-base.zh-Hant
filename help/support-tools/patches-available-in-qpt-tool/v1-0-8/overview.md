---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.8呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.8。
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8概覽

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.0.8。

QPT v1.0.8包含下列修補程式：

1. **MDVA-28357**：以自訂分析器取代標準分析器，替換為中SKU欄位的關鍵字代碼器 [!DNL ElasticSearch] 索引，讓萬用字元搜尋查詢可搭配包含連字型大小(「 — 」)的SKU運作。
1. **MDVA-29954**：修正的問題： *新的公司註冊要求* 和 *您已連結至公司* 電子郵件是從錯誤的地址傳送的。
1. **MDVA-30112**：修正訂購數量超過 *bunch-size* 值，Adobe Commerce會考量以下訂單： *擱置中* 狀態為不一致。
1. **MDVA-30963**：修正產品篩選結果設為僅包含指定值的問題 *所有商店檢視* 在「管理員」中的範圍，包括在存放區檢視層級上覆寫值的產品。
1. **MDVA-31150**：修正GETInvoice Rest API呼叫未傳回商店信用卡與禮品卡餘額的問題，發票是以Rest API呼叫過帳且訂單部份由商店信用卡與禮品卡帳戶支付。
1. **MDVA-31242**：修正中顯示錯誤貨幣符號的問題 [!UICONTROL Credit Memo] 格線。
1. **MDVA-31295**：修正部分訂單完成且專案納稅後未計算獎勵點數的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
