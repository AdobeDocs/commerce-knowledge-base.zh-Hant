---
title: 「MDVA-32545修補程式：訂單發票不會自動傳送」
description: MDVA-32545修補程式修正了發票電子郵件不會針對管理員下的訂單自動傳送給客戶的問題。 這會影響任何具有**Sale**交易型別的付款方式，例如**Braintree**或**PayPal Payflow Pro**。
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-32545修補程式：訂單發票不會自動傳送

MDVA-32545修補程式修正了發票電子郵件不會針對管理員下的訂單自動傳送給客戶的問題。 這會影響任何具有&#x200B;**Sale**&#x200B;交易型別的付款方式，例如&#x200B;**Braintree**&#x200B;或&#x200B;**PayPal Payflow Pro**。

安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.2版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.2-p2

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 啟用任何具有&#x200B;**Sale**&#x200B;交易型別的付款方法。 (例如： **Braintree**&#x200B;或&#x200B;**PayPal Payflow Pro**。)
1. 建立簡單的產品。
1. 在前端建立客戶帳戶。
1. 向管理員下訂單。

<u>預期結果</u>：

發票電子郵件會如預期自動傳送給客戶。

<u>實際結果</u>：

商業發票電子郵件不會自動傳送給客戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
