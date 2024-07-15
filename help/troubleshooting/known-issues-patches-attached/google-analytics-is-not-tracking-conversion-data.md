---
title: Google Analytics未追蹤轉換資料
description: 針對與Google Analytics不追蹤轉換資料相關的已知Adobe Commerce 2.2.4問題，本文提供修補程式。
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Google Analytics未追蹤轉換資料

針對與Google Analytics不追蹤轉換資料相關的已知Adobe Commerce 2.2.4問題，本文提供修補程式。

>[!NOTE]
>
>Adobe Commerce 2.2.6已修正問題。

## 問題

由於Google Analytics元件程式碼發生錯誤，Google Analytics未追蹤轉換資料。

<u>要再現的步驟</u>：

1. 在Commerce管理員的&#x200B;**商店** > **設定** > **設定** > **銷售** > **Google API** > **Google Analytics**&#x200B;下啟用並設定Google Analytics功能。
1. 按一下&#x200B;**儲存設定**。
1. 在店面下訂單。
1. 移至&#x200B;**Google Analytics儀表板** > **轉換** > **總覽**。
1. 將日期範圍設定為目前日期。

<u>預期結果</u>：

順序會顯示在轉換資料中。

<u>實際結果</u>：

該順序未出現在轉換資料中。

## 解決方案

此修補程式修正了Google Analytics元件程式碼中的錯誤。 套用修補程式轉換資料後，Google Analytics會加以追蹤。

## 修補

此修補程式已附加至本文。 若要下載，請向下捲動至文章結尾，然後按一下檔案名稱或按一下以下連結：

[下載MDVA-11263\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### 相容的Adobe Commerce版本：

已建立下列專案的修正程式：

* Adobe Commerce內部部署2.2.4

此修補程式也與下列Adobe Commerce版本相容（但可能無法解決問題）：

* Adobe Commerce內部部署2.2.5
* 雲端基礎結構上的Adobe Commerce 2.2.4、2.2.5

## 如何套用修補程式

如需指示，請參閱[如何套用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的撰寫器修補程式。

## 附加的檔案
