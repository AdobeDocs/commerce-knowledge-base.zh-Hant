---
title: 可用於Adobe Commerce的安全性更新 — [!DNL APSB24-73]
promoted: true
description: 套用隔離修補程式，以針對Adobe Commerce 2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10及只執行 [!DNL B2B] 模組的舊版執行個體修正 [!DNL critical, important, and moderate vulnerabilities] 。
feature: Compliance, Security
role: Developer
source-git-commit: 694cb7519733e950b55006866e585097bc2429f4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 可用於Adobe Commerce的安全性更新 — [!DNL APSB24-73]

在2024年10月8日，Adobe已發行Adobe Commerce和[!DNL Adobe Commerce Webhooks Plugin]的定期排程安全性更新。
此更新解決[[!DNL critical, important]和 [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)漏洞。 成功利用此漏洞可能會導致執行任意程式碼、讀取任意檔案系統、略過安全性功能以及提升許可權。 公告是[Adobe安全性公告([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

>[!NOTE]
>
>以上安全性公告中列出的&#x200B;**[!DNL CVE-2024-45115]僅適用於使用[!DNL B2B]模組。**&#x200B;為了協助確保儘快套用此漏洞的補救，Adobe也發行了解決[!DNL CVE-2024-45115]的隔離修補程式。

**請儘快套用最新的安全性更新。 若未這麼做，您就容易受到這些安全性問題的攻擊，而Adobe的協助補救方式有限。**

>[!NOTE]
>
>如果您在套用安全性修補程式/隔離修補程式時遇到任何問題，請連絡支援服務。

## 受影響的產品和版本

雲端上的Adobe Commerce和Adobe Commerce內部部署：

* 2.4.7-p2和更舊版本
* 2.4.6-p7和更舊版本
* 2.4.5-p9和更舊版本
* 2.4.4-p10和較舊版本

B2B：

* 1.4.2-p2和較舊版本
* 1.3.5-p7和更舊版本
* 1.3.4-p9和更舊版本
* 1.3.3-p10和較舊版本


## 適用於Adobe Commerce on Cloud和Adobe Commerce內部部署軟體的解決方案

若要協助解決受影響產品和版本的弱點，您必須套用[!DNL CVE-2024-45115]獨立修補程式。

## 隔離的修正程式詳細資訊

使用以下附加的隔離修補程式：

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## 如何套用隔離的修補程式

解壓縮檔案，並參閱我們的支援知識庫中的[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的撰寫器修補程式，以取得指示。

## 僅適用於Adobe Commerce on Cloud商家 — 如何分辨是否已套用隔離的修補程式

考慮到無法輕易檢查問題是否已修補，您可能想要檢查[!DNL CVE-2024-45115]隔離的修補程式是否已成功套用。

<u>您可以執行下列步驟，以檔案`VULN-27015-2.4.7_COMPOSER.patch` **為例**</u>：

1. [安裝品質修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
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

* [Adobe安全性公告([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
