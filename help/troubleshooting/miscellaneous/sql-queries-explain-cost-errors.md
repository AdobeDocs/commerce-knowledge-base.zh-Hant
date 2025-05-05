---
title: 「SQL查詢：說明成本錯誤」
description: 本文提供執行失敗SQL查詢時EXPLAIN成本錯誤的解決方案。 PostgreSQL會使用名為[the EXPLAIN命令](https://www.postgresql.org/docs/9.5/static/using-explain.html)的程式碼來判斷SQL查詢的成本。 我們建置SQLReport Builder也是為了使用此命令，也就是說，如果成本太高（執行查詢所需的資源量超過我們的臨界值），查詢將不會執行，且會顯示EXPLAIN訊息。
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL查詢：說明成本錯誤

本文提供執行失敗SQL查詢時EXPLAIN成本錯誤的解決方案。 PostgreSQL使用名為[EXPLAIN命令](https://www.postgresql.org/docs/9.5/static/using-explain.html)的程式來判斷SQL查詢的成本。 我們建置SQLReport Builder也是為了使用此命令，也就是說，如果成本太高（執行查詢所需的資源量超過我們的臨界值），查詢將不會執行，且會顯示EXPLAIN訊息。

發生此情形有幾個原因。 以下是您可能會收到的訊息、其含義以及如何進行疑難排解。

## 無法執行查詢。 \[xxx\]的EXPLAIN成本值太高，無法執行此查詢。

如果您看到此訊息，則表示該查詢被視為太昂貴，無法執行。 針對這種情況，我們有兩個建議：一個是從您的查詢中排除任何ORDER BY條款，因為它們的作業成本很高。 第二個是遵循我們[最佳化文章](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html?lang=zh-Hant)中的秘訣，調整您的查詢。

## 無法執行查詢。 此查詢會傳回\[xxx\]列，超過我們10,000列的限制

在此情況下，可能的結果數超過SQLReport Builder的設定最大值。 有幾種方法可以減少結果數量：

* 嘗試將一些篩選器新增到您的查詢。
* 如有可能，請使用LIMIT 。 有些表格有大量的列，限制結果可讓您保持在列限制之下。

## 無法剖析EXPLAIN回應。

糟糕。 此訊息通常表示我們這邊可能出現了問題。 如果您持續收到此錯誤，請聯絡支援人員。
