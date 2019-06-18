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

<https://www.cnblogs.com/fnlingnzb-learner/p/5831284.html>

# 3、文件系统和目录结构

## 3.1、Linux目录结构

​	Linux用 / 表示根目录，也就是整个目录树的顶层，其他目录都位于/之下

​	所有的目录都至少包含两个子目录：**.  和  . .**

​	. 表示当前目录

​	. . 表示上一层目录

​	/也有 . . ，但是指向的是自己

​      **保存用户信息：/etc/passed**

​       **保存用户密码：/etc/shadow**

​       **保存用户组信息的文件：/etc/group**

## 3.2、最常用的命令

### 3.2.1、ls

​	ls命令用于查看文件/目录的信息。直接输入ls默认显示当前目录的情况。

| 命令   | 说明                                 |
| ------ | ------------------------------------ |
| ls -a  | 显示所有文件，包括隐藏文件           |
| ls -l  | 显示详细信息                         |
| ls -R  | 递归显示信息                         |
| ls -sh | 以易读的方式显示文件大小             |
| ls -s  | 按文件大小排序显示，大文件在前       |
| ls -t  | 以创建时间排序显示，最近创建的在前面 |

### 3.2.2、cd

​	cd默认会切换到用户主目录。cd[目录名]切换到指定目录

| 命令       | 说明                                       |
| ---------- | ------------------------------------------ |
| cd         | 在任何目录下，直接输入cd会切换到用户主目录 |
| cd ..      | 回到上一层目录，在/下输入cd..还是在/       |
| cd -       | 回到刚才的目录                             |
| cd[目录名] | 切换到指定目录，比如cd /tmp                |

## 3.3、Linux目录说明

| 目录        | 说明                                                 |
| ----------- | ---------------------------------------------------- |
| /root       | root用户主目录                                       |
| /boot       | 系统启动文件所在目录，包括grub以及内核               |
| /lib        | 程序链接库所在目录                                   |
| /dev        | 设备文件目录，外接设备会在此目录映射为一个文件       |
| /media      | U 盘、光盘等外接存储会挂载到此目录                   |
| /proc       | 虚拟目录，系统信息、进程信息等在以文件形式此目录     |
| /var        | 软件安装包信息、日志文件等所在目录                   |
| /sys        | 硬件设备驱动程序所在目录                             |
| /lost+found | 一般为空，系统异常关机时会有一些信息存入此目录       |
| **/tmp**    | **临时文件所在目录`**                                |
| /usr/bin    | **虚拟目录，系统信息、进程信息等在以文件形式此目录** |
| /usr/sbin   | 用户程序所在目录，需要超级用户权限                   |

## 3.4、查看存储占用情况

​	df命令查看硬盘的存储使用情况，默认按照字节显示

​	df -TH会根据大小按照B、K、M等单位显示

# 4、shell基础

## 4.1、终端和shell

​	终端是计算机最外围设备。用户获取用户输入，并显示程序的输出结果。

​	shell本身就是一个程序，主要工作室运行命令，并把命令输出的结果呈现给用户。

## 4.2、命令分类

​	内建命令：是shell的一部分，是shell自带的

​	外部命令：独立存在的一个程序文件，存在于某一目录下。（例：ls命令路径为/bin/ls）

​	**确定命令的类型**：type（type本是内建命令，可通过type type验证）

​	**知道命令所在路径**：whereis/which

​	**查看命令的手册(联机文档)**： man ls（man查看外部）

​							help：help cd（help查看内部）

## 4.3、shell命令的运行基本过程

shell是通过环境变量中的PATH设置的路径查找命令。

echo $PATH可以输出默认搜索命令的路径。

当在终端里输入命令并确认， shell 会从 PATH设置的路径逐个查找，如果文件存在则执行。
如果在两个目录中存在同名的程序，则先找到救执行，不会继续寻找。

![1560512287110](E:\大二下\base_nodes\img\shell.png)

![1560511069236](E:\大二下\base_nodes\img\shell执行过程.png)

## 4.4、shell快捷操作

Ctrl+L 清理屏幕，等同于 clear 命令。
Ctrl+W 按词删除，空格分割表示一个单词。
方向键‘上’可以查找之前输入过的命令。
Ctrl+C 终止当前执行的命令。
Ctrl+A 跳转到行首， Ctrl+E 跳转行尾。

## 4.5、shell常用命令

| 命令  | 说明          | 示例                                                         |
| ----- | ------------- | ------------------------------------------------------------ |
| mkdir | 创建目录      | mkdir abc                                                                        mkdir -p a/b/c(父及目录不存在自动创建) |
| rmdir | 删除空目录    | rmdir abc                                                    |
| touch | 创建空文件    | touch a.c                                                    |
| cat   | 显示文件内容  | cat /etc/passwd                                                                   cat -n /etc/group 显示行号 |
| cp    | 赋值文件/目录 | cp abc tmp/bcd                                                                 cp  -R  tmp/     backup/（复制目录） |
| rm    | 删除文件/目录 | rm  abc                                                                                  rm  -rf tmp/ (删除目录，目录可以不为空) |
| echo  | 输出字符串    | echo ‘Hello Linux’                                           |
| mv    | 移动文件/目录 | mv abc bcd(这是重命名操作)                                               mv tmp / backup /（移动目录不需要-R） |

# 5、用户与文件

**用户操作的是文件**

Linux设计思想：一切皆文件

## 5.1、超级用户

Linux默认有一个root用户，超级用户，具有所有的权限。

## 5.2、sudo

sudo 命令允许用户临时以 root 权限运行命令。
sudo 默认以 root 身份执行命令。
sudo -u [ 用户名 ] 可以指定其他用户身份。

# 13、shell脚本基础![shell执行过程](E:\大二下\base_nodes\img\shell执行过程.png)

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

# 15、Linux C编程基础

## 15.1、程序的参数

```c
#include<stdio.h>
#include<stdlib.h>

int main(int argc,char * argv[]){
    for(int i=0;i<argc;i++){
        printf("%s\n",argv[i]);
    }
    return 0;
}
/*
	根据argc输出每个参数，参数是通过argv传递的
	argc是参数的个数，最小为1，因为argv[0]永远都是程序的名称。
*/
/*
	程序返回值
		程序最后的返回值为0表示争取
		非0值表示程序出错。
*/
```

## 15.2、验证返回值的脚本

```c
#!/bin/bash

if ./bin/outr -r abcdef ; then
	echo '[OK]'
else
    echo '[NOT OK]'
if
    
echo ''

if ./bin/outr -r 12345 -r ; then
	echo '[OK]'
else
    echo '[NOT OK]'
if
/*
	验证脚本和编译程序在同一目录。
	在此目录有bin目录，编译好的程序都放在bin
*/
```

## 15.3、获取PID

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc,char * argv[]){
    printf("%d\n",getpid());
    return 0;
}
/*
	getpid调用可以获取进程自己的PID
	getppid获取父进程的PID
*/

```

## 15.4、创建子进程

​	fork创建子进程

fork返回值在父进程中返回子进程的PID，子进程中返回0

父进程和子进程都执行fork之后，如果失败，fork调用返回-1