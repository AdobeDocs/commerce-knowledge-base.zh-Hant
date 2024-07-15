---
title: Adobe Commerce雲端基礎結構2.3.1+升級後的Elasticsearch問題
description: 如果您使用Elasticsearch版本2.x和5.x，本文會討論在雲端基礎結構版本2.3.1+上升級至Adobe Commerce後，部署期間問題的修正。
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Adobe Commerce雲端基礎結構2.3.1+升級後的Elasticsearch問題

>[!WARNING]
>
>將在Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中移除[MySQL目錄搜尋引擎。 您必須先安裝並設定Elasticsearch主機，才能安裝2.4.0版。請參閱[安裝及設定Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)。

>[!WARNING]
>
>請注意，我們無法在未提前48個營業時間通知基礎架構團隊的情況下，將服務升級推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

如果您使用Elasticsearch版本2.x和5.x，本文會討論在雲端基礎結構版本2.3.1+上升級至Adobe Commerce後，部署期間問題的修正。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.3.1+
* Elasticsearch2.x和5.x

## 原因

在雲端基礎結構（版本2.3.1及更高版本）上升級至Adobe Commerce，且使用6.x之前的Elasticsearch版本的商家在部署時可能會遇到錯誤。 這是因為Elasticsearch版本2.x和5.x是[生命週期結束](https://www.elastic.co/support/eol)，Adobe Commerce不再支援。 Elasticsearch使用者端必須是最新的，或執行部署時可能會觸發錯誤。 若要深入瞭解，請參閱我們的開發人員檔案中的[變更Elasticsearch使用者端](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html)。

## 問題

部署時，您會看到類似下列的錯誤訊息，指出您的Elasticsearch版本不相容：基礎建設層上的&#x200B;*Elasticsearch服務版本5.2.2與您的Magento應用程式使用的elasticsearch/elasticsearch模組(6.7.0.0)目前版本不相容。* *您可以將Magento雲端基礎結構上的Elasticsearch服務升級至6.x*&#x200B;版來修正此問題。 此問題的其他症狀可能是缺少影像，以及您環境中的篩選器問題。

## 解決方案

>[!WARNING]
>
>如果您有共用環境，請確認測試與生產環境已準備好升級。

若要解決此問題，Elasticsearch使用者端模組和Elasticsearch服務必須使用最新建議版本：

1. 請依照我們的開發人員檔案中的指示[變更Elasticsearch模組](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-downgrade.html)，讓您可以擁有最新建議版本的Elasticsearch使用者端模組。
1. [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，並要求在中繼和生產環境中將Elasticsearch服務更新至6.x。 請注意，升級Elasticsearch服務可能需要一些時間才能完成。

## 相關閱讀

* 在開發人員檔案中[Adobe Commerce 2.3技術棧疊需求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements-tech.html)。
* 在開發人員檔案中[設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/project-conf-files_services-elastic.html)。
* 在開發人員檔案中[安裝並設定Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)。
* [請確定Elasticsearch已正確安裝](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)我們的支援知識庫。
