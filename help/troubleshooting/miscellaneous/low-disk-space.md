---
title: 磁碟空間不足
description: 本文針對雲端基礎結構上Adobe Commerce的特定環境空間不足的情況提供解決方案。
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 磁碟空間不足

本文針對雲端基礎結構上Adobe Commerce的特定環境空間不足的情況提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，全部 [支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

在可寫入目錄的磁碟上，您的磁碟空間已用完。 一個症狀可能是 [停滯部署](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

若要檢查磁碟使用量，請執行以下命令：

```bash
df -h var/
```

## 原因

此 `var` 目錄通常需要佔用大量空間，而且容易清除。

Adobe Commerce將所有記錄檔儲存在 `var` 目錄。 會建立新記錄檔，並每天封存舊記錄檔。 但是，如果產生的錯誤數量持續增加，記錄檔會佔用越來越多的空間。

自訂匯入/匯出檔案也會儲存在 `var` 目錄，如果數字增加，則取用空格。

## 解決方案

解決方案選項：

* 檢查是否有大型記錄檔，並調查其大型的原因，修正產生大量記錄輸出的問題。
* 清除 `var` 目錄。
* 設定cron工作以追蹤 `var` 目錄並加以清除。
* 如果您有未使用的磁碟空間，請分配更多磁碟空間。 （如需如何檢查您的空間限制的詳細資訊，請參閱下節。）
   * 對於入門計畫、所有環境和Pro計畫整合環境，如果您有一些未使用的磁碟空間，則可以配置磁碟空間，如中所述 [管理磁碟空間：配置磁碟空間](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * 對於Pro計畫測試和生產環境，如果您有一些未使用的磁碟空間，請聯絡支援以分配更多磁碟空間。
* 如果您已達到空間限制，但仍遇到空間不足的問題，請考慮購買更多磁碟空間，並連絡您的Adobe帳戶團隊以取得詳細資料。

### 檢查磁碟空間限制

若要檢查您在雲端基礎結構環境中每個Adobe Commerce有多少空間：

1. 登入 [雲端主控台](https://console.adobecommerce.com).
1. 在 **[!UICONTROL All projects]** 控制面板，選取相關專案。 左角顯示磁碟空間可用性。

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
