---
title: 尋找大型MySQL表格
description: '''若要識別大型資料表，請依照[連線至資料庫](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database)文章中的說明連線至資料庫，然後執行下列命令，其中''project_id''是您的Cloud專案ID：'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# 尋找大型MySQL表格

若要識別大型資料表，請依照以下說明連線至資料庫： [連線到資料庫](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) 並執行下列指令，其中 `project_id` 是您的Cloud專案ID：

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

這會顯示完整的表格清單及其大小。 您可以瀏覽清單，並找出哪些表格因大小過大而需要注意。
