---
title: 'MDVA-34867：未儲存排定更新的條件欄位集值'
description: MDVA-34867修補程式可解決在編輯型錄價格規則時，新排程更新中的條件值未儲存的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867：未儲存排定更新的條件欄位集值

MDVA-34867修補程式可解決在編輯型錄價格規則時，新排程更新中的條件值未儲存的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17時，即可使用此修補程式。 請注意，Adobe Commerce 2.4.3版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.0-p1

**與Adobe Commerce版本相容：**

雲端基礎結構上的Adobe Commerce和Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編輯型錄價格規則時，未儲存新排程更新中的條件值。

<u>要再現的步驟</u>：

1. 登入管理員。
1. 建立具有&#x200B;**條件** = &quot;*類別為1*&quot;的&#x200B;**目錄規則**。
1. 將更新排程為將來的開始日期（範例：明天）並設定&#x200B;**條件** = &quot;*類別為2， 3*&quot;，然後儲存更新。
1. 按一下&#x200B;**檢視/編輯**&#x200B;以上建立的更新，然後檢查條件欄位。

<u>預期結果</u>：

**目錄規則的** **條件** = &quot;*類別是2， 3*&quot;，如預期。

<u>實際結果</u>：

**目錄規則的** **條件** = &quot;*類別是1*&quot;，表示未儲存更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
