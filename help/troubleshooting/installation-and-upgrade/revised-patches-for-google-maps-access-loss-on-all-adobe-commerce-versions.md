---
title: 修訂所有Adobe Commerce版本上Google地圖存取遺失的修補程式
description: 「本文針對Adobe Commerce商家不相容於3.54+以上任何最新 [!DNL Google Maps] 版本的商戶提供修正。」
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 修訂所有Adobe Commerce版本上[!DNL Google Maps]存取權遺失的修補程式

本文針對Adobe Commerce商家不相容於3.54+以上任何最新[!DNL Google Maps]版本的商戶提供修正。 此修正旨在解決Adobe Commerce商家無法再存取任何版本Adobe Commerce中的[!DNL Google Maps]的問題。

## 受影響的版本和產品

* Adobe Commerce和/或其他所用技術的版本。
* 雲端和內部部署版本上的Adobe Commerce *2.4.4* - *2.4.7*。

## 問題

在&#x200B;*2024年6月14日* [!DNL Google Maps]版本&#x200B;*3.53*&#x200B;到達生命週期結束並已由[!DNL Google]關閉。

如需詳細資訊，請參閱[[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)。

Adobe Commerce與3.54+版本的任何最新[!DNL &#x200B; Google Maps]版本不相容。

不相容性是由舊版`prototype.js script`所造成，透過`lib/web/legacy-build.min.js`載入會覆寫原生Array.from函式，導致與[!DNL &#x200B; Google Maps] API直接衝突。

請參閱[[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices)。

<u>要再現的步驟</u> ：

1. 按一下「**[!UICONTROL Content]** > **[!UICONTROL Pages]**」>並選取&#x200B;**[!UICONTROL New Page]**。
1. 展開內容區塊並按一下編輯&#x200B;**[!DNL PageBuilder]**&#x200B;按鈕。
1. 從&#x200B;**[!DNL PageBuilder]**&#x200B;功能表將「對應內容區塊」拖曳到頁面。

<u>預期結果：</u>

[!DNL Google Maps]應該會如預期般運作。

<u>實際結果：</u>

將地圖內容區塊從&#x200B;**[!DNL PageBuilder]**&#x200B;功能表拖曳至頁面時，出現錯誤訊息，例如： *「抱歉！ 發生錯誤「*」已顯示。

## 解決方案

* 任何2.4.4、2.4.5、2.4.6或2.4.7修補程式版本上的所有商戶都應將相應的修補程式套用至其版本。

## 修補

根據Adobe Commerce版本，使用以下附加修補程式：

**版本2.4.4：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**版本2.4.5：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**版本2.4.6：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**版本2.4.7：**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**請注意**

此問題將在8月僅限安全性修補程式版本的範圍內永久修正：
2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10

## 相關閱讀

[如何套用Adobe提供的撰寫器修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)