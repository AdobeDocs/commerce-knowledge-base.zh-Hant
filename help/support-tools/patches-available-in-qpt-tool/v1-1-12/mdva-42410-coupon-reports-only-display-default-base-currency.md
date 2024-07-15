---
title: 「MDVA-42410：抵用券報表僅顯示預設基本貨幣」
description: MDVA-42410修補程式修正了抵用券報表僅顯示基本貨幣的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-42410。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410：抵用券報表僅顯示預設基本貨幣

MDVA-42410修補程式修正了抵用券報表僅顯示基本貨幣的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-42410。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

抵用券報表只會顯示預設的基本貨幣。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店檢視。
1. 為此新網站設定不同的貨幣。 例如Euro。
1. 移至&#x200B;**商店** > **匯率**，並將匯率設定為&#x200B;**歐元**。
1. 使用特定優惠券建立&#x200B;**購物車價格規則** - **測試**。
1. 前往前端，在新網站上使用&#x200B;**測試**&#x200B;優惠券下訂單。
1. 移至&#x200B;**報表** > **銷售** > **優惠券**。
1. 在「範圍」下拉式清單中選取新網站。
1. 重新整理統計資料並執行報表。

<u>預期結果</u>：

優惠券報表會將新網站的貨幣顯示為歐元。

<u>實際結果</u>：

預設基本貨幣（在此案例中為USD）用於新網站的優惠券報表中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
