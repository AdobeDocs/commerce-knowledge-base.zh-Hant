---
title: Adobe Commerce 2.4.6從管理面板下訂單時發生錯誤
description: 當您從Adobe Commerce管理面板下訂單後，商店選擇卡住了，本文針對Commerce基礎架構2.4.6上的已知問題提供修補程式。
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6從管理面板下訂單時發生錯誤

當您從Adobe Commerce管理面板下訂單後，商店選擇卡住了，本文針對Commerce基礎架構2.4.6上的已知問題提供修補程式。

## 問題

從「管理員」面板下訂單時，您會卡在選取的商店上。

<u>要再現的步驟</u>

1. 移至&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;並選取要建立訂單的客戶。
2. 從商店選擇器畫面中選取要下訂單的商店。

<u>預期結果</u>

選取商店後，您就能完成訂單。

<u>實際結果：</u>

選取商店後，系統會將您重新導向回商店選擇器頁面，且您無法建立訂單。

## 修補

按一下以下連結以下載修補程式。

[下載ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### 相容的Adobe Commerce版本

此修補程式是為雲端基礎結構上的Adobe Commerce以及與Adobe Commerce內部部署2.4.6和2.4.6-p1建立及相容。

## 如何套用修補程式

* 如需在雲端基礎結構上套用Adobe Commerce修補程式的指示，請參閱我們的Commerce on Cloud Infrastructure指南中的[套用修補程式](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。
* 如需有關套用Adobe Commerce內部部署修補程式的說明，請參閱我們的Commerce升級指南中的[套用修補程式](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer)。
