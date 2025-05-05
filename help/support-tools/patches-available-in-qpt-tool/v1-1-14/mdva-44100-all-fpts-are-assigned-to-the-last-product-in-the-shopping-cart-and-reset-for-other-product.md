---
title: 'MDVA-44100：所有FPT都指派給購物車中的最後一個產品'
description: MDVA-44100修補程式解決所有FPT指派給購物車中最後一個產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44100。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100：所有FPT都已指派給購物車中的最後一個產品

MDVA-44100修補程式解決所有FPT指派給購物車中最後一個產品的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-44100。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

所有FPT都會指派給購物車中的最後一個產品，而其餘產品的FPT值則會重設。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **銷售** > **稅捐**&#x200B;並設定：
   * 啟用FPT =是
   * 沖銷稅捐至FPT =是
   * 小計中包含FPT =是
1. 移至&#x200B;**商店** > **屬性** > **產品**，然後建立型別= Fixed Product Tax的新屬性。
1. 將屬性新增至屬性集。
1. 從屬性集建立兩個產品，並設定您國家/地區和州的FPT屬性。
1. 將兩個專案新增至訂單。
1. 輸入需要支付FPT的地址。
1. 下訂單。
1. 檢查訂單上的專案清單。

<u>預期結果</u>：

FPT會顯示在每個產品下方。

<u>實際結果</u>：

兩個專案的FPT值都會顯示在第二個專案下。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
