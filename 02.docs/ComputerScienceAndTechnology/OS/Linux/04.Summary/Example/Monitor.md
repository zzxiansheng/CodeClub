# Linux服务器的监控

#  1.监控概要
Linux服务器要保证高可用性，就要对其进行有效的监控，实时了解到服务器的运行状况，各项性能指标是否正常，以防患以未然，进行运维日志的记录，图形化的监控，出现问题的消息报警机制，都是保证Linux服务器能正常对外提供服务的先决条件。

#  2.监控的内容

监控，是预防的其中的一项重要工作。这里先说说我需要监控的内容。系统负载、cpu使用率、内存占用、磁盘空间、网络流量、端口、进程、apache或tomcat的连接数、mysql的运行状态这些都是需要监控的东西。要了解服务器每时每刻的整体运行状态，单靠几个Linux自带的性能监测命令是很难实现的。所以，利用shell脚本和开源监控工具进行服务器监控成为两个主要的选择。

#  3.监控的方法

首先是要明白Linux服务器监控的一些常见命令，以及这些命令编写的监控脚本，最后，一些成熟的开源监控工具也是必要的。

3.1 常见监控命令

1) 【iostat】:iostat命令用来显示存储子系统的详细信息，通常用它来监控磁盘 I/O 的情况。

2) 【meminfo 和 free】： cat /proc/meminfo free

3) 【mpstat】:实时系统监控工具,多CPUs系统里，其不但能查看所有CPU的平均状况信息，而且能够查看特定CPU的信息

4) 【netstat】:显示了大量跟网络相关的信息

5) 【nmon】：开源工具，用以监控 Linux 系统的性能,下载及安装

6) 【pmap】：pmap 命令用来报告每个进程占用内存的详细情况，可用来看是否有进程超支了，该命令需要进程 id 作为参数。

7) 【ps pstree】：ps 告诉你每个进程占用的内存和 CPU 处理时间，而 pstree以树形结构显示进程之间的依赖关系，包括子进程信息

8) 【sar】：sar 可用来显示 CPU 使用率、内存页数据、网络 I/O 和传输统计、进程创建活动和磁盘设备的活动详情。

9) 【strace】:诊断进程工具，如 strace ls ,但是被诊断进程会变慢

10) 【tcpdump】网络监控工具，用来做基本的协议分析，看看那些进程在使用网络以及如何使用网络。

11) 【uptime】:该命令告诉你这台服务器从开机启动到现在已经运行了多长时间了

12) 【 vmstat 】来监控虚拟内存

13) 【Wireshark】:是一个网络协议检测程序，让您经由程序抓取运行的网站的相关资讯

14) 【dstat】 多类型资源统计工具：该命令整合了vmstat，iostat和ifstat三种命令

15) 【htop】: 更加友好的top,两者区别见：“关于htop和top的比较”

16) 【ss】: 用来记录套接字统计信息，它可以显示类似netstat一样的信息，同时也能显示更多TCP和状态信息

17) 【lsof】 : 列表显示打开的文件

18) 【iftop】是另一个基于网络信息的类似top的程序。它能够显示当前时刻按照带宽使用量或者上传或者下载量排序的网络连接状况

3.2  shell监控脚本

这里提供 四个脚本（performance.sh 性能监控，process.sh 进程监控，network.sh 流量监控，tongji.sh流量分析统计），并使用crontab定时执行脚本进行监控数据的记录，形成每天的监控日志放在如下相应的文件夹，并且超过自己设定的告警值后发邮件通知，那些有免费短信通知功能的邮箱如腾讯企业邮箱，163邮箱可以尝试一下，收到邮件告警后很快就能收到短信了，很方便。

3.2.1 性能监控脚本 performance.sh

[代码GitHub地址](http://t.cn/Ro0H1EV)
代码有四个:

性能监控脚本01-监控cpu负载

性能监控脚本02-监控cpu使用率

性能监控脚本03-监控交换分区

性能监控脚本04-监控磁盘空间

3.2.2 进程监控脚本 process.sh

[代码GitHub地址](http://t.cn/Ro0R9pG)



3.2.3 流量监控脚本 network.sh

代码GitHub地址：



3.2.4 流量分析统计脚本 tongji.sh

[代码GitHub地址](http://dwz.cn/6b8y48)


3.3 监控工具

3.3.1) Cacti+Nagios

【Cacti】：Cacti是一套基于PHP,MySQL,SNMP及RRDTool开发的网络流量监测图形分析工具。

【Nagios】: Nagios是一个监视系统运行状态和网络信息的监视系统。能监视所指定的本地或远程主机以及服务，同时提供异常通知功能等

3.3.2）Zabbix

【Zabbix】: Zabbix除了能监视各种网络参数，保证服务器系统的安全运营之外，还能提供如短信、邮件、jabber等通知机制以让系统管理员快速定位/解决存在的各种问题。基本上能实现cacti+nagios的功能