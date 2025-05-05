---
title: MDVA-43859：刪除客戶登入時記錄「沒有具有customerId =」的這類實體」錯誤
description: MDVA-43859修補程式修正錯誤*當已刪除的客戶嘗試登入時，不會記錄具有customerId=*的此類實體問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43859。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859：刪除客戶登入時記錄「沒有具有customerId =」的這類實體」錯誤

MDVA-43859修補程式修正錯誤&#x200B;*當已刪除的客戶嘗試登入時，不會記錄具有customerId =*&#x200B;的這類實體。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43859。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤&#x200B;*當已刪除的客戶嘗試登入時，不會記錄具有customerId =*&#x200B;的此類實體。

<u>要再現的步驟</u>：

1. 從前端建立客戶帳戶。
1. 登出並登入在步驟一中建立的客戶帳戶。
1. 在另一個瀏覽器中載入後端，並前往客戶網格。
1. 刪除在步驟一中建立的客戶。
1. 切換回第一個瀏覽器，然後嘗試登出。

<u>預期結果</u>：

系統會將客戶重新導向至登入頁面，不會發生任何錯誤。

<u>實際結果</u>：

客戶收到下列錯誤： *沒有具有customerId =*&#x200B;的這類實體。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)修補程式。
