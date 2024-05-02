---
title: '由Fastly提供支援的Web應用程式防火牆(WAF)：常見問題集'
description: Web應用程式防火牆(WAF)會根據一組安全性規則來篩選流量，以防止惡意流量進入網站和網路。 觸發任何規則的流量會先遭到封鎖，然後才能損害您的網站或網路。
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# 由Fastly提供支援的Web應用程式防火牆(WAF)：常見問題集

## Adobe Commerce的受管理雲端WAF （由Fastly提供技術支援）如何運作？

Web應用程式防火牆(WAF)防止 [惡意流量](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) 根據一組安全性規則篩選流量，以阻止進入網站和網路。 觸發任何規則的流量會先遭到封鎖，然後才能損害您的網站或網路。

Adobe Commerce的雲端WAF提供WAF原則及規則集，專為保護Adobe Commerce Web應用程式免受各種攻擊而設計。

WAF會檢查網頁和管理流量，以識別任何可疑活動。 它會評估GET和POST流量（HTTP API呼叫），並套用規則集以決定要封鎖的流量。 WAF可以封鎖各種攻擊，包括SQL插入攻擊、跨網站指令碼攻擊、資料匯出攻擊和HTTP通訊協定違規。

作為雲端型服務，WAF不需要安裝或維護任何硬體或軟體。 Fastly是現有的技術合作夥伴，提供軟體與專業知識。 Fastly全球傳遞網路的每個快取節點都擁有高效能、永遠開啟的WAF。

## WAF是否適用於所有雲端客戶？

是，雲端WAF服務包含在您的Adobe Commerce雲端基礎結構訂閱中，適用於Adobe Commerce雲端基礎結構入門計畫架構和Adobe Commerce雲端基礎結構專業計畫架構計畫，不需額外付費。 WAF服務可用於生產和中繼環境。

## WAF是否符合PCI DSS 6.6的要求？

是。

## 如果我的雲端基礎結構帳戶上的Adobe Commerce管理多個網域上的網站，WAF設定檔是否會針對每個網域進行微調，或針對所有網域進行整體微調？

WAF會針對單一雲端帳戶下的所有網域進行整體調整。

## WAF使用哪些規則？

在雲端基礎結構生產環境中，套用至您Adobe Commerce的WAF設定檔中的規則集是以OWASP前10名威脅防護規則集為基礎，該規則集涵蓋常見的Web服務利用方式。 其中也包含TrustWave SpiderLabs所開發的Adobe Commerce特定規則。 Fastly的安全性研究團隊也新增了規則，保護您的網站和網路免受常見的攻擊：不正確的IP位址、不正確的使用者代理程式，以及已知的殭屍網路命令和控制節點。 我們在OWASP Paranoia Level 3或更低等級啟用規則，提供高安全性的涵蓋範圍。

## 如何存取記錄檔？

若要將記錄檔傳送至您的記錄工具，請與您的技術客戶經理(TAM)合作，在Fastly中新增記錄端點。

## 區塊要求是什麼樣子？

封鎖的要求會傳回一個含有要求識別碼的403頁面。

只要自訂包含請求識別碼，您就可以自訂此頁面。 如需詳細資訊，請聯絡您的技術客戶經理。

## 如何更新WAF規則集？ WAF規則的變更或更新速度，以及如何在生產中全域套用？

作為雲端WAF服務的一部分，Fastly管理來自商業第三方、Fastly研究和開放來源的規則更新。 使用者會視需要或在可從個別來源取得規則變更時，將已發佈的規則更新至原則。 啟用後，符合規則發佈類別的新規則也會插入任何服務的WAF執行個體中。 這有助於確保即時涵蓋新的或不斷演變的利用漏洞。 您可以檢閱資訊 [關於規則更新與維護](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) 在Fastly檔案網站上。

## Adobe Commerce的雲端WAF與Fastly提供給直接客戶的WAF解決方案有何不同？

Fastly直接銷售的WAF解決方案是付費產品，包含更廣泛的規則集和額外功能，例如規則自訂和惡意程式碼保護。 Adobe Commerce的雲端WAF解決方案包含以Adobe Commerce應用程式為目標的規則子集，且僅針對每個客戶的生產環境包含一個規則集。

## WAF可針對哪些型別的安全性威脅提供保護？

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">威脅</th>
<th style="width: 497.5px; text-align: left;">WAF保護</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">SQL插入攻擊</td>
<td style="width: 497.5px;">OWASP ModSecurity核心規則集和TrustWave商業規則集都包含SQL插入攻擊及其變體的特定篩選器。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>跨網站插入</p>
</td>
<td style="width: 497.5px;">OWASP規則集可抵禦跨網站插入攻擊。 Fastly針對每個尋求跨網站注入和對來源的其他威脅的請求利用評分機制。 我們會根據整個核心規則集對每個請求進行評分，並驗證請求分數是否低於可設定的臨界值，以便讓請求通過。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">暴力攻擊</td>
<td style="width: 497.5px;">由OWASP規則集涵蓋。 Fastly也會使用可識別特定來源、請求的VCL程式碼，或在任何流量到達原始資料中心之前嘗試使用暴力或壓倒安全性控制項，來封鎖暴力執行活動。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">網路攻擊</td>
<td style="width: 497.5px;">Fastly會自動管理網路攻擊，或是以網路基礎架構為目標的攻擊。 Fastly不會將DNS傳遞給來源，而且不符合窄HTTP、HTTPS或DNS設定檔的流量會在網路邊緣捨棄。 針對控制通訊協定的攻擊可透過驗證整個網路的端點來防禦。 此外，Fastly網路上使用的網路通訊協定也經過強化，以確保無法將其用作放大或反射的手段。 客戶有責任利用Fastly快取IP位址空間（已作為CDN服務的元件發佈給我們的客戶），來防禦略過Fastly網路的攻擊。 建議不要在公用DNS中發佈來源IP位址空間，以確保略過攻擊無法將這些位址作為目標。</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">JavaScript插入攻擊</td>
<td style="width: 497.5px;">WAF規則可防止惡意JavaScript程式碼插入使用者端與Web服務的通訊中。 透過WAF篩選常見的利用漏洞模式或分數，以確保原始服務的完整性。</td>
</tr>
</tbody>
</table>

