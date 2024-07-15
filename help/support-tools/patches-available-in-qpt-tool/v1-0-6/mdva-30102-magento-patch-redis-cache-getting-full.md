---
title: 'MDVA-30102：Redis快取已滿'
description: MDVA-30102修補程式可解決Redis快取已滿並產生錯誤，導致產品清單頁面(PLP)和產品詳細資料頁面(PDP)發生問題，例如遺失產品的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6後，即可使用此修補程式。
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102：Redis快取已滿

MDVA-30102修補程式可解決Redis快取已滿並產生錯誤，導致產品清單頁面(PLP)和產品詳細資料頁面(PDP)發生問題，例如遺失產品的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6時，即可使用此修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.3.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Redis快取已滿，而且配置的`maxmemory`似乎不足。 配置快取沒有TTL且未被逐出，導致快取成長和逐出Redis中的其他索引鍵。 因此，所有Redis記憶體都已配置給配置快取。

<u>必要條件</u>：

* 使用者必須使用Adobe Commerce 2.4，並擁有100K簡單產品（產品型別不重要）和50個類別。
* Redis快取必須依照開發人員檔案之[Adobe Commerce設定指南>針對Adobe Commerce頁面使用Redis和預設快取](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command)中提供的步驟進行設定。

<u>要再現的步驟</u>：

1. 瀏覽所有PDP和PLP。 您可以使用[OWASP ZAP](https://www.zaproxy.org/)來編目網站。
1. 觀察Redis記憶體的使用狀況。
1. 此外，檢查目前的設定和使用的記憶體。 在CLI中執行以下命令。 它會檢查已使用的記憶體、最大記憶體、已收回金鑰以及Redis啟動時間（以天為單位）：

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>預期結果</u>：

Redis快取不應快速增長。

<u>實際結果</u>：

Redis快取可擴充至約5GB。 Redis的記憶體上限為8GB，因此如果您有100萬種產品，記憶體很快就會用完。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
