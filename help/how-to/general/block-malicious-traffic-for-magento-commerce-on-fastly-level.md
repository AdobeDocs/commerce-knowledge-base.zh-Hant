---
title: 在Fastly層級封鎖Adobe Commerce的惡意流量
description: 本文提供當您懷疑雲端基礎結構存放區上的Adobe Commerce遭到DDoS攻擊時，封鎖惡意流量可採取的步驟。
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# 在Fastly層級封鎖Adobe Commerce的惡意流量

本文提供當您懷疑雲端基礎結構存放區上的Adobe Commerce遭到DDoS攻擊時，封鎖惡意流量可採取的步驟。

## 受影響的產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.3.x

在本文中，我們假設您已擁有惡意IP及/或其國家/地區和使用者代理。 雲端基礎結構上的Adobe Commerce使用者通常可以從Adobe Commerce支援取得此資訊。 以下小節提供根據此資訊封鎖流量的步驟。 所有變更都應在生產環境中完成。

## 存取管理面板

如果您的網站被DDoS超載，您可能無法登入您的Commerce管理員（並執行本文中進一步說明的所有步驟）。

若要存取Admin，請依照[啟用或停用維護模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)並將您的IP位址列入白名單中的說明，將您的網站置於維護模式。 完成後停用維護模式。

## 依IP封鎖流量

對於雲端基礎結構存放區上的Adobe Commerce而言，按特定IP位址和子網路封鎖流量的最有效方式是在Commerce管理員中新增Fastly的ACL。 以下是包含更多詳細指示連結的步驟：

1. 在Commerce管理員中，瀏覽至&#x200B;**商店** > **設定** > **進階** > **系統** > **全頁快取** > **Fastly設定**。
1. [使用您要封鎖的IP位址或子網路清單，建立新的ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md)。
1. 將其新增到ACL清單並封鎖，如Adobe Commerce的Fastly\_Cdn模組的[封鎖](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)指南中所述。

## 依國家/地區封鎖流量

對於雲端基礎結構存放區上的Adobe Commerce而言，按國家/地區封鎖流量的最有效方式是在Commerce管理員中新增Fastly的ACL。

1. 在Commerce管理員中，瀏覽至&#x200B;**商店** > **設定** > **進階** > **系統** > **全頁快取** > **Fastly設定**。
1. 選取國家/地區並使用ACL設定封鎖，如用於Adobe Commerce的Fastly\_Cdn模組的[封鎖](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md)指南中所述。

## 依使用者代理程式封鎖流量

若要根據使用者代理建立封鎖，您需要將自訂VCL程式碼片段新增到Fastly設定。 若要這麼做，請執行下列步驟：

1. 在Commerce管理員中，瀏覽至&#x200B;**商店** > **設定** > **進階** > **系統** > **全頁快取**。
1. 然後&#x200B;**Fastly組態** > **自訂VCL程式碼片段**。
1. 依照Fastly\_Cdn模組的[自訂VCL程式碼片段](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md)指南中的說明，建立新的自訂程式碼片段。 您可以使用以下程式碼範例作為範例。 此範例不允許`AhrefsBot`和`SemrushBot`使用者代理程式的流量。

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## 速率限制（實驗性Fastly功能）

雲端基礎結構上的Adobe Commerce實驗性Fastly功能可讓您指定特定路徑和編目程式的速率限制。 如需詳細資訊，請參考[Fastly模組檔案](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md)。

功能必須先在測試環境中經過全面測試，才能用於生產環境，因為這樣可能會封鎖合法的流量。

## 建議：請考慮更新robots.txt

更新您的`robots.txt`檔案有助於防止某些搜尋引擎、編目程式和機器人編目特定頁面。 例如，搜尋結果頁面、結帳、客戶資訊等頁面不應進行編目。 避免機器人編目這些頁面，有助於減少這些機器人產生的請求數量。

使用`robots.txt`時，有兩個重要的考量事項：

* 機器人可以忽略您的`robots.txt`。 尤其是惡意程式碼自動機制，它會掃描網頁以找出安全漏洞，而垃圾郵件傳送者使用的電子郵件地址收集器則不會受到任何注意。
* `robots.txt`檔案是公開可用的檔案。 任何人都可以看到您不希望機器人使用的伺服器區段。

基礎資訊和預設Adobe Commerce `robots.txt`設定可在開發人員檔案的[搜尋引擎機器人](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots)文章中找到。

如需`robots.txt`的一般資訊和建議，請參閱：

* [由Google支援建立robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt)檔案
* [關於/robots.txt](https://www.robotstxt.org/robotstxt.html) by robotstxt.org

請與您的開發人員和/或SEO專家合作，決定您要允許哪些使用者代理，或您想禁止哪些使用者代理。

## 相關閱讀

* [雲端上Adobe Commerce的產品特定授權條款](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* 在Commerce on Cloud指南中[封鎖要求的自訂VCL](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
