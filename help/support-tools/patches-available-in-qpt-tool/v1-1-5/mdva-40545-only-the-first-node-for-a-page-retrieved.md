---
title: 'MDVA-40545：僅擷取頁面的第一個節點'
description: MDVA-40545修補程式可解決即使同一頁面有多個節點，僅擷取頁面的第一個節點的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-40545。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: ac7aaed9-5e81-45fe-b699-40d9c086a05c
feature: CMS, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-40545：僅擷取頁面的第一個節點

MDVA-40545修補程式可解決即使同一頁面有多個節點，僅擷取頁面的第一個節點的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-40545。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使同一頁面有多個節點，也只會擷取頁面的第一個節點。

<u>要再現的步驟</u>：

1. 在管理面板中，移至&#x200B;**階層**&#x200B;並新增兩個功能表專案/節點。
1. 將相同的CMS頁面新增至每個節點。
1. 清除快取並檢查前端。
1. 檢查第一個新增子功能表的連結和階層連結。
1. 檢查第二個新增子功能表的連結和階層連結。

<u>預期結果</u>：

第二個子功能表上的階層連結和連結與第二個節點相關。

<u>實際結果</u>：

第二個子功能表上的階層連結和連結與第一個子功能表相同。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
