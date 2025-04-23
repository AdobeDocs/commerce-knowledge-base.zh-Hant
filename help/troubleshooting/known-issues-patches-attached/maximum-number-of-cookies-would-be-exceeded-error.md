---
title: Adobe Commerce中超過Cookie最大數量的錯誤
description: 瞭解如何解決發生錯誤的Adobe Commerce問題，說明會超過Cookie的最大數量。
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 在Adobe Commerce中超過&#x200B;*Cookie數量上限*&#x200B;個錯誤

本文提供修補程式，以解決在Adobe Commerce中出現&#x200B;*Cookie數目上限將超過*&#x200B;的錯誤。

## 受影響的產品和版本

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7，並套用下列其中一項修補程式：

* 使用[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)套用MDVA-12304修補程式
* [APSB25-08隔離式安全性修補程式](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [適用於 [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)的雲端修補程式

## 問題

與Adobe Commerce中的Cookie相關的問題導致下列錯誤出現在錯誤記錄中：

*report.WARNING：無法傳送Cookie。 將超過Cookie數目上限。*

### 原因

發生此問題是因為允許的Cookie數目上限設為&#x200B;*50*。

## 解決方案

1. 如果您使用[!DNL Quality Patches Tool (QPT)]套用MDVA-12304修補程式，請移除該修補程式。

   * 針對雲端基礎結構上的Adobe Commerce，請從`.magento.env.yaml`移除修補程式。
   * 針對Adobe Commerce內部部署，請執行以下命令來還原修補程式：

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. 根據您的Adobe Commerce版本套用附加的修補程式：

   * 若為版本2.4.4-p12、2.4.5-p11、2.4.6-p9和2.4.7-p4，請套用[ACSD-64710修補程式](assets/acsd-64710_2.4.5-p11.patch.zip)。

   * 若為版本2.4.4-p13、2.4.5-p12、2.4.6-p10、2.4.7-p5和2.4.8，請套用[ACSD-65562修補程式](assets/acsd-65562_2.4.5-p12.patch.zip)。

### 相關閱讀

* 在Adobe Commerce升級指南中[套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/apply)
* [大規模發佈Adobe Commerce修補程式的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) (在Adobe Commerce實作行動手冊中)
* 雲端指南中Commerce Cloud Commerce Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite)的[發行說明。
