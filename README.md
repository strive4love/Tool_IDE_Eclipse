# 简介
--------------
Eclipse 是一个开放源代码的、基于Java的可扩展开发平台。最初是由IBM公司开发,2001年11月贡献给开源社区，现在它由非营利软件供应商联盟Eclipse基金会（Eclipse Foundation）管理，Eclipse基金会每年都会安排同步发布新的版本。就其本身而言，它只是一个框架、平台，但是众多插件的支持使得Eclipse拥有其他功能相对固定的IDE软件很难具有的灵活性，许多软件开发商以Eclipse为框架开发自己的IDE。

# 版本
-------------
版本代号       平台版本
Eclipse galieo 3.5
Eclipse Helios 3.6.0
Eclipse Indigo 3.7
Eclipse Kepler 4.3 
Eclipse Luna   4.4
Eclipse Mars   4.5
可通过导航栏里的Help -> About Eclipse 查看其版本
Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）。

# Open all type of text file
---------------
Eclipse支持各种类型文件的查阅，但需事先配置。点击导航栏里的 window -> Preferences->General -> Content Types->Text，add各种类型的文本文件（*.sql *.csv for example）

# 字符集设置
---------------
Navication window -> Preferences->General -> Workspace, You can find Default Caricater Set is GBK on right, You can click Ohter radio to change caricater set.

# 插件机制
----------------
Eclipse使用插件来提供所有的附加功能。Eclipse 附带了一个标准的插件集，包括Java开发工具（Java Development Kit，JDK）。插件架构能够支持将任意的扩展加入到现有环境中，例如配置管理，而决不仅仅限于支持各种编程语言。
Eclipse的设计思想是：一切皆插件。Eclipse核心很小，其它所有功能都以插件的形式附加于Eclipse核心之上。Eclipse基本内核包括：图形API (SWT/Jface)， Java开发环境插件(JDT )，插件开发环境(PDE)等。

