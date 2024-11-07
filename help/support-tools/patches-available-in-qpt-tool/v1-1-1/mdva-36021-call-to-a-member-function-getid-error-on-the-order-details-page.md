---
title: 'MDVA-36021：開啟訂單詳細資料時，使用者收到錯誤訊息'
description: MDVA-36021修補程式解決使用者嘗試開啟訂單詳細資料時，收到*Call to a member function getId()*錯誤訊息的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1後，即可使用此修補程式。 修補程式ID為MDVA-36021。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021：開啟訂單詳細資料時，使用者收到錯誤訊息

MDVA-36021修補程式解決使用者嘗試開啟訂單詳細資料時，收到&#x200B;*對成員函式getId()*&#x200B;錯誤訊息的呼叫的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1時，即可使用此修補程式。 修補程式ID為MDVA-36021。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.1、2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者嘗試開啟訂單詳細資料時，下列錯誤訊息會顯示在Admin的訂單詳細資料頁面中： *report.CRITICAL：錯誤：呼叫/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62*&#x200B;陣列上的成員函式getId()。

<u>必要條件</u>：

系統應具有稅捐設定及具有特定稅率的訂單。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 移至&#x200B;**銷售** > **訂單** > **未結訂單**。

<u>預期結果</u>：

未發生任何錯誤即開啟訂單。

<u>實際結果</u>：

您收到類似下列的錯誤訊息： *report.CRITICAL：錯誤：呼叫/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62*&#x200B;中陣列上的成員函式getId()。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
