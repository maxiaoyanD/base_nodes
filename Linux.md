sudo：可以获取用户权限

设置root密码：sudo passwd root

切换到root用户：su + root刚设置的密码

创建普通用户：adduser +创建名（没有权限在前面加sudo）

创建用户组：sudo addgroup h5

创建用户指定用户组：sudo adduser   -- ingroup 组名 用户名

删除用户：sudo deluser + 名称

删除组：sudo delgroup + 组名





sudo mkdir /phy_share/leonard

sudo mkdir /phy_share/sheldon

ll /phy_share/

sudo chown leonard:physics /phy_share





3.sudo 





nano

配置：sudo nano /etc/nanorc

//03/26

大于号就是输出重定向

小于号就是输入重定向

wc -l :按行统计Ctrl+d退出



2019-4-2 

所有的父进程是1的都是守护进程

grep 匹配 前面的输出与后面匹配

正则表达式中 ^表示开头 .表示  * 表示后面有任意个数

ps -e -o user,pid,ppid,comm,args | grep 'nginx'

所有的命令后 加 &符号表示转到后台运行

jobs查看后台任务 

fg 任务编号 转到前台继续执行

bg 任务编号 转到后台执行

# 13、shell脚本基础

```shell
shell脚本语言
#!/bin/bash
uname -a
lspci -vt
```









