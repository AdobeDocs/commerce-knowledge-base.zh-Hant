---
title: 'MDVA-34023修補程式：「沒有這類具有addressId的實體」錯誤'
description: MDVA-34023修補程式解決在客戶的網頁瀏覽器上隨機發生「沒有這類具有addressId的實體」錯誤的問題。
exl-id: bdf8f97d-856a-4dd7-bf21-941d1493496c
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-34023修補程式：「沒有這類具有addressId的實體」錯誤

MDVA-34023修補程式可解決客戶網頁瀏覽器上隨機發生`No such entity with addressId`錯誤的問題。

安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.15時，即可使用此修補程式。 請注意，此問題已排程在Adobe Commerce 2.4.3版中修正。

## 受影響的產品和版本

**在雲端基礎結構2.3.1上為Adobe Commerce版本** Adobe Commerce建立修補程式

**與Adobe Commerce版本相容：**&#x200B;雲端基礎結構上的Adobe Commerce以及Adobe Commerce內部部署2.3.0 - 2.4.2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **設定** > **設定** > **客戶標籤** > **永久購物車**。
1. 設定&#x200B;**啟用持續性** = *是*，設定&#x200B;**登出時清除持續性** = *否*。    ![persistent_shopping_cart_magento_2.4.1.png](/help/support-tools/patches-available-in-qpt-tool/assets/persistent_shopping_cart_magento_2.4.1.png)
1. 建立新客戶，並定義預設的出貨地址與帳單地址。
1. 登出。
1. 使用&#x200B;**記住我**&#x200B;核取方塊登入。
1. 移至`customer_entity`資料庫資料表，並將`default_billing`與`default_shipping`識別碼變更為非現有識別碼。
1. 登出。

<u>預期結果</u>：

如預期般不會出現任何錯誤。

<u>實際結果</u>：

例外狀況記錄會產生：

```php
Exception.log:
{"0":"No such entity with addressId = XXXXX","1":"#0 /vendor\/magento\/module-customer\/Model\/AddressRegistry.php(49): Magento\\Framework
Exception
NoSuchEntityException::singleField('addressId', 'XXXXX')
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT工具中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)區段中的[修補程式。
