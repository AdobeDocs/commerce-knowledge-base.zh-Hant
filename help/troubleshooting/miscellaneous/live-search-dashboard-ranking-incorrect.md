---
title: '[!DNL Live Search]儀表板和搜尋結果排名不正確'
description: 如果[!DNL Live Search]儀表板中的資料不正確，或是搜尋結果的排名與您的預期不符，本文會提供疑難排解資訊。
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# [!DNL Live Search]儀表板和搜尋結果排名不正確

如果您注意到[!DNL Live Search]儀表板中顯示的資料不正確，或搜尋結果[&#128279;](https://experienceleague.adobe.com/zh-hant/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies)的排名不是您預期的，請參閱以下可能的原因：

* `productView`個事件中產品內容的`topLevelSku`欄位遺失。 這會導致空白的轉換和其他非預期的量度。

* `add-to-cart`事件未設定並填入`productContext`欄位。

* 環境型別不正確。 例如，如果環境設定為&#x200B;*[!UICONTROL Testing]*&#x200B;而非&#x200B;*[!UICONTROL Production]*。 如需詳細資訊，請參閱[店面內容](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md)。

* [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md)事件中缺少搜尋結果內容。
