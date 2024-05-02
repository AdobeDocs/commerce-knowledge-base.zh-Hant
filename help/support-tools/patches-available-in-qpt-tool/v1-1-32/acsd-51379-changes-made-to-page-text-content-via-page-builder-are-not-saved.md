---
title: 「ACSD-51379：變更頁面文字內容，透過 [!DNL Page Builder] 未儲存」
description: 套用ACSD-51379修補程式，修正透過對頁面文字內容進行變更的Adobe Commerce問題。 [!DNL Page Builder] 未儲存。
exl-id: e274ca03-b675-4ded-9820-1d60978685d0
feature: Page Builder, Page Content
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-51379：透過變更頁面文字內容 [!DNL Page Builder] 未儲存

ACSD-51379修補程式修正透過對頁面文字內容進行變更的問題 [!DNL Page Builder] 未儲存。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.32。 修補程式ID為ACSD-51379。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過對頁面文字內容進行的變更 [!DNL Page Builder] 未儲存。

<u>要再現的步驟</u>：

1. 登入管理員。
1. 前往 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**.
1. 建立測試頁面，在頁面上包含一個列和一個文字元素 **[!UICONTROL Content]** 標籤。
1. 儲存頁面並返回 **[!UICONTROL Content]** 標籤。
1. 選取文字並加以變更，即可編輯文字。

   **注意：** 僅當選擇並變更文字而未啟動編輯器時，該問題才可重現。

1. 按一下 **[!UICONTROL Save and Close]** 按鈕。
1. 再次開啟測試頁面並檢查 **[!UICONTROL Content]** 標籤。

<u>預期結果</u>：

新文字已成功儲存為原始和重複的文字元素。

<u>實際結果</u>：

文字元素已成功複製，但未儲存新文字。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
