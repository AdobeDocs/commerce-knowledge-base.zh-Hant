---
title: 疑難排解雲端基礎結構上Adobe Commerce的New Relic
description: 本文提供雲端基礎結構上Adobe Commerce上New Relic的疑難排解資源。
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# 疑難排解雲端基礎結構上Adobe Commerce的New Relic

本文提供雲端基礎結構上Adobe Commerce上New Relic的疑難排解資源。

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>問題</strong></td>
<td class="wysiwyg-text-align-center"><strong>原因</strong></td>
<td class="wysiwyg-text-align-center"><strong>資源</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">存取問題</td>
</tr>
<tr>
<td>
<p><u>在New Relic中看不到專案。</u></p>
<p>您登入 <em>New Relic</em> 但看不到您應有權檢視/存取的專案。</p>
</td>
<td>
<p>在這些情況下，管理員使用者需要將您新增至專案。</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html">存取New Relic服務</a> 在我們的支援知識庫中。</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">資料問題</td>
</tr>
<tr>
<td>
<p><u>安裝後遺失資料。</u></p>
<p>使用 <a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic診斷公用程式</a> 以找出原因。 如果這樣沒有幫助，請檢視代理程式專用的解決方案。 右側欄會提供包含這些解決方案的文章連結。</p>
</td>
<td>
<p>遺失資料可能有不同的原因。 您可能需要：</p>
<ul>
<li>驗證是否已安裝代理程式。</li>
<li>驗證您的應用程式名稱和授權金鑰。</li>
<li>重新啟動您的網頁伺服器。</li>
<li>確定您的系統符合相容性需求。</li>
<li>INI設定。</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic檔案&gt; APM代理程式&gt;沒有看到資料</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic檔案&gt; New Relic瀏覽器&gt;看不到資料</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic檔案&gt; New Relic基礎結構&gt;沒有看到資料</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic檔案&gt; New Relic Mobile &gt;看不到資料</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>交易時間戳記不一致。</u> 您可能很難使用New Relic UI找到較長的交易（超過5分鐘）。 您也可以在預期的時間範圍之外找到顯示的交易。</p>
</td>
<td>
<p>New Relic UI會顯示交易結束時間，而非交易開始時間。</p>
</td>
<td>
<p>若要使用New Relic UI計算交易的開始，請檢查交易的持續時間。 從New Relic UI提供的時間戳記（交易結束）中減去持續時間金額。</p>
</td>
</tr>
<tr>
<td>
<p><u>NerdGraph GraphQL <code>curl</code> 使用特殊字元的查詢，例如 <code>|</code> 和 <code>%</code> 無法運作</u>.</p>
</td>
<td>
<p>NerdGraph中的New Relic「複製至curl」功能目前不提供處理特殊字元的方式，例如 <code>|</code> 和 <code>%</code>.</p>
</td>
<td>
<p>使用不同的API程式庫來解決特殊字元的問題。 例如，Python上Graphql API的GraphQLClient程式庫，或由Java語言呼叫執行的Apache.commons。 檢閱使用者端資料庫 <a href="https://graphql.org/code/">GraphQL</a>.</p>
</td>
</tr>
<tr>
<td>
<p><u>圖表和控制面板顯示問題。</u></p>
</td>
<td>
<p>將New Relic網域新增至允許清單或解除安裝造成問題的瀏覽器擴充功能，以解決遺漏的圖表。</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic檔案&gt;圖表遺失或不呈現</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">PHP代理程式問題</td>
</tr>
<tr>
<td>
<p><u>PHP代理程式未顯示正確的執行個體計數。</u></p>
</td>
<td>
<p>執行個體的數量會依後端處理作業和輸送量而增加。 伺服器值之間的差異可能是因為某個伺服器上執行的處理序，而非其他伺服器上執行的處理序。</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic檔案&gt;疑難排解PHP代理程式執行個體計數</a> </p>
</td>
</tr>
</tbody>
</table>
