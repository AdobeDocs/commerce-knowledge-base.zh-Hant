---
title: Commerce管理員中的鎖定欄位
description: 本文提供您無法修改Commerce管理員中欄位時的解決方案。
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Commerce管理員中的鎖定欄位

本文提供您無法修改Commerce管理員中欄位時的解決方案。

## 受影響的產品和版本

* Adobe Commerce內部部署2.3.x、2.4.x
* 雲端基礎結構上的Adobe Commerce 2.3.x、2.4.x

## 問題

將您設定的變更儲存到 `app/etc/env.php` 或 `app/etc/config.php`，則您無法修改「管理員」中的設定。

<u>要再現的步驟</u>：

注意：此為範例 — 問題會影響所有已儲存的設定。

1. 商家在終端機中使用以下命令儲存其傳送方法認證： `./vendor/bin/ece-tools config:dump`. 這會將認證儲存在 `app/etc/env.php` 檔案。
1. 商家稍後會嘗試變更認證。

<u>預期結果</u>：

商家可以在「管理員」欄位設定中設定值並儲存。

<u>實際結果</u>：

管理員中的欄位已鎖定，或值可以變更但不會儲存在管理員中。

## 原因

當設定儲存到時 `env.php` 或 `config.php`，您將無法修改管理員中的設定。 若要允許編輯設定，您必須從移除設定 `env.php` 或 `config.php`.

## 解決方案

確認組態尚未儲存至 `app/etc/env.php` 或 `app/etc/config.php`. 如果已儲存，請嘗試下列步驟：

* `config.php`  — 移除設定，然後重新部署。
* `env.php`  — 直接在伺服器上修改此專案並移除設定，然後執行 `bin/magento app:config:import`.

## 相關閱讀

* [匯出設定](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) （位於我們的開發人員檔案中）。
* [設定設定值](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) （位於我們的開發人員檔案中）。
* [雲端基礎結構上的Adobe Commerce：透過設定管理減少部署停機時間](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) 在我們的支援知識庫中。
