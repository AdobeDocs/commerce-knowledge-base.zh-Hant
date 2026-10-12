---
title: 顯示Adobe Commerce錯誤報告編號而非Fastly 503錯誤
description: 依預設，Fastly會隱藏**503服務無法使用**錯誤背後的所有Adobe Commerce錯誤。 若要顯示Adobe Commerce錯誤記錄報告編號（以便能夠在記錄中找到它並檢視錯誤詳細資料），請使用以下步驟開啟省略Fastly的網站：
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# 顯示Adobe Commerce錯誤報告編號而非Fastly 503錯誤

依預設，Fastly會隱藏&#x200B;**503服務無法使用**&#x200B;錯誤背後的所有Adobe Commerce錯誤。 若要顯示Adobe Commerce錯誤記錄報告編號（以便能夠在記錄中找到它並檢視錯誤詳細資料），請使用以下步驟開啟省略Fastly的網站：

1. 將應用程式的網域和IP位址新增至本機電腦上的主機檔案。
1. 清除瀏覽器快取和Cookie （或切換到無痕模式）。
1. 再次開啟商店網站以檢視Adobe Commerce錯誤。

檢視真實的Adobe Commerce錯誤和錯誤報告編號後，您可以按照以下步驟在錯誤報告檔案中獲取詳情：

1. ssh連線至受影響的環境。 在開發人員檔案中，請參閱[SSH至環境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)。
1. 找到`./var/report/{error_number}`檔案。

## 將應用程式網域和IP位址新增至hosts檔案：詳細步驟

1. 在本機電腦的命令列執行`nslookup`命令，檢查存放區的伺服器IP：
   * 專業架構使用者（測試和生產環境）：

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * 入門架構使用者（所有環境）；專業架構使用者（整合環境）：

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. 使用以下格式，將商店網域和應用程式伺服器IP新增至本機電腦的主機檔案：

```
{server_IP} {store_domain}
```
