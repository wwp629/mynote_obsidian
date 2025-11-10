---
tags:
  - LLM/KnowledgeBase
  - Dev/Docker
  - AI/RAG
  - Tools/MaxKB
aliases:
  - Docker部署MaxKB
  - MaxKB本地知识库
---

# 基于 Docker 部署 MaxKB 及应用

本文档将指导您如何基于 Docker 部署 MaxKB 开源知识库问答系统，并进行初步配置。

## 1. Docker 概述

Docker 是一组平台即服务（PaaS）产品。它利用操作系统层级的虚拟化技术，将软件及其依赖项打包为**容器**。托管容器的软件称为 Docker 引擎。Docker 能够帮助开发者在轻量级容器中自动部署应用程序，并使得不同容器中的应用程序彼此隔离，高效运行。

简而言之，Docker 是一种虚拟化技术，可以将软件及其依赖环境打包成相互独立、隔离的容器，从而确保各个软件可以独立高效地运行。

## 2. MaxKB 概述

MaxKB 是一款基于大语言模型（LLM）和 RAG（检索增强生成，Retrieval-augmented Generation）技术的开源知识库问答系统。RAG 是当前热门的大模型前沿技术之一。

无论是 MaxKB 还是其他基于大模型的本地知识库框架，其核心原理都是先利用 RAG 技术将本地知识文档进行向量化。当模型需要生成文本或回答问题时，它会从向量化后的文档集合中检索出相关信息，然后利用这些检索到的信息来指导文本生成，从而提高预测的质量和准确性。

> [!NOTE] 本地研究建议
> MaxKB 需要 Docker 部署，对于本地研究可能略显复杂。如果仅用于本地研究，可以考虑使用 CherryStudio 等工具直接安装使用，其安装过程可能更简便。

## 3. Windows Docker Desktop 安装

### 3.1 下载与自定义安装路径

1.  **下载安装程序**：访问 Docker 官网下载 Docker Desktop 安装程序。
2.  **自定义安装路径**：
> [!WARNING] 默认安装路径
    > Docker Desktop 默认安装在 C 盘。若需修改安装盘，需要通过命令行进行。
    > 以管理员身份运行 `CMD`。
    > 执行以下命令，将 Docker 安装到指定目录 (请确保指定目录文件夹已提前创建好)：
    > ```bash    
		> D:\Docker Desktop Installer.exe" install --installation-dir="D:\DockerDesktop
	> ```
	> (将 `D:\Docker Desktop Installer.exe` 替换为你的安装程序路径，`D:\DockerDesktop` 替换为你希望的安装目录)。

### 3.2 启动与 WSL 升级

1.  **启动 Docker**：安装后，尝试启动 Docker。
> [!TIP] 启动问题
    > 如果 Docker 无法启动，尝试重启电脑，或多次重启。
2.  **WSL 升级**：如果 Windows Subsystem for Linux (WSL) 版本不符合 Docker 运行要求，`CMD` 中会提示 `update wsl`。
    *   运行升级命令（正常情况下速度可能较慢）。
    *   开启 VPN 全局模式可以显著加速下载和升级过程。
    *   升级完成后，重启电脑。

## 4. MaxKB 部署 (基于 Docker)

在 Docker Desktop 正常运行的前提下，进行 MaxKB 的部署。

1.  **安装 Docker**：确保 Docker Desktop 已成功安装并运行。
2.  **检索 MaxKB 镜像**：在 Docker 应用程序中，检索 `maxkb`，找到并下载 `1panel/maxkb` 镜像。
3.  **运行 Docker 容器**：
    *   打开 `CMD`。
    *   执行以下 `docker run` 命令安装 MaxKB 到指定目录 `F:\maxkb_data`。
> [!IMPORTANT] 目录准备
    > 在运行此命令前，请务必先创建好 `F:\maxkb_data` 的父目录（例如 `F:\`）。
    > ```bash
    > docker run -d --name=maxkb -p 8080:8088 -v F:\maxkb_data:/var/lib/postgresgl/data 1panel/maxkb
    > ```
    > **(可选)** 你也可以参考 Bilibili 上的相关视频教程：[https://www.bilibili.com/video/BV1yPBvYrEMY/](https://www.bilibili.com/video/BV1yPBvYrEMY/)

4.  **访问 MaxKB UI**：Docker 镜像启动运行后，在浏览器中输入以下地址访问 MaxKB 登录界面：
    http://192.168.71.4:8080/ui/login
    (请将 `192.168.71.4` 替换为你的本机 IPv4 地址)。

5.  **默认登录凭证**：
    *   用户名：`admin`
    *   密码：`MaxKB@123..`

6.  **修改密码**：首次登录后，请务必修改默认密码以确保安全。

## 5. MaxKB 应用配置

MaxKB 部署完成后，进行知识库和模型的配置。

1.  **新建知识库**：
    *   根据系统指引创建新的知识库。
    *   将需要纳入知识库的数据资料上传，进行向量化处理。
> [!NOTE] 数据质量
    > 知识库问答系统的效果高度依赖于投喂的数据资料质量。建议使用能够直接识别的文档格式。例如，许多 PDF 文件是图片格式，识别度会很低。

2.  **配置大模型**：
    *   你可以选择**本地部署的大模型**，也可以通过**在线 API 调用**。
> [!TIP] 模型选择
    > 除非本地模型（如 `deepseek70b` 尺寸的模型）能够流畅运行，否则通常建议使用在线 API 调用，因为其配置相对简单，且性能更稳定。具体 API 调用方法请参考各大平台的说明。

3.  **新建问答应用 (基于本地知识库)**：
    *   创建新的问答应用时，务必将已配置好的知识库添加进去。
    *   如果未添加知识库，则会是一个纯粹依赖大模型、不具备本地知识库能力的问答应用。

4.  **新建纯粹大模型问答应用**：
    *   参考步骤 3，创建应用时不添加任何知识库即可。