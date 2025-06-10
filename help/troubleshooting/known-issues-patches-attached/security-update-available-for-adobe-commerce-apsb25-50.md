---
title: 可用於Adobe Commerce的安全性更新 — [!DNL APSB25-50]
promoted: true
description: 套用隔離修補程式來修正Adobe Commerce 2.4.8、2.4.7-p5、2.4.6-p10、2.4.5-p12、2.4.4-p13及舊版的 [!DNL critical and important vulnerabilities] 。
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# 可用於Adobe Commerce的安全性更新 — [!DNL APSB25-50]

2025年6月10日，Adobe發佈了定期排程的Adobe Commerce和Magento Open Source安全性更新。 此更新解決[[!DNL critical] 和 [!DNL important]](https://helpx.adobe.com/tw/security/severity-ratings.html)漏洞。 成功利用這些漏洞可能導致安全功能略過、許可權提升和任意程式碼執行。

如需詳細資訊，請參閱[Adobe安全性公告([!DNL APSB25-50])此處](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

>[!NOTE]
>
>**為了協助確保可以儘快套用上述安全性公告中所列[!DNL CVE-2025-47110]的修正，Adobe也發行了解決[!DNL CVE-2025-47110]的隔離修補程式。 這可讓商家單獨套用修正，並降低因潛在整合問題而造成的延遲風險。**

**請儘快套用最新的安全性更新。 若未這麼做，您就容易受到這些安全性問題的攻擊，而Adobe協助進一步修正此問題的方法有限。**

您可以在這裡閱讀有關[我們的隔離修補程式部署程式的詳細資訊。](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>對於Managed Services上的Adobe Commerce客戶，您的客戶成功工程師可提供套用修補程式的額外指引。

>[!NOTE]
>
>如果您在套用安全性修補程式/隔離修補程式時遇到任何問題，請連絡支援服務。

提醒您，您可以在這裡找到[可用於Adobe Commerce的最新安全性更新。](https://helpx.adobe.com/tw/security/products/magento.html)

## 受影響的產品和版本

Adobe Commerce （所有部署方法）：

* 2.4.8
* 2.4.7-p5和更舊版本
* 2.4.6-p10和較舊版本
* 2.4.5-p12和較舊版本
* 2.4.4-p13和較舊版本

## 問題

### I. CVE-2025-47110：透過Adobe Commerce 2.4.7-p4中的伺服器端範本插入來儲存XSS

<u>受影響的產品和版本</u>：

Adobe Commerce （所有部署方法）：

* 2.4.8
* 2.4.7-p5和更舊版本
* 2.4.6-p10和較舊版本
* 2.4.5-p12和較舊版本
* 2.4.4-p13和較舊版本

<u>解決方案</u>：

若為Adobe Commerce版本：

* 2.4.8
* 2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3、2.4.7-p4、2.4.7-p5
* 2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8、2.4.6-p10
* 2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10、2.4.5-p11、2.4.5-p12
* 2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11、2.4.4-p12、2.4.4-p13

**套用下列獨立的修補程式或升級至最新的安全性修補程式。**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### 二、 VULN-31547：marketplace.magento.com中反映的XSS +一鍵式ATO問題影響IMS執行個體

<u>受影響的產品和版本</u>：

Adobe Commerce （所有部署方法）：

* 2.4.8

<u>解決方案</u>：

若為Adobe Commerce版本：

* 2.4.8

**套用下列獨立的修補程式或升級至最新的安全性修補程式。**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## 如何套用隔離的修補程式

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hant)提供的撰寫器修補程式，以取得指示。

## 僅適用於Adobe Commerce on Cloud商家 — 如何分辨是否已套用隔離的修補程式

考慮到無法輕易檢查問題是否已修補，您可能想要檢查[!DNL CVE-2025-47110]隔離的修補程式是否已成功套用。

>[!NOTE]
>
><u>您可以執行下列步驟，以檔案`VULN-27015-2.4.7_COMPOSER.patch` **作為範例**</u>：

1. [安裝品質修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant)。
1. 執行命令： <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您應該會看到類似以下的輸出，其中VULN-27015傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## 安全性更新

Adobe Commerce可用的安全性更新：

* [Adobe安全性公告([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [可用於Adobe Commerce的最新安全性更新](https://helpx.adobe.com/tw/security/products/magento.html)
