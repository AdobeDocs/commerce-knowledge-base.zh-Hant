---
title: Adobe Commerce安全性掃描工具疑難排解指南
description: 瞭解如何針對Adobe Commerce和Magento Open Source的安全性掃描工具的各種問題進行疑難排解。
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 525352027bfa4a8728bdbbfe61af3dca5dbb18f9
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Adobe Commerce安全性掃描工具疑難排解指南

瞭解如何針對Adobe Commerce和Magento Open Source的安全性掃描工具的各種問題進行疑難排解。

## 問題：無法提交網站

安全性掃描工具要求您先證明網站的所有權，才能將網域新增至安全性掃描工具。 您可以使用HTML註解或`<meta>`標籤將確認代碼新增至您的網站來執行此操作。 HTML註解應放置在`<body>`標籤內，例如在頁尾區段。 `<meta>`標籤應放置在頁面的`<head>`區段內。

當安全性掃描工具無法確認商戶的網站擁有權時，商戶會遇到一個常見問題。

如果您收到錯誤且無法送出您的網站進行掃描，請參閱我們的支援知識庫中的將網站新增至安全性掃描時[錯誤訊息](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md)疑難排解文章。

## 問題：安全性掃描工具產生的空白報表

您從安全性掃描工具取得空白的掃描報告，或取得僅包含一個錯誤的報告，例如&#x200B;*安全性工具無法連線到基礎URL*，或在提供的URL *上找不到* Magento安裝。

### 解決方案

1. 檢查52.87.98.44、34.196.167.176和3.218.25.102 IP是否未在80和443連線埠上封鎖。
1. 檢查提交的重新導向URL （例如`https://mystore.com`重新導向至`https://www.mystore.com`或反之，或重新導向至其他網域名稱）。
1. 調查遭拒絕/未履行請求的WAF/Web伺服器存取記錄檔。 HTTP 403 `Forbidden`和HTTP 500 `Internal server error`是造成產生空白報表的常見伺服器回應。 以下是封鎖使用者代理程式請求的確認程式碼範例：

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

您也可以在我們的支援知識庫中看到[安全性掃描工具報告為空白](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md)文章，以取得詳細資訊。

## 問題：安全性問題已解決，但在掃描中仍顯示為易受攻擊

您已解決安全性問題，並期待安全性掃描顯示您不再容易受到新解決問題的攻擊。 相反地，您會發現安全性掃描產生的報告仍然報告您容易受到安全性問題的攻擊。

### 原因

僅針對`active`和`live`雲端專案收集雲端執行個體中繼資料，而且不是即時程式。

統計資料收集指令碼每天執行一次，之後安全性掃描工具必須擷取新資料。

預期的同步處理週期延遲最長為一週，最少需要24小時。

檢查中可能會顯示下列狀態：

1. **通過**：安全性掃描工具已掃描您更新的資料並核准變更。
1. **未知**：安全性掃描工具還沒有您網域的資料；請等候下一個同步處理週期。
1. **失敗**：如果狀態顯示失敗，您必須修正問題（啟用2FA、變更管理員URL等） 並等待下一個同步處理週期。

如果對執行個體進行變更後24小時已經過去，且變更未反映在安全性掃描報告中，您可以[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。 提交票證時提供存放區URL。

## BotNet可疑失敗

您會收到有關「BotNet可疑」失敗的通知。

### 原因

1. 商店網域名稱在2019年進入「潛在BotNet參與者清單」，它公開顯示管理面板、下載者或RSS功能，和/或其URL已在CC略過論壇中提及。
1. 此警示可能是由於存放區遭到危害和/或惡意程式碼的跡象所造成，例如頁面上所顯示的JavaScript。
1. 這不一定是持續性的問題。 如果商店之前遭到破壞，其主機名稱仍可作為「受害者」名稱在黑暗的網頁上浮動。
1. 也有可能不是因為Adobe Commerce，而是因為系統損毀（在作業系統層級）所造成。

### 解決方案

1. 檢查新建立的SSH帳戶、檔案系統變更等。
1. 執行安全性審查。
1. 請檢視Adobe Commerce版本並升級，尤其是如果它仍在執行已不支援的Magento1。
1. 如果問題仍然存在，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)並提供商店URL。

## 問題：危害性插入失敗

您收到有關「洩露插入」失敗的錯誤。

### 解決方案

1. 檢閱「安全性掃描工具」報告中指示的指令碼。
1. 檢閱首頁來源內文以瞭解內嵌指令碼插入。
1. 執行系統組態變更檢閱，尤其是在`footer`區段值中的自訂`HTML head`和`Miscellaneous HTML`。
1. 執行程式碼和資料庫審查，以找出不熟悉的變更和插入的惡意程式碼跡象。

如果上述方法都沒有幫助，請[提交支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，並提供報表中的商店URL和錯誤訊息。

## 常見問題

### 安全性掃描是否會影響我網站的效能？

不適用。 安全性掃描會像單一使用者一樣，逐一處理所有要求。 因此，安全性掃描不應影響網站效能。

### Adobe Commerce會將安全性掃描報告保留多長時間？

您可以從終端產生前10個報表。 如果需要較舊的報告，請聯絡Adobe Commerce支援。

### 提交支援票證時需要哪些資訊？

請務必提供網域名稱。

### 如果我從掃描工具掃描中移除存放區，會發生什麼事？

如果您刪除存放區提交，所有相關的資料（包括掃描報告）都會被刪除。 這個操作是不可逆的。 刪除存放區網域後提交會建立「新」提交。
