---
title: 'MDVA-30963：管理員產品搜尋篩選器未如預期運作'
description: MDVA-30963修補程式解決Commerce管理員和產品搜尋篩選器無法如預期運作的問題。 篩選**所有存放區檢視**存放區檢視範圍時，也會考慮在存放區檢視範圍中覆寫的值。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963：管理員產品搜尋篩選器未如預期運作

MDVA-30963修補程式解決Commerce管理員和產品搜尋篩選器無法如預期運作的問題。 篩選&#x200B;**所有存放區檢視**&#x200B;存放區檢視範圍時，也會考慮在存放區檢視範圍中覆寫的值。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.2 - 2.4.1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

<u>要再現的步驟</u>：

1. 設定&#x200B;**商店** > **設定** > **目錄** > **目錄** > **價格** > **目錄價格範圍** = *網站*。
1. 建立兩個使用兩種不同貨幣的網站(例如，預設網站為印度商店\[盧比₹\]，第二個網站為美國商店\[美元$\])。
1. 設定下列&#x200B;**基本貨幣**、**預設顯示貨幣**&#x200B;和&#x200B;**允許的貨幣**：
   * **預設設定** = *美元（預設）*
   * **主要網站** = *印度盧比*
   * **WebsiteUS** = **使用預設值** = *美元*
1. 設定&#x200B;**商店** > **貨幣匯率** = *1:1*。
1. 建立指派給兩個網站的測試簡單產品，其價格如下：
   * **預設價格** = **美國網站價格** = *123美元*
   * **主要網站價格** = *321盧比*
1. 建立僅能存取美國商店的subAdmin使用者。
1. 前往美國店面，並將產品放入購物車中（範例： *123 USD價格*）。
1. 以剛建立的subAdmin登入管理員（範例： *僅限美國admin*）。
1. 移至&#x200B;**報表** > **購物車中的產品**。

<u>預期結果</u>：

在&#x200B;**所有存放區檢視**&#x200B;存放區檢視範圍內進行篩選時，產品篩選應該取得該特定範圍內的值集。

<u>實際結果</u>：

篩選「所有存放區檢視」存放區檢視範圍時，也會考量存放區檢視範圍中覆寫的值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修補程式。
