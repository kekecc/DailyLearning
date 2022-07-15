# Linux
## 系统定时任务与软件包管理
* crontab -l : 查询定时任务
* crontab -e : 编辑定时任务
* crontab -r : 删除用户所有的定时任务
* rpm -qa : 查询所有rpm软件包
* rpm -qi 软件名 ： 显示该软件安装的详细信息
* rpm -e 软件名 ： 删除该软件包
* rpm -ivh 软件名 ： 下载软件包 
* yum -y install 包名: 下载并安装软件包
* yum -y remove 包名: 移除软件包
* yum -y update 包名: 更新软件包
* yum list : 列出所有的软件包
* yum clean : 清除缓存
## shell