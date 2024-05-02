---
title: 如何取得與套用 [!UICONTROL security patch]
description: 本文提供如何取得及套用 [!UICONTROL security patch] 已發行，但無法取得指示。
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: b15a1d008b6cc2bdce797768e6ee7029a747e6da
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 如何取得與套用 [!UICONTROL security patch]

本文提供如何取得及套用 [!UICONTROL security patch] 已發行，但無法取得指示。

## 受影響的產品和版本

Adobe Commerce On-Premise和Cloud — 所有版本

## 原因

最多 [!UICONTROL Security Patches] 發行時不會套用任何實體檔案或hotfix。

## 解決方案


### 案例I：

如果發行說明中提及實體修補程式檔案/Hotfix：

* 從的下載區段下載檔案 [https://account.magento.com](https://account.magento.com/downloads/view/). （共用存取許可權的使用者必須先獲得帳戶擁有者/授權持有者的下載許可權）

**警告：**

如果您使用舊版Adobe Commerce且已購買擴充支援，您的版本必須是下列其中一個版本才能套用安全性修補程式：

* 2.4.2 - p2
* 2.4.3 - p3

如果您沒有「延伸支援」，您可以要求「支援」與您共用修補程式，但無法解決您在套用修補程式時可能遇到的任何問題/錯誤。

### 案例II：

如果發行說明中未提及實體修補程式檔案/Hotfix：

* **雲端：**

1. 部分 [!UICONTROL Security Patches] 可以在Commerce雲端修補程式底下的最新版Cloud Tools Suite (ECE Tools)中包含/發行 — 檢視 [發行說明](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)，而且如果發行版本中有提及安全性修正，請將套件升級至該版本。
1. 如果發行說明未提及安全性修正，請繼續閱讀。

* **雲端或內部部署：**

* 如果無法使用實體修補程式檔案/Hotfix， [升級雲端上的Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X版更新至2.4.X-pY版的最新修補程式。
* 如果無法使用實體修補程式檔案/Hotfix， [升級Adobe Commerce版本On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X版更新至2.4.X-pY版的最新修補程式。

## 相關閱讀

* 另請參閱 [Commerce Cloud Tools Suite發行說明](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite) 在 *雲端基礎結構上的Adobe Commerce指南*.
* 另請參閱 [升級Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 在 *雲端基礎結構上的Adobe Commerce指南*.
