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
如果在两个目录中存在同名的程序，则先找到就执行，不会继续寻找。

![1560512287110](E:\大二下\base_nodes\img\shell执行过程.png)

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

获取root权限用sudo或su

## 5.2、sudo

sudo 命令允许用户临时以 root 权限运行命令。
sudo 默认以 root 身份执行命令。 
sudo -u [ 用户名 ] 可以指定其他用户身份。

获取软件包更新：sudo apt update

查看磁盘分区：sudo fdisk -l

设置root密码：sudo passwd root

su用于切换用户，默认切换到root用户。

切换到指定用户：sudo -l 【用户名】

## 5.3、创建普通用户、用户组

创建oklinux用户：sudo adduser oklinux

创建用户组：sudo addgroup h5

创建用户指定用户组：sudo --ingroup h5 linuxer（创建linuxer并指定组为h5）

​			 如果h5的ID是1003也可以是sudo --ingroup 1003 linuxer

## 5.4、保存用户和组的文件

保存用户的信息：/etc/passwd 

保存用户组的信息：/etc/group

查看文件内容：cat /etc/passwd

用户的权限是其所在组权限之和。

修改用户的信息：usermod -a/-g（配合完成）

把oklinux加入到sudo组：sudo usermod -G sudo -a oklinux

删除用户：sudo deluser oklinux（sudo deluser --remove-home oklinux同时删除用户主目录）

删除用户组：sudo delgroup h5

## 5.6、文件及文件权限

文件具有所属用户以及用户组，并具备可操作的权限。
通常来说除 root 用户之外，其他用户都只能操作自己的文件或用户所在组的文件。

查看文件权限：ls -l（查看文件详细信息，第一项显示了文件权限）

r，w，x：可读、可写、可执行

第三项和第四项表示所属用户和用户组

# 6、文件、存储、权限

I-node 结构是大小固定的，对于存储超大文件就会有限制，所以往往会把实际记录文件位置的信息也放在 Data 区域，并存储指向这些区域的指针。

## 6.1、I-node号和权限

查看文件的I-node编号以及权限：ls -li

查看i-node号：ls -i

目录记录的信息：在目录中创建文件时，会创建一个i-node，并在目录中添加一条i-node编号和文件名映射的记录：i-node number：filename

## 6.2、文件权限与标志位

r ：可读； w ：可写； x ：可执行。

八进制表示：r：100；W：010；x：001

| 用户         | 用户组 | 其他用户 |
| ------------ | ------ | -------- |
| rwx          | r-x    | r-x      |
| 111          | 101    | 101      |
| 八进制表示： | 0755   |          |

文件的默认权限查看：umask（默认权限是通过权限掩码生成的）

设置权限掩码：umask 022

## 6.3、权限掩码

创建空文件：touch 【文件名】

如果权限掩码为 0022, 则文件的权限为： 0644
计算方式： 0777 按位减去掩码对应的位，如果是文件再去掉可执行权限。

## 6.4、更改文件权限

chmod设置文件权限

u 表示该文件的拥有者，g 表示与该文件的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。

chmod +x bin/pse 添加可执行权限，所属用户与用户组具有可执行权限

chmod -w bin/pse 去掉写权限，用户，用户组，其他用户去掉写权限。

chmod u=rwx,g=rw,o=r bin/pse相当于chmod 754 bin/pse

chmod 754 -R bd递归操作

## 6.5、更改文件所属用户和用户组

修改文件所属用户和组：chown

| 命令                          | 说明                                     |
| ----------------------------- | ---------------------------------------- |
| chown oklinux:oklinux hdl     | 更改文件hdl所属用户和组为oklinux         |
| chown : helo hdl              | 更改文件hdl所属用户组为helo              |
| chown oklinux :hdl            | 更改文件hdl所属用户为oklinux             |
| chown oklinux:oklinux tmp/ -R | 目录tmp中所有文件所属用户和组改为oklinux |

## 6.6、硬链接

硬链接没有创建新文件，只是多了一个别名。只是在目录中多了一个记录，指向同一个I-node号。硬链接本质上是增加了i-node引用计数。删除文件的时候实际上删的也是硬链接计数，计数为0则i-inde标记的存储区域被释放掉，才是真正的删除文件。

创建硬链接：ln 【目录文件】【硬链接名】

## 6.7、软链接（符号链接）

创建软链接：ln -s【目录文件】【软链接名】

