---
title: 'MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤'
description: MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201：搭配地區設定PT使用DOB欄位時發生錯誤

MDVA-43201修補程式可解決在葡萄牙地區設定的客戶登錄檔單中使用DOB客戶屬性時發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10時，即可使用此修補程式。 修補程式ID為MDVA-43201。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

將DOB客戶屬性新增至葡萄牙地區設定的客戶登錄檔單時，表單會提供錯誤&#x200B;*傳遞給iterator_to_array()的引數1必須實作介面可移轉，指定null*。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 移至[管理] > **商店** > **設定** > **一般** > **地區設定選項**，將地區設定設為&#x200B;**葡萄牙文（葡萄牙）**，然後按一下[儲存] **&#x200B;**。
1. 重新索引並清除快取。
1. 移至&#x200B;**商店** > **屬性** > **客戶**。
1. 開啟DOB客戶屬性並將&#x200B;**在店面顯示**&#x200B;設定為&#x200B;**是**。
1. 從&#x200B;**表單中選取要在**&#x200B;中使用的全部。
1. 儲存屬性。
1. 前往前端的「建立新帳戶」頁面。

<u>預期結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時沒有提供錯誤。

<u>實際結果</u>：

葡萄牙商店的客戶登錄檔單在新增DOB屬性時發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
