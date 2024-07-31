---
title: '[!DNL Live Search]儀表板和搜尋結果排名不正確'
description: 如果 [!DNL Live Search] 儀表板中的資料不正確，或搜尋結果的排名與您的預期不符，本文會提供疑難排解資訊。
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# [!DNL Live Search]儀表板和搜尋結果排名不正確

如果您注意到[!DNL Live Search]儀表板中顯示的資料不正確，或搜尋結果](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)的[排名不是您預期的，請參閱以下可能的原因：

* `productView`個事件中產品內容的`topLevelSku`欄位遺失。 這會導致空白的轉換和其他非預期的量度。

* `add-to-cart`事件未設定並填入`productContext`欄位。

* 環境型別不正確。 例如，如果環境設定為&#x200B;*[!UICONTROL Testing]*&#x200B;而非&#x200B;*[!UICONTROL Production]*。 如需詳細資訊，請參閱[店面內容](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)。

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md)事件中缺少搜尋結果內容。
