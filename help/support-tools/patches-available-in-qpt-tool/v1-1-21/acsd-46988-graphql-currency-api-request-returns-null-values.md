---
title: 「ACSD-46988：GraphQL currency API要求傳回null值」
description: ACSD-46988修補程式修正GraphQL貨幣API請求傳回自訂貨幣的null值的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21後，即可使用此修補程式。 修補程式ID為ACSD-46988。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988：GraphQL貨幣API要求傳回null值

ACSD-46988修補程式修正GraphQL貨幣API請求傳回自訂貨幣的null值的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46988。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL currency API要求傳回自訂貨幣的null值。

<u>要再現的步驟</u>：

1. 在「管理員」中設定自訂貨幣。 移至&#x200B;**系統** > **組態** > **一般** > **貨幣設定**。
1. 傳送包含下列裝載的GraphQL請求：

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>預期結果</u>：

該請求會傳回貨幣值而不是null值。

<u>實際結果</u>：

該請求會傳回多個null值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [品質修補工具>使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) （在品質修補工具指南中）。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 安裝修補程式後所需的其他步驟

對於內部部署使用者：

* 執行： `composer require symfony/intl:"~5.4.11"`

對於雲端使用者：

* 執行： `composer require symfony/intl:"~5.4.11"`
* 將`composer.json`和`composer.lock`檔案連同修補程式檔案一起推送到Git存放庫。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱「品質修補程式工具」指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
