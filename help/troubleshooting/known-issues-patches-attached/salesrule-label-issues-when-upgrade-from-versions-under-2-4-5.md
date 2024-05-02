---
title: 『[!UICONTROL salesRule] 從版本&lt； 2.4.5升級時出現標籤問題
description: 套用修補程式以處理**[!UICONTROL salesRule]**正從Adobe Commerce版本&lt； 2.4.5升級時發生的問題。
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** 從版本&lt; 2.4.5升級時出現標籤問題

此 **[!UICONTROL salesRule]** Adobe Commerce中引進了標籤暫存功能 [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). 當您從Adobe Commerce &lt; 2.4.5升級到任何版本>= 2.4.5時，此變更可能會導致問題。升級之後，可能會 **[!UICONTROL salesRule]** 標籤不相符。 若要解決此問題，請在升級到較新的Adobe Commerce版本後立即套用修補程式。

## 受影響的產品和版本

雲端基礎結構上的Adobe Commerce &lt; 2.4.5

## 修補

使用以下附加的修補程式：

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## 如何套用修補程式

1. 請依照中的步驟操作 [執行升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) Commerce指南中的。
1. 在之前套用附加的修補程式 **[!UICONTROL Update metadata]** 階段。
(您也可以在完成下列作業後套用修正程式： **[!UICONTROL Update metadata]** 階段，但接著您需要執行 `bin/magento setup:upgrade` 再來一次)。
1. 繼續進行中的其餘步驟 [執行升級](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
