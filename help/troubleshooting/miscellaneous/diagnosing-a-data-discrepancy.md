---
title: 診斷資料差異
description: 本文提供疑難排解Magento Business Intelligence(MBI)報表與查詢或協力廠商報表之間差異的解決方案。
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 診斷資料差異

本文提供疑難排解Magento Business Intelligence(MBI)報表與查詢或協力廠商報表之間差異的解決方案。

根據分析的複雜性，產生對應的MBI報告可能需要熟悉平台的許多不同面向。 此檢查清單和相關連結將幫助您瞭解報告背後的邏輯，讓您識別任何差異的來源。

1. 如果您的團隊的其他成員已建立報告，請從確認其分析的目標和引數開始。
1. 根據查詢、第三方報告工具或公式產生預期資料點，以與MBI報告進行比較。
1. 從Report Builder中的量度連結或造訪[系統摘要](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary)索引標籤，檢閱並確認[量度](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html)定義：
   * 資料表
   * 作業
   * 運算元欄，包括它的計算（若是衍生的） （透過[系統摘要]）
   * 時間戳記
   * 訂閱量度：開始和結束日期
   * 篩選器，包括任何套用的[篩選器集](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html)中所包含的篩選器
1. 檢閱並確認報表中的其他資料操作：
   * 公式已計算
   * [群組](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [觀點](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [時間選項](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * 針對[同類群組分析](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)：同類群組日期
   * 對於[同類群組分析](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)：同類群組觀點
1. 如果差異與最近的資料有關，請查閱連線頁面上的&#x200B;**更新詳細資料**&#x200B;區段，以確認最新的可用資料點。
1. 如果分析中使用的量度是建置在資料庫中的資料表（資料表資料列會從中刪除），請與MBI支援小組確認資料表是否正在檢查刪除的資料列，以及資料表的重新檢查頻率和[復寫方法](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html)。
1. 同樣地，如果可在新增資料列之後修改分析中使用的資料行，請確認支援人員正在[檢查這些資料行的修改](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html)，以及重新檢查的頻率。

**仍使用戳記？**&#x200B;別擔心 — 我們隨時為您提供協助。 使用[這些指示](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md)傳送要求給我們。
