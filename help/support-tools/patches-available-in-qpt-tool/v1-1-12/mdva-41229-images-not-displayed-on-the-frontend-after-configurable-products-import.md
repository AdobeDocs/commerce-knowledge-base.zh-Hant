---
title: 'MDVA-41229：可設定產品匯入後，前端未顯示可用的影像'
description: MDVA-41229修補程式可解決可設定產品匯入後，前端上未顯示可用影像的問題。 安裝[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-41229。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229：可設定產品匯入後，前端上未顯示可用的影像

MDVA-41229修補程式可解決可設定產品匯入後，前端上未顯示可用影像的問題。 安裝[品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-41229。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.2-p2和2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯入可供設定的產品後，前端上可用的影像不會顯示在前端上。

<u>要再現的步驟</u>：

1. 安裝乾淨的Adobe Commerce。
1. 透過以下設定移至&#x200B;**商店** > **屬性** > **產品** > **新增屬性**&#x200B;來新增自訂屬性：

   * 屬性：
      * 屬性特性：

         * 預設標籤：設定大小
         * 存放區所有者的目錄輸入型別：文字色票
         * 需要的值：否
         * 更新產品預覽影像：是

      * 管理色票（屬性值）：

        | 為預設 | 管理色票 | 管理員說明 | 預設存放區檢視色票 | 預設存放區檢視說明 |
        |---|---|---|---|---|
        | 否 | 4 | 4 | 4 | 4 |
        | 否 | 24 | 24 | 24 | 24 |
        | 否 | 30 | 30 | 30 | 30 |
        | 否 | 60 | 60 | 60 | 60 |
        | 否 | 68 | 68 | 68 | 68 |

      * 進階屬性特性：

         * 屬性代碼： set_size
         * 範圍：全域
         * 唯一值：否
         * 商店所有者的輸入驗證：無
         * 新增至欄選項：否
         * 使用篩選器選項：否

   * 管理標籤：

      * 管理標題（大小、顏色等）

         * 預設存放區檢視：設定大小

   * 店面屬性：

      * 用於搜尋：是
      * 搜尋權數： 1
      * 在進階搜尋中可見：否
      * 店面比較：是
      * 用於分層導覽：可篩選（含結果）
      * 用於搜尋結果階層導覽：是
      * 用於促銷規則條件：否
      * 在店面的目錄頁面上可見：是
      * 用於產品清單：是
      * 用於產品清單中的排序：否

1. 將此屬性新增至產品詳細資料群組內的預設屬性集（**商店** > **屬性** > **屬性集**）。
1. 將影像集下載至Adobe Commerce根目錄內的var資料夾。
1. 移至&#x200B;**系統** > **資料傳輸** >並使用下列選項匯入檔案：

   * 匯入設定：

      * 實體型別：產品

   * 匯入行為：

      * 匯入行為：新增/更新
      * 驗證策略：發生錯誤時停止
      * 允許的錯誤計數：1
      * 欄位分隔符號： `;`
      * 多值分隔符號： `,`
      * 屬性值常數： EMPTYVALUE
      * 欄位附件：未勾選

   * 要匯入的檔案：

      * 選取要匯入的檔案
      * 影像檔案目錄：保留空白

1. 前往店面至`/product-set.html`頁，並在不同的集大小之間切換。 對於「設定大小24」，將不會有相簿。

<u>預期結果</u>：

可設定產品內所有簡單產品的相簿會與所有相關影像一起顯示。

<u>實際結果</u>：

沒有產品收藏館。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 雲端基礎結構上的Adobe Commerce： [我們的開發人員檔案中的「升級和修補程式>套用修補程式」](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [品質修補程式工具已發行：我們支援知識庫中的自助式品質修補程式](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)的新工具。
* [使用我們的支援知識庫中的品質修補程式工具](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱我們的開發人員檔案中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修補程式。
