---
title: 'MDVA-35312：空的GraphQL請求擲回500錯誤而不是200確定'
description: MDVA-35312修補程式修正空白GraphQL請求擲回錯誤回應代碼500的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18後，即可使用此修補程式。 修補程式ID為MDVA-35312。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312：空的GraphQL請求擲回500錯誤而不是200確定

MDVA-35312修補程式修正空白GraphQL請求擲回錯誤回應代碼500的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18時，即可使用此修補程式。 修補程式ID為MDVA-35312。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Magento版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.4.2

**與Magento版本相容：**

Adobe Commerce內部部署和Adobe Commerce on cloud infrastructure 2.4.1-p1-2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

空的GraphQL請求擲回錯誤回應代碼500，而不是200代碼。

<u>要再現的步驟</u>：

傳送GraphQL請求，例如：

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>預期結果</u>：

回應： *200確定*。

<u>實際結果</u>：

回應： *HTTP/1.1 500內部伺服器錯誤*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
