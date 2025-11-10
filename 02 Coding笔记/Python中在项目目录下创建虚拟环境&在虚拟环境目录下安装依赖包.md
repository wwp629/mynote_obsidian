---
tags:
  - Python/Venv
  - Tools/VSCode
aliases:
  - Python虚拟环境
  - VSCode创建venv
---

### 1. VSCode 终端设置 (Windows)

> [!TIP] 前提步骤
> 在 Windows 上，建议将 VSCode 的默认终端修改为 `Command Prompt`，以确保 `venv` 相关命令能正确执行。

1.  按 `Ctrl+Shift+P` 打开命令面板。
2.  输入 `Terminal: Select Default Profile` 并选择 `Command Prompt`。
3.  重启 VSCode 终端 (`Ctrl+` ` ` ``)。

### 2. 创建虚拟环境

1.  在 VSCode 中打开你的项目文件夹。
2.  打开终端 (`Ctrl+` ` ` ``)。
3.  执行 `venv` 创建命令：
<smtcmp_block language="bash">
# 基本命令格式
python -m venv <环境目录名>

# 示例1: 使用通用名称 .venv (推荐，为隐藏文件夹)
python -m venv .venv

# 示例2: 自定义名称
python -m venv spiceenv
    执行成功后，项目根目录下会生成一个与环境同名的子目录。

### 3. 激活与验证

1.  **执行激活命令**：

基本命令格式 (Windows)
`.\<环境目录名>`

示例1: 激活 .venv 环境
`.\.venv\Scripts\activate`

示例2: 激活 spiceenv 环境
`.\spiceenv\Scripts\activate`

2.  **验证激活状态**：
    观察终端提示符，若路径前出现用括号包裹的环境名，则表示激活成功。
激活前
`F:\Python\circuitSPICE>`

激活后
`(spiceenv) F:\Python\circuitSPICE>`

3.  **配置 VSCode 解释器**：
    激活后，确认 VSCode 右下角的状态栏已自动切换到新创建的虚拟环境解释器。若未切换，请手动点击并选择它。

### 4. 安装依赖包

-   确保虚拟环境已激活，此时使用 `pip install` 命令安装的依赖包将被隔离在此环境中。
-   安装的包会存放在虚拟环境目录下的 `Lib\site-packages` 文件夹内（例如 `.\spiceenv\Lib\site-packages`）。