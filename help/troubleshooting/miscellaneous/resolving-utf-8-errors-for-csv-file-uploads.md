---
title: 解決CSV檔案上傳的UTF-8錯誤
description: 本文提供當您收到錯誤訊息「CSV檔案必須使用UTF-8編碼」時的修正。 此錯誤訊息表示您嘗試上傳的檔案包含非法字元或不允許的字元。 雖然UTF-8編碼可允許[大部分字元](https://www.fileformat.info/info/charset/UTF-8/list.htm)，但有些與MagentoBI不相容。
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 解決CSV檔案上傳的UTF-8錯誤

本文提供當您收到錯誤訊息「CSV檔案必須使用UTF-8編碼」時的修正。 此錯誤訊息表示您嘗試上傳的檔案包含非法字元或不允許的字元。 而UTF-8編碼允許 [大部分字元](https://www.fileformat.info/info/charset/UTF-8/list.htm)，有些與MagentoBI不相容。

若要修正問題，您必須變更檔案的編碼。 以適當的編碼重新儲存檔案通常可解決問題，但請注意，在執行此操作時，您可能會遺失一些資訊（例如，可能會捨棄非法字元）。

我們建議使用 [華麗文字](https://www.sublimetext.com/2) 以儲存並編碼檔案。

1. 在Microsoft Excel、Google檔案、Apple編號或您選擇的程式中開啟檔案。
1. 按一下&#x200B;&#x200B; **檔案** > **另存為** 並&#x200B;&#x200B;選擇&#x200B;&#x200B; **逗號分隔值(.csv)** 格式以儲存檔案。
1. 以Sublime Text開啟CSV檔案。
1. 在Sublime文字中，瀏覽&#x200B;至&#x200B; **檔案** > **以編碼方式儲存** > **UTF-8\*&#x200B;** . 這會以UTF-8編碼儲存CSV檔案。    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [上傳資料](https://docs.magento.com/mbi/data-analyst/importing-data/connecting-data/using-file-uploader.html) （在我們的使用手冊中）新增至MagentoBI中的表格。
