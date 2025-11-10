---
tags:
  - AI/Coding
  - Dev/Tools
  - Python/Anaconda
aliases:
  - Aider AI Code
  - Aider安装配置
  - Aider IDE集成
---

# Aider AI Code 工具使用指南

Aider 是一款在终端运行的 AI 编程辅助工具。

## 1. Anaconda 环境安装与配置

### 1.1 创建并配置 Conda 环境

首先，创建一个新的 Anaconda 环境，并安装 Python 和 Git：
```
conda create --name aider python=3.10.11 git -y
```

> [!NOTE] Python 版本选择
> 建议指定 Python 版本为 `3.10.11`，以避免在后续安装 `aider` 时可能遇到的兼容性问题。

### 1.2 激活 Aider 环境
```
conda activate aider
```

### 1.3 安装 Aider
```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple aider-chat
```

> [!TIP] 安装失败处理
> 如果 `pip install` 命令安装失败，可以尝试使用 Python 解释器的完整路径进行安装：
> D:\anaconda3\envs\aider\python.exe -m pip install -i https://pypi.tuna.tsinghua.edu.cn/simple aider-chat

### 1.4 验证安装
```
aider --version
```

## 2. 在 IDE 工具中使用 Aider

### 2.1 项目准备
1.  新建一个专门用于 `aider` 的项目文件夹。
2.  在项目文件夹中创建 `.env` 文件，并配置 AI 模型及其 API Key：
```
AIDER_MODEL=deepseek/deepseek-chat
DEEPSEEK_API_KEY=sk-9c22d0a19ccd4f7e9de0a9c8e588000c
```
3.  在 IDE 中新建项目并打开该文件夹，将项目的编译解释器环境设置为之前创建的 `aider` Conda 环境。

### 2.2 启动 Aider
1.  在 IDE 终端中输入 `aider` 命令以启动。
```
aider
```

下图显示 `aider` 已成功启用：
    ![[image.png]]

2.  
>[!WARNING] Git 仓库注意事项
    > 启用 `aider` 时，**切勿在当前项目目录或其上级目录建立本地 Git 仓库**。
    >
    > **原因解释**：`aider` 可能会与现有项目的 `.git` 或 `.idea` 等缓存文件产生冲突，导致路径配置不一致，从而无法正常启用。
    >
    > 如果必须在现有项目中启用 `aider`，请务必先手动删除项目及其上级目录中所有不必要的缓存文件（如 `.git` 文件夹、`.idea` 文件夹）。
> ![[image 1.png]]