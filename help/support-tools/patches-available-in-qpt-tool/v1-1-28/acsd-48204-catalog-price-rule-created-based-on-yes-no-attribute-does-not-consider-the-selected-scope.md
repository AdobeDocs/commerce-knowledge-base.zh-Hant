---
title: 「ACSD-48204：根據*是/否*屬性建立的型錄價格規則不考慮選取的範圍」
description: 套用ACSD-48204修正程式，修正根據*是/否*屬性建立的型錄價格規則未考慮所選範圍的Adobe Commerce問題。
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204：型錄價格規則建立依據 *是/否* 屬性未將選取的範圍列入考量

ACSD-48204修補程式修正了目錄價格規則建立時所依據的問題 *是/否* 屬性未考慮選取的範圍。 此修補程式適用於 [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.28。 修補程式ID為ACSD-48204。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用其他具有新修補程式的版本 [!DNL Quality Patches Tool] 發行版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

目錄價格規則建立依據 *是/否* 屬性未考慮選取的範圍。

<u>要再現的步驟</u>：

1. 建立兩個網站（預設和W2）。
1. 建立產品屬性 *是/否* 型別。
   * 設定 [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 根據具有兩個變數（V1和V2）的任何屬性建立可設定的產品。
   * 新增 *是/否* 屬性至可設定的變數屬性集
   * 針對其中一個變數(V1)，將值設為 *[!UICONTROL Yes]* 位於非預設網站(W2)
1. 建立目錄規則：
   * 已套用至兩個網站
   * 條件： *是/否* 屬性值是 *[!UICONTROL Yes]*
   * 折扣= 50%
1. 在非預設網站(W2)上開啟可設定的產品。
1. 檢查V1變化是否已套用50%的折扣。
1. 在Adobe Commerce管理員中開啟V1變數。
   * 切換至預設網站
   * 不做變更並儲存產品
1. 重新整理可設定的產品店面頁面。

<u>預期結果</u>：

由於未進行任何變更，V1變化仍套用50%折扣。

<u>實際結果</u>：

折扣會消失。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 雲端基礎結構指南中的Commerce 。

## 相關閱讀

若要深入瞭解 [!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：提供自助式品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [檢查是否有修補程式可用於您的Adobe Commerce問題，使用 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
