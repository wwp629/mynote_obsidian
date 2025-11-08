### 项目目录下创建虚拟环境（以VSCode为IDE工具）

- 修改VSCode默认的终端类型（否则无法执行一些命令）：
    1. **快捷键** `**Ctrl+Shift+P**` 打开命令面板。
    2. 输入 `**Terminal: Select Default Profile**` 并选择 `**Command Prompt**`。
    3. **重启 VS Code 终端。**
- 创建虚拟环境
    1. **打开 VS Code 终端**（快捷键 ``**Ctrl+`**``）。
    2. **执行命令**：复制下载
        
        bash
        
        ```Plain
        python -m venv <自定义环境目录名>
        
        
        ```
        
        bash
        
        ```Plain
        python -m venv .venv# 默认常用名称（隐藏文件夹）
        python -m venv my_project_env# 显式命名
        
        \#例如创建名为spiceenv的电路仿真环境
        python -m venv spiceenv
        
        \#创建成功后，项目目录下会生成一个spiceenv的子目录
        ```
        
    3. **激活环境**：
        
        bash
        
        ```Plain
        .\<环境目录名>\Scripts\activate
        # 例如（如果采用默认常用名称）：
        .\.venv\Scripts\activate
        # 例如（如果采用显示命名）：
        .\spiceenv\Scripts\activate
        ```
        
- 终端中路径前面出现创建的虚拟环境名，表明已经激活了虚拟环境
    
    \#激活前终端如下：
    
    F:\Python\circuitSPICE>
    
    \#激活后终端如下：
    
    (spiceenv) F:\Python\circuitSPICE>
    
- 激活后，在vscode中，确认下右下角运行环境是所激活的，如果不是点击选择一下创建的激活环境
- 此时再执行pip install命令即可在当前项目目录下安装依赖包
    
    安装需要的依赖包后，路径F:\Python\circuitSPICE\spiceenv\Lib\site-packages下可以查看到安装的依赖包文件夹