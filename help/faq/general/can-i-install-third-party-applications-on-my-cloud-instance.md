---
title: 我可以在我的雲端例項上安裝協力廠商應用程式嗎？
description: 不適用。 不允許在雲端基礎結構伺服器上的Adobe Commerce上安裝協力廠商應用程式（例如WordPress或Drupal）。 您必須在外部伺服器上裝載這類應用程式。
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 我可以在我的雲端例項上安裝協力廠商應用程式嗎？

不適用。 不允許在雲端基礎結構伺服器上的Adobe Commerce上安裝協力廠商應用程式（例如WordPress或Drupal）。 您必須在外部伺服器上裝載這類應用程式。

## 原因

### 服務合約條款

雲端基礎結構上的Adobe Commerce版本[服務條款合約](https://magento.com/legal/terms/cloud-terms)在第18條中說明下列事項：

> 客戶同意Adobe Commerce及本服務不用於裝載其他不直接依存於本軟體的協力廠商軟體應用程式。

身為雲端解決方案，Adobe對伺服器的安全性負全責。 為確保高安全性，我們僅允許在專用的雲端伺服器上託管Adobe Commerce應用程式。

### PCI法規遵循

作為PCI認證的第1級解決方案供應商，雲端基礎結構上的Adobe Commerce必須遵守PCI資料安全性標準，並確保：

>...開發及維護安全的系統與應用程式
> ([PCI法規遵循的Adobe方法](https://magento.com/pci-compliance)需求6，維護弱點管理程式)

由於Adobe無法保證協力廠商應用程式的PCI相容性，因此不允許在雲端伺服器上安裝此類應用程式。

## 提示：使用Commerce Marketplace擴充功能以獲得更好的整合

若要改善雲端基礎結構應用程式上的Adobe Commerce與託管於外部伺服器上的協力廠商解決方案的整合，我們建議您使用可能符合您用途的[Commerce Marketplace](https://marketplace.magento.com)擴充功能。
