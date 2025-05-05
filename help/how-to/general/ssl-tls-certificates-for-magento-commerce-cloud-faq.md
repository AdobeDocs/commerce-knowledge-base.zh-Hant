---
title: 雲端基礎結構上Adobe Commerce的SSL (TLS)憑證
description: 本文提供在我們的雲端基礎結構上取得您Adobe Commerce網站的SSL (TLS)憑證相關問題的快速解答。
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 7694e6cb739d73a28c902e95d324b1317f4daaf6
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# 雲端基礎結構上Adobe Commerce的SSL (TLS)憑證

本文提供在我們的雲端基礎結構上取得您Adobe Commerce網站的SSL (TLS)憑證相關問題的快速解答。

## Adobe提供哪些SSL/TLS憑證？

Adobe提供網域驗證的[讓我們加密SSL/TLS憑證](https://letsencrypt.org/)，以提供來自[!DNL Fastly]的安全HTTPS流量。 Adobe為雲端基礎結構上的每個Adobe Commerce提供一個憑證專業規劃架構、中繼和Adobe Commerce雲端基礎結構入門規劃架構環境，以保護該環境中的所有網域。

## 憑證涵蓋哪些內容？

對於Pro計畫架構，測試和生產專用環境都會建立SSL憑證。 Platform-as-a-Service (PaaS)整合環境以外的每個專用環境都會擁有此憑證，以用於指派給該環境的URL。

對於入門計畫架構和PaaS整合環境，將有預設技術網域布建環境，並以個別憑證保護。

## 如何為現有憑證新增網域？

若要在[!DNL Fastly]中將網域新增至服務：

1. 將您在DNS中的網域指向prod.magentocloud.map.fastly.net並等候最多6小時。
1. [送出支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求在Nginx設定中新增此網域（如果先前未完成）。

## 如何要求憑證？

案例1

如果您尚未啟動網站，您可能會收到客戶技術顧問(CTA)提供的ACME挑戰CNAME。 如果您無法立即將DNS指向您的生產URL，而且需要預先建立SSL憑證，則您只需要ACME質詢。

案例2

如果您的網站已經上線及/或您可以立即指向將用於上線網站的URL，則不需要請求ACME CNAME。 一旦您在雲端基礎結構網站上視需要將URL新增到您的Adobe Commerce並將您的DNS指向[!DNL Fastly]後，HTTP驗證將可運作，並且第一次建立您的SSL憑證或使用其他URL更新您的憑證。

## 我可以使用自己的SSL/TLS憑證嗎？

您可以提供您自己的SSL/TLS憑證，而不使用Adobe提供的[Let&#39;s Encrypt憑證](https://letsencrypt.org/)。

不過，此程式需要額外的設定和維護工作。 您首先需要產生網站網域名稱（或一般名稱）的憑證申請檔(CSR)，然後將其提供給您的SSL供應商以提供SSL憑證。

取得SSL憑證後，請提交[Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，或搭配您的CTA將自訂裝載的憑證新增至您的雲端環境。

* 如果網域已不再使用，系統會自動清除這些網域，您就不需要採取任何進一步的動作。
* 如果您已經擁有憑證，請使用SFTP （SSH檔案傳輸通訊協定）使用者端將其上傳到伺服器上無法存取Web的檔案位置，並[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，讓他們知道檔案路徑。

>[!WARNING]
>
>請勿將憑證檔案直接上傳到票證，這點很重要。 否則，這些憑證將被視為已洩漏，Adobe將需要請求新的憑證。
>檔案應透過SFTP上傳至伺服器至您選擇的資料夾，例如`var/ssl`、`/tmp/ssl`等。  — 請勿使用任何其他方法，例如將檔案提交至您的存放庫（只應針對不含敏感資料的不可變檔案進行）。

## 憑證的名稱

SSL憑證的名稱僅對主要URL重要，它是由第一個URL命名的主要主機名稱，且必須符合以驗證和建立。 如果您有幾個URL，則會將這些URL新增為憑證的主體替代名稱專案。 如果您在雲端基礎結構網站上有多個URL指向一個Adobe Commerce，則您將只有一個通用名稱URL憑證，該憑證接著會附加主體替代名稱，以使用SSL保護您的網站。

## 憑證的「一般名稱」欄位中會顯示哪個網域？

憑證上顯示的網域只是新增到TLS憑證的第一個網域，它會填入&#x200B;**一般名稱** (**CN**)欄位，而瀏覽器會先顯示此名稱。 **主體替代名稱** (**SAN**)欄位包含TLS憑證的所有DNS名稱。 無法變更或要求顯示的一般名稱。

## 我可以使用萬用字元TLS憑證嗎？

萬用字元TLS憑證只能與您的自訂憑證搭配使用，而不能與Adobe Commerce Let&#39;s Encrypt憑證搭配使用。 作為TLS最佳化的一部分，Adobe將終止支援萬用字元TLS憑證。 我們正在識別並連絡使用萬用字元憑證搭配Adobe的Let&#39;s Encrypt憑證，並在Adobe Commerce的[!DNL Fastly]主控台中設定的商家。 我們要求將這些萬用字元憑證取代為確切的網域，以確保TLS涵蓋範圍。 若要取代萬用字元TLS憑證，請造訪[!DNL Fastly]外掛程式的[網域區段](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains)。 從這裡，可以新增確切的網域，並移除萬用字元。 請注意，DNS必須指向[!DNL Fastly]，這些新網域才能透過CDN路由。 新增網域並更新DNS之後，將會布建相符的[Let&#39;s Encrypt](https://letsencrypt.org/)憑證。 如果您未使用萬用字元移除指向[!DNL Fastly]的網域，Adobe將會刪除共用憑證。 如果您未設定URL FQDN並在DNS中設定相同的URL FQDN，這可能會導致網站中斷。 因此，您應該確認設定的URL在其DNS中也有指向[!DNL Fastly]的一對一相符專案。

## 如果我的網域不再指向Adobe Commerce，怎麼辦？

如果您的網域不再指向Adobe Commerce，請從[!DNL Fastly]/Adobe Commerce系統中將其移除。 請參閱[!DNL Fastly] [刪除網域](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain)以瞭解更多資訊。 雖然不需要將您的網域指向Adobe Commerce，但請確認是否需要頂層網域TLS憑證。 如果需要最上層網域，請更新您的DNS以指向Adobe Commerce。 如果它已經指向Adobe Commerce，請更新您的CAA記錄以包含[lets-encrypt](https://letsencrypt.org/)。 如果您執行這些步驟，您將會看到LE憑證已更新為該憑證涵蓋的必要次要URL&#x200B;。

## 相關閱讀

在開發人員檔案中[布建SSL/TLS憑證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)
