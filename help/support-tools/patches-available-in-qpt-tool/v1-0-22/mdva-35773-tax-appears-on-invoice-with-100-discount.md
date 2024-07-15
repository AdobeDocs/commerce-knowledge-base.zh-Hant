---
title: 'MDVA-35773：稅捐出現在含100%折扣的商業發票上'
description: MDVA-35773修補程式修正了100%折扣訂單的商業發票上「總計」未顯示為零的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-35773。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773：稅捐會出現在含100%折扣的商業發票上

MDVA-35773修補程式修正了100%折扣訂單的商業發票上「總計」未顯示為零的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-35773。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.6

**與Adobe Commerce版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.3.7和2.4.1-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 瀏覽至&#x200B;**商店** > **設定** > **組態** > **銷售** > **稅捐**。
1. 設定&#x200B;**目錄價格**&#x200B;和&#x200B;**套用價格折扣**&#x200B;至&#x200B;*含稅*。
1. 瀏覽至&#x200B;**商店** > **稅捐規則** > **新增稅捐規則**。
1. 建立稅捐規則（範例：稅率為10%的所有美國）並套用它。
1. 導覽至&#x200B;**行銷** > **購物車價格規則**，然後&#x200B;**新增規則**。
1. 為所有使用者建立&#x200B;**100%折扣的規則**。
1. 在店面下訂單：

   * 選擇&#x200B;**免運費**。
   * 套用&#x200B;**優惠券代碼**。

1. 導覽至&#x200B;**銷售** > **訂單**，然後開啟您的訂單。
1. 建立訂單的商業發票，並開啟它。

<u>預期結果</u>：

發票總計= *$0.00*。

<u>實際結果</u>：

已建立商業發票總計= *稅捐金額*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
