---
title: 當雲端基礎結構上的Adobe Commerce中的磁碟空間用完時，安全地刪除檔案
description: 本文提供解決方案，協助您因磁碟空間不足而需要安全地移除檔案。 在考慮此動作之前，請檢閱我們的開發人員檔案中的[管理磁碟空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left)。 如果該文章中的步驟不適合您或者沒有解決問題，請檢視本文中的步驟。
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 86515936f72bbd0a5778cb81f665993ed91e4707
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 當雲端基礎結構上的Adobe Commerce中的磁碟空間用完時，安全地刪除檔案

## 受影響的產品和版本

* 雲端基礎結構上的Adobe Commerce 2.4.2 - 2.4.7
* 這專屬於專用的Pro叢集。 入門和整合環境是單一節點，沒有 `/data/exports` 目錄。

## 磁碟空間不足的跡象

您用盡磁碟空間的跡象可能是部署停滯、磁碟已滿警告以及效能不佳。
若要檢視檔案系統使用的磁碟空間量，請在CLI/終端機中執行以下命令：

`df -h`


## 如何安全地刪除檔案以增加磁碟空間

您可以從應用程式的掛載點刪除檔案，從 `/app` 路徑或至 `/mnt/shared`. 它們是存取相同檔案的兩種不同方式。

>[!WARNING]
>
>**切勿修改或刪除內容`/data/exports`**.
>
>`/data/exports` 是共用檔案系統背後的基礎儲存裝置，由GlusterFS管理。
>
>該處的檔案系統不僅包含檔案內容，還包含有關檔案系統狀態的中繼資料，以允許叢集節點之間的同步。 **直接在此檔案系統中變更或刪除檔案將會損毀共用的檔案系統，需要進行大量的修復或資料復原。**

若要找出可能適合清除的最大檔案，請執行以下命令（在大型或繁忙的專案上，最多可能需要一小時）：

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

指令的輸出將包含已指定大小的最大檔案和目錄清單。

## 相關閱讀

在我們的支援知識庫中：

* [增加雲端整合環境的磁碟空間](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [磁碟空間不足](/help/troubleshooting/miscellaneous/low-disk-space.md)

在我們的開發人員檔案中：

* [管理磁碟空間](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
