---
title: 將非規則運算式重新導向解除安裝到Fastly而非Nginx （路由）
description: 此主題針對您在雲端基礎結構上的Adobe Commerce中將非規則運算式重新導向解除安裝到Fastly而非Nginx時可能遇到的典型重新導向效能問題提供解決方案。
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# 將非規則運算式重新導向解除安裝到Fastly而非Nginx （路由）

此主題針對您在雲端基礎結構上的Adobe Commerce中將非規則運算式重新導向解除安裝到Fastly而非Nginx時可能遇到的典型重新導向效能問題提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce （所有版本） `Master/Production/Staging`環境利用Fastly

## 問題

在雲端基礎結構上的Adobe Commerce中，無法在Nginx層執行大量非規則運算式重新導向/重新寫入，因此可能會導致效能問題。

## 原因

`.magento/routes.yaml`目錄中的`routes.yaml`檔案定義雲端基礎結構上Adobe Commerce的路由。

如果`routes.yaml`檔案的大小為32KB或更大，您應該將非Regex重新導向/重寫解除安裝至Fastly。

此Nginx層無法處理大量非Regex重新導向/重新寫入，否則會導致效能問題。

## 解決方案

解決方案是將這些非規則運算式重新導向解除安裝到Fastly。 建立一般錯誤路徑以重新導向到Fastly。

以下步驟將詳細說明如何在Fastly上而不是Nginx上放置重新導向。

1. 建立Edge字典。

   首先，您可以使用Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)中的[VCL片段來定義邊緣字典。 這將包含重新導向。

   對此有一些警告：

   * Fastly無法在字典專案上執行regex。 只有完全相符的專案。 如需這些限制的詳細資訊，請參閱[Fastly的邊緣字典限制檔案](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations)。
   * Fastly在單一字典中的限製為1000個專案。 Fastly可以擴大此限制，但這引出第三個警告。
   * 每當您更新專案並將更新的VCL部署到所有節點時，幾何載入時間會隨著擴充字典而增加 — 也就是說，2000專案的字典實際載入速度會比1000專案的字典慢3倍到4倍。 但只有在部署VCL （更新字典或變更VCL函式程式碼）時，才會發生這個問題。

     它不會影響Fastly處理請求所需的時間；只會影響Fastly推出新設定所需的時間。

     一般而言，設定變更平均需要數秒的時間，通常不超過5至10秒。 因此，字典專案增加2倍需要30秒以上才能轉出您的設定。 每增加4倍，大約需要2分鐘。 這引出了第四個警告。

   * 邊緣字典嚴格限製為10,000個專案。

   強烈建議整合您的重新導向清單。 您可以使用多個字典，但請注意，您對VCL所做的任何更新都需要幾分鐘才能實際填入Fastly。

1. 比較URL與字典。

   進行URL查詢時，會進行比較以在找到相符專案時套用自訂錯誤代碼。

   使用其他VCL程式碼片段將類似下列的專案新增至`vcl_recv`：

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   在此，我們正在檢查該URL是否存在於表格專案中。 如果出現這個錯誤，我們會呼叫內部Fastly錯誤，並將來自表格的重新導向URL傳入該錯誤。

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
>如果您想嘗試上述所有步驟，強烈建議您設定Adobe Commerce中繼環境。 如此一來，您就可以針對Fastly服務執行測試，確保一切如您預期般運作。

如果您不想執行Adobe Commerce中繼環境，但想檢視這些重新導向的外觀，您可以直接在Fastly上設定中繼帳戶。

## 相關閱讀

* [Fastly VCL參考](https://docs.fastly.com/vcl/)
* [在開發人員檔案中設定路由](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html)。
* 在開發人員檔案中[設定Fastly](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。
* 開發人員檔案中的[VCL規則運算式速查表](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet)。
