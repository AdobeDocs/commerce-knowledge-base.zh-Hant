---
title: 可用於Adobe Commerce的安全性更新 — [!DNL APSB25-08]
promoted: true
description: 套用隔離修補程式來修正Adobe Commerce 2.4.8-beta1、2.4.7-p3、2.4.6-p8、2.4.5-p10、2.4.4-p11及舊版的 [!DNL critical, important, and moderate vulnerabilities] 。
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: aba9548c0b5a06ffd0cddce630e53e5664bb9aac
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# 可用於Adobe Commerce的安全性更新 — [!DNL APSB25-08]

2025年2月11日，Adobe發佈了定期排程的Adobe Commerce和Magento Open Source安全性更新。 此更新解決[[!DNL critical, important]和 [!DNL moderate]](https://helpx.adobe.com/tw/security/severity-ratings.html)漏洞。 成功利用這些漏洞可能會導致執行任意程式碼、略過安全性功能以及提升許可權。 如需詳細資訊，請參閱[Adobe安全性公告([!DNL APSB25-08])此處](https://helpx.adobe.com/tw/security/products/magento/apsb25-08.html)。

>[!NOTE]
>
>**為了協助確保可以儘快套用上述安全性公告中所列的[!DNL CVE-2025-24434]的修正，Adobe也發行了解決[!DNL CVE-2025-24434]的隔離修補程式。 這可讓商家單獨套用修正，並降低因潛在整合問題而造成的延遲風險。**

**請儘快套用最新的安全性更新。 若未這麼做，您就容易受到這些安全性問題的攻擊，而Adobe協助進一步修正此問題的方法有限。**

>[!NOTE]
>
>如果您在套用安全性修補程式/隔離修補程式時遇到任何問題，請連絡支援服務。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce、內部部署的Adobe Commerce和Magento Open Source：

* 2.4.8-beta1和更舊版本
* 2.4.7-p3和更舊版本
* 2.4.6-p8和更舊版本
* 2.4.5-p10和較舊版本
* 2.4.4-p11和較舊版本

## 適用於Adobe Commerce on Cloud、Adobe Commerce內部部署和Magento Open Source軟體的解決方案

>[!NOTE]
>
>此問題已由[最新雲端修補程式更新](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest)解決。 當雲端修補程式更新中的修正已就緒時，嘗試套用隔離的修補程式可能會導致安裝失敗。

為協助解決受影響產品和版本的弱點，您必須根據您的Adobe Commerce/Magento Open Source版本套用[!DNL CVE-2025-24434]獨立修補程式。

## 隔離的修正程式詳細資訊

根據您的Adobe Commerce/Magento Open Source版本，使用以下附加的隔離修補程式：

### 對於2.4.8-beta1版：

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### 若為版本2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3：

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### 若為版本2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8：

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### 若為版本2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10：

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### 針對版本2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11：

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## 如何套用隔離的修補程式

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hant)提供的撰寫器修補程式，以取得指示。

## 僅適用於Adobe Commerce on Cloud商家 — 如何分辨是否已套用隔離的修補程式

考慮到無法輕易檢查問題是否已修補，您可能想要檢查[!DNL CVE-2025-24434]隔離的修補程式是否已成功套用。

>[!NOTE]
>
><u>您可以執行下列步驟，以檔案`VULN-27015-2.4.7_COMPOSER.patch` **為例**</u>：

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

* [Adobe安全性公告([!DNL APSB25-08])](https://helpx.adobe.com/tw/security/products/magento/apsb25-08.html)
* [可用於Adobe Commerce的最新安全性更新](https://helpx.adobe.com/tw/security/products/magento.html)
