---
tags:
  - LLM/Deployment
  - AI/Ollama
  - Tools/Windows
aliases:
  - Ollama部署
  - 开源大模型本地部署
---

## Ollama 部署开源大模型 (Windows)

本文档将指导您如何在本地 Windows 电脑上使用 Ollama 部署开源大模型。

### 1. Ollama 安装与配置

#### 1.1 安装 Ollama

1.  **下载安装包**: 从 [Ollama 官网](https://ollama.com/download/OllamaSetup.exe) 下载 `OllamaSetup.exe`。
> [!NOTE] 跨平台支持
    > Ollama 是一个开源大模型部署工具，支持 Windows、macOS 和 Linux。本文档主要针对 Windows 系统。

2.  **选择安装路径 (重要)**:
> [!WARNING] 默认安装路径
    > Ollama 安装程序不支持可视化选择安装路径，默认安装在 C 盘。如果 C 盘空间不足，可能导致拉取的大模型（如 DeepSeek）无法存放。
    >
    > **建议**：不要直接双击 `exe` 文件安装。通过命令行指定安装路径。

打开 `CMD` (命令提示符)。
`cd` 到 `OllamaSetup.exe` 所在的文件夹 (例如，如果 `exe` 放在 `D` 盘根目录)。
        cd D:\
在目标路径下新建安装文件夹 (例如 `D:\Program Files\ollama`)。
运行以下命令进行安装：
```
OllamaSetup.exe /DIR="D:\Program Files\ollama"
```
这将把 Ollama 安装到指定路径。

#### 1.2 验证 Ollama 安装
1.  打开 `CMD`。
2.  执行以下命令：
```
ollama --version
```
如果显示 Ollama 的版本信息，则表示安装成功。

### 2. 大模型管理

#### 2.1 拉取/安装开源大模型

1.  在 Ollama 模型库 [ollama.com/library](https://ollama.com/library) 中选择你想要安装的模型，例如 `deepseek-r1`。
2.  复制其安装命令，例如 `ollama run deepseek-r1:7b`。
3.  在 `CMD` 中运行该命令开始安装
```
ollama run deepseek-r1:7b
```
> [!TIP] 加速下载
    > 如果下载速度慢，可以尝试开启全局代理。

#### 2.2 查看已安装模型

1.  在 `CMD` 中执行以下命令：
```
ollama list
```
这将列出所有已安装的本地大模型，确认模型是否安装成功。

### 3. 运行大模型与前端集成

#### 3.1 在 CMD 中运行大模型进行问答

1.  在 `CMD` 中执行命令：
  ```
  ollama run deepseek-r1:1.5b
  ```
你就可以在命令行中与本地部署的大模型进行交互问答了。

#### 3.2 接入前端应用

要将本地大模型接入前端应用，可以参考部署以下工具：

*   **MaxKB**
*   **CherryStudio** (推荐研究使用，安装配置相对简单)

这些工具通常支持搭建本地知识库，并提供接入本地大模型的接口。请参考相应工具的官方文档，了解具体的接入方法。