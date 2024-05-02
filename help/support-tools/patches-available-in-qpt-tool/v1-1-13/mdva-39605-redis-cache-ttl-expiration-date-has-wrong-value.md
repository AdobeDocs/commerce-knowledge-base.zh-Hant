---
title: 'MDVA-39605：Redis快取TTL （到期日）的值錯誤'
description: MDVA-39605修補程式解決了Redis快取TTL （到期日）的值錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-39605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605： Redis快取TTL （到期日）的值錯誤

MDVA-39605修補程式解決了Redis快取TTL （到期日）的值錯誤的問題。 此修補程式適用於 [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安裝1.1.13。 修補程式ID為MDVA-39605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**此修補程式是針對Adobe Commerce版本建立的：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請更新 `magento/quality-patches` 封裝至最新版本，並檢查 [[!DNL Quality Patches Tool]：搜尋修正程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Redis快取TTL （到期日）的值錯誤。

<u>要再現的步驟</u>：

為了測試此修正，請排清快取並在店面開啟可設定的產品。 然後開啟終端機（主控台）並遵循以下步驟：

1. 執行命令： `redis-cli`.
1. 執行 `KEYS "*PRICE"` (結果中應該只有一個索引鍵，例如， `zc:ti:e54_PRICE`)。 複製金鑰。
1. 執行 `SMEMBERS` 後面接著上一個步驟的鍵(例如， `SMEMBERS zc:ti:e54_PRICE`)。 從結果複製任何金鑰(例如，e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421)。
1. 執行 `KEYS "*<key>"` 使用上一步驟中的金鑰名稱來取得完整的金鑰名稱(例如， `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`)。 結果中應該只有一個索引鍵(例如， `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`)。 您可能會注意到，完整的金鑰名稱只是前置詞為&#39;&#39;的金鑰名稱`zc:k:`「。 現在複製完整金鑰名稱。
1. 執行 `HGETALL` 後接步驟4的完整金鑰名稱以檢查值。 值應包含相關可設定產品之相關產品的序列化資料。
1. 執行 `TTL` 之後是步驟4中的完整金鑰名稱，以檢查金鑰是否有到期日。 結果應與 **-1** 和 **-2** 和應該約為2592000 （30天）。 雖然程式碼中設定的到期日為一年，但Adobe Commerce中使用的Redis程式庫具有2592000s的硬性最大到期限制。

<u>預期結果</u>：

到期限製為2592000s

<u>實際結果</u>：

到期限制已設定為 **-1** 或 **-2**.

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) （位於我們的開發人員檔案中）。
* 雲端基礎結構上的Adobe Commerce： [升級與修補程式>套用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) （位於我們的開發人員檔案中）。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我們的支援知識庫中。
* [使用Quality Patches Tool檢查是否有修補程式可解決Adobe Commerce問題](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我們的支援知識庫中。

如需QPT中其他修補程式的詳細資訊，請參閱 [QPT中可用的修補程式](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) （位於我們的開發人員檔案中）。
