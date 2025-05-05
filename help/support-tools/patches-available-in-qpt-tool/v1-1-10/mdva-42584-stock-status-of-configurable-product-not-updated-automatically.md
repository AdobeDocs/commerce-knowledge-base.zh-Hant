---
title: 「MDVA-42584：可設定產品的庫存狀態未自動更新」
description: MDVA-42584修補程式可解決在簡單產品更新時，可設定產品的庫存狀態未自動更新的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-42584。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584：可設定產品的庫存狀態未自動更新

MDVA-42584修補程式可解決在簡單產品更新時，可設定產品的庫存狀態未自動更新的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-42584。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當其簡單產品透過API或匯入設定為&#x200B;**庫存**&#x200B;時，後端可設定產品的庫存狀態不會自動更新。

<u>必要條件</u>：

已安裝MSI。

<u>要再現的步驟</u>：

1. 使用兩個選項建立可設定的產品&#x200B;**InvCheck001**： **InvCheck001-M**&#x200B;和&#x200B;**InvCheck001-L**。
1. 簡單產品都應該有數量，而且它們應該是&#x200B;**庫存**，這樣可設定的產品在後端也是&#x200B;**庫存**。
1. 現在，請更新簡單產品，並將「數量」設定為&#x200B;**0**，並將「庫存狀態」設定為&#x200B;**缺貨**。
1. 重新整理可設定的產品，並確認庫存狀態已更新為&#x200B;**缺貨**。
1. 使用下列API端點，並將簡單產品&#x200B;**InvCheck001-M**&#x200B;設定為&#x200B;**庫存**，數量> 0。

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. 移至後端，並驗證簡單產品&#x200B;**InvCheck001-M**&#x200B;的數量和庫存狀態。 已更新為&#x200B;**庫存**。
1. 重新整理可設定產品並檢查庫存狀態。

<u>預期結果</u>：

後端可設定產品&#x200B;**InvCheck001**&#x200B;的庫存狀態會自動更新為&#x200B;**庫存**。

<u>實際結果</u>：

可設定產品的庫存狀態仍為&#x200B;**缺貨**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
