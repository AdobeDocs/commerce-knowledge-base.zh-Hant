---
title: 衝突的元件相依性
description: 本文提供衝突元件相依性的解決方案。 嘗試使用Web安裝精靈設定或更新Adobe Commerce時，您會看到*「我們找到衝突的元件相依性」*撰寫器錯誤訊息。
exl-id: 782049c4-b6e1-4ead-a00f-80d2aa8475c9
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 衝突的元件相依性

本文提供衝突元件相依性的解決方案。 嘗試使用Web安裝精靈來安裝或更新Adobe Commerce時，您會看到&#x200B;*「我們發現衝突的元件相依性」* Composer錯誤訊息。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x
* Magento Open Source2.2.x、2.3.x


## 問題 {#issue}

發生衝突的元件相依性錯誤訊息，類似於以下內容（實際的封裝名稱和版本會有所不同）：

```bash
We found conflicting component dependencies.
You are trying to update package(s) magento/module-sample-data to 1.0.0-beta
We have detected conflicts with the following packages:
- magento/sample-data version 0.74.0-beta15. Please try to update it to one of the following package versions: 0.74.0-beta16, 0.74.0-beta14, 0.74.0-beta13, 0.74.0-beta12, 0.74.0-beta11, 0.74.0-beta10, 0.74.0-beta9, 0.74.0-beta8, 0.74.0-beta7
```

## 原因

如果Composer無法決定要安裝或更新哪些元件，則會顯示此訊息。

## 解決方案

兩種主要情況可能會導致元件相依性衝突。 按一下您的情境以取得疑難排解步驟。

* [升級Adobe Commerce](#upgrading-magento)
* [與第三方模組不相容：](#incompatibility-third-party-modules)
   * [Adobe Commerce （所有部署型別）](#magento-commerce-magento-commerce-cloud)
   * [Magento Open Source](#opensource)

## 升級Adobe Commerce {#upgrading-magento}

如果您在雲端基礎結構上升級Adobe Commerce，請嘗試下列步驟來解決衝突的元件相依性：

* 檢查用於升級的金鑰。 金鑰是否從正確的電子郵件帳戶產生？
* 檢查許可權並確保其符合Magento升級要求。 檢閱開發人員檔案中的[Magento升級概觀>更新及升級檢查清單>檔案系統許可權](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites#verify-file-system-permissions)。

## 與第三方模組不相容： {#incompatibility-third-party-modules}

相衝突的元件相依性也可能是由第三方模組所造成，這些模組相依於您所安裝的舊版Commerce元件。 請嘗試下列步驟：

1. 在前面的[example](#issue)中，安裝的套件magento/sample-data版本0.74.0-beta15無法升級至1.0.0-beta。 不過，0.74.0-beta15可以升級至0.74.0-beta16 （或其他）。 編輯`composer.json`以進行這些變更。 通常，您專案要求的版本將會在該JSON檔案中物件的`require`或`require-dev`屬性中定義。 視提供的封裝版本選項而定，它們可能會指定特定版本或限制。 如需如何使用撰寫器的一般指引，如果您在我們的雲端基礎建設上，請參考開發人員檔案中的[Cloud for Adobe Commerce >技術和需求>撰寫器](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#files)。 如果您位於Adobe Commerce內部部署，請參閱[Adobe Commerce >安裝指南>使用撰寫器安裝Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) 。
1. 現在嘗試進行整備檢查。 檢閱開發人員檔案中的[Adobe Commerce升級概觀>執行模組管理員>步驟1整備檢查](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/overview)。
1. 如果整備檢查因另一個元件相依性檢查失敗訊息而失敗，則根據您是使用[Adobe Commerce](#magento-commerce-magento-commerce-cloud)還是[Magento Open Source](#opensource)，按一下下列連結以取得進一步的疑難排解步驟。

## Adobe Commerce {#magento-commerce-magento-commerce-cloud}

1. 請洽詢擴充功能的開發人員，以便他們協助您。 您可以在Commerce Marketplace上您所購買擴充功能的頁面上，找到他們的聯絡資訊。 尋找右側面板上顯示的&#x200B;**聯絡賣家**&#x200B;按鈕。 所有Commerce開發人員在Marketplace上發佈擴充功能時，都必須提供使用者和安裝指南。 兩者皆可在登陸頁面的右側找到。
1. 如果您沒有在合理的時間內收到賣家的回應，請[連絡市集支援](mailto:commercemarketplacesupport@adobe.com)，以便我們提醒他們客戶支援承諾。

## Magento Open Source {#opensource}

請透過[我們的主要論壇](https://community.magento.com/)或[聯絡協助Source開啟問題的其他Adobe Commerce合作夥伴](https://magento.com/find-a-partner)。
