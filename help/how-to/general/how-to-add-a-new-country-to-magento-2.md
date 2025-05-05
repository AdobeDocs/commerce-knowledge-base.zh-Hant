---
title: 如何為Adobe Commerce新增國家/地區
description: 本文說明如何新增Adobe Commerce和Zend地區設定資料庫中不存在的國家/地區。 這需要程式碼和資料庫變更，這些變更根據您適用的合約條款構成「客戶自訂」。 請注意，本文包含的範例資料係依「現況」提供，不含任何保固。 Adobe或任何關聯實體均無義務維護、更正、更新、變更、修改或以其他方式支援這些材料。 我們在這裡將說明達成此目標所需完成作業的基本原則。
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# 如何為Adobe Commerce新增國家/地區

本文說明如何新增Adobe Commerce和Zend地區設定資料庫中不存在的國家/地區。 這需要程式碼和資料庫變更，這些變更根據您適用的合約條款構成「客戶自訂」。 請注意，本文包含的範例資料係依「現況」提供，不含任何保固。 Adobe或任何關聯實體均無義務維護、更正、更新、變更、修改或以其他方式支援這些材料。 我們在這裡將說明達成此目標所需完成作業的基本原則。

在此範例中，我們會建立新的Adobe Commerce模組，其資料修補程式會套用於Adobe Commerce安裝或升級流程，並新增抽象國家/地區（國家/地區代碼為XX）至Adobe Commerce。 [Adobe Commerce目錄](https://developer.adobe.com/commerce/php/module-reference/module-directory/)會建立初始國家/地區清單，然後使用安裝修補程式將地區附加至該清單。 本文說明如何建立新模組，以將新國家/地區附加至清單。 您可以檢閱現有Adobe Commerce目錄模組的程式碼以作參考。 這是因為下列範例模組會繼續進行建立國家和地區清單的目錄模組工作，並重複使用Adobe Commerce目錄模組安裝修補程式的部分程式碼。

## 建議檔案

您必須熟悉Adobe Commerce模組開發，才能建立新的模組。

在嘗試建立新模組之前，請參閱開發人員檔案中的下列主題：

* [PHP開發人員指南](https://developer.adobe.com/commerce/php/development/)
* [模組總覽](https://developer.adobe.com/commerce/php/architecture/modules/overview/)
* [建立新模組](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/backend-development/create-module)
* [模組組態檔](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/module-files)

## 必要資訊

新的國家/地區在Adobe Commerce中必須有唯一的名稱、國家/地區ID、ISO2和ISO3代碼。

## 模組結構

在此範例中，我們將建立名為\&#39;ExtraCountries\&#39;的新模組，其目錄結構如下：

（如需模組結構的詳細資訊，請參閱我們的開發人員檔案中的[模組概觀](https://developer.adobe.com/commerce/php/architecture/modules/overview/)）。

<pre>&lt;ExtraCountries>
 |
 &lt;etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 &lt;Plugin>
 | |
 | &lt;Framework>
 |   |
 |   &lt;Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 &lt;Setup>
 | |
 | &lt;Patch>
 |   |
 |   &lt;Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 composer.json
 registration.php</pre>

>[!NOTE]
>
>本文的每個「標題」區段都說明模組結構區段中的檔案。

## ExtraCountries/etc/config.xml

新的模組組態定義於此XML檔案中。 可以編輯以下設定和標籤，以調整新的國家/地區預設設定。

* `allow` — 若要依預設將新新增的國家/地區新增至「允許國家/地區」清單，請將新的國家/地區代碼附加至`allow`標籤內容的結尾。 國家代碼以逗號分隔。 請注意，此標籤會覆寫`Directory`模組組態檔&#x200B;*(Directory/etc/config.xml)* `allow`標籤中的資料，因此我們會重複此處的所有程式碼，並加入新的程式碼。
* `optional_zip_countries` — 如果新新增國家/地區的郵遞區號應為選擇性，請將國家/地區代碼附加至`optional_zip_countries`標籤內容的結尾。 國家代碼以逗號分隔。 請注意，此標籤會覆寫`Directory`模組組態檔&#x200B;*(Directory/etc/config.xml)* `optional_zip_countries`標籤中的資料，因此我們會重複此處的所有程式碼，並加入新的程式碼。
* `eu_countries` — 如果新加入的國家預設必須是歐盟國家清單的一部分，請將國家代碼附加到`eu_countries`標籤內容的末尾。 國家代碼以逗號分隔。 請注意，此標籤會覆寫`Store`模組組態檔&#x200B;*(\_Store/etc/config.xml\_)* `eu_countries`標籤中的資料，因此我們會在此重複所有程式碼並加入新程式碼。
* `config.xml`檔案範例

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

如需模組組態檔的詳細資訊，請參閱我們的開發人員檔案中的[PHP開發人員指南>定義組態檔](https://developer.adobe.com/commerce/php/development/build/required-configuration-files/)。

請注意，這些變更是選用的，只會影響新國家/地區在「允許國家/地區」、「郵遞區號為選用的」和「歐盟國家/地區」清單中的預設所屬國家/地區。 如果從模組結構略過此檔案，仍會新增新的國家，但必須在&#x200B;**管理員** > **商店** > *設定* > **設定** > **一般** > **國家選項**&#x200B;設定頁面中手動設定。

### ExtraCountries/etc/di.xml

`di.xml`檔案會設定物件管理員要插入的相依性。 如需有關`di.xml`的詳細資訊，請參閱我們的開發人員檔案中的<a>PHP開發人員指南> di.xml</a>。

在我們的範例中，如果Zend地區設定程式庫本地化資料中沒有代碼，我們必須註冊`_TranslatedListsPlugin_`，以便將新引進的「國家/地區代碼」轉換成完整的「國家/地區名稱」。

`di.xml`範例

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

在模組註冊檔案中，我們必須指定「Adobe Commerce目錄」模組的相依性，以確保「額外國家/地區」模組會在目錄模組之後註冊及執行。

如需模組相依性的詳細資訊，請參閱開發人員檔案中的[管理模組相依性](https://developer.adobe.com/commerce/php/architecture/modules/dependencies/#managing-module-dependencies)。

`module.xml`範例

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

在`aroundGetCountryTranslation()`外掛程式方法中，我們必須將國家/地區代碼轉譯為完整的國家/地區名稱。 對於在「Zend地區設定資料庫」中沒有與新國家/地區代碼相關聯之完整名稱的國家/地區，這是必要的步驟。

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

此資料修補程式會在Adobe Commerce安裝/升級過程中執行，並將新增國家/地區記錄至資料庫。

請參閱我們的開發人員檔案中的[開發資料和結構描述修補程式](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/)，以取得資料修補程式的詳細資訊。

在下列範例中，您可以看到方法`apply()`的`$data`陣列包含新國家/地區的國家/地區識別碼、ISO2和ISO3代碼，而且此資料正在插入資料庫中。

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

這是registration.php檔案的範例。 若要瞭解模組註冊的詳細資訊，請參閱我們的開發人員檔案中的[PHP開發人員指南>註冊您的元件](https://developer.adobe.com/commerce/php/development/build/component-registration/)。

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

這是composer.json檔案的範例。

若要進一步瞭解composer.json，請參閱我們的開發人員檔案中的[PHP開發人員指南> The composer.json檔案](https://developer.adobe.com/commerce/php/development/build/composer-integration/)。

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## 模組安裝

若要瞭解如何安裝模組，請參閱開發人員檔案中的[模組位置](https://developer.adobe.com/commerce/php/architecture/modules/overview/#module-locations)。

將模組目錄放置到正確位置後，請執行`bin/magento setup:upgrade`以套用資料修補程式並註冊轉譯外掛程式。

您可能需要清除瀏覽器快取，新變更才能運作。
