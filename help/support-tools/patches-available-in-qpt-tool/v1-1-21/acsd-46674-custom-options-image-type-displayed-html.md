---
title: 「ACSD-46674：在客戶電子郵件中顯示為HTML的影像型別的自訂選項」
description: 套用ACSD-46674修補程式來修正Adobe Commerce問題，該問題導致客戶電子郵件中將影像型別的自訂選項顯示為HTML。
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674：在客戶電子郵件中顯示為HTML的影像型別的自訂選項

ACSD-46674修補程式修正客戶電子郵件中將影像型別的自訂選項顯示為HTML的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.21。 修補程式ID為ACSD-46674。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

影像型別的自訂選項在客戶電子郵件中會顯示為HTML。

<u>要再現的步驟</u>：

1. 使用自訂選項建立產品。
   * 選項型別： *檔案*
   * 相容的副檔名： *png， jpg， gif*
   * 必填： *是*
1. 在上傳為自訂選項的影像中，為此產品下訂單。
1. 為步驟2中建立的訂單建立商業發票。
1. 建立銷退折讓單。
1. 檢查所有確認電子郵件。

<u>預期結果</u>：

確認電子郵件會顯示上傳的影像。

<u>實際結果</u>：

確認電子郵件包含純HTML代碼，而非產品自訂選項影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tools] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

有關中可用的其他修補程式的資訊 [!DNL QPT]，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
