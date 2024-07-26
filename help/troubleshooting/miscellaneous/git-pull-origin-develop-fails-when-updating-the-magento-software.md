---
title: 更新Adobe Commerce軟體時，Git Pull Origin開發失敗
description: 本文提供執行「Git提取來源開發」時無法更新Adobe Commerce軟體的修正。
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 更新Adobe Commerce軟體時，Git Pull Origin開發失敗

本文提供執行`git pull origin develop`時無法更新Adobe Commerce軟體的修正。

## 詳細資料

更新Adobe Commerce軟體的步驟之一，就是透過執行下列動作來更新本機存放庫：

```bash
$ git pull origin develop
```

可能會顯示下列錯誤：

```bash
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

若要尋找哪些檔案可能會被覆寫，請閱讀訊息或輸入：

```bash
git status
```

下一節將討論建議的解決方案。

### 建議的解決方案

您的解決方案取決於您是否刻意修改Adobe Commerce檔案系統中的檔案。 如需詳細資訊，請參閱下列其中一節。

#### 您刻意修改檔案

以一般方式手動解決衝突。 如果您不確定要做什麼，請參閱[GitHub說明](https://help.github.com/)。

#### 您沒有刻意修改任何檔案

請嘗試下列任一操作：

* 如果您確定未修改任何檔案，且不介意移除或覆寫Adobe Commerce檔案系統中的變更，請輸入：

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  之後，繼續進行Adobe Commerce更新的後續步驟。

* GitHub組態設定在未來可能會防止這些錯誤。 依預設，GitHub會使用作業系統預設的行尾字元來儲存內容。 如果您使用Linux，但其他共同作業人員使用Windows提交變更，則在您複製或提取時，GitHub會將Windows行尾轉換為Linux。 當實際上未進行任何變更時，這會顯示檔案的變更外觀。

  若要設定GitHub忽略行尾，請在Git使用者端中輸入以下命令：

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  如果您使用Windows，請輸入：

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe不建議或認可任何特定的GitHub組態設定。 前述只是建議。 如需詳細資訊，請參閱[GitHub說明](https://help.github.com/)。

  繼續進行Adobe Commerce更新的後續步驟。
