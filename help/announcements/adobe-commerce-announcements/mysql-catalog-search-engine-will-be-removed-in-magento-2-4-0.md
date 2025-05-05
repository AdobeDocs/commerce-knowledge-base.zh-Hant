---
title: Adobe Commerce 2.4.0中將移除MySQL目錄搜尋引擎
description: Adobe Commerce內部部署、Adobe Commerce on cloud infrastructure和Magento Open Source 2.4.0將在未來幾個月發行。 對於Adobe Commerce內部部署和Magento Open Source版本2.4.0，Elasticsearch6.x或7.x將是必要元件，並且MySQL搜尋引擎將被移除。 在雲端基礎結構上的Adobe Commerce中，已需要Elasticsearch。
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Adobe Commerce 2.4.0中將移除MySQL目錄搜尋引擎

Adobe Commerce內部部署、Adobe Commerce on cloud infrastructure和Magento Open Source 2.4.0將在未來幾個月發行。 對於Adobe Commerce內部部署和Magento Open Source版本2.4.0，Elasticsearch6.x或7.x將是必要元件，並且MySQL搜尋引擎將被移除。 在雲端基礎結構上的Adobe Commerce中，已需要Elasticsearch。

>[!WARNING]
>
>嘗試升級之前若未安裝/設定Elasticsearch6/7，可能會導致Adobe Commerce發生嚴重問題。 請注意，若未事先通知我們的基礎建設團隊48個工作時間，系統無法將雲端基礎結構上Adobe Commerce的服務升級推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

移除MySQL搜尋引擎的原因是Elasticsearch提供優異的搜尋功能以及目錄效能最佳化。

## 受影響的產品和版本：

* Adobe Commerce內部部署v2.4.0
* Magento Open Sourcev2.4.0

## 升級：

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>搜尋引擎</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>動作</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">您必須安裝Elasticsearch。 請參閱我們的開發人員檔案中的<a href="https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search">安裝及設定Elasticsearch</a>。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch（未列出任何版本）</td>
<td style="width: 478.2px;">您使用Elasticsearch2且必須更新為Elasticsearch7 （偏好設定）或6。 如需詳細資訊，請參閱開發人員檔案中的<a href="https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">升級Elasticsearch</a>和<a href="https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/configure-search-engine">設定Commerce以使用Elasticsearch</a>。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH5</td>
<td style="width: 478.2px;">Elasticsearch5的<a href="https://www.elastic.co/support/eol">生命週期已結束</a>，Adobe Commerce 2.4.0已將其淘汰。更新至Elasticsearch7 （偏好設定）或6。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch6或7</td>
<td style="width: 478.2px;">升級到Adobe Commerce 2.4.0之前，您不需要執行任何其他步驟。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">協力廠商擴充功能</td>
<td style="width: 478.2px;">您不需要安裝Elasticsearch。 Adobe Commerce建議您連絡搜尋引擎廠商，判斷擴充功能是否與Adobe Commerce 2.4.0完全相容。</td>
</tr>
</tbody>
</table>

## 安裝：

發行Adobe Commerce內部部署和Magento Open Source2.4.0時，Elasticsearch將是必要元件，因此在安裝2.4.0版之前，您必須先安裝並設定Elasticsearch主機。請參閱我們的開發人員檔案中的[安裝並設定Elasticsearch](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/search/overview-search)。

依預設，Adobe Commerce搜尋將使用Elasticsearch7作為搜尋引擎，並嘗試連線至localhost：9200的伺服器。 也支援Elasticsearch6.x。 如果組態不符合預設值，您可以使用傳遞給`setup:install`的引數來設定這些設定，就像設定資料庫連線一樣。

例如， `setup:install --elasticsearch-host=es.mystore.com`

在安裝期間，將會檢查Elasticsearch連線，如果Adobe Commerce無法連線到Elasticsearch主機，安裝將會失敗。 如果發生這種狀況，請檢查您的Elasticsearch是否正常運作，以及您是否已提供正確的連線引數。
