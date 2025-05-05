---
title: 受限的管理員存取權造成效能問題
description: 本文提供解決方案，適用於使用使用手冊中[角色範圍受網站限制的管理員角色](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)而效能受到負面影響的情況。
exl-id: da168d6b-9cda-41e2-aa3c-f3f0dccc803d
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# 受限的管理員存取權造成效能問題

本文提供解決方案，適用於使用使用使用手冊中受網站[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles#step-2assign-resources)限制角色範圍的管理員角色，而效能受到負面影響的情況。

## 受影響的產品和版本

* Adobe Commerce內部部署2.2.x、2.3.x
* 雲端基礎結構上的Adobe Commerce 2.2.x、2.3.x

## 問題

當具有受網站限制角色範圍的管理員使用者在管理員面板中執行操作（包括登入、儲存產品等）時，Adobe Commerce會重建儲存的快取。 重建快取對效能造成負面影響，並可能導致網站中斷，尤其是在業務和/或高流量時段。

Adobe Commerce 2.2.10和2.3.3已修正此問題。

## 解決方案

以下是可避免問題的選項：

* 將Adobe Commerce應用程式版本升級至2.2.10或2.3.3。 (如需指示，請參閱我們的開發人員檔案中的[在雲端基礎結構版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)上升級Adobe Commerce)。
* 儘可能避免依網站限制管理員使用者角色範圍。
* [提交Magento支援票證](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以請求修補程式（如果可用）。

## 相關閱讀

* 使用手冊中的[使用者角色](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles)。
