---
title: Adobe Commerce支援知識庫
description: 疑難排解與維護Commerce商店所需瞭解的一切。
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---

# Adobe Commerce支援知識庫

>[!NOTE]
>
>Adobe Commerce支援知識庫指南即將重組，其內容會移至Adobe Experience League內的其他位置。 與此同時，我們將繼續維護並更新本指南中的內容。

![知識庫首頁](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

此知識庫中的資訊是設計成補充[Adobe Commerce開發人員檔案](https://developer.adobe.com/commerce/docs)和[Adobe Commerce商家指南](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)，以及其他Adobe Commerce出版物。 內容涵蓋疑難排解和最佳作法、發佈公告、回答常見問題，並強調官方檔案（出於任何原因）未提及的特定案例。

## 此知識庫包含哪些內容？

| 類別 | 說明 |
| --- | --- |
| [支援工具](/help/support-tools/overview.md) | 透過Adobe Commerce提供的各種支援工具，改善您的電子商務商店體驗。 我們提供個人化的最佳實務、診斷和監控工具，以及有關您網站的最相關資訊。 |
| [公告](/help/announcements/overview.md) | 從 Adobe Commerce 團隊取得重要更新。 |
| [疑難排解](/help/troubleshooting/overview.md) | 從Adobe Commerce支援團隊取得自助解決方案和修補程式。 |
| [說明中心使用手冊](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | 瞭解如何有效管理支援票證、授予共用存取許可權及瀏覽知識庫。 |
| [操作說明](/help/how-to/overview.md) | 從Adobe Commerce支援團隊取得清楚的逐步指示。 |
| [常見問題集](/help/faq/overview.md) | 尋找有關Adobe Commerce政策、策略的常見問題，以及有關Adobe Commerce功能的細節。 |

## 新增功能

<table style="width:100%">
  <tr>
    <th style="width:70%">說明</th>
    <th style="width:15%">型別</th>
    <th style="width:15%">日期</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">安全性掃描工具傳回「無法判斷您的伺服器是否使用2FA」：</a>若要解決錯誤，請檢查<code>Magento_TwoFactorAuth</code>模組是否已停用。 若要通過檢查，通常應該啟用。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632：每次嘗試訂購時儲存的地址：</a> ACSD-60632修補程式修正每次嘗試訂購時儲存新地址的問題，無論是否成功建立訂單。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.51時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326：關於客戶退貨狀態的GraphQL查詢發生錯誤：</a> ACSD-60326修補程式修正了GraphQL查詢中針對客戶退貨狀態發生錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.51時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925：在GraphQL中依位置排序媒體集中的專案：</a> ACSD-59925修補程式修正了媒體集中的專案未依位置排序，導致顯示順序不正確的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.52時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322：未指派給共用目錄的產品包含在XML Sitemap：</a> ACSD-61322修補程式修正未指派給預設（一般）群組之共用目錄的產品/類別仍包含在XML Sitemap中的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.52時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590：增強Bestsellers彙總每日報表產生的效能：</a> ACSD-60590修補程式修正Bestsellers彙總每日報表需要大量時間才能產生大量訂購的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.52時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865：由於產品數量不足，購物車價格規則無法取消先前的規則：</a> ACSD-59865修補程式修正了<em>固定金額折扣</em>、<em>產品價格折扣百分比</em>和<em>購買X取得Y</em>購物車價格規則不再取消先前規則動作的問題。 <em></em>安裝[!DNL Quality Patches Tool (QPT)] 1.1.52時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">在Admin中篩選訂單時發生錯誤：</a>本文針對Adobe Commerce問題提供修補程式，當嘗試在Admin中依日期篩選訂單時發生錯誤，顯示訊息： <em>完整性條件約束違規： 1052資料行'created_at' where子句模稜兩可</em>。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce：在內容安全性原則(CSP)限制模式下，結帳頁面出現內嵌JavaScript問題：</a>本文會針對啟用<strong>CSP限制模式</strong>時，透過Adobe Commerce 2.4.7中的Adobe Commerce Admin和Google Tag Manager新增自訂JavaScript，針對結帳時遇到的問題，提供詳細的說明和解決方案。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195：購物車GraphQL請求無法在最終頁面上傳回專案：</a> ACSD-61195修補程式修正了在購物車GraphQL請求的最後一頁未傳回購物車專案的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.51時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514：使用頁面產生器的Admin中的Forms在瀏覽器控制檯中擲回錯誤：</a> ACSD-59514修補程式修正了使用頁面產生器的Admin中的表單擲回錯誤<em>頁面產生器在提交表單後持續呈現5秒而未釋放瀏覽器控制檯中的鎖定</em>的問題，且無法儲存變更。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538：如果在<em>所有商店檢視中停用產品，則屬性無法正確顯示</em>：</a> ACSD-60538修補程式修正了以下問題：如果產品在<em>所有商店檢視</em>中停用，並且只在特定商店檢視範圍中啟用，則產品屬性無法在GraphQL回應中正確顯示，導致產品無法正確顯示。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.51時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352：透過GraphQL API傳回預設存放區的傳回屬性標籤：</a> ACSD-58352修補程式修正了在要求標頭中指定非預設存放區檢視時，透過GraphQL API傳回預設存放區的傳回屬性標籤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">您的帳戶中缺少<em>Switch帳戶</em>下拉式清單：</a>本文針對Adobe Commerce問題提供解決方案，您的帳戶中缺少<em>Switch帳戶</em>下拉式清單，而且您失去代表商家提交票證的存取權。
    </td>
    <td>新增文章</td>
    <td>2024年10月17日</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979：刪除中繼更新後移除的產品影像：</a>ACSD-56979修補程式修正刪除中繼更新後移除產品影像的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.49時，即可使用此修補程式。  
    </td>
    <td>新增文章</td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210：存放區檢視特定範圍屬性覆寫全域值：</a> ACSD-48210修補程式修正了在特定存放區檢視中更新<em>網站範圍</em>屬性時覆寫全域範圍中屬性值的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280： 2.4.4-pX安裝中的ReflectionUnionType：：getName()錯誤：</a> ACSD-59280修補程式修正了在安裝2.4.4-pX版本期間發生呼叫未定義方法<code>ReflectionUnionType::getName()</code>錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887：客戶購物車在客戶工作階段過期後會被清除：</a> ACSD-54887修補程式修正了客戶工作階段過期後客戶購物車會被清除的問題，並啟用了<em>永久購物車</em>。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303：啟用HTML縮制後已解決管理員訂單放置問題：</a> ACSD-60303修補程式修正啟用HTML縮制後無法放置管理員訂單的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045： URL重寫造成在<em>網站根目錄</em>從階層取消核取後出現無限頁面回圈：</a> ACSD-57045修補程式修正URL重寫造成在<em>網站根目錄</em>從階層取消核取後出現無限頁面回圈的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.49時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446：透過GraphQL刪除具有子項使用者或團隊的團隊會產生無資訊的錯誤訊息：</a> ACSD-58446修補程式修正了Adobe Commerce的問題，也就是透過GraphQL刪除具有子項使用者或團隊的團隊時，會傳回與UI不一致的無資訊錯誤訊息。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.49時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735：未正確設定的YouTube API金鑰會導致在商店檢視層級新增視訊時發生錯誤：</a> ACSD-58735修補程式修正了在商店檢視層級新增YouTube視訊時，錯誤YouTube API金鑰設定會導致錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.49時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086：來自啟用條款與條件之非預設網站的訂單處理不正確：</a> ACSD-57086修補程式修正來自啟用條款與條件之非預設網站的訂單未正確處理的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.49時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141：如果已啟用L2 Redis快取，PHPSESSID會在登入客戶的POST要求上重新產生：</a> ACSD-58141修補程式修正了以下問題：如果已啟用L2 Redis快取，且客戶已從Admin更新，則PHPSESSID會在登入客戶的POST要求上重新產生。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790：修正Chrome上行動檢視中產品詳細資料頁面影像的縮放夾功能：</a> ACSD-58790修補程式修正Chrome上行動檢視中的影像未如預期放大影像的Adobe Commerce問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。 
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442：修正寬度768px的裝置被視為行動裝置，導致功能表和標題載入行動檢視而非桌上型電腦的問題：</a> ACSD-58442修補程式修正Adobe Commerce裝置寬度768px被視為行動裝置，導致功能表和標題載入行動檢視而非桌上型電腦的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.50時，即可使用此修補程式。
    </td>
    <td>新增文章 </td>
    <td>2024年10月17日</td>
  </tr>
</table>
