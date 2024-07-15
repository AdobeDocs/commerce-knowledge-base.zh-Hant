---
title: 升級至v10 DHL結構描述以繼續提供DHL運送
description: 本文提供解決方案，可讓商家在DHL schema 6.2於2022年12月淘汰後，透過升級至schema 10.0或套用AC-3023修補程式，繼續提供DHL傳送。
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 升級至10.0版DHL結構描述以繼續提供DHL運送

本文提供解決方案，讓商家在DHL結構描述6.2版於2022年12月底淘汰後繼續提供DHL運送。

## 受影響的產品和版本

* Adobe Commerce 2.4.5及舊版、所有部署方法。

## 問題

在2022年8月，我們發行了DHL結構描述6.2版的[升級，以及修正修補程式](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html)，讓商家能夠繼續提供DHL運送。 DHL於2022年10月再次推出較新的結構描述（10.0版），而舊版（6.2結構描述）將於2022年12月底淘汰。 Adobe Commerce 2.4.5和更早版本的DHL整合僅支援版本6.2。

## 解決方案

2022年10月發行的Adobe Commerce 2.4.5-p1和2.4.4-p2包含新的DHL schema版本10.0。因此，升級至2.4.5-p1和2.4.4-p2的商家不必採取任何動作，即可繼續提供DHL出貨。 我們鼓勵所有商戶在2022年12月底淘汰DHL schema 6.2之前，升級至2.4.5-p1和2.4.4-p2。

如果商戶不想升級至2.4.5-p1和2.4.4-p2，且想要在2022年12月之後繼續提供DHL傳送，則需套用修正修補程式。

## 修補

修補程式ID為AC-3023，可在[!DNL Quality Patches Tool] 1.1.21版中使用。

請參閱下列連結，瞭解如何使用[!DNL Quality Patches Tool]並根據您的部署方法安裝修補程式：

* Adobe Commerce內部部署與Magento Open Source： [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in Adobe Experience League。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

**此修補程式適用於下列Adobe Commerce版本（所有部署方法）：**

* 2.3.7、2.4.0、2.4.1、2.4.2、2.4.3、2.4.3-p2、2.4.3-p3、2.4.4

## 有用的連結

* Adobe Experience League中的[[!DNL Quality Patches Tool] >發行說明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)。

* [[!DNL Quality Patches Tool]：在Adobe Experience League中搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。

## 相關閱讀

* [套用修補程式，以繼續將DHL作為支援知識庫中的運送業者](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html)。

* 使用手冊中的[運送公司> DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html)。
* 使用手冊中的[設定參考>銷售>傳遞方法](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html)。
