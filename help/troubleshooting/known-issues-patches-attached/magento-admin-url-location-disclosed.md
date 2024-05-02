---
title: Adobe Commerce管理員URL位置已公開
description: 本文提供Adobe Commerce安全性問題的修補程式，其中可披露「管理員」面板的URL位置。 知道URL位置有助於更輕鬆地自動執行攻擊。
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Adobe Commerce管理員URL位置已公開

本文提供Adobe Commerce安全性問題的修補程式，其中可披露「管理員」面板的URL位置。 知道URL位置有助於更輕鬆地自動執行攻擊。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.X.X
* Adobe Commerce內部部署2.X.X
* Magento Open Source2.X.X

## 問題

在Magento Open Source和Adobe Commerce中發現可用於揭露管理員面板URL位置的問題。 雖然目前沒有理由相信此問題會直接造成危害，但瞭解URL位置有助於更輕鬆自動化攻擊。

## 解決方案

若要修正此問題，請套用本文附加的修補程式。 若要下載，請按一下以下連結：

* 下載 [PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip)  — 適用於2.1.13-2.1.17版、Adobe Commerce、Magento Open Source
* 下載 [PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip)  — 適用於2.2.0 - 2.2.8版，所有版本
* 下載 [PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip)  — 適用於2.3.0 - 2.3.1版，所有版本

如果您沒有看到產品/版本的修補程式，請升級至最新的安全性版本，然後套用修補程式。

Adobe強烈建議您儘快套用修補程式，即使您未遇到任何攻擊症狀。

## 如何套用修補程式

另請參閱 [如何套用Adobe Commerce提供的撰寫器修補程式](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以取得指示。

## 其他安全性建議

Adobe也強烈建議商家部署工具來保護其管理面板，包括雙因素驗證、VPN、IP AllowListing等。 如需詳細資訊，請參閱下列部落格和檔案：

* [Protect的5個立即動作以抵禦暴力攻擊](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect您的Magento安裝密碼猜測新更新](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [安全性最佳實務](https://magento.com/security/best-practices/security-best-practices)
* 在Adobe Commerce中新增及設定雙因素驗證，用於 [2.3.x](https://docs.magento.com/user-guide/v2.3/stores/security-two-factor-authentication.html) 和 [2.4.x](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)
