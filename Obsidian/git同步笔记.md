## git插件
- 安装插件
- 设置git.exe路径
![[Pasted image 20251108212233.png]]
## 命令行git操作
- `git init`初始化仓库
- 修改`.gitignore`文件，添加`.obsidian`、`/00 Attachment(附件保存目录)`
	- `.obsidian`是保存一些设置等数据，不要同步；
	- `/00 Attachment`是附件保存目录（这里涉及设置-文件与链接-附件默认保存位置的修改），该文件夹保存大量图片、pdf等附件，一方面影响同步速度，一方面GitHub容量有限制；
- `git banch -M main`创建本地main分支
- `git add .`暂存
- `git commit -m "初始化提交"`本地commit
- `git remote add origin https://github.com/wwp629/mynote_obsidian.git`连接远程库
- `git push -u origin main`推送本地commit到远程库
## 插件操作
如果直接用git插件，不是很方便，因为obsidian中命令行不好用，初始化一些操作很麻烦，所以先完成上述[[#命令行git操作]]，再用git插件管理就很方便了。
插件git，只需要在想同步到git的时候，点击左侧的commit-and-sync（会要求选择分支，输入main就可以），脚本就会自动完成同步操作。
![[Pasted image 20251108213628.png]]
同步远程库，点击插件中的pull。
`注意：不允许在两个终端同时编辑笔记，特别是同一个笔记页面，很容易造成冲突，而导致无法完成git同步。`正确的做法是，在一个终端中修改笔记后，同步，关闭笔记。然后在另外一个终端中拉取，查看-修改-同步-关闭笔记。