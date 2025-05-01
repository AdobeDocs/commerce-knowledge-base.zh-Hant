---
title: 如何取得並套用[!UICONTROL security patch]
description: 本文提供如何取得及套用已發行的[!UICONTROL security patch]的指示，但無法取得指示。
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 3c7234b52e5e4465d95c95345e1c070c28600dfb
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# 如何取得並套用[!UICONTROL security patch]

>[!NOTE]
>如果您有內部部署安裝，而且未使用[!DNL CVS]或[!DNL GitHub]等版本控制系統來管理您的程式碼，您的Web主機或許可以協助套用修補程式。 歡迎聯絡他們以尋求支援。

本文提供如何取得及套用已發行的[!UICONTROL security patch]的指示，但無法取得指示。

## 受影響的產品和版本

Adobe Commerce On-Premise和Cloud — 所有版本


## 原因

大部分[!UICONTROL Security Patches]已發行，但未套用任何獨立的修補程式或Hotfix，因此需要升級至[!UICONTROL Security Patch]發行版本。

## 解決方案


### 案例I：

* 如果[發行說明](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite)中提及隔離的修補程式檔案/Hotfix，請從[https://account.magento.com](https://account.magento.com/downloads/view/)的下載區段下載檔案。 共用存取許可權的使用者必須先獲得帳戶擁有者/授權持有者的下載許可權。

**警告：**

如果您使用舊版Adobe Commerce (2.4.4)，系統會自動提供延伸支援。 您的版本必須是下列不支援的版本之一，才能套用最新的安全性修補程式：

2.4.4 - 2.4.4-p11

不支援的版本(2.3.x、2.4.0 - 2.4.3)不符合支援資格，您必須先升級至支援的版本，才能利用最新的安全性修正。

如果您沒有「延伸支援」，您可以要求「支援」與您共用修補程式，但無法解決您在套用修補程式時可能遇到的任何問題/錯誤。

### 案例II：

隔離的修補程式僅於例外情況下提供，並非實作安全性修正的推薦形式。

如果發行說明中未提及隔離的修補程式檔案/Hotfix：

* **雲端：**

1. 在適用於Commerce的雲端修補程式底下，最新版本的雲端工具套件(ECE Tools)中可能包含/發行了某些[!UICONTROL Security Patches] — 請檢視[發行說明](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)，如果發行版本中提到安全性修正，請將套件升級至該版本。
1. 如果發行說明未提及安全性修正，請繼續閱讀。

* **雲端或內部部署：**

* 如果無法使用隔離的修補程式檔案/Hotfix，[請將Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X上的Adobe Commerce版本升級至最新的修補程式版本2.4.X-pY。
* 如果無法使用隔離的修補程式檔案/Hotfix，[請將Adobe Commerce Version On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X升級至最新的修補程式版本2.4.X-pY。

## 相關閱讀

* 請參閱&#x200B;*雲端基礎結構上的Commerce Cloud指南*&#x200B;中的[Adobe Commerce Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)發行說明。
* 請參閱&#x200B;*雲端基礎結構指南上的Adobe Commerce*&#x200B;中的[升級Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)。
