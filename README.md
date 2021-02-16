# Linux-Commands
 总结常用的Linux命令
## 1、查看当前文件有多少个文件
功能 | 命令
-------- | -----
查看目录下有多少个文件及文件夹| ls \| wc -w
查看目录下有多少个文件| ls \| wc -c
查看文件夹下有多少个文件，多少个子目录|ls -l \|wc -l
若只想知道文件的个数| /bin/ls -l \|grep ^- \|wc -l

## 2、查看python正在执行的程序

> Ps aux | grep python

## 3、程序挂在后台运行
功能     | 命令
-------- | -----
 创建名为name的会话 | tmux new -s name
恢复上一次的会话| tmux a 
查看会话列表|tmux ls 
恢复名为name的会话 | tmux a -t name 
退出会话（直接Ctrl+d会关闭会话）| Ctrl+b ，再按d 

## 4、查看内存
功能     | 命令
-------- | -----
查看整体内存|df -h 
查看文件夹大小| du -sh 文件名 

## 5、基础命令

1. 创建/删除空目录 - mkdir / rmdir。

> [root ~]# mkdir abc 
> [root ~]# mkdir -p xyz/abc
> [root ~]# rmdir abc

  2. 创建/删除文件 - touch / rm。

> [root ~]# touch readme.txt 
> [root ~]# touch error.txt [root ~]# rm
> error.txt rm: remove regular empty file ‘error.txt’? y 
> [root ~]# rm -rf xyz
> 

 - touch命令用于创建空白文件或修改文件时间。在Linux系统中一个文件有三种时间：

> 更改内容的时间 - mtime。
> 更改权限的时间 - ctime。
>  最后访问时间 - atime。

 - rm的几个重要参数：

> -i：交互式删除，每个删除项都会进行询问。 
> -r：删除目录并递归的删除目录中的文件和目录。 			
> -f：强制删除，忽略不存在的文件，没有任何提示。

3. 切换和查看当前工作目录 - cd / pwd。

 - 说明：cd命令后面可以跟相对路径（以当前路径作为参照）或绝对路径（以/开头）来切换到指定的目录，也可以用cd
   ..来返回上一级目录。请大家想一想，如果要返回到上上一级目录应该给cd命令加上什么样的参数呢？

4. 查看目录内容 - ls。

> -l：以长格式查看文件和目录。
> -a：显示以点开头的文件和目录（隐藏文件）。
> -R：遇到目录要进行递归展开（继续列出目录下面的文件和目录）。
> -d：只列出目录，不列出其他内容。
> -S / -t：按大小/时间排序。

5. 查看文件内容 - cat / tac / head / tail / more / less / rev / od。
	
6. 拷贝/移动文件 - cp / mv。

> [root ~]# mkdir backup 
> [root ~]# cp sohu.html backup/ 
> [root ~]# cd backup 
> [root backup]# mv sohu.html sohu_index.html

7. 文件重命名 - rename。

> [root ~]# rename .htm .html *.htm

8. 查找文件和查找内容 - find / grep。
9. 压缩/解压缩和归档/解归档 - gzip / gunzip / xz。 
> [root@~]# gunzip redis-4.0.10.tar.gz

10. 归档和解归档 - tar。

> [root@~]# tar -xvf redis-4.0.10.tar

## 6、用户管理
1. 创建和删除用户 - useradd / userdel。

> [root home]# useradd user1
> [root home]# userdel user1

2. 修改密码 - passwd。

> [root ~]# passwd user1
> New password: 
> Retype new password: 
> passwd:all authentication tokens updated successfully.

说明：输入密码和确认密码没有回显且必须一气呵成的输入完成（不能使用退格键），密码和确认密码需要一致。如果使用passwd命令时没有指定命令作用的对象，则表示要修改当前用户的密码。如果想批量修改用户密码，可以使用chpasswd命令。

> -l / -u - 锁定/解锁用户。
> -d - 清除用户密码。
> -e - 设置密码立即过期，用户登录时会强制要求修改密码。
> -i - 设置密码过期多少天以后禁用该用户。

3. 切换用户 - su。

> [root ~]# su user1
> [user1root]$

4. 以管理员身份执行命令 - sudo。

> [user1~]$ ls /root 
> ls: cannot open directory /root: Permission denied 
> [user1~]$ sudo ls /root 
> [sudo] password for user1:

说明：如果希望用户能够以管理员身份执行命令，用户必须要出现在sudoers名单中，sudoers文件在 /etc目录下，如果希望直接编辑该文件也可以使用下面的命令。

## 7、文件系统
1. 目录结构

	1. /bin - 基本命令的二进制文件。
	2. /boot - 引导加载程序的静态文件。
	3. /dev - 设备文件。
	4. /etc - 配置文件。
	5. /home - 普通用户主目录的父目录。
	6. /lib - 共享库文件。
	7. /lib64 - 共享64位库文件。
	8. /lost+found - 存放未链接文件。
	9. /media - 自动识别设备的挂载目录。
	10. /mnt - 临时挂载文件系统的挂载点。
	11. /opt - 可选插件软件包安装位置。
	12. /proc - 内核和进程信息。
	13. /root - 超级管理员用户主目录。
	14. /run - 存放系统运行时需要的东西。
	15. /sbin - 超级用户的二进制文件。
	16. /sys - 设备的伪文件系统。
	17. /tmp - 临时文件夹。
	18. /usr - 用户应用目录。
	19. /var - 变量数据目录。
2. 修改权限

项目     | Value
-------- | -----
chmod |改变文件模式比特
chown | 改变文件所有者
chgrp | 改变用户组

## 8、Linux命令行常用快捷键
快捷键| 功能
-------- | -----
tab|自动补全命令或路径
Ctrl+a|将光标移动到命令行行首
Ctrl+e|将光标移动到命令行行尾
Ctrl+f|将光标向右移动一个字符
Ctrl+b|将光标向左移动一个字符
Ctrl+k|剪切从光标到行尾的字符
Ctrl+u|剪切从光标到行首的字符
Ctrl+w|剪切光标前面的一个单词
Ctrl+y|复制剪切命名剪切的内容
Ctrl+c|中断正在执行的任务
Ctrl+h|删除光标前面的一个字符
Ctrl+d|退出当前命令行
Ctrl+r|搜索历史命令
Ctrl+g|退出历史命令搜索
Ctrl+l|清除屏幕上所有内容在屏幕的最上方开启一个新行
Ctrl+s|锁定终端使之暂时无法输入内容
Ctrl+q|退出终端锁定
Ctrl+z|将正在终端执行的任务停下来放到后台
!!|执行上一条命令
!数字|执行数字对应的历史命令
!字母|执行最近的以字母打头的命令
!$ / Esc+.|获得上一条命令最后一个参数
Esc+b|移动到当前单词的开头
Esc+f|移动到当前单词的结尾


**本文长期更新...**
