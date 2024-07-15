---
title: 如果上線網站使用相同的網域，請在生產上進行Fastly測試
description: 如果您的生產網域(「example.com」)上有一個上線網站在運作，並且您需要在雲端基礎結構啟用Fastly CDN的生產環境上測試Adobe Commerce的新存放區，我們建議使用子網域（例如「prod.example.com」），而之前已將它新增到Fastly，以用於任何啟動前測試活動。 本文會討論詳細資訊，並提供相關Adobe Commerce檔案資源的實用連結。
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# 如果上線網站使用相同的網域，請在生產上進行Fastly測試

如果您的生產網域(`example.com`)上有一個上線網站在執行，而且您需要在雲端基礎結構啟用Fastly CDN的生產環境中測試Adobe Commerce上的新存放區，我們建議使用子網域（例如`prod.example.com`），而之前已將其新增到Fastly中，以用於任何啟動前測試活動。 本文會討論詳細資訊，並提供相關Adobe Commerce檔案資源的實用連結。

## 問題

您目前使用`example.com`生產網域的存放區已上線且運作中。 不過，您需要測試新商店、在雲端基礎結構上使用Adobe Commerce建置並部署至生產環境，同時啟用Fastly全頁快取服務。

問題是雲端基礎結構專案上Adobe Commerce的生產環境使用相同的即時網域(`example.com`)，而且您無法將新網站切換至此網域，同時讓目前的即時商店在相同的網域上執行。

### 為何要在生產環境中使用Fastly進行測試？

理論上，您可以跳過使用Fastly CDN，並在未啟用全頁快取的生產環境上的雲端基礎結構存放區上測試您的Adobe Commerce。

不過，啟用全頁快取後，商店的執行方式會不同；如果您在啟動前未透過CDN測試網站，就永遠無法得知網站的真實即時效能。 在啟用Fastly CDN的情況下在生產環境中測試您的商店是Adobe Commerce的官方建議。

## 解決方案：使用生產子網域

在生產環境的雲端基礎結構存放區中，針對您的新Adobe Commerce使用第一層子網域(`prod.example.com`)，同時將目前的即時網站保留在基本網域(`example.com`)上。

在雲端基礎結構專案上規劃Adobe Commerce時，您可以指定這樣的生產子網域，並要求雲端基礎結構團隊將子網域指向Fastly服務。

請依照下列步驟，在雲端基礎結構專案上處理Adobe Commerce中的子網域：

* [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求將子網域新增到Fastly服務/Nginx設定(適用於雲端基礎結構上的Adobe Commerce Pro計畫架構)。
* 在您的一側設定對應的DNS設定。

執行子網域設定的步驟後，您也必須採取這些步驟來驗證SSL憑證的生產網域：

* 上傳DNS TXT記錄以進行生產網域的SSL驗證。
* [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求驗證SSL憑證的生產網域。

使用子網域可讓您日後對商店執行「軟啟動」，因為此啟動只需要更新對應的DNS設定。

## 相關檔案

在我們的支援知識庫中：

* [在測試和生產環境中設定Fastly DNS設定](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [在雲端上設定Fastly以開始計畫](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* 在雲端基礎結構的Adobe Commerce上啟動[可能的封鎖程式](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

在我們的開發人員檔案中：

* [Fastly總覽](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [上線檢查清單： Fastly的DNS設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
