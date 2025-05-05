---
title: 核心Adobe Commerce付款整合的折舊
description: 由於支付服務指示PSD2 (請參閱使用手冊中[支付服務指示](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=zh-Hant)的詳細資料)以及許多API的持續發展，許多Adobe Commerce核心支付整合可能會過時，且未來不再符合安全性要求。 為此，許多核心支付整合已經或很快會遭到淘汰，我們建議轉換至其對應的Commerce Marketplace擴充功能。 請閱讀以下文章的其餘部分，以檢閱付款整合的最新淘汰情形。 可在我們的使用手冊中找到每個**Status**連結。 **下列整合功能將會從Adobe Commerce的2.4.0版本中移除，並且在2.3版本中已淘汰。**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# 核心Adobe Commerce付款整合的折舊

由於付款服務指示PSD2 （請參閱使用手冊中[付款服務指示](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html?lang=zh-Hant)的詳細資料）和許多API的持續演化，許多Adobe Commerce核心付款整合可能會過時，且未來不再符合安全性要求。 為此，許多核心支付整合已經或很快會遭到淘汰，我們建議轉換至其對應的Commerce Marketplace擴充功能。 請閱讀以下文章的其餘部分，以檢閱付款整合的最新淘汰情形。 在我們的使用手冊中找到每個&#x200B;**狀態**&#x200B;連結。 **以下整合將從Adobe Commerce的2.4.0版本中移除，並從2.3版本棄用。**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>付款方法整合</strong></td>
<td style="width: 226.364px;"><strong>狀態</strong></td>
<td style="width: 226.364px;"><strong>Adobe Commerce 2.X建議</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=zh-Hant#recommended-solutions">自2.3.5</a><br>2.4.0起已棄用 — 將完全移除</td>
<td style="width: 226.364px;">請詢問您的付款提供者，他們建議採用哪種解決方案來遵守PSD2的要求。</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=zh-Hant#recommended-solutions">自2.3.4</a><br>2.4.0起已棄用 — 將完全移除</td>
<td style="width: 226.364px;">請改用Commerce Marketplace的<a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">正式副檔名</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (直接Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=zh-Hant#recommended-solutions">自2.3.1</a><br>2.4.0起已棄用 — 將完全移除</td>
<td style="width: 226.364px;">請改用Commerce Marketplace的<a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">正式副檔名</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">網路來源</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=zh-Hant#recommended-solutions">自2.3.3</a><br>2.4.0起已棄用 — 將完全移除</td>
<td style="width: 226.364px;">請改用Commerce Marketplace的<a href="https://marketplace.magento.com/cybersource-global-payment-management.html">正式副檔名</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=zh-Hant#recommended-solutions">自2.3.3</a><br>2.4.0起已棄用 — 將完全移除</td>
<td style="width: 226.364px;">請詢問您的付款提供者，他們建議採用哪種解決方案來遵守PSD2的要求。</td>
</tr>
</tbody>
</table>

**請注意，PayPal核心支付方式整合將不會被取代或移除，並且所有2.3.x和2.4.x版本仍受支援。**

## 如何確保您的支付安全邁向未來

對於仍在使用已棄用付款整合的所有Adobe Commerce和Magento Open Source部署，請遵循下列建議，以確保您的客戶付款安全、付款不會被拒絕，並準備升級至Adobe Commerce 2.4.0：

* 如上表所述，從[Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043)安裝並設定正式付款方式延伸。
* 在Admin中停用已棄用的付款整合（將&#x200B;**Enabled**&#x200B;設定選項設為&#x200B;*No* ），如此一來，這些付款整合就不會再以付款選項的形式顯示在您的店面。 請確定所有新訂單都是透過擴充功能整合支付。
* 由於來自Commerce Marketplace的新整合將無法處理使用已棄用的付款整合所進行的付款交易，因此我們建議在部分期間同時使用這兩種付款方法；但僅用於完成已過帳的交易和可能的退款。 為此，請停用已棄用的付款方法，但保留所有設定欄位填入。
