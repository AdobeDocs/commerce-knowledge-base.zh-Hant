---
title: '將非[!DNL regex]重新導向解除安裝到 [!DNL Fastly] 而非 [!DNL Nginx] （路由）'
description: 此主題針對您在雲端基礎結構上的Adobe Commerce中將非[!DNL regex]重新導向解除安裝到 [!DNL Fastly] 而非 [!DNL Nginx] 時可能會遇到的典型重新導向效能問題，提供解決方案。
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# 將非[!DNL regex]重新導向解除安裝到[!DNL Fastly]而非[!DNL Nginx] （路由）

此主題針對您在雲端基礎結構上的Adobe Commerce中將非[!DNL regex]重新導向解除安裝到[!DNL Fastly]而非[!DNL Nginx]時可能遇到的典型重新導向效能問題，提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本） `Master/Production/Staging`環境利用[!DNL Fastly]

## 問題

在雲端基礎結構上的Adobe Commerce中，[!DNL Nginx]層無法執行大量非[!DNL regex]重新導向/重新寫入，因此可能會導致效能問題。

## 原因

`.magento/routes.yaml`目錄中的`routes.yaml`檔案定義雲端基礎結構上Adobe Commerce的路由。

如果`routes.yaml`檔案的大小為32KB或更大，您應該將非[!DNL regex]重新導向/重寫解除安裝至[!DNL Fastly]。

此[!DNL Nginx]層無法處理大量非[!DNL regex]重新導向/重新寫入，否則會產生效能問題。

## 解決方案

解決方案是將這些非[!DNL regex]重新導向解除安裝至[!DNL Fastly]。 建立一般錯誤路徑以重新導向至[!DNL Fastly]。

下列步驟將詳細說明如何在[!DNL Fastly] （而非[!DNL Nginx]）上放置重新導向。

1. 建立Edge字典。

   首先，您可以使用Adobe Commerce[&#128279;](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)中的[!DNL VCL] 代碼片段來定義邊緣字典。 這將包含重新導向。

   對此有一些警告：

   * [!DNL Fastly]無法在字典專案上執行[!DNL regex]動作。 只有完全相符的專案。 如需這些限制的詳細資訊，請參閱[[!DNL Fastly]的邊緣字典限制檔案](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations)。
   * [!DNL Fastly]在單一字典中的限製為1000個專案。 [!DNL Fastly]可以擴大此限制，但會導致第三個警告。
   * 每次更新專案並將更新[!DNL VCL]部署到所有節點時，幾何載入時間會隨著擴充字典而增加 — 也就是說，2000專案字典的載入速度實際上會比1000專案字典慢3倍至4倍。 但只有在部署[!DNL VCL] （更新字典或變更[!DNL VCL]函式程式碼）時，才會發生此問題。

     不會影響[!DNL Fastly]處理請求所需的時間，只會影響[!DNL Fastly]推出新設定所需的時間。

     一般而言，設定變更平均需要數秒的時間，通常不超過5至10秒。 因此，字典專案增加2倍需要30秒以上才能轉出您的設定。 每增加4倍，大約需要2分鐘。 這引出了第四個警告。

   * 邊緣字典嚴格限製為10,000個專案。

   強烈建議整合您的重新導向清單。 您可以使用多個字典，但請注意，您對[!DNL VCL]所做的任何更新都需要幾分鐘才能實際填入[!DNL Fastly]。

1. 比較[!DNL URL]與字典。

   當[!DNL URL]查詢發生時，這將進行比較以在找到相符專案時套用自訂錯誤代碼。

   使用另一個[!DNL VCL]程式碼片段將類似下列的專案新增到`vcl_recv`：

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   在此，我們正在檢查表格專案中是否存在[!DNL URL]。 如果是，我們會呼叫內部[!DNL Fastly]錯誤，並從資料表傳遞重新導向[!DNL URL]至該錯誤。

1. 管理重新導向。

   找到相符專案時，會採取為該`obj.status`定義的動作，在此案例中為301永久移動重新導向。

   在`vcl_error`中使用最終程式碼片段，將301個錯誤碼傳送回使用者端：

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   透過此區塊，我們正在檢查從`vcl_recv`傳入的錯誤碼是否相符，若相符，我們會將位置設定為傳入的錯誤訊息，然後將狀態碼變更為301，並將訊息變更為「已永久移動」。 此時，回應應該已準備好返回使用者端。

### 中繼服務

>[!WARNING]
>
>如果您想嘗試上述所有步驟，強烈建議您設定Adobe Commerce中繼環境。 如此一來，您可以針對[!DNL Fastly]服務執行測試，以確定所有專案皆如您預期般運作。

如果您不想執行Adobe Commerce中繼環境，但想檢視這些重新導向的外觀，您可以直接在[!DNL Fastly]上設定中繼帳戶。

## 相關閱讀

* [[!DNL Fastly VCL] 參考](https://docs.fastly.com/vcl/)
* 在開發人員檔案中[設定路由](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html)
* 在開發人員檔案中[設定 [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* 開發人員檔案中的[[!DNL VCL] 規則運算式速查表](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet)
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
