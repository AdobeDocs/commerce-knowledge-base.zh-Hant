---
title: Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0相容性套件Hotfix
description: 本文提供Hotfix，為雲端基礎結構2.4.7-p4上的新 [!DNL HIPAA] 套件1.2.0新增與Adobe Commerce的相容性
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0相容性套件Hotfix

本文提供Hotfix，為新的&#x200B;**[!DNL HIPAA]套件1.2.0**&#x200B;新增與Cloud基礎結構2.4.7-p4上Adobe Commerce的相容性。

此問題將在2.4.7-p5版本中修正。

## 受影響的版本和產品

雲端基礎結構上的Adobe Commerce 2.4.7-p4和更早版本

## 先決條件

* Adobe已布建您的Adobe Commerce帳戶以存取&#x200B;**[!DNL HIPAA Ready]**&#x200B;擴充功能。 請參閱Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)的[[!DNL HIPAA] 整備程度，以取得我們&#x200B;**Adobe Commerce：快速入門手冊**&#x200B;的詳細資料。
* 存取[repo.magento.com](https://repo.magento.com)以安裝擴充功能。 如需金鑰產生和取得必要許可權，請參閱&#x200B;**Adobe Commerce：安裝指南**&#x200B;中的[取得您的驗證金鑰](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys)。

## 問題

[!DNL HIPAA]套件1.1.0與Adobe Commerce 2.4.7x版本行不相容。

## 解決方案

透過此Hotfix，在雲端基礎結構2.4.7-p4上執行Adobe Commerce的商家將能使用[!DNL HIPAA]套件1.2.0。

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0僅與Adobe Commerce 2.4.7-p5相容。 如果您想要新增與Adobe Commerce 2.4.7-p4的[!DNL HIPAA] 1.2.0相容性，請安裝提供的修補程式。<br><u>如果您不在Adobe Commerce 2.4.7-p4上，您必須先升級至Adobe Commerce 2.4.7-p4，才能使用此修補程式</u>。**

若要修正雲端基礎結構2.4.7-p4上Adobe Commerce的問題，您應套用修補程式：

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## 如何套用修補程式

解壓縮檔案，並在我們的支援知識庫中參閱[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的撰寫器修補程式，以取得指示。

## 僅適用於Adobe Commerce on Cloud商家 — 如何判斷是否已套用修補程式

考慮到無法輕鬆檢查問題是否已修補，您可能想要檢查是否已成功套用修補程式。

>[!NOTE]
>
><u>您可以依照下列步驟來執行，將檔案`VULN-27015-2.4.7_COMPOSER.patch` **當做範例**</u>：

1. [安裝品質修補工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 執行命令： <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您應該會看到類似以下的輸出，**<u>其中此處使用的範例VULN-27015</u>**&#x200B;傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
