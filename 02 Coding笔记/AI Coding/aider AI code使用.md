  

aider是终端运行AI code工具。

  

一、通过Anaconda Prompt进行安装配置

1、创建环境，并将git安装到环境中

`conda create --name aider python=3.10.11 git -y`

注意，此处新建aider环境，指定了系统安装的Python版本为3.10.11，为什么要指定该版本呢？因为最新版本的python在后续安装aider时，可能遇到各种解决不了的问题，使用3.10.11暂时没有发现问题。

2、激活aider环境

`conda activate aider`

3、安装aider

`pip install -i https://pypi.tuna.tsinghua.edu.cn/simple aider-chat`

可能会安装失败，则根据提示进行安装如下

`D:\anaconda3\envs\aider\python.exe -m pip install -i` `[https://pypi.tuna.tsinghua.edu.cn/simple](https://pypi.tuna.tsinghua.edu.cn/simple)` `aider-chat`

4、验证安装

`aider --version`

  

二、IDE工具中，使用aider

1、新建一个专用于aider的项目文件夹

2、在项目文件夹中新建.env文件，写入模型及其key

`AIDER_MODEL=deepseek/deepseek-chat`

`DEEPSEEK_API_KEY=sk-9c22d0a19ccd4f7e9de0a9c8e588000c`

3、使用IDE工具，新建项目，打开aider项目文件夹，设置编译解释器环境为一中设置的“aider”环境

4、IDE工具中，终端，输入aider，启用aider，如下图表示启用成功

![[image.png]]

5、启用aider注意不要建立本地git仓，如下图

![[image 1.png]]

  

三、注意：为什么要新建项目呢？而不是直接在原始项目中使用呢

1、理论上也可以在原来项目文件中使用，只需要在二中，2~4针对原来项目文件夹进行处理即可。

但是必须将原来项目文件中.idea文件夹（如果有.git文件夹也需要删除）删除，如果有其他不必要的文件，也请一并删除，不然这些缓存文件，可能保存了项目原来的一些配置，会导致aider与git路径配置不一致，从而无法启用aider。

如果上级目录也有.git或者.idea文件夹，也需要一并删除。

  

2、启用aider