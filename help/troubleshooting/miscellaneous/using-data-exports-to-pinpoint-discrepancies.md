---
title: 使用資料匯出功能來精確找出差異
description: 本文提供疑難排解MagentoBI資料中差異的解決方案。 資料匯出是將您的MagentoBI資料與來源資料進行比較的實用工具，以找出報告中的資料差異，尤其是當[資料差異診斷檢查清單](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)無法協助您找出問題時。 本文將逐步解說如何使用「資料匯出」來精確指出資料差異的實際範例。
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---

# 使用資料匯出功能來精確找出差異

本文提供疑難排解MagentoBI資料中差異的解決方案。 資料匯出是將您的MagentoBI資料與來源資料進行比較的實用工具，以找出報表中的資料差異，尤其是當 [資料差異診斷檢查清單](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) 無法協助您找出問題。 本文將逐步解說如何使用「資料匯出」來精確指出資料差異的實際範例。

舉例來說，以下列分析為例：

![](assets/Exports_Discrepancies_1.png)

2014年11月出現可疑下降。 收入$500,780.94？ 聽起來不對。 您已確認來源資料庫中有更多顯示的2014年11月收入，且您已仔細檢查 **收入** 此報表中使用的量度已正確定義。 MagentoBI資料倉儲中的資料似乎不完整，可以使用「資料匯出」來確認。

## 匯出資料 {#export}

若要開始，請按一下圖表右上角的齒輪，然後按下拉式選單中的「原始匯出」選項。 這可提供圖表背後資料的原始匯出。

![](assets/Export_Discrepancies_5.gif)

在「原始資料匯出」選單中，您可以選取要匯出的表格以及要包含在匯出中的欄。 篩選條件也可套用至結果集。

在我們的範例中， **收入** 用於此報告上的量度使用 **order\_total** 上定義的欄位 **訂購** 表格，使用 **日期** 做為時間戳記。 在我們的匯出中，我們想要包含所有 **order\_id** 2014年11月的值及其 **order\_total** . 此 **收入** 量度不使用任何篩選器，但我們將為匯出新增篩選器，以將結果集限製為僅2014年11月。

以下是此範例中「原始資料匯出」功能表的外觀：

![](assets/Exports_Discrepancies_2.png)

按一下「匯出資料」開始匯出。 將會顯示一個視窗，其中包含匯出的詳細資訊，包括狀態。 準備匯出作業需要幾分鐘的時間，現在正是在2014年11月進行類似來源資料擷取的好時機，包括 **日期，order\_id** ，以及 **order\_total** . 我們將在Excel中開啟此檔案，並保留下來，因為稍後我們將重新檢視它。

當「原始資料匯出」視窗中出現「下載」按鈕時，按一下該按鈕即可下載包含CSV檔案的zip檔案。

![](assets/Export_Discrepancies_6.png)

此時，我們需要將所有資料放進一個工作表來找出問題。 我們會將CSV檔案(從MagentoBI匯出)匯入包含來源資料的另一張Excel檔案中。

## 找出問題 {#pinpoint}

現在，所有資料都在一個位置，我們可以尋找差異的來源。 比較每個工作表中的列數有助於我們找出問題。 讓我們更詳細地瞭解一下每種情況。

### 兩個頁面包含相同數量的列

如果兩個系統有相同的列數和 **收入** 量度不符合來源資料，則 **order\_total** 必須不在某處。 可能是 **order\_total** 欄位已在您的來源資料庫中更新，且MagentoBI未擷取這些變更。

若要確認此專案，請檢視 **order\_total** 正在重新檢查欄。 前往「Data Warehouse管理員」，然後按一下「訂單」表格。 您將會看到 [重新檢查頻率](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) 列於「變更？」中 欄。 此 **order\_total** 欄位應該設定為依預期變更的頻率重新檢查；如果沒有，請繼續並將其設定為您所需的重新檢查頻率。

### ![](assets/Export_Discrepancies_4.gif)

如果重新檢查頻率已正確設定，則表示有其他錯誤。 請參閱 [連絡支援區段](#support) 於本文結尾以瞭解後續步驟。

## 來源資料庫的資料列數超過MagentoBI {#morerows}

如果來源資料庫的列數超過MagentoBI，而且間隔大於您預期在更新週期期間會傳入的訂單數，則可能存在連線問題。 這表示MagentoBI無法從來源資料庫提取新資料，原因有很多。

導覽至「連線」頁面，並檢視包含訂單表格的資料來源狀態：

1. **如果狀態為「重新驗證」** ，連線未使用正確的認證。 按一下連線，輸入正確的認證，然後再試一次。
1. **如果狀態為「失敗」** ，伺服器端的連線可能未正確設定。 連線失敗通常是因為不正確的主機名稱或目標伺服器不接受指定連線埠上的連線。按一下連線，然後再次檢查主機名稱的拼字，以及是否輸入正確的連線埠。 在伺服器端，請確定連線埠可以接受連線，而且您的防火牆已允許Magento的BI IP位址(54.88.76.97/32)。 **如果連線持續失敗** ，請參閱 [連絡支援區段](#support) 於本文結尾以瞭解後續步驟。
1. **如果狀態為「成功」** ，連線就不會有問題，RJ支援需要介入。 請參閱 [連絡支援區段](#support) 於本文結尾以瞭解後續步驟。

## 來源資料庫的資料列數少於MagentoBI {#lessrows}

如果來源資料庫的資料列數少於MagentoBI，則資料列可能會從來源資料庫刪除，而MagentoBI無法擷取這些刪除專案。 ** [刪除資料](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) 可能會導致不一致、更新時間延長，以及一系列後勤問題**，因此我們強烈建議您不要刪除資料，除非確實有必要。

但是，如果從表格中刪除列，請檢視主索引鍵上的重新檢查頻率。 重新核取主索引鍵表示將檢查表格中是否有已刪除的列。

在「Data Warehouse管理員」中，主索引鍵欄會標示索引鍵符號。 在我們的範例中，主索引鍵是 **order\_id** 欄：

![](assets/Export_Discrepancies_3.png)

如果主索引鍵已設定為重新核取，或從未從此表格中刪除資料列，則您需要RJ支援才能找出問題。 如需後續步驟，請參閱以下章節。

## 連絡支援人員 {#support}

如果您無法查明問題的來源，則需要在RJ支援中執行回圈。 送出票證前，請遵循下列步驟：

* **如果來源資料庫和MagentoBI的列數相同** 且重新檢查頻率已正確設定，請在試算表中執行VLOOKUP **以找出哪些order\_id值在MagentoBI與您的來源資料庫之間有不同的order\_total值。** 在提交票證時包含這些值。
* **如果來源資料庫的ROWS多於MagentoBI** 連線顯示為「成功」或繼續失敗，我們需要知道連線的名稱和您看到的錯誤訊息（如果有的話）。
* **如果來源資料庫比MagentoBI的資料列少，** 不會從表格中刪除列，且重新檢查頻率已正確設定，請在試算表中執行VLOOKUP **以尋找MagentoBI中的order\_id值** 但不會在來源資料庫中。 在提交票證時包含這些值。

## 相關

* [資料差異診斷檢查清單](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [提交資料差異票證](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
