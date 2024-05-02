---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# 中繼資料驗證指南

為了確保MD檔案中的中繼資料格式正確，我們已實施中繼資料驗證測試。 本檔案提供的指引，可協助貢獻者避免一些最常見的中繼資料驗證錯誤。

**中繼資料範例：**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## 常見驗證錯誤及避免/修正方法

以下是中繼資料驗證錯誤發生的一些最常見情況。

### 中繼資料中的冒號

如果標題或標籤或兩者都有冒號，就會發生驗證錯誤。

**範例：**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

若要避免此錯誤，請以括住標題或標籤（或兩者皆含冒號） **單引號**.

**範例：**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### 中繼資料中的冒號和單引號

如果標題或標籤中有冒號、單引號或單引號，之前的解決方案將無法運作。

**範例：**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

此錯誤可透過包住標題或標籤（或兩者）來修正 **雙引號**.

**範例：**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### 中繼資料中的冒號、雙引號及單引號或單引號

**範例：**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

發生此情況時，請將標題或標籤（或兩者）包裝在 **雙引號** 並使用 **反斜線** 以逸出標題和標籤中的所有雙引號。

**範例：**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### 中繼資料中缺少欄位

如果中繼資料中缺少標題欄位或標籤欄位，則會發生驗證錯誤。

**範例：**

```markdown
---
title: This is a title
---
```

或

```markdown
---
labels: article,labels,tags
---
```

要避免此錯誤，請在中繼資料中包含這兩個欄位。

標籤欄位可以保留為空白，這不會產生錯誤，但必須填寫標題欄位。

**範例：**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
