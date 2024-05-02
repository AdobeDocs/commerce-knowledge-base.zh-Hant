---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.33呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.33。
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.33

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.33。

QPT v1.1.33包含下列修補程式：

1. **ACSD-50478**：修正資料庫傾印包含觸發器和分隔符號SQL命令時的資料庫復原命令。
1. **ACSD-50512**：修正錯誤： *可下載的連結和產品無關。 請驗證連結，然後再試一次。*  更新可下載產品測試更新的開始日期時，就會發生這種情況。
1. **ACSD-50949**：修正中的價格篩選器問題 [!UICONTROL Advanced Search] 搭配SKU篩選器使用時未傳回正確結果。
1. **ACSD-51645**：修正儲存新檔案時擲回的錯誤 [!UICONTROL Cart Price Rule] 如果副檔名 `Magento_OfflineShipping` 已停用。
1. **ACSD-50895**：修正以下問題： [!DNL Google Analytics] 3 GTM標籤不會引發，如果 [!DNL Google Analytics] 4 GTM未設定。
1. **ACSD-51102**：修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。
1. **ACSD-50368**：修正客戶的問題。 `group_id` 透過Async REST API或Async Bulk REST API建立客戶時會被忽略。
1. **ACSD-51497**：修正客戶無法依排序目錄頁面的問題 [!UICONTROL Custom Attribute] 下拉式清單型別的。
1. **ACSD-51408**：修正訂單專案狀態錯誤設定為的問題 [!UICONTROL Backordered].
1. **ACSD-51735**：修正訂單專案狀態錯誤設定為的問題 [!UICONTROL Ordered] 當產品庫存為 *0*.
1. **ACSD-51792**：修正以下情況時頁面沒有曝光事件的問題： [!DNL Google Tag Manager] 4已啟用。
1. **ACSD-51471**：修正管理員使用者無法為使用簡單產品（本身有排程更新）的套件產品儲存排程更新的問題。
1. **ACSD-51700**：修正在Admin的可下載產品編輯頁面上切換商店檢視時發生的錯誤。
1. **ACSD-51120**：修正含有透過中繼更新更新更新的CMS區塊的CMS頁面未清除GraphQLGET請求快取的問題。
1. **ACSD-51240**：修正透過公司登錄檔單進行註冊時，上傳的檔案遺失的問題。
1. **ACSD-51907**：修正受限管理員使用者無法以離線退款建立銷退折讓單的問題。
1. **ACSD-52148**：修正的問題： [!UICONTROL Google V3 reCAPTCHA Admin] 登入偶爾會失敗。
1. **ACSD-51431**：修正即使變更記錄檔中沒有新專案，索引子狀態仍正常運作的問題。
1. **ACSD-51892**：修正部署期間設定檔案載入多次的效能問題。

使用左側的功能表，導覽至特定的修補程式頁面。
