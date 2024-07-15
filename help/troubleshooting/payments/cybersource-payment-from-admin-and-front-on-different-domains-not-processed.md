---
title: 系統不會處理來自不同網域之管理員和前端的數位來源付款
description: 針對已知的Adobe Commerce 2.3.0限制，提供修補程式，限制無法從店面和Commerce管理員（若位於不同網域）處理網路來源付款。
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 系統不會處理來自不同網域之管理員和前端的數位來源付款

針對已知的Adobe Commerce 2.3.0限制，提供修補程式，限制無法從店面和Commerce管理員（若位於不同網域）處理網路來源付款。

>[!NOTE]
>
>核心的Adobe Commerce網路來源支付整合自2.3.3之後已淘汰，並將在2.4.0中完全移除。請改用marketplace的[正式副檔名](https://marketplace.magento.com/cybersource-global-payment-management.html)。

## 問題

先前實施的Cybersource整合僅允許處理來自一個網域的付款。 因此，如果您的Adobe Commerce店面與Commerce管理員位於不同的網域，當您嘗試在管理員中使用網路來源下訂單時，會出現下列錯誤： &quot; *Load denied by X-Frame-Options： https://%your\_domain%/cybersource/SilentOrder/TokenResponse/不允許跨來源框架。* ...&quot;

<u>要再現的步驟</u>：

1. 在不同的子網域上設定管理員。
1. 設定&#x200B;**商店** >設定> **設定** > **銷售** > **付款方式** > **網路來源**&#x200B;下之商店的網路來源。
1. 移至&#x200B;**銷售** > **訂單**。
1. 建立新訂單。
1. 建立新客戶。
1. 輸入客戶明細。
1. 輸入訂單詳細資料（產品、送貨方式）。
1. 選取Cybersource作為付款方式。
1. 提交訂單。

<u>預期結果</u>：下單沒有問題。

<u>實際結果</u>：「訂單」頁面會顯示載入圖示，但從未下訂單。 錯誤會顯示在主控台中。

## 解決方案

附加的修補程式改善了與Cybersource的整合。 套用修補程式後，您需要建立另一個設定檔，讓電腦來源在管理員中處理付款，並在Commerce管理員的&#x200B;**商店** >設定> **設定** > **銷售** > **付款方式** > **電腦來源**&#x200B;下電腦來源設定中新增必要的認證。

>[!NOTE]
>
>此改善包含在Adobe Commerce內部部署和雲端基礎結構2.2.9和2.3.1中。

## 修補

本文附加了數個修補程式，不同版本有不同的修補程式。 若要下載修補程式，請向下捲動至文章結尾並按一下檔案名稱，或按一下下列連結：

* [下載MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [下載MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [下載MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [下載MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## 相容的Adobe Commerce版本

修正程式是為修正程式檔案名稱中註明的特定版本而建立的。 例如，MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch是針對Adobe Commerce 2.1.9建立的，是適用於此版本的最佳修補程式。

這些修補程式也與下列版本相容：

* Adobe Commerce內部部署2.1.3-2.1.17；雲端基礎結構上的Adobe Commerce 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce內部部署2.2.0-2.2.3；雲端基礎結構上的Adobe Commerce 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce內部部署2.2.4-2.2.7；雲端基礎結構上的Adobe Commerce 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce內部部署2.2.8、2.3.0；雲端基礎結構上的Adobe Commerce 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
