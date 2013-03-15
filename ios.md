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
Objective-C是苹果应用软件（包括苹果电脑上的Mac OS App和移动设备上的iOS App）的开发语言。它是一种面向对象的编程语言。

苹果公司还提供了一个软件（Interface Builder，简称IB）用于可视化的界面制作，就像用Dreamweaver做网页，或者像Visual Basic做桌面软件一样。但这篇文档不讲IB，只讲Objective-C，因为：

- 基本上，每一本讲iOS开发的书（纸质书、电子书），都有大量的截图一步一步教如何用IB开发iOS应用，而讲Objective-C开发应用的书却没有那么多。
- IB可以用来直观方便地画界面、设置控件属性、建立代码与控件的联系，但后台的业务逻辑和数据处理仍然要靠Objective-C，可见，不管用不用IB，Objective-C都是绕不过去的。

### C的超集
Objective-C扩展了ANSI C，是C的超集，也就是说：

- 任何C源程序，不经修改，即可通过Objective-C编译器成功编译
- Objective-C源程序中可以直接使用任何C语言代码

除了面向对象有语法是SmallTalk风格的（下面会讲到），其它非面向对象的语法、数据类型，与C完全相同，所以本文就不再赘述。
来看一个经典的Hello World示例吧：

	#import <Foundation/Foundation.h>
	int main(int argc, char *argv[]){
		@autoreleasepool{
			NSLog(@"Hello World!");
		}
		return 0;
	}
是不是仿佛穿越回了大一学习C语言的时代，看起来和C几乎没有区别，是吧？是的，因为还没用到它的面向对象特性，哈哈！

### SmallTalk的消息传递语法风格
Objective-C的面向对象语法源自SmallTalk，消息传递（Message Passing）风格。在源码风格方面，这是它与C Family语言（包括C/C++、Java、PHP）差别最大的地方。

在Java、C++世界，我们调用一个对象的某方法，在Objective-C里，这称作给类型发送一个消息，这可不仅仅是文字游戏，他们的技术细节也是不同的。

在Java里，对象和方法关系非常严格，一个方法必须属于一个类/对象，否则编译是要报错的。而在Objective-C里，类型和消息的关系比较松散，消息处理到运行时（runtime）才会动态决定，给类型发送一个它无法处理的消息，也只会抛出一个异常，而不会挂掉。

	[obj undefinedMethod];

在代码里调用没定义的方法（这是Java世界的习惯说法啊，专业的叫法是，给obj对象传递它无法处理的消息），XCode会警告，但编译能成功，运行的时候会出错。它会输出这样一个错误：

	Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[NSObject undefinedMethod]: unrecognized selector sent to instance 0x8871710'

### 类似Java的OOP概念
Objective-C中一些面向对象的概念，也可以在Java中找到类似的实现（只能说是类似，不是完全相同），我的读者基本都是Java和PHP程序员，我会在下文中尽量用Java的概念来类比。

