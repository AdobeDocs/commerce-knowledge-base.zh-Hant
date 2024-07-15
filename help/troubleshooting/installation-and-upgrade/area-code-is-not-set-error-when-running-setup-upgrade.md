---
title: 執行setup：upgrade時出現「區碼未設定」錯誤」
description: 本文為雲端基礎結構2.2.3上與*區碼未設定*錯誤（執行setup：upgrade命令時）相關的已知Adobe Commerce問題提供修補程式。
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 執行`setup:upgrade`時發生「未設定區碼」錯誤

本文提供雲端基礎結構2.2.3上已知Adobe Commerce問題的修補程式，此問題與執行下列命令時取得&#x200B;*「未設定區碼」*&#x200B;錯誤有關：

```bash
setup:upgrade
```

>[!NOTE]
>
>Adobe Commerce 2.2.4已修正問題。

## 問題

執行時

```bash
bin/magento setup:upgrade
```

命令，您會收到下列錯誤訊息： *&quot;模組&#39;Magento\_AdvancedSalesRule&#39;：正在安裝資料……未設定區碼：必須先設定區碼，才能啟動工作階段&quot;*，而且命令執行已中斷。 出現此問題是因為在實際設定區域組態之前即已要求該區域組態。 此修補程式可擷取錯誤，而不會中斷升級程式。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱，或按一下以下連結：

[下載MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.3

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.2.0 - 2.2.3

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
