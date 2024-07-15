---
title: Adobe Commerce Fastly疑難排解員
description: 此Adobe Commerce使用者的Fastly疑難排解員會根據您對症狀的回應，將您引導至解決方案。 按一下問題以檢視下一個選項或答案。
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Adobe Commerce Fastly疑難排解員

此Adobe Commerce使用者的Fastly疑難排解員會根據您對症狀的回應，將您引導至解決方案。 按一下問題以檢視下一個選項或答案。

## 步驟1 — 驗證Fastly服務 {#step-1}

+++**客戶回報與Fastly有關的問題。 Fastly服務停止了嗎？**

a.是 — 檢查[Fastly服務狀態](https://status.fastly.com/)，並[提交Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 繼續進行[步驟2](#step-2)。

+++

## 步驟2 — 檢查VCL組態檔 {#step-2}

+++**當您執行Backend Tester時是否有任何錯誤？**

透過[後端測試器 — Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/)執行您的專案URL。 它會顯示VCL組態檔的版本（如果頁面可快取）、Fastly模組的版本以及其他有用的疑難排解資訊。 您是否有任何錯誤？

a.是 — 您有訊息&#x200B;_外掛程式VCL版本已過時！ 請重新上傳。_&#x200B;如需此錯誤的解決方案，請參閱[Fastly錯誤：外掛程式VCL版本已過時！ 請重新上傳](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md)。\
b.否 — [步驟3](#step-3)。

+++

## 步驟3 — 檢查影像最佳化錯誤 {#step-3}

+++**影像最佳化錯誤？**

a.是 — [啟用影像最佳化時發生錯誤](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md)。\
b.否 — 在CLI/終端機中執行，以檢查DNS： `dig [your website.com] + short`。 繼續進行[步驟4](#step-4)。

+++

## 步驟4 — 驗證DNS {#step-4}

+++**當您執行`dig`時會發生什麼事？**

當您執行`dig`時，它傳回指向prod.magentocloud.map.fastly.net或下列IP位址之一的記錄（請參閱我們的開發人員檔案中的[使用生產設定更新DNS設定](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns)）：

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a.是 — 問題與DNS無關。 繼續進行[步驟5](#step-5)。\
b.否 — 此問題可能與DNS有關。 客戶應[檢查DNS設定](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns")或連絡其DNS提供者以取得詳細資訊。

+++

## 步驟5 — 確認連線 {#step-5}

+++**在CLI/終端機執行`curl -svo /dev/null "https://website.com"`時，您收到「連線不安全」或「不安全」訊息嗎？**

a.是 — 這可能是憑證問題。 在瀏覽器中造訪網站，然後選取鎖定圖示並尋找憑證到期日。 繼續進行[步驟6](#step-6)。\
b.否 — 造訪[http://fastly-debug.com](https://www.fastly-debug.com/)，並在[Adobe Commerce支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)中共用此資訊。

+++

## 步驟6 — 確認您擁有有效的TSL憑證 {#step-6}

+++**憑證是否已過期？**

a.是 — 您需要向憑證授權單位(CA)更新TLS憑證。\
b.否 — 您可能完全沒有憑證。 如果您有Adobe Commerce，建議您購買TLS憑證。 如果您在雲端基礎結構上的Adobe Commerce上，您可以擁有網域已驗證的Let&#39;s Encrypt SSL/TLS憑證以提供來自Fastly的安全HTTPS流量。 請參閱我們的開發人員檔案中的[布建SSL/TLS憑證](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)。

+++

[回到步驟1](#step-1)
