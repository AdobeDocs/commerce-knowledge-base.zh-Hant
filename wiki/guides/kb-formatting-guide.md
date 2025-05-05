---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# KB格式指南

## Markdown中的作者

一般而言，我們使用[Adobe Experience League Markdown語法樣式指南](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en)，但會有一些差異和例外。 此外，在某些情況下，還需要某些HTML標籤。

以下範例是存放庫中最常使用的Markdown格式設定。

## 基本格式

若要將文字的格式設為粗體，請以雙星號括住文字：

`This will be **bold** text`

若要將文字的格式設為斜體，請使用單星號：

`This text will be *italics*`

若要將文字的格式設定為底線，請使用`<ins>`標籤：

`<ins>This text will be underlined</ins>`

若要新增分行符號，請使用`<br>`HTML標籤。


## 標頭

對從H2到H5的標題使用以下格式。 由於文章標題會視為H1，因此絕不會使用H1。

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## 程式碼內嵌和區塊

使用單一反引號將您要反白顯示的程式碼元素括住：

這是文欄位落中的\&#39;內嵌程式碼\&#39;。

### 程式碼區塊

若要插入程式碼區塊，請以三個反引號括住程式碼區塊，並在開啟三個反引號後指定語言：

\`\`\` sql

選取TABLE_NAME作為`Table`，
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024)做為`Size (MB)`
從information_schema.TABLES
其中TABLE_SCHEMA = &quot;%project_id%&quot;
排序依據(DATA_LENGTH + INDEX_LENGTH) DESC；

\`\`\`

這會呈現為：

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

根據我們的篩選規則，您一律需要指定程式碼區塊的語言。

如需支援的語言清單，請造訪https://github.com/github/linguist/blob/master/lib/linguist/languages.yml。

如果醒目提示對Markdown中的特定語言沒有作用（即不支援語言），若要使其在發佈至https://support.magento.com/hc/en-us/時至少醒目提示，請使用下列HTML：

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

其中``%language-code%``是由[Prism.js支援的語言](https://prismjs.com/#supported-languages)所定義的程式碼。

## 清單

清單與其他內容一律以空白行分隔。 清單的前後應加上空白行。

針對排序清單使用以下格式：

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

若要建立未排序的專案符號清單，請在文字行的開頭使用*、+或 — 。 但請選取一種方法，並在整篇文章中一致使用。

範例：

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

若要在清單專案之間新增內容，請在行首新增4個空格：

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

您也可以以這種方式內嵌清單。

## 連結

外部連結簡單明瞭：

```markdown
[Adobe](https://www.adobe.com)
```

### 附件的連結

任何型別的附件都應採用.png、.jpg和.jpeg格式。 基於安全考量，我們僅接受三種格式之一的附件。

若要插入影像，請將影像放置在與文章相同的區段資料夾中的&#x200B;*assets*&#x200B;子資料夾中，並使用下列語法將影像插入文章：

```markdown
![alt text](assets/image.png)
```

如果您想要自訂影像的大小，必須使用下列HTML標籤進行此操作：

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### 文章中特定區段的連結

如果您需要在文章中參考區段，就不需要建立個別的錨點。 所有H2-H6標題發佈時，都會自動建立錨點。 錨點是從標頭產生的，方法是將所有文字變為小寫並使用「 — 」來分隔文字。

範例：

```markdown
## This is header
```

此為連結至此標題：

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

如果您需要參考標頭以外的元素，請使用HTML來定義要新增的元素，並使用[id屬性](https://www.w3schools.com/html/html_id.asp)。 然後您可以使用Markdown或HTML來參照此ID。

### 其他文章的相對連結和連結

請勿使用相對連結來參考我們的支援知識庫文章。 當您的文章在[Adobe Commerce說明中心](https://support.magento.com/hc/en-us)中發佈時，這些連結將無法運作。
請使用[Adobe Commerce說明中心](https://support.magento.com/hc/en-us)的完整超連結。


## 表格

對表格[&#128279;](https://www.w3schools.com/html/html_tables.asp)使用HTML格式。


## 警告和資訊區塊

成功備註區塊：

```
>![success]
>
>This is a success note
```

警告區塊：

```
>![warning]
>
>This is a warning
```

資訊備註區塊：

```
>![info]
>
>This is a block with additional info
```
