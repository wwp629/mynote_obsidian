四、maxkb部署  
1、安装docker；  
2、在docker中，检索maxkb，找到1panel/maxkb下载；  
3、cmd，通过docker run -d --name=maxkb -p 8080:8088 -v F:\\maxkb_data: /var/lib/postgresgl/data 1panel/maxkb，安装maxkb到指定目录F:\\maxkb_data，需要先把maxkb的父目录建立好，再运行此命令；（也可以参考：https://www.bilibili.com/video/BV1yPBvYrEMY/?spm_id_from=333.337.top_right_bar_window_history.content.click&vd_source=817f0c547eb9122ea4d657e02e74b0a1）  
4、docker启动运行镜像后，浏览器输入http://192.168.71.4:8080/ui/login，IP为本机IP4地址；  
5、输入用户名amdin，密码MaxKB@123..；  
6、修改密码；

一、docker：  
Docker是一组平台即服务（PaaS）的产品。它基于操作系统层级的虚拟化技术，将软件与其依赖项打包为容器。托管容器的软件称为Docker引擎。Docker能够帮助开发者在轻量级容器中自动部署应用程序，并使得不同容器中的应用程序彼此隔离，高效工作。  
即可以理解为docker一种虚拟技术，它可以将一个个软件及其依赖环境打包为彼此独立隔离的容器，从而使得各个软件可以独立高效的运行。

二、maxkb（maxkb需要docker部署，本地研究不是很方便，可以使用cherrystudio直接安装使用）：  
‌MaxKB是一款基于大语言模型和RAG（检索增强生成（Retrieval-augmented Generation），当下热门的大模型前沿技术之一）的开源知识库问答系统。不管是Maxkb还是其他基于大模型的本地知识库框架基本都是先利用RAG技术将本地知识文档进行向量化，然后当模型需要生成文本或者回答问题时，它会先从向量化后的文档集合中检索出相关的信息，然后利用这些检索到的信息来指导文本的生成，从而提高预测的质量和准确性。

三、windows docker desktop安装  
1、docker官网下载安装程序，但是注意dockers默认是安装在C盘，要修改安装盘，需要通过命令行修改；  
2、管理员运行cmd，命令行"D:\Docker Desktop Installer.exe" install --installation-dir="D:\DockerDesktop"安装docker到指定目录下，注意先将指定目录文件夹创建好；  
3、安装后，启动docker（如果不能启动，重启电脑，或多次重启电脑），如果WSL不符合docker运行要求的版本，会在cmd中提示update wsl，运行升级即可（正常运行速度非常慢，开启VPN全局模式很快就能下载升级好），升级后重启电脑；

五、maxkb配置  
1、新建知识库，根据指引建立知识库后，将需要建立到知识库中的数据资料上传到建立好的知识库中进行向量化（注意知识库问答系统的好坏取决于投喂的数据资料质量，最好使用能够直接识别的文档格式，pdf文件很多是图片格式，识别度很低）；  
2、配置大模型，可以是本地的，也可以是在线api调用，除非本地模型能够顺畅运行如deepseek70b尺寸的模型，否则建议使用在线api调用（api调用参考各大平台api调用说明，比较简单）；  
3、新建基于本地知识库的大模型问答应用，新建应用需要将知识库添加进去，否则就是一个没有本地知识库的纯大模型问答应用。  
4、新建纯粹大模型问答应用，参考3，不添加知识库即可。