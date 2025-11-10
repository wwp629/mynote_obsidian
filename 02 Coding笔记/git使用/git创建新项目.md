---
tags:
  - Dev/Git
  - Dev/GitHub
  - CS/VersionControl
aliases:
  - Git新项目创建
  - GitHub项目初始化
  - 从零开始Git项目
---

好的，这是从零开始创建全新项目并推送到 GitHub 的完整流程。

这个流程分为三个阶段：

1.  **在 GitHub 上：** 创建一个空的远程仓库（作为“保险库”）。
2.  **在本地电脑上：** 创建项目、初始化 Git、进行首次提交。
3.  **连接与推送：** 将本地的代码推送到 GitHub。

---

### 阶段一：在 GitHub 上创建远程仓库

1.  登录 GitHub.com。
2.  点击右上角的 **“+”** 号，选择 **New repository** (新建仓库)。
3.  **填写仓库信息：**
    *   **Repository name (仓库名)：** 填写你的项目名称（例如 `my-new-project`）。
    *   **Description (描述)：** （可选）填写项目描述。
    *   **Public / Private：** 选择“公开”或“私有”。
4. 
> [!IMPORTANT] 重要：不要勾选任何选项！
    > *   不要勾选 "Add a README file"
    > *   不要勾选 "Add .gitignore"
    > *   不要勾选 "Choose a license"
    > **原因：** 我们要创建一个**完全空**的仓库，以便接收你本地的 `main` 分支作为它的“第一次”提交。
5.  点击 **Create repository** (创建仓库)。
6.  创建后，GitHub 会显示一个新页面，里面有“...or create a new repository on the command line”的指引。复制这个仓库的 URL，它看起来像这样：
    `https://github.com/你的用户名/my-new-project.git`
    （我们稍后会用到这个 URL）。

---

### 阶段二：在本地电脑上创建项目和 Git 仓库

1.  **打开你的终端** (CMD, PowerShell, Bash 或 Cursor 里的终端)。

2.  **创建并进入你的项目文件夹：**
创建一个新文件夹
```
mkdir my-new-project
```

进入这个文件夹

```
cd my-new-project
```

3.  **初始化本地 Git 仓库：**
    (这会在文件夹里创建一个隐藏的 `.git` 目录，用来跟踪所有更改)
```
git init
```

4.  **创建 main 分支：**
    (新版 Git 默认可能就是 `main`，但为保险起见，使用 `-M` 命令可以强制创建/重命名为 `main`)
```
git branch -M main
```

5.  **创建你的第一个项目文件：**
    (你可以创建任何文件，这里用 `README.md` 举例)
Windows CMD
```
echo # My New Project > README.md
```

PowerShell / macOS / Linux
```
echo "# My New Project" > README.md
```

6.  **将文件添加到 Git 暂存区：**
    ( `.` 代表“所有文件”)
```
git add .
```

7.  **提交你的第一个更改：**
    (这是你的第一个历史记录快照)
```
git commit -m "Initial commit"
```

### 阶段三：连接本地仓库并推送到 GitHub

1.  **连接到你的 GitHub 仓库：**
    (告诉本地 Git，远程仓库的地址在哪里。将 `<URL>` 替换成你阶段一第6步复制的 URL)
```
git remote add origin <你复制的GitHub仓库URL>
```

示例：git remote add origin https://github.com/你的用户名/my-new-project.git

2.  **(可选) 验证连接是否成功：**
```
git remote -v
```
(它应该会显示 `origin` 指向你设置的 URL)

3.  **推送！将本地 main 分支推送到 GitHub：**
    (这是最关键的一步。`-u` 会将你的本地 `main` 和远程 `origin/main` 永久关联起来)
```
git push -u origin main
```

### 完成！

现在，刷新你的 GitHub 仓库页面，你将看到你本地创建