GoogleCode上有人整理了Java和Objective-C的概念、数据类型对应表，[参见这里](http://code.google.com/p/j2objc/wiki/JavaConversions)

### 字符串
Objective-C里有字符串是由双引号包裹，并在引号前加一个@符号，例如：

	title = @"Hello";
	if(title == @"hello") {}

PHP程序员要注意，在这里不能用单引号，即使只有一个字符也不能用。Objective-C与Java、C一样，双引号表示字符串。

### 函数调用
前文述及，不涉及面向对象时，它和C是完全一样的。以下是几个函数调用的示例：

#### 不带参数

	startedBlock();

#### 带参数

	NSLog(@"decrypted string: %@", str);
	CGRectMake(0,0,0,0);

### 传递消息给类/实例方法

#### 不带参数

	[obj method];

对应的Java版本

	obj.method();

#### 带一个参数：

	[counter increase:1];

对应的Java版本

	counter.increase(1);

#### 带多个参数
对C Family程序员来说，这是最难接受的，最反人类的：
	
	- (void) setColorToRed: (float)red Green: (float)green Blue:(float)blue {...} //定义方法
	[myObj setColorToRed: 1.0 Green: 0.8 Blue: 0.2]; //调用方法

对应的Java版

	public void setColorToRedGreenBlue(float red, float green, float blue) {...}
	myObj.setColorToRedGreenBlue(1.0, 0.8, 0.2);

#### 消息嵌套

	UINavigationBar *bar = [[[UINavigationBar alloc] init] autorelease];

对应的Java版

	UINavigationBar bar = UINavigationBar.alloc().init().autorelease();//Java没有指针，所以星号去掉了

### 类

#### 接口和实现
Objective-C的类分为接口定义和实现两个部分。接口定义（Interface）放在头文件中，文件扩展名是.h，实现（implementation）放在实现文件中，文件扩展名是.m（也有.mm的扩展名，表示Objective-C和C++混编的代码）。

`接口定义也可以写在.m文件中，但最好不要这么干`

需要注意的是，与Objective-C的interface概念最接近的是C和C++里的头文件，它与implementation是成双成对出现的，作用是声明类的成员变量和方法。它与Java的interface概念完全不同：

- Objective-C里，interface有且只有一个实现，Java的interface可以有0-N个实现
- Objective-C里，interface可以定义成员属性，Java里不可以
- Objective-C里，interface可以定义私有方法，Java里的interface定义的方法都是public的

和Java里的Interface概念相似的是Protocol，下文会讲到。

请看示例：

Interface

	@interface MyClass {
    	int memberVar1;
    	id  memberVar2;
	}

	-(return_type) instance_method1; 
	-(return_type) instance_method2: (int) p1;
	-(return_type) instance_method3: (int) p1 andPar: (int) p2;
	@end

Implementation

	@implementation MyClass {
		int memberVar3;
	}
 
	-(return_type) instance_method1 {
    	....
	}
	-(return_type) instance_method2: (int) p1 {
    	....
	}
	-(return_type) instance_method3: (int) p1 andPar: (int) p2 {
    	....
	}
	@end

接口和实现以@interface、@implementation开头，都以@end结束。“@”符号在Objective-C中是个很神奇的符号。

冒号也是方法名的一部分，method和method:是两个不同的方法名，不是overload，第二个带参数。

上述代码对应的Java版：

	public class MyClass {
		protected int memberVar1;
		protected pointer memberVar2;
		private int memberVar3;
		
		public (return_type) instance_method1() {
			....
		}
		
		public (return_type) instance_method2(int p1) {
			....
		}
		
		public (return_type) instance_method3andPar(int p1, int p2) {
			....
		}
	}

#### 私有方法和公开方法
写在.h头文件里的方法都是公开的，Objective-C里没有私有方法的概念（没有你说个蛋啊，哈哈哈哈）。

要实现私有方法的效果只能借助Category，知道有这么回事就可以了，这里不深讲。

#### 类方法和实例方法
##### 类方法
类方法就是Java、PHP里的Static Method，不用实例化就能调。类方法有一个加号前缀。
示例：

类定义

	@interface MyClass
		+(void) sayHello;
	@end

	@implementation MyClass
 
	+(void) sayHello {
    	NSLog(@"Hello, World");
	}
	@end

使用

	[MyClass sayHello];

##### 实例方法
实例方法就是Java、PHP里的普通方法，必须实例化才能调。实例方法有一个减号前缀。
示例：

类定义

	@interface MyClass : NSObject
	-(void) sayHello;
	@end

	@implementation MyClass
 
	-(void) sayHello {
    	NSLog(@"Hello, World");
	}
	@end

使用

	mycls = [MyClass new];
	[mycls sayHello];

#### Selector
selector就是一个方法指针，类似PHP里的动态方法名：

	<?php
	class Hello {
		public function sayHello() {}
		
		public function test() {
			$fun_name = "sayHello";
			$this->$fun_nam();
		}
	}

在Objective-C里，selector主要用来做两类事情：

##### 绑定控件触发的动作

	@implementation DemoViewController
	- (void)downButtonPressed:(id)sender {//响应“按钮被按下事件”的方法
		UIButton *button = (UIButton*)sender;
		[button setSelected:YES];
	}
	
	- (void)drawAnButton {
		UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom]; 
		btn.frame = _frame; 
		btn.tag = 1;
		btn.backgroundColor = [UIColor clearColor];
		[btn addTarget: self action: @selector(downButtonPressed:) forControlEvents: UIControlEventTouchUpInside];//当这个按钮被按下时，触发downButtonPressed:方法
	}
	@end

#### 延时异步执行

	@implementation ETHotDealViewController
	- (void)viewDidLoad {
		
		//获取数据源
		HotDealDataSource *ds = [[HotDealDataSource alloc]init];
		[ds reload];
		_items = ds.items;
		
		[self performSelector:@selector(refreshTable) withObject:self afterDelay:0.5];//延迟0.5秒调用refreshTable方法
	}
	
	-(void)refreshTable
	{
		[self.tableView reloadData];
	}
	@end

