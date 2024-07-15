---
title: 'MDVA-26639：新訂單確認電子郵件範本中沒有訂單專案'
description: MDVA-26639修補程式修正建立新訂單時，確認電子郵件範本中缺少訂單專案的問題。
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639：新訂單確認電子郵件範本中沒有訂單專案

MDVA-26639修補程式修正建立新訂單時，確認電子郵件範本中缺少訂單專案的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20時，即可使用此修補程式。 修補程式ID為MDVA-26639。 請注意，問題已在Adobe Commerce 2.3.6中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.3-p1上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **銷售** > **銷售電子郵件** > **新訂單確認**&#x200B;並選取&#x200B;**範本：新接單訂單**。
1. 移至&#x200B;**銷售** > **訂單：選取訂單**，然後移至&#x200B;**資訊**，並選取&#x200B;**傳送郵件**。

<u>預期結果</u>：

訂單專案會如預期顯示在客戶訂單電子郵件中。

<u>實際結果</u>：

客戶訂單電子郵件中缺少訂單專案。 如果您建立新範本並選取範本「新訂單」或「新訂單」(Luma)，同樣適用。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修補程式區段。
