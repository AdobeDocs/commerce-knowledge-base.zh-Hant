---
title: 解決不合法的位移錯誤
description: 本文提供在Adobe Commerce 2.1或更新版本中，當您在Commerce管理員中建立新產品時，收到「解決不合法的位移錯誤」的解決方案。
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 解決不合法的位移錯誤

本文提供在Adobe Commerce 2.1或更新版本中，當您在Commerce管理員中建立新產品時，收到「解決不合法的位移錯誤」的解決方案。

在Adobe Commerce 2.1或更新版本中，在Commerce Admin中建立新產品時，可能會顯示下列錯誤：

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## 詳細資料

Adobe Commerce 2.1和更新版本在`Magento\Framework\Api\ExtensionAttributesFactory.php`的[`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73)方法的`getDocComment`驗證呼叫中使用PHP程式碼註解。

如果您已啟用PHP OPcache （我們建議使用），則會顯示此錯誤，因為預設會停用OPcache設定[`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments)。

## 因應措施

若要解決此問題，請找出您的OPcache組態設定並啟用`opcache.save_comments`，如下所示：

### 步驟1：找出您的OPcache設定

#### 若要尋找OPcache組態設定：

PHP OPcache設定通常位於`php.ini`或`opcache.ini`中。 位置可能取決於您的作業系統和PHP版本。 OPcache組態檔可能有`[opcache]`區段或類似於`opcache.enable`的設定。

請使用下列准則來尋找它：

* Apache網頁伺服器： <br>

對於具有Apache的Ubuntu，OPcache設定通常位於`php.ini`。<br>
對於具有Apache或nginx的CentOS，OPcache設定通常位於`/etc/php.d/opcache.ini`。<br>
如果沒有，請使用下列命令來尋找它：

```bash
    $ sudo find / -name 'opcache.ini'
```

* PHP-FPM的nginx Web伺服器： `/etc/php5/fpm/php.ini`。

如果您有多個`opcache.ini`，請修改全部。


### 步驟2：啟用`opcache.save_comments`

1. 在文字編輯器中開啟OPcache設定檔案。
1. 找到`opcache.save_comments`並取消註解（如有必要）。
1. 請確定它的值設定為`1`。
1. 儲存變更並退出文字編輯器。
1. 重新啟動您的網頁伺服器：

   * Apache， Ubuntu： `service apache2 restart`
   * Apache， CentOS： `service httpd restart`
   * nginx、Ubuntu和CentOS： `service nginx restart`

1. 重新產生DI組態及所有可自動產生的遺失類別：

```bash
    $ bin/magento setup:di:compile`
```
