参考论文排版中内容，在插入题注时，如果“新增标签”如“表1-”，然后在此基础上，插入题注，会出现“表1- 1XXXX”，**这里出现两个问题，一个是“表****1-****”后面，编号“****1****”之前会被****word****自动添加一个空格。同时编号“****1****”后面与标题“****XXX****”之间又没有空格**。这两点与我们需要的格式正好是违背的。可以通过手动删除/增加空格来解决。  
但是当遇到编制大型文档时，很容易忘记进行手动操作，从而导致格式不统一。针对该问题，可以建立宏来解决。具体如下：  
一、新建宏  
1.工具栏——视图——宏——录制宏  
录制宏的“宏名”不用修改，后续宏代码保存会自动更改。  
“将宏保存为”下拉选择为“所有文档（Normal.dotm）”

![Exported image](Exported%20image%2020251107224244-0.png)

2.录制确认后，再次回到工具栏——视图——宏——停止录制，这个“宏1”就完成了保存。  
二、修改宏  
1.工具栏——视图——宏——查看宏，找到第一步中新录制的宏，“宏1”

![Exported image](Exported%20image%2020251107224247-1.png)

2.打开“宏1”，代码是空白的，将下述代码复制进去

![Exported image](Exported%20image%2020251107224250-2.png)  

Sub InsertCaption() '修改系统插入“题注”命令
 
'功能：自动删除标签与编号间的空格（英文除外），并在题注数字后添加一个空格；适用于：Word 2003 - 2013，不兼容WPS文字！  
'真正从原理上协同系统插入题注，无任何前提条件；用户照常插入题注即可，甚至感觉不到程序的存在！  
'Endlesswx于2015年8月4日   '另,如果插入的始终未域代码而不是数字，非程序问题，Alt+F9一次即可   Dim Lab As String, startPt As Long, endPt As Long, myrang As Range  
'On Error Resume Next '发生错误时让程序继续执行下一句代码  
' Application.ScreenUpdating = False '关闭屏幕更新，2013在此处关闭更新会导致输入框灰色不可选，故修正在调出对话框之后   startPt = Selection.Start 'startPt标注起始点   '***将if条件隐藏隐藏即可实现----手动替换题注空格***  
If Application.Dialogs(357).Show = -1 Then '插入“题注”对话框秀出来,如果按确定结束时执行以下程序，避免按取消后的空格,357也可换成wdDialogInsertCaption   Application.ScreenUpdating = False '关闭屏幕更新   Lab = Dialogs(357).label  
endPt = Selection.Start 'endPt标记插入的题注部分终点  
Selection.Start = startPt '选定插入的整个题注   '删除标签与编号间的空格（英文后的保留）  
With Selection.Find  
.Text = Lab & " "  
.Forward = True 'False=向上查找,(True=向下查找)  
.MatchWildcards = False '不使用通配符  
If Lab Like "*[0-9a-zA-Z.]" Then '此处判断标签的最后一个字符是否为英文或数字，是则不删除空格  
Else  
.Replacement.Text = Lab  
.Execute Replace:=wdReplaceOne '替换找到的第一个，此处用作删除空格  
endPt = endPt - 1 '删除空格后，末位减1  
Selection.End = endPt  
End If  
End With   '在题注数字后添加一个空格  
Selection.Fields.ToggleShowCodes '切换域代码，这样才能用^d查找域  
With Selection.Find  
.Text = "^d"  
.Replacement.Text = "^& "  
.Forward = False 'False=向上查找,(True=向下查找)  
.MatchWildcards = False '不使用通配符  
.Execute Replace:=wdReplaceOne '替换找到的第一个，此处用作添加空格  
End With   '选定整个插入的题注内容，将域代码切换回来  
endPt = endPt + 1 '增加空格后，末位加1  
With Selection  
.Start = startPt  
.End = endPt  
.Fields.ToggleShowCodes '切换域代码（切换回来）  
End With   '将光标定位至题注所在段尾处  
' Selection.MoveRight Unit:=wdCharacter, Count:=1 '此句光标返回插入题注前的原始位置，对于已经输好标题的情况并不合适  
'选择段尾回车符  
With Selection.Find  
.Text = "^13"  
.Forward = True 'False=向上查找,(True=向下查找)  
.MatchWildcards = False '不使用通配符  
.Wrap = wdFindContinue '继续查找  
.Execute  
End With  
Selection.MoveLeft Unit:=wdCharacter, Count:=1 '定位到段尾回车前
 
End If  
Application.ScreenUpdating = True '恢复屏幕更新   End Sub
 
3.保存宏，即可使用。
 
三、插入题注  
不用进行任何额外操作，正常操作插入题注后，就能得到正确格式的题注如“表1-1 XXX”（如果没有上述宏的操作，格式是“表1- 1XXX”）