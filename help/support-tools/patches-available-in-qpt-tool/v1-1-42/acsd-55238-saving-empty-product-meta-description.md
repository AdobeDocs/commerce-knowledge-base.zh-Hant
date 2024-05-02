---
title: 'ACSD-55238：儲存空白的產品中繼說明'
description: 套用ACSD-55238修補程式以修正Adobe Commerce問題，其中產品說明包含產生的HTML代碼 [!DNL Page Builder] 或者另一個HTML編輯器會始終顯示在中繼描述中，並且無法將其設定為空白。
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238：儲存空的產品中繼說明

ACSD-55238修補程式修正了中繼說明中一律顯示包含HTML編輯器所產生HTML程式碼的產品說明的問題。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.42。 修補程式ID為ACSD-55238。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品說明，其中包含產生的HTML代碼 [!DNL Page Builder] 或者另一個HTML編輯器會始終顯示在中繼描述中，並且無法將其設定為空白。

<u>要再現的步驟</u>：

1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** 以及建立包含任何內容的新區塊。
1. 前往 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** 並建立新產品。 將中繼說明設定為空白。
1. 使用新增上面建立的區塊 *[!DNL Page Builder]* 在 *[!UICONTROL Content]* 標籤並儲存產品。
1. 在店面開啟產品並檢查其檔案元素 `meta name = "description"`.

<u>預期結果</u>：

中繼說明是空的。

<u>實際結果</u>：

當產品的描述中有區塊時，即會用於產品中繼描述。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
