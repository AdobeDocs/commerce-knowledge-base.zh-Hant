---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# 知識庫標籤指南

本檔案提供在Adobe Commerce支援知識庫文章中新增標籤的指引。
標籤（也稱為標籤）可改善[Adobe Commerce支援知識庫](https://support.magento.com/hc/en-us)中的搜尋體驗。
標籤會新增到文章檔案之中繼資料區段的「標籤」欄位中，並以逗號分隔，逗號與下一個標籤之間沒有空格。
如需詳細資訊，請參閱[../../.github/CONTRIBUTING.md#metadata]。

## 一般規定

為每篇文章新增下列標籤型別：

* 產品的標籤。 （必要）
* 受影響版本的標籤。 （必要，一般支援相關文章除外）
* 內容型別的標籤。 （必要）
* 主要技術元件的標籤。（如果適用）
* 正在疑難排解/描述之程式/功能的標籤。 （如果適用）
* 修正/說明問題的標籤。 （如果適用）

如需如何為每種標籤型別定義標籤的詳細建議，請參閱以下各節。

## 產品標籤

<table>
<tbody>
  <tr>
    <th>產品名稱</th>
    <th>標籤</th>
  </tr>
  <tr>
    <td>Adobe Commerce （所有部署方法） </td>
    <td>
    「Adobe Commerce，雲端基礎結構，內部部署」
    </td>
  </tr>
  <tr>
    <td>雲端基礎結構上的Adobe Commerce</td>
    <td>
      "Adobe Commerce，雲端基礎結構"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce內部部署</td>
    <td>"Adobe Commerce，內部部署"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence(MBI)</td>
    <td>
        "Magento Business Intelligence，MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>適用於Adobe Commerce的B2B</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>Adobe Commerce的PWA</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Venia店面專案</td>
    <td>「威尼斯」</td>
  </tr>
  <tr>
    <td>品質修補工具，QPT</td>
    <td>「品質修補工具，QPT修補程式」</td>
  </tr>
  </tbody>
</table>

## 產品版本的標籤

* 為每個Adobe Commerce版本新增個別的標籤。 範例： &quot;2.3.7&quot;
* 請勿為間隔新增標籤。
亦即，如果2.3.0-2.3.5受到影響，請新增：「2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2」
不是「2.3.0-2.3.5」
* 請勿新增標籤為.x。範例： &quot;2.3.x&quot;

## 內容型別的標籤（根據類別）

<table>
  <tbody>
    <tr>
      <th>類別</th>
      <th>標籤</th>
    </tr>
    <tr>
      <td>最佳實務</td>
      <td>"best practices" （而非"Best Practice"或"best practice"）</td>
    </tr>
    <tr>
      <td>
        疑難排解
      </td>
      <td>
      "疑難排解"
      </td>
    </tr>
    <tr>
      <td>操作說明</td>
      <td>「如何」</td>
    </tr>
    <tr>
      <td>常見問題集</td>
      <td >「常見問題集」</td>
    </tr>
  </tbody>
</table>

## 主要技術元件的標籤

* 根據元件的正式命名使用大寫。
* 請勿使用同義字，一個元件使用一個標籤。
* 最好使用一個單字標籤，但如果元件名稱包含多個單字，請使用多個單字。 請勿新增問題說明。 也就是說，請改用「Elasticsearch」而非「Elasticsearch問題」。
* 如果內容僅與特定版本的元件相關，請新增包含名稱+版本的標籤。\
  範例：「Elasticsearch5」。 如果它與數個特定版本相關，請新增多個此型別的標籤。 範例：「Elasticsearch5」、「Elasticsearch6」。 相關時，請針對多個版本使用「x」。 範例：「Elasticsearch2.x」

範例：

* &quot;Elasticsearch&quot;
* &quot;New Relic&quot;
* 「Web設定精靈」

## 正在疑難排解/說明的流程/功能標籤

* 使用小寫，專有名詞除外。
* 請勿使用同義字，一個實體使用一個標籤。
* 最好使用一個單字標籤。 不要新增問題說明。 也就是說，請輸入「資料庫」而非「資料庫當機」。

範例： 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;deployment&quot;
* 「大量更新」

## 正在修正/描述的問題標籤

* 使用小寫，專有名詞除外。
* 請勿使用同義字，一個實體使用一個標籤。
* 最好使用一個單字標籤。 請勿將錯誤訊息轉換為標籤。

範例：

* &quot;網站關閉&quot;
* 「500錯誤」
* 「卡住cron」
