onedrive会在其目录下建立一个存储状态的文件，如果该文件无法写入，就会一直进行同步工作，即使已经完成同步。  
这是由于重装系统后新用户没有权限操作旧用户的文件造成的。  
onedrive文件夹右键属性安全中添加当前用户的完全控制权限即可
 \> 来自 \<[https://github.com/baidut/windowsSystemHelper/issues/27](https://github.com/baidut/windowsSystemHelper/issues/27)\>