创建软链接实际上是创建了新的文件，文件类型标记为符号链接，存储内容是目标文件的路径。创建软链接可以跨分区，可以跨文件系统。删除目标文件不会删除符号链接，如果以相同的名称创建新的文件，则符号链接继续指向该文件。删除符号链接不会删除目标文件。符号链接的权限是目标文件的权限。

# 7、软件安装

## 7.1、deb软件包

deb文件是一个压缩包形式，可以解压软件包查看内容

移除软件包：sudo dpkg --remove fish

​			sudo dpkg --remove fish-common

包管理命令：

| 命令      | 说明                                               |
| --------- | -------------------------------------------------- |
| apt       | 从软件源安装软件，卸载软件，获取更新，系统更新升级 |
| dpkg      | 安装本地deb软件包，卸载软件                        |
| apt-cache | 从软件源搜索软件                                   |
| apt-get   | 安装/卸载软件，系统更新                            |

## 7.2、apt

安装vim：sudo apt install 【软件包名称】

获取软件包更新：sudo apt update

升级软件包：sudo apt upgrade

移除软件包：sudo apt remove【软件包名称】

自动清除不需要的软件包：sudo apt autoremove

## 7.3、文本编辑工具-nano、vim

打开文件：nano 【文件名】

保存文件：Ctrl+S

另存为：Ctrl+O

退出：Ctrl + X

打开文件： vim [文件名 ]。如果文件不存在则会在保存时创建。

按 ESC 回到 ‘命令模式’
输入 : 切换到 ‘底行模式’
输入 q! 不保存退出，保存退出wq

# 8、IO重定向和管道

8.1、理解IO重定向

IO重定向就是更改输入输出数据的流向。

shell中【>】表示输出重定向

文件描述符0,1,2分别表示：

​	标准输入stdin、标准输出stdout、标准错误输出stderr

【理解IO重定向】：默认情况下，文件描述符 0 关联输入设备的设备
文件，在 PC 上，为键盘对应的设备文件。默认文件描述符 1,2 都关联输出设备的设备文件，在 PC 上，为当前显示设备对应文件，可简单理解为向屏幕输出。以输出重定向为例，如果程序运行时，文件描述符 1 不再关联输出设备的设备文件，而是关联到一个其他的文件。比如一个普通的文件，则输出结果就写入到文件，而不是输出到屏幕，这就是输出重定向。

![1560933461297](E:\大二下\base_nodes\img\重定向.png)

## 8.2、shell与重定向

| 符号     | 作用                 | 说明                                                         |
| -------- | -------------------- | ------------------------------------------------------------ |
| >    >>  | 输出重定向           | 重定向到指定文件，文件不存在则会创建，如果文件存在， > 会导致之前的内容丢失， >> 则会追加到文件末尾 |
| <        | 输入重定向           | 从指定文件获取输入，而不是通过键盘。                         |
| 2>   2>> | 错误输出重定向       | 错误输出重定向到文件，其他参考输出重定向                     |
| &>   &>> | 输出和错误输出重定向 | 标准输出和错误输出重定向                                     |

【示例】

**wc -l n.c 或 wc -l < n.c**
	–统计文件的行数，第一种情况是读取文件统计，第二种是获取输入并统计，但是输入重定向到 n.c 。
**find / -iname gcc* > find_tmp**
	–全盘搜索名称为 gcc 开头的文件，把结果保存到find_tmp ，但是错误信息会输出到屏幕。

**grep ‘runlevel’ /etc -R > greptmp 2> /dev/null**
	–在 /etc 目录递归搜索文件中的 runlevel ，把结果保存到 greptmp ，错误信息重定向到 /dev/null 。

## 8.3、管道

管道用于连接一个程序的输出和另一个程序的输入。
通过管道可以把多个命令组合在一起完成复杂的功能

shell中的管道字符： 【|】

shell解析命令遇见【|】就会创建管道。并且把前一个程序的输出重定向到管道，后一个程序的输入重定向到管道

【示例】

**cat a.c | less**
	–获取 a.c 文件的内容并使用 less 分页查看。
**find / -iname *gnome* | wc -l**
	–全盘搜索名称含有 gnome 的文件并通过 wc -l 统计结果

只有标准输出才会重定向到管道，标准错误输出不会。

# 9、进程管理

## 9.1、Linux进程基础

运行中的程序就是进程。系统会给每个进程分配一个数字进行标记，此数字就是进程ID，一般以PID表示。

