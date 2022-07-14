# Linux
## 磁盘管理
* tree 目录名 : 树状查看当前目录情况
* du 目录/文件 ： 显示每个目录下子目录的磁盘使用情况
* du -a/-c/-s : 显示包括文件的全部使用情况/显示包括文件的全部使用情况后显示总和/只显示总和
* df : 查看磁盘的使用情况
* free : 查看内存的使用情况
* lsblk : 显示设备挂载情况
* lsblk -f : 同时显示文件系统的信息
* mount device dir : 挂载设备到对应的目录上去
* umount device/dir : 卸载相应的设备
* fdisk -f: 查看磁盘分区情况
* fidsk device : 将新硬盘进行分区
## 进程管理
* ps : 显示当前用户使用的进程与终端相关的进程
* ps aux : 显示所有进程,会显示CPU和内存占用率
* ps -ef : 可以查看所有进程,会显示父子进程关系(PPID)
* ps aux | grep 名称 ： 筛选进程
* kill 进程号 : 杀死对应进程
* kill -9 进程号 : 强制杀死进程
* killall 进程名称 ： 通过进程名杀死全部进程(支持通配符)
* pstree : 显示进程树
* pstree -p/-u : 显示进程PID/显示进程所属用户
* top : 实时显示进程的状态
* top -d 秒数 : 按指定秒数更新进程状态
* top -i : 不显示闲置或僵尸进程
* top -p 进程号: 仅查看指定进程 
* netstat -anp | grep 进程号 : 查看该进程的网络信息
* netstat -nlp | grep 端口号 : 查看网络端口号占用情况
