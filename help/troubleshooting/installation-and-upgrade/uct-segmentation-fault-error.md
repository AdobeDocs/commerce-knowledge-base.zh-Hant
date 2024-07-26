---
title: 疑難排解升級相容性工具錯誤
description: 本文會說明您在使用升級相容性工具時可能遇到的錯誤，並提供解決方案來修正這些錯誤，以便您能夠成功執行該工具。
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 疑難排解升級相容性工具錯誤

本文會說明您在使用升級相容性工具時可能遇到的錯誤，並提供解決方案來修正這些錯誤，以便您能夠成功執行該工具。

## 受影響的產品和版本

* [升級相容性工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html)與2.3.0以後的Adobe Commerce版本相容。

## 分段錯誤錯誤

<u>原因</u>：

當兩個模組具有相同名稱時，升級相容性工具會顯示分段錯誤錯誤。

<u>解決方案</u>：

若要避免此錯誤，建議將模組的路徑指定為引數：

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> 如果程式碼基底在方法之間包含循環相依性，則升級相容性工具可能無法分析程式碼基底。

## 空輸出

<u>要再現的步驟</u>：

1. 如果執行此命令後：

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. 唯一的輸出為`Upgrade compatibility tool`：

   ```bash
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>原因</u>：

可能的原因是PHP記憶體限制。

有兩種可能的解決方案可避免此PHP記憶體限制。

<u>解決方案1</u>：

將`memory_limit`設定為`-1`以覆寫記憶體限制：

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION`是您要與Adobe Commerce執行個體比較的目標Adobe Commerce版本。

<u>解決方案2</u>：

新增`-m`選項可讓升級相容性工具獨立分析每個特定模組，以避免在您的Adobe Commerce執行個體中遇到兩個名稱相同的模組。

這個命令選項也允許升級相容性工具分析包含數個模組的資料夾：

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

如需命令列介面選項的詳細資訊，請參閱[在命令列介面中執行工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html)頁面。
