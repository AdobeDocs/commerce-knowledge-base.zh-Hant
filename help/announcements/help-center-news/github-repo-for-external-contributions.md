---
title: Adobe Commerce支援知識庫開始接受貢獻
description: 自6月15日起，Adobe Commerce支援知識庫團隊開始接受外部Adobe Commerce社群透過[magento/知識庫](https://github.com/magento/knowledge-base) GitHub存放庫提供的直接編輯和新文章貢獻內容！
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Adobe Commerce支援知識庫開始接受貢獻

自6月15日起，Adobe Commerce支援知識庫團隊開始接受外部Adobe Commerce社群透過 [magento/知識庫](https://github.com/magento/knowledge-base) GitHub存放庫！

注意到我們其中一篇文章有錯字或是疑難排解步驟不完整？
您現在可以自行修正並取得貢獻點數！

## Contribute

我們樂於接受各種協助撰寫，從輕微的錯字更正到完整的疑難排解文章。 為這個存放庫貢獻內容會獲得獎勵點數，類似於為Adobe Commerce程式碼和我們的開發人員檔案貢獻內容。 另請參閱 [貢獻獎勵點數](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) 以取得詳細資訊。

### 一般貢獻流程

1. 建立此存放庫復本。
1. 編輯取用的存放庫。
1. 提交提取請求(PR)至此存放庫。
1. 執行測試：
   * Adobe CLA — 確認已簽署Adobe開放原始碼貢獻者授權合約。
   * Markdown Litting測試 — 確認Markdown語法正確。
   * 檔案結構驗證測試 — 確保提交是根據 [必要的檔案結構](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. PR核准流程：
   1. 支援知識庫(KB)作者會在數天的時間範圍內檢閱PR並新增標籤。
   1. 知識庫寫入器可以核准/拒絕/要求變更。
   1. 如果核准，知識庫撰寫器會新增與PR中提供的輸入層級對應的標籤，而內部主題專家(SME)會審閱PR。
   1. SME可以核准/拒絕/要求變更。
1. 完成所有更正後（如果有要求），且知識庫撰寫人員和SME都核准PR後，知識庫撰寫人員就會將內容匯入內部存放庫並內部合併。
1. 此 [magento/知識庫](https://github.com/magento/knowledge-base) repo會在20分鐘內與內部repo同步。
1. 存放庫同步之後，您的PR就會關閉，而您 [貢獻點](#contribution-points).

如需貢獻流程的詳細資訊，請參閱 [投稿人指南](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
如需範本、風格指南和格式指南，請參閱 [檔案](https://github.com/magento/knowledge-base/tree/main/docs).

### 在Github上尋找支援知識庫文章檔案

在支援知識庫(KB)中，文章會以區段來整理，這些區段會以類別下巢狀內嵌。

例如， [如何訂閱AdobeMagento狀態更新](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) 文章屬於「使用方式」類別中的「一般」區段。

您可以在文章頁面的階層連結路徑中看到區段和類別名稱，請參閱下圖：

![類別和區段階層連結](assets/breadcrumbs.png)

文章檔案的編排方式與中的相同 [magento/知識庫](https://github.com/magento/knowledge-base) 存放庫。
所有內容都儲存在 `src` 資料夾，包含類別資料夾和區段的巢狀資料夾；檔案名稱可能與文章標題一致或類似。

您也可以在存放庫內，使用支援知識庫文章中的文字片段作為搜尋字串來搜尋。 當搜尋傳回包含此字串的檔案時，請務必選擇屬於正確區段和類別的檔案。

### 貢獻點

此 [magento/知識庫](https://github.com/magento/knowledge-base) 存放庫與Magento社群工程整合，提供貢獻點與支援。

請參閱 [貢獻點](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) 檔案以瞭解獎勵點數的方式。
