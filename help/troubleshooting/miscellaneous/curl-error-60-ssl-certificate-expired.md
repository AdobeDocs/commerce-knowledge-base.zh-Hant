---
title: cURL錯誤60： SSL憑證已過期
description: 本文說明如何在收到cURL錯誤60後檢查上次部署分支的時間： Adobe Commerce雲端基礎結構上的主要或整合分支中的SSL憑證已過期。
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL錯誤60： SSL憑證已過期

本文說明如何在雲端基礎結構上接收`cURL error 60`之後，檢查上次部署分支的時間： Adobe Commerce上的[!DNL Master]或[!DNL Integration]分支中的[!DNL SSL certificate]已過期。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，[所有支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 原因

這些分支中的[!DNL SSL certificates]僅在30天內有效，而該分支可能在30天內未重新部署。

錯誤看起來會類似這樣：

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>[!DNL Let's Encrypt]或[!DNL DigiCert]等知名外部憑證授權單位(CA)未簽署這些憑證。 為了測試和開發的目的，這些憑證由Adobe平台管理，並且可能不預設在瀏覽器或curl中受到信任，除非您明確信任發行憑證的根目錄。

## 解決方案

檢查上次部署分支的時間。 如果超過30天的臨界值，則重新部署分支。

檢查上次執行部署的時間的兩種方法：

* [方法1：使用 [!DNL magento-cloud] CLI](#meth2)。
* [方法2：開啟 [!DNL Project URL]](#meth3)。

如果部署已成功完成，[!DNL SSL certificate]將會自動續約。

如果部署失敗，而您需要協助解決此問題，請[提交支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant#submit-ticket)。

### 方法1：使用[!DNL magento-cloud] CLI {#meth2}

執行此命令： `magento-cloud activity:list --type=environment.push`

### 方法2：開啟[!DNL Project URL] {#meth3}

移至，例如： `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`，然後檢查上次執行部署的時間。

## 相關閱讀

在我們的開發人員檔案中：

* [Cloud Manager API： SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [設定Fastly：布建SSL/TLS憑證](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

在我們的支援知識庫中：

* [自訂SSL憑證到期資訊](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=zh-Hant)
* 雲端基礎結構上Adobe Commerce的[SSL (TLS)憑證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=zh-Hant)
