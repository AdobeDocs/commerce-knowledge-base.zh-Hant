---
title: 過多Ajax請求導致的效能問題
description: 針對過多Ajax請求所導致的已知Adobe Commerce效能問題，本文提供修補程式。 Adobe Commerce 2.3.4已修正問題。
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# 過多Ajax請求導致的效能問題

針對過多Ajax請求所導致的已知Adobe Commerce效能問題，本文提供修補程式。 Adobe Commerce 2.3.4已修正問題。

## 問題

Adobe Commerce可能從店面傳送備援[Ajax要求](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md)至伺服器，以取得橫幅資訊和客戶資訊。 這些Ajax請求會影響效能，尤其是在高負載（高流量和高流量）的情況下。 因此，如果未使用橫幅功能，建議您完全[停用Adobe Commerce橫幅模組輸出](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)並套用修補程式，以改善客戶資訊的擷取。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### 相容的Adobe Commerce版本

此修補程式適用於下列產品和版本：

* 雲端基礎結構上的Adobe Commerce 2.2.9
* Adobe Commerce內部部署2.2.9

如果您有其他版本的Adobe Commerce，請考慮更新至最新的2.3.x版本。 如果目前無法使用此選項，請[連絡Adobe Commerce支援](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，要求您版本的修補程式。

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
