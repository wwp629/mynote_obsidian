### git版本管理基本原则

在main分支上，通过打标签及创建分支来管理版本。发布版本前，请确认代码版本信息已经正确配置。然后创建发布版本分支，如release/v1.0.1，然后打上标签tag，然后推送该分支及tag到远程。

### git打标签操作

- **切换到目标分支**

```Plain
git checkout main
git pull
```

- **创建并切换到新分支**

```Plain
git checkout -b [新分支名] # 如release/v1.0.1
```

- **确定打标签的提交**

```Plain
git log --oneline # 简洁查看提交历史（推荐）

git log --graph --oneline --decorate # 查看详细提交历史

git log --oneline -10 # 查看特定数量的提交
```

- **找到目标提交的哈希值**

从提交历史中找到需要打标签的提交，记录其完整的或**前7位哈希值**。

- **创建标签**

```Plain
git tag -a [标签名] -m "[标签描述]" # 为当前最新提交打标签，如v1.0.1 -m "发布版本v1.0.1"

git tag -a [标签名] [提交哈希] -m "[标签描述]" # 为特定提交打标签（推荐，避免出错）
```

- **标签命名规范**
    
    版本标签：`v1.0.1`、`v2.3.4` ，此处根据项目实际版本规则处理
    
    预发布标签：`v1.0.1-rc1`、`v2.0.0-beta`
    
    功能标签：`feature/user-auth`、`bugfix/login-issue`
    
- **验证标签（可选，也可以通过可视化界面查看）**

```Plain
git tag
git tag -l
git tag -l "v1.*"# 按模式筛选
git show [标签名]
```

- **推送标签到远程**

```Plain
git push origin [标签名] # 推送指定标签名
git push origin --tags # 推送所有标签名
```

## ==以下为特殊情况==

- **修改历史提交并打标签（使用变基）**
    
    此情况，是指某些情况下，我们要打标签的文件，可以漏掉了版本配置（比如V1），已经完成了提交，且之后又有新的提交上去了（V2）。这时候，我们因为除了打标签，还要将V1代码中的版本配置为正确的V1，这样才能形成完整的追溯。该如何处理呢？这时候就要用到变基处理了，大体流程如下，但是注意，变基操作大部分会遇到修改冲突，处理起来很复杂。尽量不要操作变基，而是在有升级版本时，就要在代码中严格配置版本信息。
    

```Plain
# 开始交互式变基git rebase -i [目标提交的父提交哈希]

# 在编辑器中标记要修改的提交为 "edit"# 修改文件后git add [修改的文件]
git commit --amend
git rebase --continue

# 打标签git tag -a [标签名] -m "[描述]"
```

- **删除标签**

bash

```Plain
# 删除本地标签git tag -d [标签名]

# 删除远程标签git push origin --delete [标签名]
```

## **常见问题解决**

- **标签已存在**

```Plain
# 删除旧标签
git tag -d [标签名]
git push origin --delete [标签名]

# 重新打标签
git tag -a [标签名] -m "[新描述]"
git push origin [标签名]
```

- **推送被拒绝**

```Plain
# 强制推送（谨慎使用）
git push --force-with-lease origin [分支名]
```