这个例子中，获取数据源是通过ASIHTTP组件异步调用服务端HTTP接口，refreshTable要用到数据源返回回来的数据，如果不延迟0.5秒，就会立刻执行，执行的时候页面就是空白了（这时候数据还在路上呢）。

### 继承
继承是写在Interface定义里面的。语法为：子类名在左，父类名在右，中间用冒号分隔。
示例：

	@interface MyClass : NSObject
	@end

对应的Java版本是：

	public class MyClass extends NSObject {
	}

### 协议（Protocol）
就是Java、PHP里的Interface。

#### 协议的定义
协议的定义用@protocol关键字：

	@protocol Printable
		-(void)print:(NSString)str;
	@end

对应的Java版本是：

	publilc interface Printable {
		public void print(String str);
	}

##### 协议的继承
协议本身也可以继承别的协议：

	@protocol Printable <NSObject>
		-(void)print:(NSString)str;
	@end

对应的Java版本：

	public interface Printable extends NSObject {
		public void print (String str);
	}

##### 可选方法
协议可以包含可选方法，顾名思义，可选方法可以不被类实现：

	@protocol Printable
	@optional
		-(void)print:(NSString)str;
	@end

加了@optional关键字，一个类在implements这个协议时，便可以不实现print:方法。

Java里没有类似的实现，除了Collection里会有一些方法带有optional的注释，但Collection是个特例。
	
#### 协议的实现
一个类实现某些协议是写在Interface定义里面的。语法为：协议名用尖括号包裹，多个协议名用逗号隔开，协议写在父类的右边（如果没有父类就直接写在子类右边）。

示例：

	@interface  class MyClass : NSObject <Printable, Drawable>
	@end

Printable, Drawablw就是两个协议。

对应的Java版本是：

	public class MyClass extends NSObject implements Printable, Drawable {
	}

### 分类（Category）
分类可以给一个已经存在的类增加方法，而不用去改它的源码。Java和PHP中都没有类似的特性。

比如说，NSObject是一个Objective-C内置的系统类，我们想给它增加toJson方法，就像这样：

头文件：NSObject+Json.h

	@interface NSObject (Json)
		-(NSString)toJson;
	@end
	
实现文件：NSObject+Json.m

	@implementation NSObject (Json)
		-(NSString)toJson {
			//...
		}
	@end

使用的时候，只要包含NSObject+Json.h，实例化NSObject类，就可以使用toJson方法了：

	import "NSObject+Json.h"
	@implatementation XYZController
		-(void)test {
			NSObject *obj = [[NSObject alloc]init];
			NSString *str = [obj toJson];
		}
	@end

当然了，NSObject本来的那些方法依然还是可以用的，什么都没变，只是多了个toJson方法。看起来是不是和继承没太多差别呢（除了使用的时候实例化的是NSObject，而不是JsonObject）？再看一个继承实现不了的例子：

头文件：NSObject+Json+XML.h

	@interface NSObject (Json)
		-(NSString)toJson;
	@end
	
	@interface NSObject (XML)
		-(NSString)toXML;
	@end
	
实现文件：NSObject+Json+XML.m

	@implementation NSObject (Json)
		-(NSString)toJson {
			//...
		}
	@end
	
	@implementation NSObject (XML)
		-(NSString)toXML {
			//...
		}
	@end

使用：

	import "NSObject+Json+XML.h"
	@implatementation XYZController
		-(void)test {
			NSObject *obj = [[NSObject alloc]init];
			NSString *json = [obj toJson];
			NSString *xml = [obj toXML];
		}
	@end

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

### 开源代码
* [Apple官方的Sample Code](https://developer.apple.com/library/ios/navigation/#section=Resource%20Types&topic=Sample%20Code)
* [维基百科上的开源iOS App](http://en.wikipedia.org/wiki/List_of_free_and_open_source_iOS_applications)
* [iOS Opensource](http://www.iosopensource.com/) --Domain Parking了，以前可以下载Twitter和Wordpress客户端的
* [code 4 app](http://code4app.com/)
* [UI 4 app](http://ui4app.com/)， code4app的姐妹站

### Objective-C教程
- [Apple官方教程](http://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html)
- [Cocoa Dev Center](http://cocoadevcentral.com/d/learn_objectivec/)
- [维基上的Objective-C语言简介](http://zh.wikipedia.org/wiki/Objective-C) --中文，十分钟可读完，推荐
