---
tags:
  - Obsidian/标注
  - Markdown语法
  - 笔记技巧
aliases:
  - Obsidian标注
  - Callouts
  - 标注类型
---
# Obsidian 内置标注 (Callouts) 详解

Obsidian 提供了多种内置标注类型（Callouts），每种类型都拥有独特的背景颜色和图标，用于突出显示不同类别的信息。

除非使用[自定义标注](https://publish.obsidian.md/help-zh/%E7%BC%96%E8%BE%91%E4%B8%8E%E6%A0%BC%E5%BC%8F%E5%8C%96/%E6%A0%87%E6%B3%A8#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A0%87%E6%B3%A8)，否则任何未识别的标注类型都会默认显示为 `note` 类型。类型标识符不区分大小写，且部分类型支持别名，以提供更灵活的调用方式。

## 内置标注类型概览

Obsidian 内置了以下标注类型及其别名：

| 类型       | 主要别名             | 其他别名/说明       |
| :--------- | :------------------- | :------------------ |
| `note`     | -                    | 默认类型            |
| `abstract` | `summary`, `tldr`    | 摘要、总结          |
| `info`     | -                    | 信息                |
| `todo`     | -                    | 待办事项            |
| `tip`      | `hint`, `important`  | 提示、重要          |
| `success`  | `check`, `done`      | 成功、完成          |
| `question` | `help`, `faq`        | 问题、帮助、常见问题 |
| `warning`  | `caution`, `attention` | 警告、注意          |
| `failure`  | `fail`, `missing`    | 失败、缺失          |
| `danger`   | `error`              | 危险、错误          |
| `bug`      | -                    | Bug、缺陷           |
| `example`  | -                    | 示例                |
| `quote`    | `cite`               | 引用、引文          |

## 标注语法示例

以下是 Obsidian 标注的几种常见书写格式：

### 1. 基本标注格式

一个带有标题和内容的简单标注。

```md
> [!note] 标注标题
> Note正文内容
```

### 2. 标注内嵌套代码块

在标注中嵌入代码块以展示代码示例。

```md
> [!info] 代码示例
> 这是一个在标注中嵌套代码块的例子：
> ```python
> def hello_world():
>     print("Hello, Obsidian!")
> ```
```

### 3. 多层标注嵌套

标注支持多层嵌套，可以创建复杂的层次结构。

```md
> [!question] 标注可以嵌套吗？
> question标注正文内容。
> > [!todo] 可以。
> > todo标注正文内容。
> > > [!example] 你甚至可以使用多层嵌套。
> > > example标注正文内容。
```

## 各类型标注效果预览

以下是所有内置标注类型的实际显示效果和用法示例：

### Note

> [!note] 这是一个Note标注
> Note标注的示例内容，用于提供一般性信息。

### Abstract
别名：`summary`, `tldr`
> [!abstract] 这是一个Abstract标注
> Abstract标注的示例内容，通常用于提供总结或概要。

### Info
> [!info] 这是一个Info标注
> Info标注的示例内容，用于提供额外的信息或背景知识。

### Todo
> [!todo] 这是一个Todo标注
> Todo标注的示例内容，表示需要完成的任务或待办事项。

### Tip
别名：`hint`, `important`
> [!tip] 这是一个Tip标注
> Tip标注的示例内容，用于提供有用的提示或重要信息。

### Success
别名：`check`, `done`
> [!success] 这是一个Success标注
> Success标注的示例内容，表示操作成功或已完成。

### Question
别名：`help`, `faq`
> [!question] 这是一个Question标注
> Question标注的示例内容，用于提出问题或寻求帮助。

### Warning
别名：`caution`, `attention`
> [!warning] 这是一个Warning标注
> Warning标注的示例内容，用于提醒用户注意潜在问题。

### Failure
别名：`fail`, `missing`
> [!failure] 这是一个Failure标注
> Failure标注的示例内容，表示操作失败或信息缺失。

### Danger
别名：`error`
> [!danger] 这是一个Danger标注
> Danger标注的示例内容，用于表示严重错误或危险情况。

### Bug
> [!bug] 这是一个Bug标注
> Bug标注的示例内容，用于记录软件缺陷或问题。

### Example
> [!example] 这是一个Example标注
> Example标注的示例内容，用于展示某个概念或功能的例子。

### Quote
别名：`cite`
> [!quote] 这是一个Quote标注
> Quote标注的示例内容，用于引用他人的言论或文献。
</smtcmp_block>

### 嵌套标注示例
> [!question] 标注可以嵌套吗？
> question标注正文内容。
> > [!todo] 可以。
> > todo标注正文内容。
> > > [!example] 你甚至可以使用多层嵌套。
> > > example标注正文内容。