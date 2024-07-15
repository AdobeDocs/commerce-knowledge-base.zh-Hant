---
title: 'MDVA-20376：沒有具有customerId的這類實體'
description: MDVA-20376修補程式解決下單後登入客戶的*無customerId = 1*這類實體錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13後，即可使用此修補程式。 請注意，Adobe Commerce 2.3.4版已修正問題。
exl-id: a12865d0-4ac2-444f-b8b6-22cae249f5d4
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-20376：沒有具有customerId的這類實體

MDVA-20376修補程式解決下單後登入客戶的&#x200B;*沒有customerId = 1*&#x200B;的這類實體錯誤的問題。 安裝[品質修補工具(QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13時，即可使用此修補程式。 請注意，Adobe Commerce 2.3.4版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

雲端基礎結構上的Adobe Commerce 2.3.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

登入的客戶在下單後收到&#x200B;*customerId = 1*&#x200B;的這類實體錯誤。

<u>要再現的步驟</u>：

1. 導覽至店面，並以註冊使用者身分登入。
1. 下訂單。
1. 在CLI中，移至`var/log`，您將會看到`exception.log`檔案。

<u>預期結果</u>：

如預期，記錄中不應出現任何錯誤。

<u>實際結果</u>：

例外記錄會填滿類似下列的錯誤：

```php
report.CRITICAL: No such entity with customerId = 1 {"exception":"[object] (Magento\\Framework\\Exception\\NoSuchEntityException(code: 0): No such entity with customerId = 1 at /mnt/data/home/nyarlaga/dev/232/vendor/magento/framework/Exception/NoSuchEntityException.php:50)"} []
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
