已剪辑自: [https://www.zhihu.com/question/477999464/answer/2058402779?utm_id=0](https://www.zhihu.com/question/477999464/answer/2058402779?utm_id=0)  
按道理实体店不应该有这样的操作设置来砸自己的脚，也许是个别的。楼主本可以找实体店理论的。现提供以下方法可以尝试一下:  
♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠  
**【设置一】、**  
**⚓**Windows Update设置；  
1、按Win+R 运行，输入services.msc，然后点击确定，  
2、进入到服务窗口，在服务列表中找到Windows Update选项，点击鼠标右键，在弹出菜单中选择启用
 
2、在左侧选用户配置—管理模板—Windows组件—Windows 更新—在右侧选“删除 使用所有Windows更新功能的访问权限”双击它，  
3、在打开的对话框中选择“已启用”然后按应用确定，重启电脑即可！
 
♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠  
⚓**注：Windows Update设置不能修改的情况：按下图操作修改权限后重复以上步骤！**  
WIN+R键，输入 regedit 确定！  
找到HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv
 ![WudfPf WUDFRd WLJDFWpdFs WUDFWpdMtp WwanSvc w e KE...](Exported%20image%2020251107224424-0.jpeg)  

♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠♠  
**【设置二】、**  
1、首先按键盘win+R 运行输入gpedit.msc 点击确定打开；  
3、根据路径打开：计算机配置-管理模板-系统；  
4、在系统的文件夹里下滑找到系统还原点击一下；  
6、选择未配置最后点击确定既可完成设置。