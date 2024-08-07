---
title: 「在Admin中儲存主題設定時出現『區域已設定』錯誤」
description: 本文為雲端基礎結構2.2.4上已知的Adobe Commerce問題提供修補程式，該問題與嘗試在Commerce管理員中設定預設商店檢視的主題時取得*「區域已設定」*錯誤訊息有關。
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 在Admin中儲存主題設定時出現「區域已設定」錯誤

本文為雲端基礎結構2.2.4上已知的Adobe Commerce問題提供修補程式，該問題與嘗試在Commerce管理員中設定預設存放區檢視的主題時，取得&#x200B;*「區域已設定」*&#x200B;錯誤訊息有關。

## 問題

儲存此設定時，您收到「*發生錯誤：區域已設定*」嘗試為預設存放區檢視設定主題時的錯誤訊息。

<u>要再現的步驟</u>：

1. 登入Commerce管理員。
1. 瀏覽至&#x200B;**內容** > **設計** > **組態**。
1. 將設定範圍設定為&#x200B;*預設存放區檢視*。
1. 在&#x200B;**套用的主題**&#x200B;下拉式清單中變更主題。 例如，從&#x200B;*Luma*&#x200B;到&#x200B;*Blank.*
1. 按一下&#x200B;**儲存組態**。

<u>預期結果</u>：選取的主題已套用至預設存放區檢視。

<u>實際結果</u> ：未套用主題，*「儲存此設定時發生錯誤：區域已設定」*&#x200B;錯誤訊息會顯示。

## 修補

此修補程式已附加至本文。 若要下載，請按一下以下連結，或向下捲動至文章結尾，然後按一下附加的檔案：

[下載MDVA-11106\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* 雲端基礎結構上的Adobe Commerce 2.2.4

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* 雲端基礎結構上的Adobe Commerce 2.0.X
* 雲端基礎結構上的Adobe Commerce 2.1.X
* 雲端基礎結構上的Adobe Commerce 2.2.0 - 2.2.5
* Adobe Commerce內部部署2.0.X
* Adobe Commerce內部部署2.1.X
* Adobe Commerce內部部署2.2.0 - 2.2.5

## 如何套用修補程式

如需指示，請參閱我們的支援知識庫中的[如何套用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
