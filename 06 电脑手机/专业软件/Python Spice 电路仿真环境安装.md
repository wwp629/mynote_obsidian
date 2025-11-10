---
Tags:
  - Python/库
  - 电子/仿真
  - 软件/安装
Aliases:
  - PySpice安装
  - Python电路仿真环境搭建
---

本指南记录了使用 Python 进行电路仿真所需的核心库 `PySpice` 及其依赖的安装步骤。

## 安装流程

安装过程分为两步，请务必按顺序执行。

### 1. 安装 PySpice 库

首先，通过 `pip` 安装 PySpice 主库。

```bash
pip install PySpice
```

### 2. 安装 NgSpice 共享库

PySpice 依赖 NgSpice 作为仿真引擎。安装完主库后，执行其自带的脚本来自动下载并安装所需的 NgSpice 共享库（在 Windows 上为 `.dll` 文件）。

```bash
pyspice-post-installation --install-ngspice-dll
```

> [!NOTE] 安装顺序
> 必须先完成第一步的 PySpice 包安装，才能执行第二步的 `pyspice-post-installation` 命令。

## 参考资料

-   **官方安装文档**: [PySpice Installation Guide](https://pyspice.fabrice-salvaire.fr/releases/latest/installation.html)