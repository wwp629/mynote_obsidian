---
tags:
  - 技巧/文本处理
  - 工具/VSCode
  - 正则表达式
aliases:
  - 如何删除TXT文件中的空白行
  - VSCode正则删除空行
---

## 需求

使用 **Visual Studio Code (VS Code)** 快速删除 `.txt` 文件中的所有空白行。

## 操作步骤

1.  在 VS Code 中打开目标 `.txt` 文件。
2.  按下快捷键 `Ctrl + H` 打开“查找与替换”工具栏。
3.  在工具栏中，点击 `.*` 图标，启用 **正则表达式** 模式。
4.  在“查找”输入框中，粘贴以下正则表达式：
<smtcmp_block language="regex">
^\s*(?=\r?$)\n
</smtcmp_block>
5.  将“替换”输入框 **留空**。
6.  点击“全部替换”按钮 (Replace All) 完成操作。