---
title: 在Adobe Commerce上使用New Relic進行效能疑難排解
description: 「本文提供使用New Relic解決Adobe Commerce雲端基礎結構效能問題的疑難排解步驟。 此外，也提供資源以取得進一步資訊。 以下是問題清單。 按一下以檢視支援知識庫中的疑難排解步驟：'
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# 在Adobe Commerce上使用New Relic進行效能疑難排解

本文提供疑難排解步驟，以使用New Relic解決Adobe Commerce的雲端基礎結構效能問題。 此外，也提供資源以取得進一步資訊。 下表包含下列問題和建議的資源：

* 低Apdex分數
* 高CPU使用量
* 高I/O作業
* 中斷

<table>
<tbody>
<tr>
<td>問題</td>
<td>疑難排解</td>
<td>資源</td>
</tr>
<tr>
<td>
<p>Apdex分數低：</p>
<p>您的New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex分數</a>可測量使用者對您網頁應用程式與服務回應時間的滿意度。</p>
</td>
<td>
<p>您登入<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt;概觀。 在「概述」頁面的右側，您會看到Apdex分數圖表。 Apdex分數為0.5或以下是值得關注的問題，值得調查：網路交易時間（伺服器要求）：</p>
<ol>
<ol>
<li>登入<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; （選取應用程式） &gt;概觀。 請確定主要圖表下拉式篩選器上的篩選條件已設為網頁交易時間。 在「交易」表格下方，尋找「應用程式伺服器時間」。 確認您是否有任何長期執行或可疑的交易。</li>
<li>請移至[監視] &gt; [交易]個別調查這些專案，並確定設定Web和最耗時<em>的篩選器。</em>
</li>
<li>然後搜尋使用資源的協力廠商模組：付款提供者、ERP等。</li>
<li>在APM的「監督」段落中：<ol>
<li>按一下「交易」。</li>
<li>向下捲動，按一下顯示所有交易表格。</li>
<li>您可以依<a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">各種引數</a>來排序交易，並跳至引起懷疑的引數。</li>
<li>複查那些具有低Apdex分數、異常高計數或高Avg時間或Dissat %的交易。</li>
<li>按一下每個個別的交易。 如果無法解決問題，<a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">請提交支援票證。</a>
</li>
<li>如果您需要進一步調查，請考慮檢查非Web交易。</li>
</ol>
</li>
</ol>
</ol>
<p>非Web交易時間（作業和背景工作）：</p>
<ol>
<ol>
<li>登入<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; （選取應用程式） &gt;概觀。 請務必在主圖表下拉式篩選器上選取非網路交易時間。 按一下「交易」表格中的個別交易。 尋找長期執行或可疑的交易。 這包括後端作業、cron作業或匯入/匯出作業，包括協力廠商。</li>
</ol>
</ol>
</td>
<td>
<p>若要深入瞭解New Relic Apdex分數，請參閱<a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic檔案&gt; APM Apdex &gt;測量使用者滿意度</a>。 您也可以在我們的支援知識庫中參考<a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Adobe Commerce的Managed警示： Apdex警告警示</a>。</p>
</td>
</tr>
<tr>
<td>
<p>高CPU使用率：</p>
<p>高CPU使用率可能表示有特別忙碌的服務，例如MySQL、Redis等。</p>
</td>
<td>
<ol>
<li>登入<a href="https://login.newrelic.com/login">New Relic</a> &gt;基礎結構&gt;程式。</li>
<li>請檢閱CPU圖表，檢視是否有任何持續或耗用時間超過100% CPU時間的處理序，並與執行個體的處理器計數進行比較。 請注意資源使用率的高峰。 不建議您終止處理序，除非它是卡住的cron。</li>
</ol>
</td>
<td>
<p>若要進一步瞭解效能測量結果，特別是CPU百分比、I/O位元組以及個別或處理序群組的記憶體使用量，請參閱<a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic檔案&gt;基礎架構UI頁面&gt;基礎架構主機頁面&gt;處理序索引標籤</a>。</p>
</td>
</tr>
<tr>
<td>
<p>高I/O作業：對於每個客戶，此數字可能是個別的，但會與平均值大不相同。</p>
</td>
<td>
<p>與先前的平均I/O作業相比，尋找不尋常的尖峰：</p>
<ol>
<li>登入<a href="https://login.newrelic.com/login">New Relic</a> &gt;基礎結構&gt;程式。</li>
<li>檢閱每秒I/O讀取位元組圖表。</li>
<li>紀錄尖峰的時間。</li>
<li>按一下APM。</li>
<li>請務必在主圖表下拉式篩選器上選取網頁交易時間。</li>
<li>設定您所記錄的尖峰時間。</li>
<li>搜尋造成高I/O作業量的異動。</li>
<li>深入研究每個交易追蹤&gt;追蹤詳細資訊，以找出可能導致問題的原因。</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>中斷：New Relic依Apdex判斷中斷情形。 您會在Apdex分數圖表中看到一條紅線，指出Apdex &lt; 0.4 （視為中斷）。</p>
</td>
<td>
<p>調查中斷可能需要幾個步驟，包括檢查Web和非Web交易、資料庫和第三方交易。 Web交易：</p>
<ol>
<li>登入<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt;概觀。 確定下拉式圖表篩選器上的篩選器已設為網頁交易時間。</li>
<li>手動縮小時間範圍。</li>
<li>按一下「交易」。 請確定篩選器已設定為網頁且最耗時。 調查執行時間最長的交易。</li>
<li>如果您需要進一步調查，請考慮檢查非Web交易。</li>
</ol>
<p>非Web交易：</p>
<ol>
<li>返回「綜覽」頁面，然後在下拉式篩選器上切換至「非Web交易」。</li>
<li>逐一檢閱頁面最下方的交易追蹤。</li>
<li>根據問題而定，您可能需要使用第三方工具（如PHP效能評測器）來尋找瓶頸。</li>
<li>如果您需要進一步調查，請考慮檢查資料庫處理作業。</li>
</ol>
<p>資料庫處理作業：</p>
<ol>
<li>在「APM」頁面上，移至「監督&gt;資料庫」。</li>
<li>依最耗時的專案排序。</li>
<li>檢閱熱門查詢。

附註： <code>更新</code> 或<code>插入</code>查詢是最耗用CPU的查詢。</li>
<li>從「排序依據」選擇器切換至「傳輸量」，並尋找導致資料庫傳輸量下拉式清單的處理程式。</li>
<li>如果您需要進一步調查，請考慮檢查協力廠商服務。</li>
</ol>
<p>協力廠商服務：</p>
<ol>
<li>在APM頁面上，前往監視&gt;外部服務。</li>
<li>從「排序依據」下拉式清單中選取最慢的平均回應時間。</li>
<li>尋找在中斷前發生的程式。</li>
</ol>
</td>
<td>
<p>若要瞭解有關調查特定效能問題的詳細資訊，請參閱<a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic檔案&gt; APM UI頁面&gt;交易頁面&gt;使用向下鑽研函式</a>。</p>
</td>
</tr>
</tbody>
</table>
