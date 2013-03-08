# iOS开发60分钟入门
本文面向已有其它语言（如Java，C，PHP，Javascript）编程经验的iOS开发初学者，初衷在于让我的同事一小时内了解如何开始开发iOS App，学习目标包括：

* 能使用XCode IDE、模拟器
* 能修改、调试已有iOS App
* 能在已有应用内创建新模块
* 能创建新应用
* 能发布应用到App Store

本文不包含任何高级的iOS开发知识，已学会iOS开发的同学不要看，看完这篇文章学会了的同学也不用再看了。


## 不仅是学习一门新语言
有过脚本开发经验的人（如Javascript，PHP，Shell）在刚开始学习iOS开发的时候，会觉得iOS开发的学习曲线比脚本语言要高，是的，这种感觉是对的。因为学iOS开发，不仅是学习一门新语言，它包括：

* 一门语言：Objective-C
* 一个框架：Cocoa Touch
* 一个IDE：XCode

初学脚本语言通常不会来绘制图形界面、与人交互，iOS如果不做图形界面，像脚本语言一样处理文本操作数据库，就没啥意思了。

所以，过去我写别的新手入门教程，通常都是写《XXX入门15分钟教程》，而iOS就要花数倍的时间来写了。

## 环境准备
做iOS开发一定要有苹果的软件环境：Mac OS操作系统、Objective-C编译器、设备模拟器等，开发工具倒不一定要用Xcode，只要是个源代码编辑工具就行（vim都行，只是没Xcode那么多功能）。


### Mac OS
拥有Mac OS环境最简单的方法是找一台苹果电脑，包括iMac, MacBook Pro, MacBook Air, Mac Mini，但不包括苹果的移动设备（iPod Touch, iPhone, iPad, iPad Mini，它们运行的是iOS系统，不是Mac OS），苹果电脑在出厂的时候就会预装Mac OS，目前比较主流的版本是Mac OS X 10.6、Max OS X 10.8。

如果囊中羞涩，可以借一台，或者上淘宝买个二手的。

