---
title: '''ACSD-55305：在編輯公司使用者期間快顯視窗凍結 [!UICONTROL My Account]『'
description: 套用ACSD-55305修補程式以修正Adobe Commerce問題，其中 [!UICONTROL Edit Company User] 上的快顯視窗 [!UICONTROL My Account] &gt； [!UICONTROL Company Structure] 在熒幕上使用載入器時，頁面會凍結。
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305：在編輯公司使用者期間快顯視窗凍結 [!UICONTROL My Account]

ACSD-55305修補程式修正以下問題：  [!UICONTROL Edit Company User] 上的快顯視窗 [!UICONTROL My Account]> [!UICONTROL Company Structure] 在熒幕上使用載入器時，頁面會凍結。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.43。 修補程式ID為ACSD-55305。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

嘗試使用時發生錯誤 *[!UICONTROL Edit Company User]* 上的快顯視窗 *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* 頁面時，其會在熒幕上顯示載入器時凍結。

<u>要再現的步驟</u>：

1. 建立B2B公司。
1. 為客戶建立多選屬性。
1. 將值指派給公司管理員新建立的屬性。
1. 以公司管理員身分登入。
1. 前往 [!UICONTROL account dashboard] 並導覽至 **[!UICONTROL Company Structure]**.
1. 選取使用者。
1. 按一下 **[!UICONTROL Edit Selected]**.

<u>預期結果</u>：

表單快顯視窗會精確顯示，提供編輯公司資訊的選項。

<u>實際結果</u>：

表單快顯視窗會出現，且無法編輯。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
