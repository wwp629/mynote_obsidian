本地windows电脑使用ollama部署大模型方法：  
1、安装ollama，https://ollama.com/download/OllamaSetup.exe；（ollama开源大模型部署工具，支持windows、Mac、Linux，本地电脑研究的话，直接使用windows安装 ）  
2、注意ollama不支持可视化选择指定安装路径，默认安装在C盘，所以会导致拉取的大模型（比如deepseek），如果C盘不够大，建议不要直接双击exe安装，通过命令行安装。cmd中通过cd指向exe存放的文件夹（比如存放在D盘根目录），目标路径下新建安装文件夹（比如D:\Program Files\ollama），然后命令行运行：OllamaSetup.exe /DIR=D:\Program Files\ollama，就可以将ollama安装到指定路径中；  
3、cmd中查看ollama是否安装成功，执行命令：ollama --version，如果出现对应版本信息，表示已经安装成功；  
4、cmd中安装deepseek-r1，也可以根据需要安装其他开源模型，在https://ollama.com/library/deepseek-r1，中选择要安装的模型，复制其中的安装命令，如：ollama run deepseek-r1:7b，复制到cmd中，开始安装，如果速度慢，开启全局代理就可以加速；  
5、cmd查看已经安装的大模型，ollama list，查看大模型是否安装成功；
 
运行安装好的大模型：  
cmd运行：ollama run deepseek-r1:1.5b，就可以在cmd中利用本地大模型进行问答使用；  
要接入到前端，参考部署maxkb或者cherrystudio（研究用，建议使用该工具，安装简单，容易配置）等前端工具（这两个工具，都支持搭建本地知识库），然后接入本地大模型（参考官方文档，研究如何接入本地模型）