# 插件安装
----------------
Eclipse插件的安装方法大体有以下几种方式：
###直接复制法
假设Eclipse的安装目录在C:\eclipse，解压下载的eclipse 插件或者安装eclipse 插件到指定目录AA(如：c:\AA)文件夹，打开AA 文件夹，在AA文件夹里分别包含两个文件夹features和plugins ，然后把两个文件夹里的文件分别复制到C:\eclipse下所对应的文件夹下的features 和plugins 下，一般的把插件文件直接复制到eclipse目录里是最直接也是最愚蠢的一种方法！因为日后想要删除这些插件会非常的困难，不推荐使用。
注意：直接将插件包解压到plugins文件夹下之后，重启eclipse，可能不会加载新的插件。
解决方法是：
1、打开命令行，到当前eclipse的目录下，输入eclipse -clean，重新启动eclipse，这样eclipse就会加上新的插件了。
2、如果插件不能生效，则请将eclipse\configuration\org.eclipse.update目录删除后再启动eclipse；
你可以在eclipse的菜单"Help"-->"About Eclipse SDK"-->"Feature Details" 和"Plug-in Details"中看到新安装的插件。
###使用link文件法
下载下来的插件可能有几种形式：一是单独的Jar文件，二是plugins和features两个文件夹，三是一个单独的eclipse文件夹。
a.准备工作:如果插件是一个单独的jar文件，那么你需要做三件事:先建一个plugins文件夹，把jar文件放入其中，再建一个eclipse文件夹，把plugins放入其中，最后打个比方：如果你下载的是一个名为WBPro的插件，你需要建一个WBPro文件夹，把刚才的eclipse文件夹放入其中。(不一定非得命名为WBPro，你可以用其他名字，如AAA，bb等，注：此句话可先不看)。好了，插件的大致结构出来了，如下 
WBPro/eclipse/plugins/**.jar 
如果插件是plugins和features两个文件夹（或只有plugins文件夹），请建一个名为eclipse的文件夹，把上面的两个文件夹放入其中，再建一个名为WBPro的文件夹，把刚才的eclipse文件夹放入其中，插件的大致结构如 下:
WBPro/eclipse /{plugins，features}
如果插件就是一个eclipse文件夹，请新建一个WBPro文件夹，把eclipse放入其中，插件的结构如下：
WBPro/eclipse 
b.开始安装:找到你的eclipse ，在其下建两个文件夹，一个是extplugins，一个是links，结构如下{eclipse/extplugins,links},把你刚才建立的插件WBPro放入extplugins中，然后在links文件夹下，建立一个txt文本，在里面写入：path=extplugins/WBPro,注意是“/”,而不是“\”,再把文本文件命名为WBPro.link，注意全名是WBPro.link，而不是WBPro.link.txt， 好了，启动eclipse，在菜单栏点击window->Preferences,在弹出来的对话框中，看左 
边的导航栏，如果里面有你的插件名，如WBPro，恭喜你插件安装成功！ 
###使用eclipse自带图形界面安装
选择Help > Software Updates > Manager Configuration，再选择Add > Extension Location 找到你要安装插件的目录就可以了。使用eclipse的help->SoftwareUpdates ->Find and install... search for new features... 输入软件安装地址进行安装强烈推荐这种方法，优点很多比如可以方便的添加删除，也不用自己写link文件！
备注：Eclipse插件的目录结构
Java代码
/eclipse-plugins/
eclipse/
.eclipseextension
features/
plugins/
第2.3种方法所指向的目录都指的是"eclipse"目录，
如果用第3种方法，在eclipse这个目录下必须有文件.eclipseextension，如果下载的插件没有这个文件，
那就随便eclipse安装目录下的那个文件拷过去就行，只要有这么个文件就可以了，内容没什么用，主要是一些版本信息。例如：
Java代码
id=org.eclipse.platform name=Eclipse Platform
version=3.1.1
id=org.eclipse.platform name=Eclipse Platform version=3.1.1
###使用dropins安装插件
Eclipse Macketpalce
Eclipse Macketpalce
从Eclipse3.5开始，安装目录下就多了一个dropins目录。只要将插件解压后拖到该目录即可安装插件。
比如安装svn插件subclipse-1.8.16.zip，只需要如下的三步即可：
1、使用winrar等压缩软件将压缩包解压至某一文件夹，比如subclipse-1.8.16
2、将此目录移动/复制至Eclipse安装目录下的dropins目录
3、重启Eclipse。
由于此种安装方式可以将不同的插件安装在不同的目录里，并且不用麻烦地写配置文件，因此管理起来会非常方便，推荐使用。
###使用Eclipse Macketplace
在新版eclipse中选择Help > Software Updates >Eclipse Macketplace，这里有eclipse的插件市场，如图所示，可以直接搜索安装需要的插件，不必配置，一键安装，使用更加方便了。
隐藏功能
每个人都会使用到一些静态方法类库。从Java 5之后，我们可以静态进入它们，所以我们不再需要像下面这样写代码。
SomeVeryImportantUtility.split(string1, string2);
但是，谁又会愿意在每一个类中去把所有那些方法都手动的进行静态进入呢? 没有人。因为你可以在选项中定义你的收藏类型和收藏成员：
Preferences > Favorites
然后，你只需要敲入开头的字母并使用自动补全功能：
自动补全
自动补全功能也可以进行必要的静态引入。比方说在使用DSL的诸多功能时，这就非常有用。很明显，你需要谨慎决断，哪些是你真正最常用到的类库，以及哪些是这些类库中你最常用到的类。如果你是jOOQ blog(或是其联盟的一员)的用户，我可以给你一个提示。即永远把org.jooq.impl.DSL纳入收藏。

#插件管理
----------------
启动eclipse，在菜单Help->Software Updates->Manage Configuration…下，启用或者禁用插件。 

# C:\Program Files\Eclipse Kepler 4.3\eclipse.ini文件
----------------
-startup
plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_1.1.100.v20110502
-product
org.eclipse.epp.package.jee.product
--launcher.defaultAction
openFile
--launcher.XXMaxPermSize//堆的最大值
256M
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
--launcher.defaultAction
openFile
-vm
D:\glassfish3\jdk\bin\javaw.exe   
//注意: -vm的设置要写在两行，写在一行不能生效；这两行要定在-vmargs之前，不然也不能生效。
//这两行的作用是为eclipse指定JRE，也可以将-vm设置为C:\Program Files\Java\jdk1.6.0_10\bin\
-vmargs //说明后面是VM的参数
-Dosgi.requiredJavaVersion=1.5
-Xms40m//虚拟机占用系统的最小内存,初始分配
-Xmx512m//虚拟机占用系统的最大内存,按需分配


#Project->Build Automatically
最近做项目，每次保存修改的东西。Eclipse都会building workspace（重新编译）一下。并且那 building的速度真是够慢的啊，严重影响编程速度。 在网上也发现遇到此问题的很多，但是解决的方法不是很多啊。大部分都是说把菜单栏project下的building automatically勾掉。不过这样是不building了。 但是你所做的修改在客户端都没有显示。必须再勾选building automatically 。这样项目还是会出现building workspace。治标不治本啊（说白点就是减少了building 次数，但是需要手动去控制building）
在网上找到了一些资料整理出了一个自己的方法：Step_1.选择菜单栏里的project里的properties；（如果properties显示为不可用（灰色），就先build all或者 build   project，就会出现properties）；Step_2.进去找到builders 把 validation和javaScript Validator 不选中。如上操作就可以了。再去Eclipse中修改保存下。building workspace应该消失了。

# 常用快捷键：
Ctrl+shift+t /检索类
Ctrl+shift+r/检索资源
Ctrl+shift+f/代码格式化
Ctrl+/或Ctrl+7/单行（取消）注释
Ctrl+q/检索java关键字
Ctrl+w/保存后关闭当前类
Ctrl+e/查看当前窗口下已打开的所有资源
Ctrl+d/删除当前行
Ctrl+g/search操作
Ctrl+h/search操作
Ctrl+l/代码行定位
Ctrl+m/最大（小）化
Alter+/: 辅助快捷键
所有快捷键的设置：windows -> properties -> General -> Keys