PPID：父进程ID。

UID：每一个进程都有一个所属用户ID，就是运行程序的用户的ID。每一个进程都有一个父进程，通常情况下子进程的UID继承自父进程。

EUID：有效用户ID。表示进程对文件和资源的访问权限。（大多数情况下EUID和UID相同）

GID和EGID：组ID和有效组ID

## 9.2、进程管理相关命令

| 命令        | 含义                                        |
| ----------- | ------------------------------------------- |
| ps          | 查看当前进程                                |
| kill        | 向进程发送信号，通常是终止进程              |
| bg shell    | 内建命令，后台继续执行，就像在命令后面加入& |
| fg shell    | 内建命令，后台转至前台                      |
| jobs shell  | 内建命令，显示后台运行的任务                |
| pgrep       | 搜索进程                                    |
| top/htop    | 动态监控进程情况，系统资源使用情况          |
| nice/renice | 调整进程优先级                              |

**【查看进程】**

ps -e：查看所有进程

ps -e | grep 【进程名字】：用于搜索进程

按照‘用户， PID ， PPID ，命令，参数’的顺序显示：
	ps -e -o user,pid,ppid,comm,args

ps -ejh：显示进程树

ps -l 【PID】：显示某一进程的详细信息

ps aux | less：分页显示

**【搜索进程】**

pgrep -a sh ： 搜索名称含有 sh 的进程并显示详细信息。
pgrep -l ab： 搜索名称含有 ab 的进程，显示名称和 PID 

使用管道 ( 正则匹配 ) ：
 ps -e -o pid,comm,args | grep ‘node.*serv’

**【终止进程】**

以 kill 就是终止进程，一般以事实上，一般以 kill 是向进程发送信号。默认发送的信号是 SIGTERM ，一般以这个信号表示中断进程，一般以通常情况，一般以进程就会退出。

kill -l：可以查看所有的信号，显示信号名称和数字编号。

## 9.3、后台任务

【**后台任务】**

一个任务如果运行时间太长 , 或者是需要长期运行的情况 , 此时想要获取终端控制权。可以把任务转至后台运行。
如果需要暂停任务，一般以也可以把任务转至后台暂停。

【**暂停任务**】

Ctrl+Z或者kill -19 【PID】

【**管理后台任务**】

jobs显示后台任务

fg【任务编号】：任务转前台执行

bg【任务编号】:后台继续执行

【**直接在后台运行命令**】

在 shell 输入命令，一般以如果最后加上 & ，一般以则会在后台执行命令。
注意，一般以如果输出没有重定向，一般以则仍然会在shell 中显示，在后台运行的任务一般把输出进行重定向。

# 10、网络相关操作

Linux进行远程连接的是SSH协议

查看ip地址：ip addr或ip address或ip a

# 11、用户与权限更多细节

【权限控制标志位】

![1561019938573](E:\大二下\base_nodes\img\权限控制标志位.png)

## 11.1、修改密码

修改密码：passwd。

保存用户密码的文件：/etc/shadow（shadow只有root用户才能修改）

问题的解决不是给所有用户都具备 /etc/shadow 文件的写权限。
而是通过设置 passwd 命令所属用户为 root ，并设置set-user-ID 标志位。这样其他用户在运行 passwd 时就好像是 root 在执行。

## 11.2、sticky

 sticky位可以允许所有用户都可以在目录下创建文件，并设置但是只能删除自己的文件。

使用命令：chmod：

使用八进制数字： chmod 1777 tmp/

使用字符： chmod o+wt tmp/

需要配合可写权限，并设置否则其他用户也无法创建文件

【ls显示权限】

![1561021618838](E:\大二下\base_nodes\img\ls显示权限.png)

## 11.2、创建系统用户和用户组

创建系统用户组servg：sudo --system servg

创建系统用户servtest：sudo adduser servtest --system \
–-disabled-login –-disabled-password \
–-no-create-home –-ingroup servg （这里的\表示折行并继续）

# 13、shell脚本基础

shell可以从一个文件读取命令并逐条执行，这个文件一般称为shell脚本

```shell
shell脚本语言
#!/bin/bash
#!/bin/bash(python、node)这个第一行只是告诉遇见这类文件用哪个程序去执行，如果没有#！会用默认的shell去执行
uname -a
lspci -vt
```

## 13.1、设置变量

变量名称可以是字母数字下划线，但不能是数字开头

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