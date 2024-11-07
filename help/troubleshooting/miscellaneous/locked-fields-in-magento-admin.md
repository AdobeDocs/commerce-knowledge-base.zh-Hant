---
title: Commerce管理員中的鎖定（灰色）欄位
description: 本文提供您無法修改Commerce管理員中欄位時的解決方案。
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Commerce管理員中的鎖定（灰色）欄位

本文提供您無法修改Commerce管理員中鎖定（灰色）欄位時的解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.x、2.4.x
* 雲端基礎結構上的Adobe Commerce 2.3.x、2.4.x

## 問題

將組態的變更儲存到`app/etc/env.php`或`app/etc/config.php`後，您就無法在Admin中修改設定。

<u>要再現的步驟</u>：

注意：此為範例 — 問題會影響所有已儲存的設定。

1. 商家在終端機中使用下列命令儲存其傳遞方法認證： `./vendor/bin/ece-tools config:dump`。 這會將認證儲存在`app/etc/env.php`檔案中。
1. 商家稍後會嘗試變更認證。

<u>預期結果</u>：

商家可以在「管理員」欄位設定中設定值並儲存。

<u>實際結果</u>：

管理員中的欄位已鎖定，或值可以變更但不會儲存在管理員中。

## 原因

當設定儲存至`env.php`或`config.php`時，您將無法在Admin中修改設定。 若要允許編輯設定，您必須從`env.php`或`config.php`移除設定。

## 解決方案

確定組態尚未儲存至`app/etc/env.php`或`app/etc/config.php`。 如果已儲存，請嘗試下列步驟：

* `config.php` — 移除設定，然後重新部署。
* `env.php` — 直接在伺服器上修改此專案並移除設定，然後執行`bin/magento app:config:import`。

## 相關閱讀

* 在開發人員檔案中[匯出設定](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration)。
* 在開發人員檔案中[設定組態值](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values)。
* 雲端基礎結構上的[Adobe Commerce：在我們的支援知識庫中使用組態管理](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)，減少部署停機時間。
