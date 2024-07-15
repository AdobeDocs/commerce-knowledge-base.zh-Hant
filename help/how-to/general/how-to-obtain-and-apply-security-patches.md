---
title: 如何取得並套用[!UICONTROL security patch]
description: 本文提供如何取得及套用已發行的[!UICONTROL security patch]的指示，但無法取得指示。
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 如何取得並套用[!UICONTROL security patch]

本文提供如何取得及套用已發行的[!UICONTROL security patch]的指示，但無法取得指示。

## 受影響的產品和版本

Adobe Commerce On-Premise和Cloud — 所有版本

## 原因

大部分的[!UICONTROL Security Patches]已發行，不需套用任何實體檔案或Hotfix。

## 解決方案


### 案例I：

如果發行說明中提及實體修補程式檔案/Hotfix：

* 從[https://account.magento.com](https://account.magento.com/downloads/view/)的下載區段下載檔案。 （共用存取許可權的使用者必須先獲得帳戶擁有者/授權持有者的下載許可權）

**警告：**

如果您使用舊版Adobe Commerce且已購買擴充支援，您的版本必須是下列其中一個版本才能套用安全性修補程式：

* 2.4.2 - p2
* 2.4.3 - p3

如果您沒有「延伸支援」，您可以要求「支援」與您共用修補程式，但無法解決您在套用修補程式時可能遇到的任何問題/錯誤。

### 案例II：

如果發行說明中未提及實體修補程式檔案/Hotfix：

* **雲端：**

1. 在適用於Commerce的雲端修補程式底下，最新版本的雲端工具套件(ECE Tools)中可能包含/發行了某些[!UICONTROL Security Patches] — 請檢視[發行說明](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)，如果發行版本中提到安全性修正，請將套件升級至該版本。
1. 如果發行說明未提及安全性修正，請繼續閱讀。

* **雲端或內部部署：**

* 如果無法使用實體修補程式檔案/Hotfix，[請將Cloud上的Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X升級至最新的修補程式版本2.4.X-pY。
* 如果無法使用實體修補程式檔案/Hotfix，[請將Adobe Commerce Version On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X升級至最新的修補程式版本2.4.X-pY。

## 相關閱讀

* 請參閱&#x200B;*雲端基礎結構上的Adobe Commerce指南*&#x200B;中的Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)的[發行說明。
* 請參閱&#x200B;*雲端基礎結構指南上的Adobe Commerce*&#x200B;中的[升級Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)。
