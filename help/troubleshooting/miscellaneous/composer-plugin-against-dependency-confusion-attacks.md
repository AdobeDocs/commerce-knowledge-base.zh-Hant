---
title: 抵禦相依性混淆攻擊的撰寫器外掛程式
description: 本文提供有關為相依性混淆攻擊發行的撰寫器外掛程式的資訊，以及有關避免錯誤的建議。 Composer外掛程式與Adobe Commerce 2.4.3版一起推出，以保護Adobe Commerce商家免受相依性混淆攻擊。
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 抵禦相依性混淆攻擊的撰寫器外掛程式

本文提供有關為相依性混淆攻擊發行的撰寫器外掛程式的資訊，以及有關避免錯誤的建議。 Composer外掛程式與Adobe Commerce 2.4.3版一起推出，以保護Adobe Commerce商家免受相依性混淆攻擊。

## 受影響的產品和版本

* Adobe Commerce 2.4.3和未來版本（所有部署方法）

## 問題

在撰寫器安裝/更新期間，撰寫器外掛程式`magento/composer-dependency-version-audit-plugin`至少透過`composer.json`中定義的一個直接或間接相依性偵測到使用中相依性混淆攻擊的潛在案例。

<u>要再現的步驟</u>：

安裝/更新composer時，如果偵測到潛在的「相依性混淆」攻擊，composer外掛程式會停止此程式。 在這種情況下，Composer安裝/更新將失敗，並出現類似於以下內容的錯誤訊息：

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## 原因

相依性混淆攻擊可透過追蹤相依性管理員（例如PHP的Composer）從公用來源下載惡意封裝，而不是從私人存放庫下載原始封裝，在伺服器上遠端執行任意程式碼。

如果攻擊者能夠維持原始封裝的功能，甚至可能偵測不到這類攻擊。

如果封裝只能透過私人存放庫取得，但未在公用存放庫中註冊，攻擊者就可以利用此漏洞。 然後攻擊者會將同名的套件上傳到公用存放庫，並提供比私人可用套件更高的版本。 相依性管理員接著會比較私人和公開可用套件的版本，並從公開存放庫中選擇最高的套件。 然後，相依性管理員下載的惡意程式碼將會以與應用程式程式碼相同的許可權執行。

## 解決方案

### Recommendations至商家

* 請認真對待外掛程式停止撰寫器安裝/更新時顯示的錯誤訊息，如果您辨識出可能有問題的套件，請聯絡擴充功能開發人員。
* 您仍然可以從Marketplace或其他信任的私人存放庫，使用封裝的安全版本安裝Adobe Commerce。
* 將composer.json中所需的套件版本變更為Marketplace中的確切版本，以繼續進行composer安裝/更新。

### 擴充功能開發人員的期望

* 如果外掛程式的套件來自公開存放庫，則無法確切判斷該套件是否已受損。 外掛程式會偵測位於packagist.org的套件公用版本何時具有高於私人存放庫（例如[repo.magento.com](https://repo.magento.com)）可用版本的版本。 我們強烈建議擴充功能開發人員避免此類情況，請勿公開發佈比[repo.magento.com](https://repo.magento.com)提供的版本還新的版本。
* Adobe Commerce瞭解市集檢閱程式可能會延遲擴充功能的發行可用性，但程式旨在保護商家的安全，並幫助擴充功能開發人員發現他們可能遺漏的意外錯誤。