## 是否提供其他功能？

Adobe Commerce的WAF產品包括PCI需求中針對OWASP Top-10威脅的保護、24x7支援（包括誤判分類及版本升級）。 標準選件不支援下列功能：

* 速率限制
* 規則自訂
* 機器人緩解
* 惡意程式碼保護

## WAF如何影響我的網站效能？

每個非快取要求都會延遲約1.5毫秒(ms)至20毫秒。

## 客戶可以建立和修改IP黑名單以封鎖流量嗎？

可以，客戶可以在雲端基礎結構的Admin UI上，從Adobe Commerce啟用依國家/地區和存取控制清單(ACL)的封鎖。 若您想要封鎖來自特定國家/地區或特定IP或IP範圍的訪客存取，請使用這些功能。 如果您希望封鎖的訪客看到自訂頁面而不是錯誤代碼，您可以在Fastly設定選單中上傳HTML來建立自訂錯誤頁面。 另請參閱 [建立自訂錯誤/維護頁面](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) （位於我們的開發人員檔案中）。

## 我可以在哪裡檢視WAF服務的運作狀態？

整體WAF服務可用性報告於 [Fastly狀態頁面](https://status.fastly.com/). 未提供個別客戶WAF的可用性報告。

## Adobe Commerce是否提供WAF服務的事件管理？

目前不提供事件管理。

## Adobe Commerce是否有安全營運中心？

雖然Adobe Commerce沒有安全性作業中心，但我們有安全性作業程式，可讓我們運用適當的資源，即時回應安全性事件。 我們亦提供全年無休的追蹤支援。

您也可以從取得Adobe Commerce相關安全性新聞和更新 [安全中心](https://helpx.adobe.com/security.html).

## 提供哪些支援？

WAF支援提供下列資源，協助您減輕不想要或惡意請求對服務的影響：

* 入門：支援Adobe Commerce管理的雲端WAF的Fastly服務啟用、初始設定和有限監控
* 持續進行誤判以處理WAF封鎖合法流量的例項
* 任何作為WAF版本升級一部分引入的新標準規則的設定

請參閱 [雲端SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) 其他支援資訊的術語，包括嚴重程度定義、回應時間、管道和可用性。

## 如果WAF封鎖合法流量或造成其他問題，我如何取得協助？

[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 在 [Adobe Commerce說明中心](https://support.magento.com). 請包含指出票證與WAF服務相關，並包含封鎖的請求識別碼(ID)。

Adobe Commerce支援票證系統可追蹤我們的支援工程師與客戶人員之間的通訊。 此系統提供有時間戳記的通訊記錄，並在票證更新時傳送電子郵件給客戶和Adobe Commerce的工作人員。

對於線上提交的所有事件，事件回執將透過Adobe Commerce的客戶說明中心票證系統確認。 收到妥善提交的事件後，支援服務將根據上述優先順序等級優先處理。

下表總結了「WAF支援」的支援通道與可用性：

<table class="table-basic">
<tbody>
<tr>
<th>支援服務</th>
<th>詳細資料</th>
</tr>
<tr>
<td>線上自助服務說明</td>
<td>無限制存取</td>
</tr>
<tr>
<td>事件報告的可用性</td>
<td>24/7</td>
</tr>
<tr>
<td>入口網站</td>
<td>可透過Zendesk取得</td>
</tr>
<tr>
<td>緊急升級*</td>
<td>請參閱 <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Adobe Commerce P1通知熱線</a> 適用於美國和國際號碼的文章。</td>
</tr>
</tbody>
</table>

*\* Adobe Commerce的免付費支援電話線僅針對「優先等級1」事件。 非優先順序1呼叫將減慢對問題的整體回應*

## 誤判會如何分級？

我們有誤判分類程式（全年無休提供），可快速處理並解決合法要求觸發WAF規則的例項。 誤判事件會視為優先順序1問題處理。 作為預設動作，我們的支援團隊可以立即更新WAF原則，以停用觸發封鎖事件的規則，並允許合法請求通過WAF。

## 如果前往雲端基礎結構網站上之Adobe Commerce管理員區段的流量觸發WAF規則，該怎麼辦？ Adobe Commerce支援是否能解決封鎖的管理流量問題？

是的，封鎖的管理流量會被視為優先順序1問題。
