微软公司出于安全的需要，将所有UWP应用都放置在沙箱中运行。  
这样做虽保证了安全，但也导致沙箱中的软件无法使用代理网络，即使设置了系统代理。**这样的设置会导致某些****uwp****运行软件不能很好的进行同步，比如****OneNote for win10****，由于在沙箱运行，会导致笔记中带有图片、视频、或者大文件时同步异常会出现异常。**  
通过下面办法可以解决OneNote同步不好的问题，对于其他微软自带软件（仅限uwp应用）如果出现同步问题也可以用以下办法解决。  
下面介绍两种方法来解除这种限制。  
工具/原料

- 软件Fiddler
- 一些基本的电脑常识

方法/步骤  
微软自带的方法￼Windows 10 自带了一款名为 CheckNetIsolation.exe 的命令行工具可以帮助我们将 UWP 及 Windows 8 Metro 应用添加到排除列表￼具体步骤如下：

![uwp](Exported%20image%2020251107224310-0.jpeg)- 1.首先需要找到需要设置代理的UWP软件的SID。￼这里的SID是UWP应用在注册表中的一个信息值，而所有的UWP应用的注册表信息都在下列位置。￼使用快捷键win+r，打开命令行输入框，然后输入regedit。回车，便能进入注册表编辑器。￼HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\Mappings￼然后挨个找到你所需要设置代理的应用的注册表信息。￼DisplayName就是应用的名称，而前面的一大串，以S-1-开头的就是该应用的SID。
![uwp](Exported%20image%2020251107224313-1.jpeg)  
![uwp](Exported%20image%2020251107224317-2.jpeg)  
![uwp](Exported%20image%2020251107224322-3.jpeg)- 然后复制该SID。（**S-1-15-2-3445883232-1224167743-206467785-1580939083-2750001491-3097792036-3019341970**，是OneNote for win10的SID）￼继续win+r打开命令行输入框，输入cmd，回车。￼接着出入以下命令。￼CheckNetIsolation.exe loopbackexempt -a -p=SID￼（记得将SID值替换上去）￼回车，然后该应用就能使用代理的网络了。
![uwp](Exported%20image%2020251107224324-4.jpeg)  
![uwp](Exported%20image%2020251107224326-5.jpeg)  
\> 来自 \<[https://jingyan.baidu.com/article/6b182309ff5b6bba58e159e0.html](https://jingyan.baidu.com/article/6b182309ff5b6bba58e159e0.html)\>  
      
\> 来自 \<[https://jingyan.baidu.com/article/6b182309ff5b6bba58e159e0.html](https://jingyan.baidu.com/article/6b182309ff5b6bba58e159e0.html)\>