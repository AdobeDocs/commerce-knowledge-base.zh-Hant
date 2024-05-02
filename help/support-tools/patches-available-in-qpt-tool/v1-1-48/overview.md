---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.48呎'
description: 此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.48。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.48

此小節提供中可用修補程式所修正問題的詳細說明。 [!DNL Quality Patches Tool] (QPT) v1.1.48。

QPT v1.1.48包含下列修補程式：

1. **ACSD-55566**：修正的問題： *[!UICONTROL mergeCart mutation]* 失敗並出現 *內部伺服器錯誤* 在合併來源和目的地購物車時，GraphQL的回應中具有相同的套件式專案。
1. **ACSD-56546**：修正可設定和隨附產品顯示為 *[!UICONTROL Out of Stock]* 在店面，當 *[!UICONTROL Display Out of Stock Product]* 設定已停用。
1. **ACSD-56635**：修正使用匯入時，匯入的客戶使用相同電子郵件地址複製的問題 [!UICONTROL Account Sharing] 設為 *[!UICONTROL Global]*.
1. **ACSD-56741**：修正錯誤訊息 *正在嘗試存取型別為null的值上的陣列位移* 期間顯示的 `setup:upgrade` 當資料庫包含與索引機制無關的自訂MySQL觸發程式時，以及 [!DNL MView].
1. **ACSD-57315**：修正中建立新交易的問題 [!DNL PayPal Payflow Pro] 每次 **[!UICONTROL Fetch]** 在的「檢視交易」畫面中按一下按鈕 [!UICONTROL Admin].
1. **ACSD-57337**：修正具有特定網站存取限制的管理員使用者可看見中所有網站的公司的問題。 *[!UICONTROL Companies]* 格線。
1. **ACSD-57394**：修正GraphQL中按多個排序欄位排序的產品不正確問題。
1. **ACSD-57565**：修正的問題： *[!UICONTROL Order]* 在更新時段之前，儀表板會顯示不正確的訂單資訊。 儀表板現在會在首次載入時顯示正確的訂單統計資料。
1. **ACSD-57854**：修正產品GraphQL請求在類別彙總中傳回停用類別的問題。
1. **ACSD-58008**：修正更新排程更新時，若未指定結束日期，會移除分段專案的先前版本的問題。

使用左側的功能表，導覽至特定的修補程式頁面。

