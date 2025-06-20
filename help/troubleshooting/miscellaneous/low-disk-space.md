---
title: 磁碟空間不足
description: 本文針對雲端基礎結構上Adobe Commerce的特定環境空間不足的情況提供解決方案。
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# 磁碟空間不足

本文針對雲端基礎結構上Adobe Commerce的特定環境空間不足的情況提供解決方案。

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 問題

在可寫入目錄的磁碟上，您的磁碟空間已用完。 一個症狀可能是[停滯部署](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-26878)。

若要檢查磁碟使用量，請執行以下命令：

```bash
df -h var/
```

## 原因

`var`目錄通常是佔用大量空間的目錄，而且可以輕易清除。

Adobe Commerce會將所有記錄檔儲存在`var`目錄中。 會建立新記錄檔，並每天封存舊記錄檔。 但是，如果產生的錯誤數量持續增加，記錄檔會佔用越來越多的空間。

自訂匯入/匯出檔案也儲存在`var`目錄中，如果檔案數量增加，則會佔用空間。

## 解決方案

解決方案選項：

* 檢查是否有大型記錄檔，並調查其大型的原因，修正產生大量記錄輸出的問題。
* 清除`var`目錄。
* 設定cron工作以追蹤`var`目錄的大小並加以清除。
* 如果您有未使用的磁碟空間，請分配更多磁碟空間。 （如需如何檢查您的空間限制的詳細資訊，請參閱下節。）
   * 對於入門計畫、所有環境和Pro計畫整合環境，如果您有一些未使用的磁碟空間，則可以配置磁碟空間，如[管理磁碟空間：配置磁碟空間](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space)中所述。
   * 對於Pro計畫測試和生產環境，如果您有一些未使用的磁碟空間，請聯絡支援以分配更多磁碟空間。
* 如果您已達到空間限制，但仍遇到空間不足問題，請考慮購買更多磁碟空間，並聯絡Adobe帳戶團隊以取得詳細資料。

### 檢查磁碟空間限制

若要檢查您在雲端基礎結構環境中每個Adobe Commerce有多少空間：

1. 登入[雲端主控台](https://console.adobecommerce.com)。
1. 在&#x200B;**[!UICONTROL All projects]**&#x200B;儀表板上，選取相關的專案。 左角顯示磁碟空間可用性。

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
