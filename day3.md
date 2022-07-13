# Linux(用户管理)
* useradd : 添加新用户
* useradd -g 组名 用户名 : 添加某个用户到用户组 
* passwd 用户名: 更改用户的密码
* id 用户名 ： 获取用户的id信息 
* cat /etc/passwd : 查看所有用户
* su 用户名 ： 跳转到某个用户(利用exit可以回退)
* sudo 命令 : 获取超级管理员权限执行命令(需要在sudoers文件中配置)
* userdel 用户 : 删除用户
* userdel -r 用户 : 删除用户(包括用户文件)
* groupadd 组名 ： 添加用户组
* usermod -g 组名 用户名 ： 将用户添加到某个用户组
* usermod -n 新组名 旧组名 ： 将旧组名改为新组名
* groupdel : 删除用户组
* cat /etc/group : 查看创建了哪些组
* chmod {ugoa}{+-=}{rwx} 文件名: 修改文件的权限
* chmod 421 文件名 ： 利用二进制修改文件权限
* chmod -R 421 目录名 : 修改该目录下所有文件的权限
* chown 用户名 文件名 ： 修改文件的属主
* chgrp 用户组 文件名 : 修改文件的属组
