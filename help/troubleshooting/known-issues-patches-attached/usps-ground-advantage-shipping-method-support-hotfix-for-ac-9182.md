---
title: '[!DNL USPS] Ground Advantage送貨方法支援AC-9182的Hotfix'
promoted: true
description: 套用修補程式以處理Adobe Commerce 2.4.4 - 2.4.6-p2的 [!DNL USPS] Ground Advantage送貨方法問題AC-9182。
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Ground Advantage送貨方法支援AC-9182的Hotfix

本文提供修補程式，可解決Adobe Commerce 2.4.4 - 2.4.6-p2中新&#x200B;**[!DNL USPS]Ground Advantage**&#x200B;送貨方法的AC-9182問題。

在2023年7月9日，美國郵政服務([!DNL USPS])發行了新的送貨方法，[[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm)。

這個新的送貨方式正在取代目前三種主要送貨方式：

* [!DNL USPS]零售區域
* [!DNL USPS]第一級封裝服務
* [!DNL USPS]包裹選取基底

[[!DNL USPS] 宣佈](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works)自2023年9月30日起，將停止提供這三個送貨方法，所有客戶都必須改用新的&#x200B;**[!DNL USPS]Ground Advantage**&#x200B;方法。

所以在2023年9月30日之後，所有使用USPS送貨方法的Adobe Commerce商家將無法再使用這三個舊送貨方法從[!DNL USPS]取得運費。

此問題將在2023年10月即將推出的僅限安全性修補程式版本2.4.6-p3、2.4.5-p5和2.4.4-p6的範圍中修正。

## 受影響的產品和版本

雲端基礎結構和On-Premise及Magento Open Source上的Adobe Commerce：

* 2.4.4
* 2.4.4 - p1
* 2.4.4 - p2
* 2.4.4 - p3
* 2.4.4 - p4
* 2.4.4 - p5
* 2.4.5
* 2.4.5 - p1
* 2.4.5 - p2
* 2.4.5 - p3
* 2.4.5 - p4
* 2.4.6
* 2.4.6 - p1
* 2.4.6 - p2

## 原因

[!DNL USPS]已進行[!DNL API]更新。

## 解決方案

若要解決2.4.4、2.4.5和2.4.6版本中的問題，您必須套用下列AC-9182修補程式。

## 修補

此修補程式已附加至本文。 若要下載，請按一下以下連結：

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## 如何套用修補程式

解壓縮檔案，並參閱我們的支援知識庫中的[如何套用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的撰寫器修補程式，以取得指示。

## 如何判斷是否已套用修補程式

考慮到無法輕易檢查問題是否已修補，您可能想要檢查AC-9182修補程式是否已成功套用。

<u>您可以執行下列步驟</u>：

1. [安裝 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 執行命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. 您應該會看到類似以下的輸出，其中AC-9182傳回&#x200B;*已套用*&#x200B;狀態：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
