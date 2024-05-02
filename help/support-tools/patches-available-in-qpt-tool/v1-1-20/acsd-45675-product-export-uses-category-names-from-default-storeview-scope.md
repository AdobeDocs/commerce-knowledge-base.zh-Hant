---
title: 'ACSD-45675：產品匯出使用預設商店檢視範圍的類別名稱'
description: ACSD-45675修補程式修正產品匯出使用預設商店檢視範圍的類別名稱的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20後，即可使用此修補程式。 修補程式ID為ACSD-45675。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675：產品匯出使用預設商店檢視範圍的類別名稱

ACSD-45675修補程式修正產品匯出使用預設商店檢視範圍的類別名稱的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.20。 修補程式ID為ACSD-45675。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯出使用預設商店檢視範圍的類別名稱。

<u>要再現的步驟</u>：

1. 建立自訂商店檢視 **[!UICONTROL Thai]** 在主商店內。
1. 製作 **[!UICONTROL Thai]** 主要網站的預設商店檢視。
1. 在「 」下建立以下類別結構 **[!UICONTROL Default Category]**：

   *[!UICONTROL Default category/Tea/Black]*

1. 選取類別 **[!UICONTROL Tea]** 並變更 **[!UICONTROL Scope]** 至 **[!UICONTROL Thai]**.
1. 設定 **[!UICONTROL Category Name]** 作為 **[!UICONTROL ชาดำ]**.
1. 建立簡單產品 **[!UICONTROL SP001]** 並指派類別 **[!UICONTROL Black]**.
1. 確定cron未執行。
1. 執行產品匯出。 依SKU篩選並選取 **[!UICONTROL SP001]**.
1. 檢查 **[!UICONTROL categories]** 欄。

<u>預期結果</u>：

由於匯出期間未選取任何存放區，因此您應會取得如下的類別路徑： *[!UICONTROL Default Category/Tea/Black]*.

<u>實際結果</u>：

類別路徑包含混合語言： *[!UICONTROL Default Category/ชาดำ/Black]*.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tools] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在「品質修補工具」指南中。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) 在我們的支援知識庫中。

有關中可用的其他修補程式的資訊 [!DNL QPT]，請參閱 [中可用的修補程式 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在「品質修補工具」指南中。
