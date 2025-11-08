### **一、命名规范区分原则**

1. **需求分支（Feature）**
    - **前缀**：`feature/` 或 `feat/`
    - **用途**：用于开发新功能或需求，从开发分支（`develop`）创建，完成后合并回`develop`。
    - **命名示例**
        - `feature/user-login_20250212_JIRA-123`
        - `feature/20250212_SSO-implementation`
        - `feat/payment-integration`
            
            _（功能描述 + 日期 + 任务ID，增强可追溯性）_
            
2. **Bug修复分支（Bugfix）**
    - **前缀：**`bugfix/` 或 `fix/`
    - **用途：**从`develop`分支创建，修复后合并回`develop`。
    - **命名示例**
        - `bugfix/login-error_20250212_JIRA-456`
        - `fix/404-page-redirect`
3. **热修复分支（Hotfix）**
    - **前缀：**`hotfix/`
    - **用途：**从`master`分支创建，修复后需同时合并到`master`和`develop`。
    - **命名示例**
        - `hotfix/security-patch_20250212`

---

### **二、核心区别**

|   |   |   |   |   |
|---|---|---|---|---|
|**分支类型**|**前缀**|**创建来源**|**合并目标**|**场景**|
|需求分支|`feature/`|`develop`|`develop`|新功能开发|
|Bug修复分支|`bugfix/`|`develop`|`develop`|普通Bug修复|
|热修复分支|`hotfix/`|`master`|`master` + `develop`|生产环境紧急修复|

### 三、git分支管理最佳实践

  

1. 你的开发工作是基于一个“干净”的 `main` 分支基础上开始的（基于，而不是直接在main分支上修改）。
2. 你的开发过程在 `dev/test` （创建新分支进行开发）分支上进行，不会污染 `main` 分支。
3. 你在合并回 `main` 之前，再次更新了 `main`，这能最大程度地减少合并冲突。
4. 最后你清理了所有已完成的分支，保持仓库整洁。

---

下面是为你整理的、基于你描述的完整步骤和对应的 Git 命令：

### 阶段一：准备工作（开始新任务）

1. **切换到主分支**Bash
    
    `git checkout main`
    
2. 拉取最新的主分支代码
    
    (确保你的本地 main 和远程 origin/main 保持一致)
    
    `git pull origin main`
    
3. 基于 main 创建并切换到新分支 dev/test（用于开发的分支名称）
    
    ( -b 标志代表 create branch 并 checkout)
    
    `git checkout -b dev/test`
    

### 阶段二：开发与推送（在新分支上工作）

1. 进行你的开发和测试
    
    (这是你写代码、修改、保存文件的过程)
    
    `... 你在 Cursor 中编写代码 ...`
    
2. 添加你的更改到暂存区
    
    ( . 代表所有更改)
    
    `git add .`
    
3. 提交你的更改
    
    ( -m 后面是你的提交信息，例如 "完成了XX功能")
    
    `git commit -m "在这里写下你的开发内容"`
    
4. 将 dev/test 分支推送到远程仓库Bash
    
    ( -u 是 --set-upstream 的缩写，它会“关联”你的本地分支和远程分支，下次推送这个分支时你只需要 git push 即可)
    
    `git push -u origin dev/test`
    

_(如果你在开发过程中有多次提交，可以重复步骤 1-3，并偶尔执行 `git push` 来同步到远程。)_

---

### 阶段三：合并（将成果并入主分支）

注意，合并命令merge是单向的，要合并到主分支，必须是先将主分支main拉取到本地，当前**激活的分支是main分支**，然后将待合并进来的本地分支比如dev/test合并到main分支中，再推送到远程。即特别需要注意，合并到主分支只能在本地进行。

1. **切换回主分支** `**main**`
    
    `git checkout main`
    
2. 再次拉取最新的 main
    
    (这是你描述的关键步骤！防止在你开发时，别人也合并了代码到 main)
    
    `git pull origin main`
    
3. **将** `**dev/test**` **合并到** `**main**`
    
    `git merge dev/test`
    
    - **如果无冲突：** Git 会自动合并。
    - **如果提示冲突 (Conflict)：** 你需要打开冲突文件，手动解决冲突，然后执行 `git add .` 和 `git commit` 来完成合并。
4. 将合并后的 main 推送到远程
    
    (现在，远程的 main 也包含了你 dev/test 的所有代码)
    
    `git push origin main`
    

---

### 阶段四：清理（保持仓库整洁）

1. 删除远程分支 dev/test
    
    (你的代码已经安全地在 main 里了，这个分支指针不再需要)
    
    `git push origin --delete dev/test`
    
2. 删除本地分支 dev/test
    
    ( -d 是安全删除，如果分支没合并会提示你)
    
    `git branch -d dev/test`
    

你现在就完成了一个完整、干净的开发周期，并且本地和远程仓库都处于整洁的状态，随时可以开始下一个任务。

  

### 补充：

上述阶段四，清理完本地的其他分支，保留main分支后，可能存在一个情况，就是本地main分支是落后与远程main分支的，需要保持本地main分支与远程main分支同步的话：

1. 切换到本地main分支
    
    `git chekout main`
    
2. 拉取远程的main分支
    
    （该操作会将远程main分支合并到本地main分支，从而确保本地main分支为最新）
    
    `git pull main`
    
    或可以简化为
    
    `git pull`
    

从上面可以看出来，修改代码时为什么强调开一个新分支进行，如果直接在本地main分支修改，可能导致与远程main分支状态混乱。

  

**开发全流程git最佳实践：**

`git checkout main`（切换到本地main）→

`git pull origin main`（拉取远程main，基于远程main更新本地main，保证本地main是最新）→

`git checkout -b dev/test`（基于本地main创建一个dev/test分支，并激活dev/test）→

开始代码工作（包括测试ok后）→

`git add .`（暂存所有更改，注意add与.之间有空格）→

`git commit -m` “修复了xxbug”（提交更改到本地dev/test分支）→

~~`git push -u origin dev/test`（推送本地修改好的dev/test分支到远程上，-u是关联本地与远程这两个分支，关联以后就可以简单用git push了，这样会直接推送本地当前激活的分支到远程关联分支上）→~~这里测试完成后不要推送远程，保证远程分支干净。

`git checkout main`（切换到本地main）→

`git pull`（本地与远程main分支关联过后，直接用这个简单命令，保证本地main跟远程main一样）→

`git merge dev/test`（本地合并dev/test到main，如果需要合并的话）→

`git push`（本地与远程main分支关联过后，直接用这个简单命令，推送到远程main上）→

`git branch -d dev/test`（删除本地分支，此时必须输入分支名称，因为此刻激活的本地main，测试开发的分支完成且已经与main合并，并已经确保推送main到远程后，删除掉开发分支）→

**版本管理（接着上面步骤）**

`git checkout -b release/v1.0.4`（生成发布版本分支）→

`git tag -a v1.0.1 -m "发布版本v1.0.1"`（生成版本标签）→

`git push -u origin release/v1.0.4` （推送标签到远程）→

`git push origin v1.0.1` （推送标签到远程）→

**新一轮工作**

`git checkout main→` …..（又开始新一轮工作流程）