adb环境安装好的前提下。先运行app，开始治疗，然后，windows cmd命令行操作如下：  

adb shell top

  

得到如下图的结果，且该结果会实时刷新。

找到对应的app包名，com.dahangqi.main

![[image 2.png|image 2.png]]

  

结果解析：

PID: 进程 ID  
USER: 进程所属用户

  
PR: 进程优先级  
NI: 进程调度优先级（Nice 值）  
VIRT: 虚拟内存使用量  
RES: 常驻内存使用量（物理内存）  
SHR: 共享内存使用量  
S: 进程状态（R=运行中，S=睡眠中，D=不可中断的睡眠中，Z=僵尸进程等）==%CPU: CPU 使用率，注意这是占据一个单核的使用率，而cpu都是多核的  
%MEM: 内存使用率==  
TIME+: 进程运行总时间  
ARGS: 进程的启动命令和参数  
————————————————

关注%CPU（要测试两种情况，在前台运行时以及在后台运行时的结果）、%MEM