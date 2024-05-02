---
title: 雲端基礎結構上Adobe Commerce的SSL (TLS)憑證
description: 本文提供在我們的雲端基礎結構上取得您Adobe Commerce網站的SSL (TLS)憑證相關問題的快速解答。
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# 雲端基礎結構上Adobe Commerce的SSL (TLS)憑證

本文提供在我們的雲端基礎結構上取得您Adobe Commerce網站的SSL (TLS)憑證相關問題的快速解答。

## Adobe提供哪些SSL/TLS憑證？

Adobe提供網域已驗證 [讓我們加密SSL/TLS憑證](https://letsencrypt.org/) 為安全的HTTPS流量提供服務 [!DNL Fastly]. Adobe在雲端基礎結構上為每個Adobe Commerce提供一個憑證專業規劃架構、中繼和在雲端基礎結構上的Adobe Commerce入門規劃架構環境，以保護該環境中的所有網域。

## 憑證涵蓋哪些內容？

對於Pro計畫架構，測試和生產專用環境都會建立SSL憑證。 Platform-as-a-Service (PaaS)整合環境以外的每個專用環境都會擁有此憑證，以用於指派給該環境的URL。

對於入門計畫架構和PaaS整合環境，將有預設技術網域布建環境，並以個別憑證保護。

## 如何為現有憑證新增網域？

新增網域至中的服務 [!DNL Fastly]：

1. 將您在DNS中的網域指向prod.magentocloud.map.fastly.net並等候最多6小時。
1. [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 請求在Nginx設定中新增此網域（如果尚未先前完成）。

## 如何要求憑證？

案例1

如果您尚未啟動網站，您可能會收到客戶技術顧問(CTA)提供的ACME Challenge CNAME。 如果您無法立即將DNS指向您的生產URL，而且需要預先建立SSL憑證，則您只需要ACME質詢。

案例2

如果您的網站已經上線及/或您可以立即指向將用於上線網站的URL，則不需要請求ACME CNAME。 在雲端基礎結構網站上視需要將URL新增到Adobe Commerce中，並將您的DNS指向 [!DNL Fastly]，HTTP驗證將可運作，並且第一次建立您的SSL憑證或使用其他URL更新您的憑證。

## 我可以使用自己的SSL/TLS憑證嗎？

您可以提供自己的SSL/TLS憑證，而不使用 [讓我們加密憑證](https://letsencrypt.org/) 由Adobe提供。

不過，此程式需要額外的設定和維護工作。 您首先需要產生網站網域名稱（或一般名稱）的憑證申請檔(CSR)，然後將其提供給您的SSL供應商以提供SSL憑證。

取得SSL憑證後，請提交 [Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 或與您的CTA合作，將自訂託管憑證新增到您的雲端環境。

* 如果網域已不再使用，系統會自動清除這些網域，您就不需要採取任何進一步的動作。
* 如果您已有憑證，請使用SFTP （SSH檔案傳輸通訊協定）使用者端將其上傳至伺服器上無法存取Web的檔案位置，並且 [提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 讓他們知道檔案路徑。

>[!WARNING]
>
>請勿將憑證檔案直接上傳到票證，這點很重要。 否則，這些憑證將被視為已洩漏，Adobe將需要請求新的憑證。
>檔案應透過SFTP上傳至伺服器 — 請勿使用任何其他方法，例如將檔案提交至您的存放庫（這應該僅針對不包含敏感資料的不可變檔案完成）。

## 憑證的名稱

SSL憑證的名稱僅對主要URL重要，它是由第一個URL命名的主要主機名稱，且必須符合以驗證和建立。 如果您有幾個URL，則會將這些URL新增為憑證的主體替代名稱專案。 如果您在雲端基礎結構網站上有多個URL指向一個Adobe Commerce，則您將只有一個通用名稱URL憑證，該憑證接著會附加主體替代名稱，以使用SSL保護您的網站。

## 憑證的「一般名稱」欄位中會顯示哪個網域？

憑證上顯示的網域只是新增到TLS憑證的第一個網域，它會填入 **一般名稱** (**CN**)欄位，且瀏覽器會先顯示此名稱。 此 **主旨替代名稱** (**SAN**)欄位包含TLS憑證的所有DNS名稱。 無法變更或要求顯示的一般名稱。

## 我可以使用萬用字元TLS憑證嗎？

萬用字元TLS憑證只能與您的自訂憑證搭配使用，而不能與Adobe Commerce Let&#39;s Encrypt憑證搭配使用。 作為我們TLS最佳化的一部分，Adobe即將終止對萬用字元TLS憑證的支援。 我們會識別並連絡使用萬用字元憑證搭配Adobe Let&#39;s Encrypt憑證的商家，這些憑證設定於 [!DNL Fastly] 適用於Adobe Commerce的主控台。 我們要求將這些萬用字元憑證取代為確切的網域，以確保TLS涵蓋範圍。 若要取代萬用字元TLS憑證，請造訪 [網域區段](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains) 的 [!DNL Fastly] 外掛程式。 從這裡，可以新增確切的網域，並移除萬用字元。 請注意，DNS需要指向 [!DNL Fastly] 透過CDN路由的新網域。 在新增網域並更新DNS後，符合的 [讓我們加密](https://letsencrypt.org/) 將會布建憑證。 如果您未移除指向的網域 [!DNL Fastly] 使用萬用字元，Adobe會刪除共用憑證。 如果您未設定URL FQDN並在DNS中設定相同的URL FQDN，這可能會導致網站中斷。 因此，您應該確認已設定的URL在其DNS中也具有一對一比對指向 [!DNL Fastly].

## 如果我的網域不再指向Adobe Commerce，怎麼辦？

如果您的網域不再指向Adobe Commerce，請從 [!DNL Fastly]/Adobe Commerce系統。 另請參閱 [!DNL Fastly] [刪除網域](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) 以進一步瞭解。 雖然不需要將您的網域指向Adobe Commerce，但請確認是否需要頂層網域TLS憑證。 如果需要最上層網域，請更新您的DNS以指向Adobe Commerce。 如果已經指向Adobe Commerce，請更新您的CAA記錄以包含 [lets-encrypt](https://letsencrypt.org/). 如果您執行這些步驟，您將會看到LE憑證已更新為該憑證涵蓋的必要次要URL&#x200B;。

## 相關閱讀

[布建SSL/TLS憑證](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) 在我們的開發人員檔案中
