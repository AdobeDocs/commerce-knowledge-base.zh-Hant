---
title: Adobe Commerce安全性掃描工具常見問題集
description: 本文回答有關Adobe Commerce安全性掃描工具的一些常見問題(FAQ)。
exl-id: 380ce617-e3d9-491b-b425-8489abd3c541
feature: Compliance
source-git-commit: cff17a83648e10e85d95a5895acd8d1916a8eef9
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Adobe Commerce安全性掃描工具常見問題集

本文回答有關Adobe Commerce安全性掃描工具的一些常見問題(FAQ)。

## 何謂「安全性掃描工具」？工具是為誰撰寫的？ {#what-is-the-magento-security-scan-tool-and-who-is-it-written-for}

安全掃描工具是免費提供的工具，可供我們的商家、開發人員和他們指定負責的人使用，監控他們的網站是否有安全風險。 它可以主動且有效率地偵測商戶商店中的惡意程式，並在出現任何安全性風險、惡意程式碼或威脅時通知商家。

## 安全性掃描工具是否適用於所有Adobe Commerce商家？ {#is-magento-security-scan-tool-available-to-all-magento-merchants}

是，所有Adobe Commerce和Magento Open Source商家都可使用安全性掃描工具。

## 有人可以使用安全性掃描工具掃描我的網站嗎？ {#can-anyone-scan-my-site-with-the-magento-security-scan-tool}

否，商家透過Token請求掃描時，會將其網站連結至其Adobe Commerce帳戶。 每個網站都是獨一無二。

## 工具是否可掃描我網站商店中的非Adobe Commerce頁面？ {#can-the-tool-scan-non-magento-pages-on-my-webstore}

安全掃描工具的設計用途是掃描Adobe Commerce網域上的弱點。 使用安全性掃描工具掃描非Adobe Commerce頁面以找出弱點，可能導致不可靠的結果。 我們強烈建議商戶不要使用安全性掃描工具來掃描其他非Adobe Commerce平台產生的頁面。

## 我可以從掃描工具中排除特定的安全性測試嗎？ {#can-i-exclude-specific-security-tests-from-magento-scan-tool}

安全性掃描工具商家無法從Adobe Commerce的安全性掃描工具掃描中排除特定的安全性測試。 每個安全性掃描工具安全性測試都是為了協助商家識別安全性風險、惡意程式碼和威脅。

## 價格為何？ {#what-does-it-cost}

安全性掃描工具是免費的。 商家必須接受法律免責宣告，依據安全性掃描的結果或其網站的設定，免除Adobe Commerce的責任。

## 安全性掃描工具如何運作？ {#how-does-the-magento-security-scan-tool-work}

安全性掃描工具是網頁式的，可從商家的Adobe Commerce線上帳戶([account.magento.com](https://account.magento.com/))存取。 安全性掃描會透過HTTP和HTTPS運作。 它會檢查已知的安全性問題，並識別遺失的Adobe Commerce修補程式和更新。

## 我要如何註冊使用安全性掃描工具？ {#how-do-i-sign-up-to-use-the-magento-security-scan-tool}

商家可以註冊使用安全性掃描工具，從其Adobe Commerce帳戶([account.magento.com](https://account.magento.com))掃描其網站商店。 請依照連結註冊[這裡](https://account.magento.com/scanner/dashboard/?_ga=2.83981338.267715797.1615821601-2099431409.1611073686)的安全性掃描工具。

## 如果在掃描報告中遇到誤判，該怎麼辦？ {#what-do-i-do-if-i-come-across-a-false-positive-in-the-scan-report}

我們建議商戶調查所有失敗的掃描，並採取適當步驟來解決此類問題。 調查後，如果商戶發現疑似誤判的掃描結果，我們會要求商戶通知Adobe採取適當的行動。

若要提交誤判報告，請輸入具有Adobe Commerce商家支援的票證，以便我們能夠評估誤判、進行必要變更和/或提供建議，以避免日後看到這類通知。
