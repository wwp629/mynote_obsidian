---
Tags:
  - 软件/Office
  - Word
  - 自动化
  - VBA
Aliases:
  - Word题注宏
  - Word自动格式化题注
---


本指南旨在通过创建一个 VBA 宏，自动修正 Word 插入题注时产生的多余空格和缺失空格问题。

## 问题描述

根据 [[01 Word 高效排版终极指南|word排版全教程]] 中的方法，当为图表创建自定义标签（如 `表1-`）并插入题注时，Word 会生成不符合规范的格式。

> [!WARNING] Word 默认格式问题
> - **默认输出**: `表1- 1XXX`
> - **存在问题**:
>     1.  标签 `表1-` 和编号 `1` 之间被 **自动添加了一个空格**。
>     2.  编号 `1` 和题注文字 `XXX` 之间 **没有空格**。
> - **目标格式**: `表1-1 XXX`

虽然可以手动修改，但在大型文档中极易遗漏。

## 解决方案：VBA 宏

通过编写一个与 Word 内置“插入题注”命令同名的 VBA 宏 (`InsertCaption`)，我们可以接管并重写其默认行为，实现插入题注时自动完成格式的修正。

## 操作步骤

1.  **打开 VBA 编辑器**
    -   在 Word 中，点击顶部菜单 **视图 → 宏 → 录制宏**。

2.  **创建宏**
    -   在弹出的“宏”对话框中，于“宏名”处输入 `InsertCaption`。
    -   确保“宏的位置”选为 `所有活动模板和文档` 或 `Normal.dotm`。
    -   点击 **确定**。
    -   回到工具栏——视图——宏——停止录制，完成宏录制。

3.  **创建宏代码**
    - 工具栏——视图——宏——查看宏，找到宏 `InsertCaption`，编辑
    - 在 VBA 编辑器中，将自动生成的 `Sub InsertCaption()...End Sub` 内容 **全部删除**。
    -   将下方的VBA代码复制并粘贴到代码窗口中。

4.  **保存并关闭**
    -   关闭 VBA 编辑器窗口，Word 会自动保存该宏到全局模板 (`Normal.dotm`) 中。

### VBA 代码

Sub InsertCaption() '修改系统插入“题注”命令
 
' 功能：自动删除标签与编号间的空格（英文除外），并在题注数字后添加一个空格。
' 适用于：Word 2003 - 2013，不兼容WPS文字！
' 作者：Endlesswx @ 2015年8月4日
 
Dim Lab As String, startPt As Long, endPt As Long, myrang As Range
startPt = Selection.Start
 
' 调用Word内置的“插入题注”对话框
If Application.Dialogs(wdDialogInsertCaption).Show = -1 Then
    Application.ScreenUpdating = False
    Lab = Dialogs(wdDialogInsertCaption).Label
    endPt = Selection.Start
    Selection.Start = startPt
 
    ' 1. 删除标签与编号之间的空格 (英文和数字标签后的空格保留)
    With Selection.Find
        .Text = Lab & " "
        .Forward = True
        .MatchWildcards = False
        If Lab Like "*[0-9a-zA-Z.]" Then
            ' Do nothing
        Else
            .Replacement.Text = Lab
            .Execute Replace:=wdReplaceOne
            endPt = endPt - 1
            Selection.End = endPt
        End If
    End With
 
    ' 2. 在题注编号后添加一个空格
    Selection.Fields.ToggleShowCodes ' 切换域代码以查找域
    With Selection.Find
        .Text = "^d" ' ^d 代表域代码
        .Replacement.Text = "^& " ' ^& 代表找到的文本
        .Forward = False
        .MatchWildcards = False
        .Execute Replace:=wdReplaceOne
    End With
 
    ' 恢复域代码显示并重新选定
    endPt = endPt + 1
    With Selection
        .Start = startPt
        .End = endPt
        .Fields.ToggleShowCodes
    End With
 
    ' 将光标定位至题注末尾
    With Selection.Find
        .Text = "^13" ' 查找段落标记
        .Forward = True
        .MatchWildcards = False
        .Wrap = wdFindContinue
        .Execute
    End With
    Selection.MoveLeft Unit:=wdCharacter, Count:=1
 
End If
Application.ScreenUpdating = True
 
End Sub

## 效果与使用

> [!SUCCESS]
> 安装此宏后，无需任何额外操作。只需像往常一样使用 Word 的“插入题注”功能，即可自动获得 `表1-1 XXX` 格式的完美题注。
