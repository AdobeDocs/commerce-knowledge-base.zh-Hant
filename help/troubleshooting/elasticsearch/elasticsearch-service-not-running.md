---
title: Elasticsearch服務未執行
description: 本文提供當Elasticsearch(ES)服務未執行（通常是當機結果）時可能遇到的錯誤解決方案。 症狀可能包括使用curl執行健康情況檢查時的錯誤、使用命令列重新索引、例外狀況和PHP錯誤，以及產品頁面上的錯誤。 此表格會列出錯誤，以及嘗試解決這些錯誤的資源連結。 一個症狀可能有多種不同的原因。
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch服務未執行

本文提供當Elasticsearch(ES)服務未執行（通常是當機結果）時可能遇到的錯誤解決方案。 症狀可能包括使用curl執行健康情況檢查時的錯誤、使用命令列重新索引、例外狀況和PHP錯誤，以及產品頁面上的錯誤。 此表格會列出錯誤，以及嘗試解決這些錯誤的資源連結。 一個症狀可能有多種不同的原因。

## Elasticsearch版本與Adobe Commerce的相容性

* 雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce：

   * v2.2.3+支援ES 5.x
   * v2.2.8+和v2.3.1+支援ES 6.x
   * 不建議使用ES v2.x和v5.x，因為[生命週期結束](https://www.elastic.co/support/eol)。 不過，如果您有Adobe Commerce v2.3.1，並且想要使用ES 2.x或ES 5.x，您必須[變更Elasticsearchphp Client](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search)。

* Magento Open Source v2.3.0+支援ES 5.x和6.x （但建議使用6.x）。

<table>
<tr>
<th>ES服務未執行時的症狀</th>
<th>詳細資料</th>
<th>資源</th>
</tr>
<tr>
<td rowspan="3">例外狀況錯誤</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
已設定<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html?lang=zh-Hant">Elasticsearch5，但搜尋頁面沒有載入我們的支援知識庫中的「Fielddata已停用……」錯誤</a>。
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
未刪除Elasticsuite索引。  請參閱我們的支援知識庫中的<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=zh-Hant">ElasticSuite追蹤索引導致Elasticsearch</a>發生問題。
 </td>
</tr>
<tr>
<td>PHP錯誤</td>
<td>
<i>在您的叢集中找不到連線的節點"，"1"："#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>磁碟空間不足的資源：<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">解決Linux與Unix系統硬碟問題的8個秘訣，例如磁碟已滿或無法寫入磁碟</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault： df表示磁碟已滿，但並未滿</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com：追蹤Linux上磁碟空間的去向？</a></li>
<li>記錄檔的定期封存不足。 請參閱我們的開發人員檔案中的<a href="https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/action-logs/action-log-archive">設定記錄封存</a>。</li>
<li>檔案系統目錄未最佳化。 請參閱我們的開發人員檔案中的<a href="https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">檔案最佳化</a>。</li>
<li>如果上述檔案中的解決方案無法解決問題，請考慮聯絡您的Adobe客戶團隊以請求額外的儲存空間。</li>
</ul>
</li>
<li>如果您的磁碟尚未用完儲存空間，但仍在左欄收到錯誤訊息，請<a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">提交支援票證</a>。</li>
</ul>
<ul>
<li>請參閱我們的支援知識庫中的<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=zh-Hant">ElasticSuite追蹤索引導致Elasticsearch</a>發生問題。
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> 錯誤</td>
<td>執行<code>curl</code>命令以檢查Elasticsearch健康狀態： <code>curl -m1 localhost:9200/_cluster/health?pretty</code>（或<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>起始帳戶）會產生此錯誤： <i>錯誤： curl： (7)無法連線到localhost連線埠9200：連線被拒</i> </td>
</tr>
<tr>
<td>命令列錯誤</td>
<td>執行<code>$ bin/magento indexer:reindex catalogsearch_fulltext</code>會產生此錯誤<i>目錄搜尋索引子處理序未知錯誤：
        在您的叢集</i>中找不到連線節點
</td>
</tr>
<tr>
<td>產品頁面上的錯誤
</td>
<td><i>處理您的請求時發生錯誤。
      基於安全理由，例外列印預設為停用</code></i>
</tr>
</table>
