---
title: 無法驗證VAT編號 — 雲端基礎結構上的Adobe Commerce
description: 本文針對VAT號碼驗證期間發生錯誤的問題提供修補程式。
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 無法驗證VAT編號 — 雲端基礎結構上的Adobe Commerce

本文針對VAT號碼驗證期間發生錯誤的問題提供修補程式。

## 受影響的產品和版本

所有雲端基礎結構版本2.3.6 （包括2.3.5-p1）以下的Adobe Commerce內部部署和Adobe Commerce都受到影響，包括已發行的p1和p2版本。 其中包括：

* 2.3.5 - p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## 問題

<u>要再現的步驟：</u>

1. 移至&#x200B;**商店** > **設定** > **客戶** > **客戶設定** > **建立新帳戶選項**&#x200B;並設定&#x200B;**啟用自動指派**&#x200B;至&#x200B;**客戶群組**&#x200B;至&#x200B;*是*。
1. 移至&#x200B;**一般** > **存放區資訊** >並設定有效的國家/地區和VAT編號。
1. 按一下&#x200B;**驗證VAT編號**。

<u>預期結果：</u>

驗證成功。

<u>實際結果：</u>

顯示下列錯誤： &quot;*VAT號碼驗證期間發生錯誤。*&quot;

## 解決方案

套用本文提供的[修補程式](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
