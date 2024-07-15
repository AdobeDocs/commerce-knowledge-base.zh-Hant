---
title: Adobe Commerce的升級相容性工具1.1.0
description: 升級相容性工具1.1.0是命令列工具，可分析安裝在Adobe Commerce自訂執行個體中的所有模組和核心程式碼，以針對特定版本檢查該執行個體。 它會傳回在升級至最新版Adobe Commerce之前必須解決的嚴重錯誤、問題和警告清單。
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Adobe Commerce的升級相容性工具1.1.0

升級相容性工具1.1.0是命令列工具，可分析安裝在Adobe Commerce自訂執行個體中的所有模組和核心程式碼，以針對特定版本檢查該執行個體。 它會傳回在升級至最新版Adobe Commerce之前必須解決的嚴重錯誤、問題和警告清單。

## UCT 1.1.0有哪些新功能？

升級相容性工具1.1.0引進重大改善，包括：

* **驗證核心檔案修改**：Adobe強烈建議不要自訂核心產品程式碼。 在此版本中，我們為客戶和合作夥伴新增了查核點，以識別核心程式碼的任何修改，並及早及快速地瞭解修改的影響。 在開發流程中新增此工具，可協助合作夥伴和商戶主動找出問題、避免未來升級期間發生問題，並降低總體擁有成本(TCO)。
* **將報告匯出至JSON檔案**：這項改善是在社群回饋意見後實施的。 現在，當您執行工具時，所有已識別問題的詳細資訊都會匯出到JSON檔案，以便使用者無需再次執行工具即可讀取、共用和管理結果。
* **已改善的VBE驗證**： VBE （廠商套件擴充功能）不是Adobe Commerce核心程式碼的一部分，但已通過Adobe測試及支援。 透過此更新，我們現在使用與核心程式碼相同的方法驗證VBE。 這項改善將有助使用者清楚瞭解與自訂專案和核心程式碼/VBE相關的問題。
* **提供錯誤碼**：我們引進了錯誤碼，以協助使用者識別、瞭解及解決升級期間的問題。 錯誤和警告訊息會提供清楚的說明和建議的解決方案。
* **僅列出嚴重問題的可能性**：透過此功能，使用者將能夠僅專注於嚴重問題，並在升級時產生問題。
* **兩個版本之間的差異問題**：透過我們的社群成員提出的這項改善措施，UCT使用者將能夠取得兩個版本之間的差異問題，這讓他們只能專注於針對他們要升級的目標版本所引進的新問題。

## 工具可以比較哪些版本？

您可以使用工具來比較任何2.x版本。

## 誰可以使用升級相容性工具1.1.0？

Adobe Commerce客戶。

## 安裝升級相容性工具1.1.0

如需安裝步驟，請參閱我們的開發人員檔案中的Adobe Commerce： [升級相容性工具>安裝](https://devdocs.magento.com/upgrade-compatibility-tool/install.html)。 如需使用工具的先決條件，請參閱開發人員檔案中的Adobe Commerce： [升級相容性工具](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html)。

## 每個問題旁邊的數目是多少？

這是錯誤訊息參考，提供執行升級相容性工具時可能發生的錯誤相關資訊。

升級相容性工具錯誤訊息依層級（嚴重問題、錯誤和警告）和型別(核心程式碼、自訂程式碼和GraphQL結構描述)進行分類。 每種型別都包含下列資訊：

* 錯誤代碼： Adobe Commerce指派的錯誤訊息識別碼。
* 錯誤說明：總結錯誤原因的說明。
* 錯誤建議動作：如果適用，提供疑難排解及解決錯誤的指引。
* 在[錯誤訊息參考頁面](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html)上列出並描述代碼。

## 我可以在哪裡分享關於該工具的意見回饋？

您可以在[#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) Slack頻道上聯絡UCT團隊。 我們期待您提供意見與建議，以改進此工具。

## 相關閱讀

* Adobe Commerce部落格： [介紹升級相容性工具(Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce：在開發人員檔案中[升級相容性工具](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html)。
