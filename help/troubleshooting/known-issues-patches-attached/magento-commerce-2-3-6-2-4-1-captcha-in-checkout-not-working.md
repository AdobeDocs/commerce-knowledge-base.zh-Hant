---
title: Adobe Commerce 2.3.6、2.4.1在簽出的驗證碼無法運作
description: 本文提供在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付供應商時，用於結帳的CAPTCHA功能在「下訂單」頁面上無法如預期運作之問題的修補程式。
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6、2.4.1在簽出的驗證碼無法運作

本文提供在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付供應商時，用於結帳的CAPTCHA功能在「下訂單」頁面上無法如預期運作之問題的修補程式。

我們的開發人員檔案中已提及此已知問題：

適用於Adobe Commerce 2.3.6</u>的<u>：

* [Adobe Commerce 2.3.6發行說明：已知問題](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/commerce-2-3-6.html)
* [Magento Open Source2.3.6發行說明：已知問題](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

適用於Adobe Commerce 2.4.1</u>的<u>：

* [Adobe Commerce 2.4.1發行說明：已知問題](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-1#known-issues)
* [Magento Open Source2.4.1發行說明：已知問題](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-1#known-issues)

## 受影響的產品和版本

* Adobe Commerce （所有部署方法） 2.3.6和2.4.1
* Magento Open Source2.3.6和2.4.1

## 問題

<u>要再現的步驟</u>

1. 在Commerce中設定以下付款方式中的至少一種：Paypal Express、Payflow Pro或CyberSource。
1. 移至&#x200B;**管理員>商店>設定>客戶>客戶設定>驗證碼** 。
   * 設定&#x200B;**在店面啟用CAPTCHA** = *是* 。
   * 在&#x200B;**Forms**&#x200B;中選取： *結帳/下訂單* 、 *登入*&#x200B;以及&#x200B;*忘記密碼* 。
   * 設定&#x200B;**顯示模式** = *嘗試登入的次數之後* （顯示&#x200B;**嘗試登入失敗的次數**&#x200B;設定）。
   * 設定&#x200B;**嘗試登入失敗的次數** = *0* （讓驗證碼隨時有效）。
1. 在前端將產品新增到購物車並嘗試結帳。
1. 在「付款資訊」頁面上，輸入驗證碼並嘗試使用Paypal Express、Payflow Pro或CyberSource進行結帳。

<u>預期結果：</u>

驗證碼功能如預期運作。

<u>實際結果：</u>

錯誤訊息顯示： *請提供驗證碼並再試一次。*

## 解決方案

根據您是在雲端基礎結構/Magento Open Source 2.3.6或2.4.1上的Adobe Commerce內部部署/Adobe Commerce上，套用以下修補程式之一。

## 修補程式

修補程式已附加至此文章，並可供以`.composer`和`.git`兩種格式下載。

若要下載修補程式，請向下捲動至文章結尾並按一下檔案名稱，或按一下下列其中一個連結：

<u>針對雲端基礎結構上的Adobe Commerce內部部署/Adobe Commerce/Magento Open Source2.3.6</u> ：

* [Composer修補程式MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修補程式MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>對於雲端基礎結構上的Adobe Commerce內部部署/Adobe Commerce/Magento Open Source2.4.1</u> ：

* [Composer修補程式MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修補程式MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

這些修補程式與任何其他Adobe Commerce或Magento Open Source版本及版本不相容。

## 如何套用修補程式

<u>Composer修補程式</u>

請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式，以取得撰寫器修補程式指示。

<u>Git修補程式</u>

如需Adobe Commerce/Magento Open Source的Git修補程式指示，請參閱開發人員檔案[套用修補程式：自訂修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches)。
