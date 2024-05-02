---
title: Adobe Commerce發行版本更新生命週期原則的常見問題集
description: 「Adobe Commerce為次要版本提供品質修正，從下一個次要軟體版本正式發行之日起至少12個月。 我們在此期間提供品質修正的方式正在改變：'
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Adobe Commerce發行版本更新生命週期原則的常見問題集

## 有什麼改變？

Adobe Commerce為次要版本提供品質修正，從下一個次要軟體版本正式發行之日起至少12個月。 我們在此期間提供品質修正的方式正在改變：

* **先前原則：** 目前，在12個月EOS視窗中前一行的品質修正會透過我們的每季修補程式發行版本提供，因此每季修補程式是安全性+品質的組合。
* **新原則：** 從2.4版開始，最新的次要發行版本行，先前支援的發行版本行(2.3)的發行修補程式將改成僅限安全性。 次要版本（如2.4）和後續新的次要版本行發行後，我們仍會在12個月的時段內提供先前支援行的品質修正，但這些修正將透過以下網址提供： [品質修補工具(QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 並且只關注重大問題。

## 此原則何時生效？

Adobe Commerce 2.3.6預計於2020年10月15日發行，並計畫成為Adobe Commerce 2.3的最後一個包含品質+安全性的修補程式版本。 在2.3.6之後，2.3.x產品線將變成僅限安全性使用，而2.3的關鍵品質問題可透過QPT修正。

>[!NOTE]
>
>我們唯一要發行2.3完整版的時候，就是我們需要維持技術棧疊的合規性，例如PHP或Elasticsearch。 這將會在2021年第2季進行，並且強制更新PHP 7.4，我們將將此行增加到2.3.7。如需詳細資訊，請參閱 [Adobe Commerce 2.3.x版本行的PHP 7.4支援](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog文章。

## 什麼是僅限安全性的版本？

僅限安全性的發行版本僅包含安全性修正，未修正品質。 不過請注意，當我們認為這些是執行Adobe Commerce絕對重要的問題時，僅限安全性的發行版本可能包含特定的修補程式。

## 最新的一行是否仍會有安全性限定的版本（截至發佈日期，2.4）？

Adobe將繼續擁有最新版本行的僅限安全性版本。 這些專案的程式概述於 [推出新的僅限安全性修補程式發行版本](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) DevBlog文章。

## 什麼是品質修補工具？

請參閱 [已發行品質修補程式工具：可自助提供品質修補程式的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 支援知識庫中的文章。

## 誰應該考慮使用此新原則？

新政策旨在為商家建立路徑，策略性地規劃年度Adobe Commerce開發成本，同時允許他們在這些策略週期中維持安全性和關鍵品質。 關心其他專案的安全性，並且通常對較舊且支援的系列的穩定性感到滿意的商家，也可以使用它。 商家可能會發現更容易針對這些升級進行規劃和預算，因為他們將更容易預測。

## 商家是否仍應升級至最新系列？

歸根結底，所有商戶仍應優先規劃，以及時採用最新的Adobe Commerce產品線。 新的「僅限安全性」系列和QPT工具的用意並非要取代商家的策略升級藍圖；相反地，它們為商戶提供了規劃升級藍圖的靈活性，以及快速回應安全性/品質問題的方式，而不必實作整個升級。

## 如何取得非最新行之受支援次要版本的品質修正？

修正可透過 [品質修補工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## 我如何取得最新產品線的品質修正？

目前這行將具有每季更新中的品質。 在發行之間，如果您聯絡支援人員以尋求最近明細行的修正，他們將透過QPT提供該修正。 然後升級到內有該修正的版本後，將透過每季修補程式套用。

## 非最新一行的受支援次要版本將修正哪些品質問題？

只有中斷核心流程的主要品質問題才會在上一行(2.3)中修正，並透過QPT傳遞。

## 任何品質修正是否會在非最新版本支援的次要版本上成為季度發行的一部分？

是，作為僅限安全性產品線的一部分，我們在該產品線中發佈Adobe所稱的「修補程式」，這些是影響Adobe Commerce應用程式的高度關鍵性問題。

## 安全性改善與QPT是否會同時提供？

僅限安全性的明細行會遵循每季發行排程，並以 — p1命名法發行。 範例2.3.6-p1。 品質將會在發現並修正品質問題時隨選發行，並透過QPT提供。

## 如果我有品質問題，但在非最新行或QPT的支援次要版本中無法解決，該怎麼辦？

前一行僅提供安全性，表示主要優點在於保持安全性。 只有破壞核心流程之主要問題的修補程式，才能透過QPT取得。

不會影響核心流程或具有因應措施的問題將僅在最近一行中修正。 Adobe鼓勵想要進行關鍵和非關鍵修正的使用者移至最新一行。

## 如果商戶在安全性支援終止前仍維持在安全性專線上，升級費用會比較高還是比較困難？

理論上來說，只要商戶沒有採用大量品質修補程式，在開發時間方面，他們的成本應該相等。 如果商家透過QPT工具發現他們需要或想要不只幾個修補程式，建議他們優先升級至最新版Adobe Commerce。 如果採用大量的「品質修補程式」，而不是升級至目前的Adobe Commerce版本，一旦僅限安全性的支援服務終止，可能會增加開發成本及升級的複雜性。

## 為何要限制透過QPT提供的品質修補程式數量？

透過套用許多個別品質修正，您能讓Adobe Commerce程式碼更複雜。 當升級至最新的版本行時，增加的複雜性可能會導致無法預測的變更。 因此我們建議謹慎使用QPT，僅針對最關鍵的修正專案。

## 技術棧疊的合規性如何？

在發行版本的生命週期中，將會更新各種技術棧疊，例如PHP或Elasticsearch，這些技術棧疊需要升級才能保持合規性。 我們會儘可能通知商家，這些商品即將推出。

注意：在2021年第2季，我們需要更新2.3.x線上的PHP和Redis以保持相容。 這會使該行增加到2.3.7。如需詳細資訊，請參閱 [Adobe Commerce 2.3.x版本行的PHP 7.4支援](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) DevBlog文章。
