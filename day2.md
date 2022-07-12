# 完成的任务
* 学习linux
* 实现树的构造
* 了解git
# Linux(文件目录操作)
* clear : 清理
* pwd : 查看当前工作目录
* cd : 切换目录
* cd .. : 返回上级菜单  cd - : 返回上次访问的目录
* ls : 列出所在目录下的文件和目录
* ls -a/-l : 列出所有(包括隐藏文件)/长数据串列出(包括权限等)
* mkdir aaa(./aaa): 在当前目录下创建aaa目录 
* mkdir /aaa : 在根目录下创建aaa目录
* mkdir -p b/c/d : 在当前目录下递归创建目录b,c,d
* rmdir aaa : 删除aaa目录
* rmdir -p b/c/d : 递归删除目录b,c,d
* touch : 创建一个新的文件(不带后缀名则默认为文本文件)
* cp source dest: 复制文件
* cp -r source dest : 递归复制整个文件夹
* rm : 删除文件
* rm -r/f/v : 递归删除目录/强制删除/显示细节
* rm -f ./* : 强制删除当前目录的所有文件
* mv 原先目录 文件名称: 重命名 
* mv 原先目录 指定目录 : 将原先目录移动到指定目录下,若指定目录不存在，则原先目录名称改为指定目录名称
* cat : 查看文件
* cat -n : 查看文件且显示行号
* more : 从第一页开始查看文件内容，按回车一行一行查看，按空格一页一页查看，按q退出
* less : 从第一页开始查看文件内容，按回车一行一行查看，按空格一页一页查看，按q退出,支持查找和PgUp翻页
* echo : 输出内容到命令行
* echo -e : 支持\转义
* \>: 输出重定向
* \>> : 追加
* ls -l > 文件名 : 将ls -l中的内容写入文件中(覆盖)
* ls -l >> 文件名 : 将ls -l中的内容追在在文件末尾
* cat 文件1 > 文件2 : 将文件1的内容覆盖到文件2中去
* echo "内容" >> 文件 ： 将内容追加到文件中去
* head 文件: 显示文件前几行内容
* head -n x 文件 : 显示前x行内容
* tail 文件: 显示文件末尾几行内容
* tail -n x 文件 : 显示末尾x行
* tail -f 文件 : 实时监控文件追加内容
* ln -s 原文件/目录 软链接名 ： 给原文件创建一个软链接
* rm -rf 软链接名 : 删除软链接
* rm -rf 软链接名/ ： 删除软链接指向的真实目录
* ln 原文件/目录 硬链接名 ： 创建一个硬链接
* history : 查看以前执行的命令