---
title: 'MDVA-39986：無法在macOS上Safari瀏覽器的管理員中下訂單'
description: MDVA-39986修補程式修正使用者無法在macOS上使用Safari瀏覽器在管理員中下訂單的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39986。 請注意，問題已在Adobe Commerce 2.4.3中修正。
exl-id: a35b6253-e03f-4bdb-a3a3-fceb70588c6e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39986：無法在macOS上Safari瀏覽器的管理員中下訂單

MDVA-39986修補程式修正使用者無法在macOS上使用Safari瀏覽器在管理員中下訂單的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39986。 請注意，問題已在Adobe Commerce 2.4.3中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法使用macOS上的Safari瀏覽器在管理員中下達訂單。

<u>要再現的步驟</u>：

1. 下訂單。
1. 使用macOS上的Safari瀏覽器前往管理員，並開啟您先前建立的訂單。
1. 按一下&#x200B;**重新排序**。
1. 嘗試更新&#x200B;**產品數量**。

<u>預期結果</u>：

使用者應能在macOS上使用Safari瀏覽器重新排序。

<u>實際結果</u>：

使用者收到JS錯誤，其中轉動的滾輪出現且無休止地執行。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
