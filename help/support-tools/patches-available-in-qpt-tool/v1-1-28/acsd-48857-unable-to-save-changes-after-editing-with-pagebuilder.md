---
title: '''ACSD-48857：使用編輯後無法儲存變更 [!DNL Page Builder]『'
description: 套用ACSD-48857修補程式，修正使用者在編輯後無法儲存變更的Adobe Commerce問題。 [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857：使用編輯後無法儲存變更 [!DNL Page Builder]

ACSD-48857修補程式修正了使用者在使用編輯後無法儲存變更的問題 [!DNL Page Builder]. 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-48857。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者在使用編輯後無法儲存變更 [!DNL Page Builder].

<u>要再現的步驟</u>

1. 登入Admin網站。
1. 瀏覽至 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** 以建立空白的CMS頁面。
1. 執行此SQL指令碼以設定下列專案 **[!UICONTROL Content]** 欄位值：

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. 返回至 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** 在Admin中。
1. 編輯您的頁面。
1. 前往 **[!UICONTROL Content]** 標籤。
1. 按一下 **[!UICONTROL Save]**.

<u>預期結果</u>

已實施HTML內容淨化。 這會移除 [!DNL Page Builder] 文字編輯器產生的內容中有保留的HTML屬性。

<u>實際結果</u>

頁面保持未儲存狀態，且載入器持續旋轉。 在主控台中會產生下列錯誤：

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