#### 黑苹果
提到iOS开发入门，似乎没办法不说黑苹果。所谓黑苹果，就是把Mac OS改造后安装在非苹果的硬件上，这是违反DMCA法案的，黑苹果的更多资料，[可以在维基上找到](http://en.wikipedia.org/wiki/OSx86)

苹果电脑价格高，国内软件开发者生存压力大，所以黑苹果在国内也有一些真实的存在，国外当然也有啦。

黑苹果基本可以胜任iOS开发，但有一些问题：

- 安装黑苹果是非法的
- 个人行为苹果公司一般不会追究，但会遭同行的鄙视
- 黑苹果超级难装，挑硬件。即使完全相同的型号，相同的批次，也有可能A机器装上了，B机器装不上
- 黑苹果系统多少都存在一些使用上的问题，像驱动Bug啦、待机恢复蓝屏啦、上网浏览有问题啦
- 黑苹果不能随意升级，可能升级一次safari就导致整个系统崩溃了

上面这些虽然不会直接影响xcode写代码、模拟器测试，但写着写着想上网查个东西的时候，safari不能翻页，确实挺影响心情的。所以，钱包允许的前提下，还是搞个苹果电脑省心一些。

### Xcode 和 模拟器
Xcode可以在苹果官网免费下载：[Xcode下载地址](https://developer.apple.com/xcode/index.php)

安装Xcode时会自动安装iOS SDK和模拟器。

这么强大的IDE居然是免费的，还是挺让人开心的。


## 从改一个现成的应用开始吧
学一门新软件开发技能，能够第一时间做出一个可运行的产品非常重要，有助于给自己下面激励，我上大学的时候，有很多次想学一门新语言，往往花了半个月，还沉浸在数据类型和语法字典里，连第一个Hello World都没做出来。

这一次，就让我们从改一个现成的应用开始吧。

### 下载
首先，我们从苹果开发者中心下载一个示例代码回来。我选了[ToolBarSearch](https://developer.apple.com/library/ios/samplecode/ToolbarSearch/ToolbarSearch.zip)。

在本文档的末尾，还有一些其它的网址可以下载开源iOS产品或者代码段，但我试了一下，还是Apple Sample Code最容易成功。

下载回来的zip文件最好保存在"下载"或者"文稿"目录里，因为在Mac OS 10.8以前，有些目录（例如/var/private/tmp）在Finder中是看不到的，要通过Finder的“前往 > 前往文件夹”功能才能进入。

### 打开
有三种方式可以打开一个iOS Project
#### 双击project文件
打开Finder，进入刚刚下载解压的ToolBarSearch目录，找到ToolBarSearch.xcodeproj文件，双击之，XCode会自动启动，并打开这个项目

#### 在XCode里选择Project打开
- 在XCode没启动的情况下（如果XCode已经启动了，就先按Command Q退出），启动XCode，会弹出“Welcome to XCode”的欢迎页，点击左下角的“Open Other”按钮，找到ToolBarSearch目录，双击ToolBarSearch目录，或者双击ToolBarSearch.xcodeproj文件都可以

- 如果Xcode处于打开状态，可以点击其菜单栏的File -> Open，或者File -> Open Recent，然后再选择要打开的项目

#### 通过命令行打开
在Mac OS 10.8以前，有些目录（例如/var/private/tmp），在Finder和XCode的File > Open对话框中，点击鼠标是找不到的，这时候就要通过命令行终端来打开了。

打开终端，执行：

	cd /ToolBarSearch的父目录/ToolBarSearch
	open -a Xcode

open -a是mac os的系统命令，除了iOS项目，别的项目也可以这样打开。

### 运行刚下载的应用
点击XCode左上角的Run按钮（或者同时按下Comman和R键），XCode会编译源码并在模拟器中运行这个应用。

编译成功会在屏幕上淡淡地显示“Build Succeeded”。反之，失败就显示“Build Failed”且不启动模拟器。


### 修改
在模拟器上看到“Performed search using…”了吧，下面我们改掉它。

- 在XCode左上角的Run按钮下方，有一排小按钮，从左到右第三个是一个放大镜图标，鼠标移上去会显示“Show the Search Navigator”，点一下它，打开搜索界面，在它下方出现的Find输入框中输入“performed”

- 搜索结果只有一条：ToolbarSearchViewController.m，点文件名下方被高亮的“Performed”字串，右侧代码编辑区会自动打开这个文件，并滚动屏幕，使包含“Performed”的这一行出现在编辑区的中间。

- 修改双引号里的字串，随便改成啥，然后按“Command S”保存。

当然，这些操作，你也可以在终端下通过grep和vim完成。

### 运行修改后的应用
按Command R运行，看看，是不是看到效果啦？

是的，修改一个应用就这么简单。


## Objective-C
### C的超集
### SmallTalk的语法风格
### 类似Java的OOP概念
GoogleCode上有人整理了Java和Objective-C的概念、数据类型对应表，[参见这里](http://code.google.com/p/j2objc/wiki/JavaConversions)
### 头文件
### 类
#### 接口和实现
#### 继承
#### 私有和公开
#### 类方法和实例方法
类方法就是Java、PHP里的Static Method，不用实例化就能调
实例方法就是Java、PHP里的普通方法，必须实例化才能调

### Protocol
就是Java、PHP里的Interface

### Category

### Selector

## Cocoa Touch
### 最常用设计模式之Delegate
### 常用控件：按钮、文本块、图片、输入框
### TableView
### WebView
### 导航条

## XCode
### 运行
### 搜索
#### 搜索文本
#### 搜索文件
### 新建文件/目录
推荐在Finder中新建好的再添加进来
### 断点
### 打包

## 从头新建一个应用：Hello World

## 其它
### 代码里的控件尺寸
是指Point，iPhone 4和iPhone 3GS的Point数是一样的，尽管iPhone 4的分辨率是3GS的2倍。

### SVN操作含有@符号的文件

### XCode中的代码结构与操作系统上的文件系统并不一致

### iPhone 5适配

### 参考代码
* [Apple官方的Sample Code](https://developer.apple.com/library/ios/navigation/#section=Resource%20Types&topic=Sample%20Code)
* [维基百科上的开源iOS App](http://en.wikipedia.org/wiki/List_of_free_and_open_source_iOS_applications)
* [iOS Opensource](http://www.iosopensource.com/) --Domain Parking了，以前可以下载Twitter和Wordpress客户端的
* [code 4 app](http://code4app.com/)
* [UI 4 app](http://ui4app.com/)， code4app的姐妹站