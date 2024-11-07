---
title: 'ACSD-45754：將優惠券套用至購物車後未新增的獎勵點數'
description: ACSD-45754修補程式解決將優惠券套用至購物車後未新增獎勵點數的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18後，即可使用此修補程式。 修補程式ID為ACSD-45754。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754：將優惠券套用至購物車後未新增的獎勵點數

ACSD-45754修補程式解決將優惠券套用至購物車後未新增獎勵點數的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18時，即可使用此修補程式。 修補程式ID為ACSD-45754。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將優惠券套用至購物車後，不會新增獎勵積分。

<u>必要條件</u>：

已設定PayPal付款方法。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **其他設定** > **獎勵匯率**，以建立獎勵點匯率。
1. 使用優惠券代碼建立購物車價格規則，為登入的客戶套用100個獎勵點。
1. 以登入客戶的身分檢視產品，並配備PayPal和優惠券代碼。
1. 檢查管理員中客戶帳戶底下的獎勵點歷史記錄。

<u>預期結果</u>：

根據價格規則將獎勵點數新增給客戶。

<u>實際結果</u>：

不會將任何獎勵點數新增至客戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
