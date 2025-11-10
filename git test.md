使用标注可以在不打乱笔记行文的情况下添加额外内容。

要创建标注，将 `[!info]` 添加到引用块的第一行即可。其中 `info` 是 _类型标识符_。类型标识符决定了标注的外观。要查看所有可用类型，请参阅[支持的类型](https://publish.obsidian.md/help-zh/%E7%BC%96%E8%BE%91%E4%B8%8E%E6%A0%BC%E5%BC%8F%E5%8C%96/%E6%A0%87%E6%B3%A8#%E6%94%AF%E6%8C%81%E7%9A%84%E7%B1%BB%E5%9E%8B)。

```markdown
> [!info]
> 这是一个标注块。
> 它支持 **Markdown**、[[Internal links|内部链接]] 和 [[Embed files|嵌入]]！
> ![[Engelbart.jpg]]
```

Info

这是一个标注块。  
它支持 **Markdown**、[内部链接](https://publish.obsidian.md/help-zh/%E9%93%BE%E6%8E%A5%E7%AC%94%E8%AE%B0%E4%B8%8E%E6%96%87%E4%BB%B6/%E5%86%85%E9%83%A8%E9%93%BE%E6%8E%A5) 和 [嵌入](https://publish.obsidian.md/help-zh/%E9%93%BE%E6%8E%A5%E7%AC%94%E8%AE%B0%E4%B8%8E%E6%96%87%E4%BB%B6/%E6%8F%92%E5%85%A5%E6%96%87%E4%BB%B6)！  
![Engelbart.jpg](https://publish-01.obsidian.md/access/cf01a21839823cd6cbe18031acf708c0/%E9%99%84%E4%BB%B6/Engelbart.jpg)

在[Obsidian 发布服务](https://publish.obsidian.md/help-zh/Obsidian+%E5%8F%91%E5%B8%83%E6%9C%8D%E5%8A%A1/%E5%8F%91%E5%B8%83%E6%9C%8D%E5%8A%A1%E7%AE%80%E4%BB%8B)中也原生支持标注。

Note

如果你同时使用 Admonitions 插件，应将其更新至 8.0.0 版本以上，以避免与标注功能冲突的问题。

### 修改标题 

默认情况下，标注的标题是其类型标识符。你可以在类型标识符后添加文本来更改它：

```markdown
> [!tip] 标注可以有自定义标题
> 就像这个一样。
```

标注可以有自定义标题

就像这个一样。

你甚至可以省略内容，创建仅带标题的标注：

```markdown
> [!tip] 仅标题的标注
```

仅标题的标注

### 可折叠标注 

你可以通过在类型标识符后添加加号（+）或减号（-）来使标注可折叠。

加号表示标注默认展开，减号表示标注收起。

```markdown
> [!faq]- 标注可以折叠吗？
> 可以！在可折叠标注中，当标注收起时，内容会被隐藏。
```

标注可以折叠吗？

### 嵌套标注 

你可以多层嵌套标注。

```markdown
> [!question] 标注可以嵌套吗？
> > [!todo] 可以。
> > > [!example]  你甚至可以使用多层嵌套。
```

标注可以嵌套吗？

可以。

你甚至可以使用多层嵌套。

### 自定义标注 

[CSS 代码片段](https://publish.obsidian.md/help-zh/%E6%89%A9%E5%B1%95+Obsidian/CSS+%E4%BB%A3%E7%A0%81%E7%89%87%E6%AE%B5) 和 [第三方插件](https://publish.obsidian.md/help-zh/%E6%89%A9%E5%B1%95+Obsidian/%E7%AC%AC%E4%B8%89%E6%96%B9%E6%8F%92%E4%BB%B6) 可以定义自定义标注，甚至覆盖默认配置。

要定义自定义标注，需创建以下 CSS 代码：

```css
.callout[data-callout="custom-question-type"] {
    --callout-color: 0, 0, 0;
    --callout-icon: lucide-alert-circle;
}
```

`data-callout` 属性的值是你想要使用的类型标识符，例如 `[!custom-question-type]`。

- `--callout-color` 使用三个数字（0-255）定义背景颜色的红色、绿色和蓝色分量。
- `--callout-icon` 是类型的图标，其可以是 [lucide.dev](https://lucide.dev/) 的图标 ID，或者一个 SVG 图标。

关于 lucide 图标版本的说明

Obsidian 定期更新 Lucide 图标。当前使用的版本如下所示。请在自定义标注中使用该版本或更早版本的图标。  

Version `0.268.0`  
ISC License  
Copyright (c) 2020, Lucide Contributors

SVG 图标

除了使用 Lucide 图标，你也可以使用 SVG 图标作为标注图标。

```css
--callout-icon: '<svg>...自定义 svg...</svg>';
```

### 支持的类型 

Obsidian 内置了多种标注类型。每种类型都带有不同的背景颜色和图标。

要使用这些默认样式，请将示例中的 `info` 替换为任何这些类型，比如 `[!tip]` 或 `[!warning]`。

除非使用[自定义标注](https://publish.obsidian.md/help-zh/%E7%BC%96%E8%BE%91%E4%B8%8E%E6%A0%BC%E5%BC%8F%E5%8C%96/%E6%A0%87%E6%B3%A8#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A0%87%E6%B3%A8)，否则任何不支持的类型都会默认为 `note` 类型。类型标识符不区分大小写，但部分类型有别名。

Note

```md
> [!note]
> Lorem ipsum dolor sit amet
```

---

Abstract

```md
> [!abstract]
> Lorem ipsum dolor sit amet
```

别名：`summary`，`tldr`

---

Info

```md
> [!info]
> Lorem ipsum dolor sit amet
```

---

Todo

```md
> [!todo]
> Lorem ipsum dolor sit amet
```

---

Tip

```md
> [!tip]
> Lorem ipsum dolor sit amet
```

别名：`hint`，`important`

---

Success

```md
> [!success]
> Lorem ipsum dolor sit amet
```

别名：`check`，`done`

---

Question

```md
> [!question]
> Lorem ipsum dolor sit amet
```

别名：`help`，`faq`

---

Warning

```md
> [!warning]
> Lorem ipsum dolor sit amet
```

别名：`caution`，`attention`

---

Failure

```md
> [!failure]
> Lorem ipsum dolor sit amet
```

别名：`fail`，`missing`

---

Danger

```md
> [!danger]
> Lorem ipsum dolor sit amet
```

别名：`error`

---

Bug

```md
> [!bug]
> Lorem ipsum dolor sit amet
```

---

Example

```md
> [!example]
> Lorem ipsum dolor sit amet
```

---

Quote

```md
> [!quote]
> Lorem ipsum dolor sit amet
```

别名：`cite`
