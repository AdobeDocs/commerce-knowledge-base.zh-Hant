---
title: 'MDVA-36832：影像在具有768px檢視寬度的頁面上複製'
description: MDVA-36832修補程式修正了檢視寬度為768px的頁面上重複顯示影像的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24時，即可使用此修補程式。 修補程式ID為MDVA-36832。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832：影像在具有768px檢視寬度的頁面上複製

MDVA-36832修補程式修正了檢視寬度為768px的頁面上重複顯示影像的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24時，即可使用此修補程式。 修補程式ID為MDVA-36832。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.5-p2上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;內部部署的Adobe Commerce和雲端基礎結構上的Adobe Commerce 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

檢視寬度為768畫素的頁面上重複的影像。

<u>要再現的步驟：</u>

1. 前往後端>內容>頁面並編輯任何頁面。
1. 新增任何影像至頁面。
1. 前往前端並開啟已編輯的頁面。
1. 在Chrome中開啟開發人員工具。
1. 啟用「裝置檢視」並選取「iPad檢視」，或設定頁面寬度為768畫素。

<u>實際結果：</u>

影像重複。

<u>預期結果：</u>

頁面上應該只會顯示一個新增的影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
