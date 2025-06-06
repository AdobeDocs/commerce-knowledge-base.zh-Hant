---
title: 從版本&amp；lt； 2.4.5升級時，'[!UICONTROL salesRule]標籤出現問題
description: 套用修補程式以處理從Adobe Commerce版本&amp；lt； 2.4.5升級時的**[!UICONTROL salesRule]**問題。
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 從版本&lt; 2.4.5升級時，**[!UICONTROL salesRule]**&#x200B;個標籤出現問題

Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html)已匯入&#x200B;**[!UICONTROL salesRule]**&#x200B;標籤暫存功能。 當您從Adobe Commerce &lt; 2.4.5升級到任何版本>= 2.4.5時，此變更可能會導致問題。升級之後，**[!UICONTROL salesRule]**&#x200B;標籤可能會不相符。 若要解決此問題，請在升級到較新的Adobe Commerce版本後立即套用修補程式。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce &lt; 2.4.5

## 修補

使用以下附加的修補程式：

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## 如何套用修補程式

1. 請依照Commerce指南中[執行升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=zh-Hant)中的步驟操作。
1. 在&#x200B;**[!UICONTROL Update metadata]**&#x200B;階段之前套用附加的修補程式。
（您也可以在完成&#x200B;**[!UICONTROL Update metadata]**&#x200B;階段後套用修補程式，但您需要再次執行`bin/magento setup:upgrade`）。
1. 在[執行升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=zh-Hant)中繼續其餘步驟。
