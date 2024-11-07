---
title: 「MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作」
description: MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984：套用中繼更新時，視覺化銷售器無法正常運作

MDVA-37984修補程式可解決Visual Merchandiser的「依規則比對產品」功能，在套用中繼更新時無法正確篩選產品的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-37984。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

套用中繼更新時，Visual Merchandiser的「依規則比對產品」功能無法正確篩選產品。

<u>要再現的步驟</u>：

1. 建立任何現有產品的排程更新。
   * 為`entity_id`和`row_id`設定不同的值。
1. 建立新的可設定產品，然後建立簡單的產品（因此新產品`entity_id`和`row_ids`也不同）。
   * 為了更輕鬆複製問題，請為簡單產品設定可區分的數量值，例如5000。
1. 移至類別> **類別**&#x200B;中的產品，並啟用&#x200B;**依規則比對產品**。
1. 現在選取「數量」作為屬性，「大於」作為運運算元，「4500」作為值。
1. 按一下&#x200B;**儲存**。

<u>預期結果</u>：

隨即列出新建立的可設定產品。

<u>實際結果</u>：

新建立的可設定產品未列出。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
