---
title: 雲端網站速度緩慢
description: 本文提供相關建議，說明如何讓雲端基礎結構網站上的Adobe Commerce在大量流量負載下表現更好，以及如何降低此負載。
exl-id: 144df36b-6305-4e57-b813-46bbb0ddedda
feature: Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# 雲端網站速度緩慢

本文提供相關建議，說明如何讓雲端基礎結構網站上的Adobe Commerce在大量流量負載下表現更好，以及如何降低此負載。

## 受影響的版本和版本

* 雲端基礎結構上的Adobe Commerce，所有版本

## 問題

<u>要再現的步驟</u>

1. 造訪您的Adobe Commerce商店。
1. 瀏覽類別頁面。
1. 新增產品至購物車。

<u>預期結果</u>

網站回應迅速，將產品新增到購物車很迅速。

<u>實際結果</u>

網站速度慢，或類別頁面快但購物車頁面慢。

## 偵錯步驟與解決方案

請依照下列步驟，找出效能緩慢的原因並加以修正。 您可以切換第一個和第二個步驟，但只有在快取設定最佳化沒有幫助時才繼續封鎖IP。

1. 檢查高流量頁面的快取命中率，並減少大量更新的資料量。
1. 檢查整體網站快取命中率，並確認一般快取/Fastly設定。
1. 識別造成高伺服器負載的Web使用者端，並封鎖IP造成高負載。

以下段落提供每個步驟的詳細資訊。

### 步驟1：檢查高流量頁面的快取命中率

修正因大量流量而陷入困境的網站的第一步，是確保能正確快取流量最大的頁面，例如商店的首頁和最上層的類別頁面。

您可以使用cURL檢閱`X-Cache` HTTP標頭來找出這些頁面的快取命中率，如Fastly檔案中的[使用cURL檢查快取](https://docs.fastly.com/guides/debugging/checking-cache#using-curl)中所述。 或者，使用您最愛網頁瀏覽器的開發人員工具列中的「網路」索引標籤，檢視相同的標題。

Fastly通常尊重來自應用程式的回應標頭；但是，如果標頭都設定為「不快取」並且頁面「過去過期」，Fastly無法快取頁面。

>[!WARNING]
>
>請注意，Fastly會變更回應標頭，因此使用cURL或網頁瀏覽器檢查主要URL時，不一定會顯示應用程式正在發出哪些標頭。 Fastly本身通常會回應沒有「快取」標題的網頁瀏覽器，但網頁應用程式本身會允許快取，而Fastly則會正確快取專案。 因此，「cache-control」和「pragma」標頭資訊在此情況下將不實用。

#### 疑難排解高流量的頁面

如果索引頁面的點選率很低，您可以減少該頁面上出現大量更新資料的量來修正此問題。

### 步驟2：檢查整體網站快取命中率

若要檢查整體快取命中率：

1. 在雲端基礎結構環境中[取得Adobe Commerce的Fastly認證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)。
1. 執行下列Linux/macOS cURL命令，以檢查網站在過去30分鐘的點選率，取代並使用您的Fastly憑證的值：

   `curl -H "Fastly-Key: " https://api.fastly.com/stats/service//field/hit_ratio?by=minute | json_pp`

   您也可以將時間範圍查詢選項從`?by=minute`變更為`?by=hour`或`?by=day`，以檢查過去一天或月份的歷史點選率。 如需有關取得Fastly快取統計資料的詳細資訊，請參閱Fastly檔案中的[查詢選項](https://docs.fastly.com/api/stats#Query)。

   `| json_pp`選項會使用`json_pp`公用程式美化列印JSON回應輸出。 如果您收到_&#39;json\_pp not found&#39;_錯誤，請安裝`json_pp`公用程式，或使用其他命令列工具進行JSON美化列印。 或者，刪除`| json_pp`引數，然後再次執行命令。 JSON回應輸出未格式化，但您可以透過JSON修飾詞執行以將其清除。

命中率超過0.90或90%表示整頁快取有效運作。

低於0.85或85%的點選率可能表示網站設定有問題，或是您可能安裝了協力廠商擴充功能，不允許快取其內容。

#### 整體快取命中率的疑難排解

1. 使用每小時和每日點選率統計資料，識別點選率何時開始下降。 如果您在將變更部署至網站的同一時間左右，點選率突然下降，請考慮復原變更，直到網站載入下降。
1. 在&#x200B;**商店** > **設定** >進階> **系統** > **整頁快取**&#x200B;底下，檢查Commerce管理員中的設定。 請確定公用內容&#x200B;**值的** TTL設定得不是太低。
1. 請確定您已[上傳VCL程式碼片段](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#upload-vcl-snippets)。
1. 如果您使用自訂VCL程式碼片段，請對其進行偵錯，以正確使用「通過」或「垂直號」動作：應小心使用，並且至少要與某種型別的條件搭配使用。 如需更多秘訣，請參閱我們的開發人員檔案中的[自訂Fastly VCL程式碼片段](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets)。

### 步驟3：找出造成伺服器負載過高的網站

您可以使用下列其中一種方法，取得存取Adobe Commerce商店的IP位址相關資訊。

* 透過SSH工作階段檢查HTTP存取記錄。
* 請聯絡Adobe Commerce支援，索取IP位址清單，造成網站負載過重。

#### 檢查HTTP存取記錄檔

若要檢視您網站的存取記錄，請從您的本機開發環境執行以下命令：

```bash
magento-cloud log access
```

使用檢視更多行

```bash
--lines
```

選項，例如：

```bash
magento-cloud log access --lines=500
```

您可以檢視此記錄並檢視大部分請求是否來自特定IP位址。 另一種方式是使用`awk` 、 `sort`和`uniq`自動計算記錄中發生頻率最高的IP位址，如下所示：

```bash
magento-cloud log access --lines 2000 | awk '{print $1}' | sort | uniq -c | sort
  -nr
```

如果

```bash
magento-cloud log
```

命令無法運作，您可以使用SSH連線到遠端伺服器，並在`/var/log/access.log`檢查記錄檔

識別造成大量伺服器負載的IP位址後，您可以從Commerce管理面板的&#x200B;**存放區** > **設定** >進階> **系統** > **全頁快取** > **快速設定** > **封鎖**&#x200B;下設定IP封鎖清單，以封鎖這些位址。

如果您由於負載過重而無法存取管理員，可以使用Fastly API來設定封鎖規則：

1. 依照[使用API](https://docs.fastly.com/guides/access-control-lists/working-with-acls-using-the-api) Fastly檔案處理ACL中的說明建立ACL。
1. 在`recv`區段中，使用下列內容建立VCL程式碼片段，並將ACL\_NAME\_GOES\_HERE取代為先前步驟中建立的ACL名稱：

   ```
   if( req.http.Fastly-Client-IP ~ ACL_NAME_GOES_HERE ) {
   error 403 "Forbidden";
   }
   ```

如需封鎖IP位址的詳細資訊，請參閱GitHub中的[Fastly Adobe Commerce模組指南](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)。
