Shell编程30分钟入门
=================
## 什么是Shell脚本
看个例子吧：

	#!/bin/bash

	#--------------------------------------------
	# 这是一个自动打ipa的脚本
	# 功能：自动为etao ios app打包，产出物为14个渠道的ipa包
	# 特色：全自动打包，不需要输入任何参数
	#--------------------------------------------

	##### 用户配置区 开始 #####
	#
	#
	# 项目根目录，推荐将此脚本放在项目的根目录，这里就不用改了
	project_path=`pwd`

	# app logo文件地址，就是那个512 * 512的PNG文件
	app_logo_path=${project_path}/Classes/NewETao/images/icon/app_icon/Icon-512.png

	# 打什么包，Release还是Debug，区分大小写
	build_config=Release
	#build_config=Debug

	# 应用名，确保和Xcode里Product下的target_name.app名字一致
	target_name="etao4iphone"
	

## 环境
shell编程跟java、php编程一样，只要有一个能编写代码的文本编辑器和一个能解释执行的脚本解释器就可以了。

### OS
当前主流的操作系统都支持shell编程，本文档所述的shell编程是指Linux下的shell，讲的基本都是POSIX标准下的功能，所以，也适用于Unix及BSD（如Mac OS）。

#### Linux
Linux默认安装就带了shell解释器。

#### Mac OS
Mac OS不仅带了sh、bash这两个最基础的解释器，还内置了ksh、csh、zsh等不常用的解释器。

#### Windows上的模拟器
windows出厂时没有内置shell解释器，需要自行安装，为了同时能用grep, awk, curl等工具，最好装一个cygwin或者mingw来模拟linux环境。

- [cygwin](www.cygwin.com)
- [mingw](www.mingw.org)

### 脚本解释器
#### sh
即Bourne shell，POSIX标准的shell解释器，它的二进制文件路径通常是/bin/sh，由Bell Labs开发。

#### bash
Bash是Bourne shell的替代品，属GNU Project，二进制文件路径通常是/bin/bash。业界通常混用bash、sh、和shell，比如你会经常在招聘运维工程师的文案中见到：熟悉Linux Bash编程，精通Shell编程。

在CentOS里，/bin/sh是一个指向/bin/bash的符号链接:

	[root@centosraw pp]# ls -l /bin/*sh
	-rwxr-xr-x. 1 root root 903272 Feb 22 05:09 /bin/bash
	-rwxr-xr-x. 1 root root 106216 Oct 17  2012 /bin/dash
	lrwxrwxrwx. 1 root root      4 Mar 22 10:22 /bin/sh -> bash

但在Mac OS上不是，/bin/sh和/bin/bash是两个不同的文件，尽管它们的大小只相差100字节左右:

	iMac:~ wuxiao$ ls -l /bin/*sh
	-r-xr-xr-x  1 root  wheel  1371648  6 Nov 16:52 /bin/bash
	-rwxr-xr-x  2 root  wheel   772992  6 Nov 16:52 /bin/csh
	-r-xr-xr-x  1 root  wheel  2180736  6 Nov 16:52 /bin/ksh
	-r-xr-xr-x  1 root  wheel  1371712  6 Nov 16:52 /bin/sh
	-rwxr-xr-x  2 root  wheel   772992  6 Nov 16:52 /bin/tcsh
	-rwxr-xr-x  1 root  wheel  1103984  6 Nov 16:52 /bin/zsh

#### 高级编程语言
理论上讲，只要一门语言提供了解释器（而不仅是编译器），这门语言就可以胜任脚本编程，常见的解释型语言都是可以用作脚本编程的，如：Perl、Tcl、Python、PHP、Ruby。Perl是最老牌的脚本编程语言了，Python这些年也成了一些linux发行版的预置解释器。

编译型语言，只要有解释器，也可以用作脚本编程，如C shell是内置的（/bin/csh），Java有第三方解释器Jshell，Ada有收费的解释器AdaScript。

## 如何选择shell编程语言
### 熟悉 vs 陌生
如果你已经掌握了一门编程语言（如PHP、Python、Java），建议你就直接使用这门语言编写脚本程序，虽然某些地方会有点啰嗦，但你能利用在这门语言领域里的经验（单元测试、单步调试、IDE、第三方类库）。

新增的学习成本很小，只要潌怎么使用shell解释器（Jshell、AdaScript）就可以了。


### 简单 vs 高级
如果你觉得自己熟悉的语言（如Java、C）写shell脚本实在太啰嗦，你只是想做一些备份文件、安装软件、下载数据之类的事情，学着使用sh，bash会是一个好主意。

shell只定义了一个非常简单的编程语言，所以，如果你的脚本程序复杂度较高，或者要操作的数据结构比较复杂，那么还是应该使用Python、Perl这样的脚本语言，或者是你本来就已经很擅长的高级语言。因为sh和bash在这方面很弱，比如说：

- 它的函数只能返回字串，无法返回数组
- 它不支持面向对象，你无法实现一些优雅的设计模式
- 它是解释型的，一边解释一边执行，连PHP那种预编译都不是，如果你有一个test.sh，其中包含语法错误，只要没执行到这一行，它就不会报错


## 第一个shell脚本
### 编写
### 运行

## 管道

## 变量

## 条件判断

## 流程控制
### if else
### for while
### switch case

## 函数

## 文件包含

## 用户输入
### 执行脚本时传入
### 脚本运行中畭
### select菜单

## stdin和stdout

## 常用的命令
### ps
### grep
### awk
### sed
### xargs
### curl