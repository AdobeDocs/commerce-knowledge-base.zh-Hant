---
title: 針對PHP漏洞的Adobe Commerce Recommendations
description: 9月3日，多狀態資訊共用與分析中心(MS-ISAC)發佈了與多個漏洞相關的警示，這些漏洞可能允許執行任意程式碼，並建議所有使用PHP的網站儘快更新為最新的PHP版本([此處提供完整警示](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/))。
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# 針對PHP漏洞的Adobe Commerce Recommendations

9月3日，多狀態資訊共用與分析中心(MS-ISAC)已發出與多個漏洞相關的警示，這些漏洞可能允許執行任意程式碼，並建議所有使用PHP的網站儘快更新為最新的PHP版本（[此處提供完整警示](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)）。

>[!WARNING]
>
>在雲端基礎結構上的Adobe Commerce上，請注意，服務升級無法在未提前48個營業時間通知我們的基礎結構團隊的情況下推送至生產環境。 這是必要措施，因為我們需要確保我們有一位基礎建設支援工程師在所需時間範圍內更新您的設定，將生產環境的停機時間降到最低。 因此，在變更需要投入生產前48小時[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，詳細說明您需要的服務升級，並陳述您想要啟動升級程式的時間。

請閱讀下文，瞭解Adobe Commerce網站的影響和步驟：

**在我們雲端產品上代管的Adobe Commerce**

如果您在雲端基礎結構上使用Adobe Commerce，請與您的技術團隊合作，隨時開始重新部署Adobe Commerce\*，以運用此更新。 我們建議商戶在9月30日前完成這項重新部署，以避免PCI法規遵循問題，這些問題可能會在本月底因這些漏洞而生效。

針對此更新重新部署雲端網站的其他附註：

* 如果您的網站仍在使用PHP 7.0版，則必須在重新部署之前先升級到支援的PHP版本，以便利用這些安全性更新。
* 若為2.1.x/2.2.x，有關升級PHP的更多資訊可在[這裡](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html)找到。

\* *本文和訊息的先前版本顯示為9月19日，但我們的團隊已提前完成工作。*

所有其他託管解決方案上的&#x200B;**Adobe Commerce**

由於Adobe Commerce仰賴PHP，因此我們建議所有使用Adobe Commerce的商家與其託管提供者一起檢閱PHP的必要更新。 我們也建議商戶在9月30日前完成這項檢閱及任何更新，以避免由於本月底的這些漏洞而可能生效的PCI法規遵循問題。

請注意其他託管解決方案中Adobe Commerce的其他詳細資料：

* 使用7.1或以上版本的PHP的Adobe Commerce 2.0或1.x版沒有提供正式的PHP修補程式。 建議的路徑是將PHP升級至支援的PHP版本。

根據警示，針對此漏洞的建議修補程式包括：

* PHP 7.1： [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2： [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3： [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

如果您想瞭解更多有關PHP和最新版本的資訊，可以造訪[PHP的網站](https://www.php.net/)。 如果您有問題或想瞭解更多有關安全性最佳實務的資訊，請參閱我們的[安全性最佳實務指南](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf)。
