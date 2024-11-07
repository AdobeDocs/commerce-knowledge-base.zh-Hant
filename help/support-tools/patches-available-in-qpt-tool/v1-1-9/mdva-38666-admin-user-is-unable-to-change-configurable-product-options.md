---
title: 'MDVA-38666：管理員使用者無法變更可設定的產品選項'
description: MDVA-38666修補程式解決管理員使用者無法變更客戶購物車中可設定產品選項的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-38666。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666：管理員使用者無法變更可設定的產品選項

MDVA-38666修補程式解決管理員使用者無法變更客戶購物車中可設定產品選項的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-38666。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法變更客戶購物車中的可設定產品選項。

<u>要再現的步驟</u>：

1. 將客戶帳戶範圍設定為「全域」。
1. 使用商店建立兩個網站。
1. 建立兩個可設定的產品並將其指派給每個網站。
1. 在前端建立客戶帳戶並登入。
1. 將產品新增至購物車並進行結帳（這麼做會使得每個網站上的報價ID不同）。
1. 新增產品至購物車並保留。
1. 切換到第二個網站並將產品新增到購物車（相同的登入應該有效，因為客戶帳戶範圍設定為Global）。
1. 從管理員開啟客戶，並導覽至購物車標籤。
1. 從下拉式清單切換存放區，然後嘗試變更設定。

<u>預期結果</u>：

使用者會取得包含可設定選項的快顯視窗。

<u>實際結果</u>：

不會出現快顯表單。 使用者無法變更設定。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
