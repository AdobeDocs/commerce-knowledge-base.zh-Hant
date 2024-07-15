---
title: 'MDVA-36718：API變更後仍保留自訂選項'
description: MDVA-36718Magento修補程式修正了透過API變更舊自訂選項後仍保留的問題。
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718：API變更後仍會保留自訂選項

MDVA-36718Magento修補程式修正了透過API變更舊自訂選項後仍保留的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22時，即可使用此修補程式。 修補程式ID為MDVA-36718。 請注意，此問題已排程在Magento 2.4.3版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.1

**與Magento版本相容：**

Adobe Commerce （所有部署方法） 2.3.0-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 新增&#x200B;**下拉式清單型別**&#x200B;自訂選項。
1. 透過API更新自訂選項：傳送`PUT`要求給`/V1/products/options/{optionId}`。

<u>預期結果</u>：

自訂選項會如預期更新。

<u>實際結果</u>：

會新增自訂選項，但會保留舊的自訂選項。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [檢查我們的支援知識庫中Quality Patches Tool的Magento問題修補程式](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
