---
title: 'MDVA-32012修補程式：南韓和阿根廷郵遞區號驗證'
description: MDVA-32012修補程式可解決阿根廷和韓國郵遞區號因國家郵遞區號格式變更或變異而無法驗證的問題。 南韓郵遞區號現在必須是5位數，而之前則為6位數。 阿根廷郵遞區號可以同時為數值和英數字元。 MDVA-32012修補程式表示這些郵遞區號值格式將適用於這些國家/地區。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9後，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2版中修正。
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-32012修補程式：南韓和阿根廷郵遞區號驗證

MDVA-32012修補程式可解決阿根廷和韓國郵遞區號因國家郵遞區號格式變更或變異而無法驗證的問題。 南韓郵遞區號現在必須是5位數，而之前則為6位數。 阿根廷郵遞區號可以同時為數值和英數字元。 MDVA-32012修補程式表示這些郵遞區號值格式將適用於這些國家/地區。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.2版中修正。

## 受影響的產品和版本

* 此修補程式是專為雲端基礎結構2.3.5上的Adobe Commerce所設計。
* 此修補程式也與下列Adobe Commerce版本相容：雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0到2.4.1。

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

輸入5位數的南韓或英數字元阿根廷郵遞區號會產生警告：

*提供的郵遞區號似乎無效。 範例： [1234 （如果輸入英數字元阿根廷位址）]或[123-456 （如果輸入5位數的南韓位址）]。 如果您認為此通知是正確的，則可以忽略此通知。*

<u>要再現的步驟</u>：

1. 開啟店面。
1. 新增專案至購物車。
1. 結帳程式。
1. 新增南韓地址作為國家/地區，並輸入5位數的郵遞區號，或新增阿根廷地址作為國家/地區，並輸入英數字元的郵遞區號。
1. 嘗試儲存。

<u>預期結果</u>：

地址應該儲存而不發出警告。

<u>實際結果</u>：

儲存位址會傳回警告。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中的[修補程式。
