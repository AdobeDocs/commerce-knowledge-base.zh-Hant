---
title: 「ACSD-51853：未使用頁面產生器套用複製的文字樣式」
description: 套用ACSD-51853修補程式，修正使用Page Builder時未套用複製文字樣式的Adobe Commerce問題。
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853：使用頁面產生器不會套用複製的文字樣式

ACSD-51853修補程式修正使用頁面產生器時，未套用複製文字樣式的問題。 此修補程式適用於 [!DNL Quality Patches Tool (QPT)] 已安裝1.1.34。 修補程式ID為ACSD-51853。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用頁面產生器時不會套用複製的文字樣式

<u>要再現的步驟</u>：

1. 登入管理員。
1. 前往> **內容** > **頁面** > **開啟任何頁面** > **使用頁面產生器編輯**.
1. 拖曳列並 *文字* 從 **[!UICONTROL Elements]**.
1. 複製 **豐富的內容**，將該文字貼入 **[!UICONTROL Page Builder]**.

<u>預期結果</u>

複製的文字會與所有樣式一起貼上。

<u>實際結果</u>

複製的文字會貼上成純文字，而所有樣式都會遺失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
