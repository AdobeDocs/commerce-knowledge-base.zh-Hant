---
title: MDVA-41236：無法為產品建立新的或編輯現有的排程更新
description: MDVA-41236修補程式修正了使用者無法建立新的或編輯產品現有排程更新（如果先前已移除「結束日期」）的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41236。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236：無法為產品建立新的或編輯現有的排程更新

MDVA-41236修補程式修正了使用者無法建立新的或編輯產品現有排程更新（如果先前已移除「結束日期」）的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41236。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果「結束日期」先前已移除，則使用者無法為產品建立新排程或編輯現有排程。

<u>要再現的步驟</u>：

1. 建立狀態設定為&#x200B;*停用*&#x200B;的產品。
1. 新增排程更新以啟用此產品。
   * 新增未來的開始和結束日期。
1. 移除&#x200B;**結束日期**&#x200B;以編輯排定的更新。
1. 再次編輯排程，並嘗試新增&#x200B;**結束日期**。 將會發生錯誤。
1. 重新整理頁面，然後再次移至&#x200B;**編輯排定的更新**。
1. 按一下&#x200B;**從更新移除** > **刪除更新**。
1. 現在您不應該在產品編輯頁面上方看到排程更新。
1. 嘗試建立與先前期間重疊的新排程更新。

<u>預期結果</u>：

* 步驟4中沒有錯誤。 由於排程尚未啟用，管理員可以更新排程更新而不會出現任何錯誤。
* 管理員使用者可以刪除先前的更新並建立新的更新。

<u>實際結果</u>：

使用者會收到下列錯誤訊息：

*錯誤：未來更新已存在於此時間範圍內。 設定不同的範圍，然後再試一次。*


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修補程式區段。
