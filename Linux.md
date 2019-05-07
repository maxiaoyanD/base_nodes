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

15、shell脚本基础 - 逻辑、循环、函数

​	test是shell的内建命令，经常用于各类的检测工作，产生的不是一般形式的输出，而是可用的退出状态。经常和if，while等用于条件的关键字配合使用。

​	test返回的结果在shell中运行不会输出，只会返回true或false（true是0，false是1）



| 命令               | 含义                              |
| ------------------ | --------------------------------- |
| test "abc" = "abc" | 检测字符串是否相等                |
| test -f  c/a.c     | 检测c/a.c文件是否存在且为普通文件 |
| test  -d bin       | 检测bin是否为目录                 |
| test -z $A         | 如果字符串为空则返回true          |
| test -n $A         | 如果字符串不为空则返回true        |

```vim
#if elif else
#写在一行要用分号分隔
if [command]; then
	[command]
elif [command];
then
	[command]
else 
	[command]
fi

#case
case WORD in
	values1)
		[command]
		;;
	values2)
		[command]
		;;
	*)
		[command]
		;;//esac之前的;;可以省略
esac

#for循环
for name in words;
do commands;
done

#while循环
while condition;
do commands
done
while循环的条件是命令的执行状态
```

shell脚本的一些特殊变量

| 变量 | 含义                                           |
| ---- | ---------------------------------------------- |
| $0   | 当前shell脚本的名称                            |
| $N   | 参数，使用$1,$2,......,10以上的要用${10}的形式 |
| $@   | 所有参数，可以使用for循环遍历                  |
| $#   | 参数个数，不包括脚本名称                       |
| $?   | 上一个命令的返回值，通常在if中使用             |
| $$   | 当前shell的PID                                 |





