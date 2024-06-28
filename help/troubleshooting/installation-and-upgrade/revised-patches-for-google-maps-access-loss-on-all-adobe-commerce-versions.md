---
title: 修訂所有Adobe Commerce版本上Google地圖存取遺失的修補程式
description: 「本文為近期不相容的Adobe Commerce商家提供修正 [!DNL Google Maps] 3.54+.'的版本
feature: Install, Upgrade
role: Developer
source-git-commit: 575fce2f678321ff184779895d43be90828c2ce4
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 修正的修補程式 [!DNL Google Maps] 所有Adobe Commerce版本的存取權遺失

本文為最近不相容的Adobe Commerce商家提供修正 [!DNL Google Maps] 3.54+版本。 此修正旨在解決Adobe Commerce商家無法存取的問題。 [!DNL Google Maps] Adobe Commerce的任何版本中。

## 受影響的版本和產品

* Adobe Commerce和/或其他所用技術的版本。
* Adobe Commerce *2.4.4* - *2.4.7* 雲端和內部部署版本。

## 問題

開啟 *2024年6月14日* [!DNL Google Maps] 版本 *3.53* 已達生命週期結束並由 [!DNL Google].

[如需詳細資訊，請參閱([!DNL Google Maps Platform: Maps JavaScript API])] (https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)。

Adobe Commerce與任何近期版本不相容 [!DNL  Google Maps] 3.54+版本。

不相容性是由舊版所造成 `prototype.js script`，透過載入 `lib/web/legacy-build.min.js` 覆寫原生Array.from函式，這會導致直接與 [!DNL  Google Maps] API。

[請參閱([!DNL Google Maps: JS Best Practices])] (https://developers.google.com/maps/documentation/javascript/best-practices)。

<u>要再現的步驟</u> ：

1. 按一下 **[!UICONTROL Content]** > **[!UICONTROL Pages]** >並選取 **[!UICONTROL New Page]**.
1. 展開內容區塊並按一下編輯 **[!DNL PageBuilder]** 按鈕。
1. 從拖曳地圖內容區塊 **[!DNL PageBuilder]** 功能表至頁面。

<u>預期結果：</u>

[!DNL Google Maps] 應該會如預期般運作。

<u> 實際結果：</u>

從拖放對應內容區塊時 **[!DNL PageBuilder]** 功能表到頁面，出現錯誤訊息，例如 *「抱歉！ 發生錯誤」* 隨即顯示。

## 解決方案

* 任何2.4.4、2.4.5、2.4.6或2.2.7修補程式版本上的所有商戶都應將相應的修補程式套用至其版本。

## 修補

根據Adobe Commerce版本，使用以下附加修補程式：

**若為版本2.4.4：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**若為版本2.4.5：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**若為版本2.4.6：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**若為版本2.4.7：**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**請注意**

此問題將在8月僅限安全性修補程式版本的範圍內永久修正： 2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10

## 相關閱讀

[如何套用Adobe提供的撰寫器修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)