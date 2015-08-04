记录android开发过程中遇到的问题。
===


##### 1.在一个xml中能否使用同一个include多次 

http://www.apkbus.com/android-104152-1-1.html


  android中include标签的使用

http://blog.csdn.net/wangljgood/article/details/6556175


##### 2. android button在 linerlayout中底部居中 

	把button外的权重设为1.0


##### 3.button  shape
	http://www.cnblogs.com/gzggyy/archive/2013/05/17/3083218.html

##### 4.  animation
	http://www.eoeandroid.com/forum.php?mod=viewthread&tid=564
	http://blog.csdn.net/feng88724/article/details/6318430
	http://www.360doc.com/content/13/0102/22/6541311_257754535.shtml
	http://blog.csdn.net/aminfo/article/details/7847761
	http://blog.csdn.net/xsl1990/article/details/19125193
	http://www.cnblogs.com/bavariama/archive/2013/01/29/2881225.html
	http://www.oschina.net/question/97118_34523
	http://www.eoeandroid.com/thread-67329-1-1.html


##### 6.imageview 按比例缩放
    android:scaleType是控制图片如何resized/moved来匹对ImageView的size。

    ImageView.ScaleType / android:scaleType值的意义区别：

    CENTER /center  按图片的原来size居中显示，当图片长/宽超过View的长/宽，则截取图片的居中部分显示

    CENTER_CROP / centerCrop  按比例扩大图片的size居中显示，使得图片长(宽)等于或大于View的长(宽)

    CENTER_INSIDE / centerInside  将图片的内容完整居中显示，通过按比例缩小或原来的size使得图片长/宽等于或小于View的长/宽

    FIT_CENTER / fitCenter  把图片按比例扩大/缩小到View的宽度，居中显示

    FIT_END / fitEnd   把图片按比例扩大/缩小到View的宽度，显示在View的下部分位置

    FIT_START / fitStart  把图片按比例扩大/缩小到View的宽度，显示在View的上部分位置

    FIT_XY / fitXY  把图片不按比例扩大/缩小到View的大小显示

    MATRIX / matrix 用矩阵来绘制，动态缩小放大图片来显示。


android如何获取时间差？  

##### 7.ImageLoader must be init with configuration before using 错误解决方法 
imageLoader.init(ImageLoaderConfiguration.createDefault(MainActivity.this));

##### 8.java.lang.StackOverflowError
StackOverflow  这个问题一般是你的程序里头可能是有死循环或递归调用所产生的；


##### 9.java.lang.ClassCastException: android.app.Application cannot be cast to MyApplication问题 

出这个异常的原因是在项目中添加了新application类（public class Application extends android.app.Application）之后，没有在manifest.xml中添加该类的声明，所以编译器抛出异常： java.lang.ClassCastException: android.app.Application cannot be cast to android_serialport_api.sample.Application

解决方法，在manifest.xml中添加：
[html] view plaincopy

    <application  
     android:name="xxx.MyApplication">  

##### 10. event.getAction();


##### 11. Found both android-support-v4 and android-support-v13 in the dependency list.
 

##### 12.   怎么关联android-support-v4源码
	问题：使用viewpager或者fragmentActivity等一些v4包下的类，当我们按F3时无法查看到源码，这个时候就需要我们关联该源码，该源码的关联与android源码的关联不一样。

	解决办法：

	1、首先在工程的libs目录下创建一个配置文件：android-support-v4.jar.properties（建议这样）

	2、查找自己安装的SDK的目录下的android-support-v4的src源码地址

	本人的为：D:\eclipse\android-sdk\extras\android\compatibility\v4\src

	3、编辑android-support-v4.jar.properties文件为：（注意是双斜杠）

	src = D:\\eclipse\\android-sdk\\extras\\android\\compatibility\\v4\\src

	4、关闭自己的工程后再打开，此时进去选择ViewPager后F3就能看到源码了。

	5、恭喜：android-support-v4 源码已经成功的关联上。

还有种方式，http://blog.csdn.net/leon90dm/article/details/8521939，没试。

****上面是eclipse中的做法，在androidstudio中的使用更简单。****

##### 13.eclipse 修改设置Ctrl+Shift+F长度 

	在window的Preferences中的Java->Code Style->Formatter

	到了这一步就是找到Ctrl+Shift+F的格式化模板了，这里不能直接修改。因为是eclipse默认的模板，是只读的。

	我们可以new 一个Formatter，然后点击edit就可以修改模板。

	我修改模板主要就是修改那个Ctrl+Shift+F后，把我的代码换多行了。

	修改选项卡中的Line Wrapping选项卡， 有一个Maximum line with： 80（默认）；

	这里默认是80我们可以把它修改成120的，那样不超过120个字符就不会被换行了！

	其他自己需要的格式都可以在这里面修改。当然你还可以导出你自定义的格式，导出的是xml格式的。以后在其他地方

	还可以导入。这样就不用再自定义了。

##### 14. android-develop 镜像路径[重点推荐]
	http://androiddoc.qiniudn.com/
   google，被和谐后，通过vpn或者访问上述镜像路径。

##### 15.fragment Andriod开发技巧——Fragment的懒加载 

一个Activity里面可能会以viewpager（或其他容器）与多个Fragment来组合使用，而如果每个fragment都需要去加载数据，或从本地加载，或从网络加载，那么在这个activity刚创建的时候就变成需要初始化大量资源。这样的结果，我们当然不会满意。那么，能不能做到当切换到这个fragment的时候，它才去初始化呢？

答案就在Fragment里的setUserVisibleHint这个方法里
http://blog.csdn.net/maosidiaoxian/article/details/38300627

结合fragment的hide和show使用。

##### 16.让多个Fragment 切换时不重新实例化
http://www.yrom.net/blog/2013/03/10/fragment-switch-not-restart/


##### 17. 关于Android的GridView添加headerView
grid-with-header-list-adapter
StickyGridHeaders/
http://www.eoeandroid.com/blog-696650-48907.html


##### 18.Eclipse设置不格式化注释 
	Eclipse设置不格式化注释
　　注释中写点带格式的文字，format后全乱了，解决办法如下：
　　Windows -> Preferces -> java -> Code Style -> Formatter -> Edit -> Comments
　　取消勾选“Enable Javadoc comment formatting”.

##### 19.android-Ultra-Pull-To-Refresh

##### 20.Linux动态gif图的录制
	

	byzanz  
	byzanz的安装与使用

	Ubuntu下安装

	  sudo add-apt-repository ppa:fossfreedom/byzanz
	sudo apt-get update sudo apt-get install byzanz

	你可以通过如下命令来完成录制过程：
	byzanz-record -d 40 -x 0 -y 0 -w 400 -h 320 byzanz-demo.gif

	其中：

	    -d 40 为录制的时长为 40 秒
	    -x 0 录制区域的横坐标
	    -y 0 录制区域的纵坐标，记住：屏幕右上角为原点（0,0）
	    -w 400 录制区域的宽度
	    -h 320 录制区域的高度

	byzanz-demo.gif 保存的文件名

	详细参数可通过byzanz-record --help查看。
	http://www.tuicool.com/articles/YFJrem

	另外：windows下 GIF屏幕录像机 V2.0

##### 22.  viewpage 无线循环
http://www.cnblogs.com/xinye/archive/2013/06/09/3129140.html

##### 23.public void onPageScrollStateChanged(int arg0)

	此方法是在状态改变的时候调用，其中arg0这个参数有三种状态（0，1，2）。arg0 ==1的时辰默示正在滑动，arg0==2的时辰默示滑动完毕了，arg0==0的时辰默示什么都没做。

	当页面开始滑动的时候，三种状态的变化顺序为（1，2，0）


##### 24.
在eclipse.ini文件中加入 -Dorg.eclipse.swt.browser.DefaultType=mozilla 
然后clean一下就OK了 执行clean命令



##### 26.viewpager实现画廊(一屏多个Fragment)效果


##### 27.svn命令
通过指令添加文件，每次都到对应文件夹 svn add。这样如果需要add的文件不在一个文件夹时会很麻烦，通过下面的 --force 可以方便的添加。
	$ svn add * --force
http://developer.51cto.com/art/201005/201633.htm

当然现在studio集成乐svn git等代码管理工具，很方便，可以直接使用。

##### 28.Array constants can only be used in initializers
	int CC [] ={1,2,3};   数组定义并附初始值的时候，数组的长度就定了，长度是3
	 而且数组重新赋值不能再像定义的时候那样
	而要一个一个地更改
	CC[0]=1;
	CC[1]=2;
	CC[2]=3;
	Array constants can only be used in initializers  好像是说数组不能用于初始化


##### 29.android 插件化


##### 30.scrollview在内容较少时也可以滚动
	在XML为ScrollView添加属性android:overScrollMode="always"即可

##### 31.gridview/listview 点击时 android默认背景是黄色的，如何去掉选中时的黄色背景

	方法一，在控件被初始化的时候设置

	gridView.setSelector(new ColorDrawable(Color.TRANSPARENT));
	listView.setSelector(new ColorDrawable(Color.TRANSPARENT))；

	方法二，在布局文件中设置listSelector属性

	 

	<GridView
		android:listSelector="@android:color/transparent"
		android:numColumns="auto_fit"
		android:columnWidth="50dp"
		android:stretchMode="spacingWidth"
		android:layout_weight="1.0"
		android:layout_height="0dip"
		android:layout_width="match_parent"/>

	<ListView
		android:listSelector="@android:color/transparent"
		android:layout_height="match_parent"
		android:layout_width="match_parent"/>

	当然也可以定制化自己想要的效果。

	推荐使用方法二，解耦逻辑代码与布局文件。 


另外listview还有两个基础问题
		问题1：

		       listview在拖动的时候背景图片消失变成黑色背景。等到拖动完毕我们自己的背景图片才显示出来。

		解决办法：

		      xml中： android:scrollingCache="false"  或者 android:cacheColorHint="#00000000"

		     代码中： setScrollingCacheEnabled(false)  或者 setCacheColorHint(0)  或者setCacheColorHint(Color.TRANSPARENT);

		问题2：

		    listview的上边和下边有黑色的阴影。

		解决办法：

		   xml中： android:fadingEdge="none"

		  代码中：setFadingEdgeLength(0);

##### 32.ScrollView仅支持一个子项，报错ScrollView can host only one direct child 
	解决办法：

	在ScrollView 中设LinearLayout为子项 ，将其它View放入LinearLayout。

##### 33.viewpager 设置间距和缓存
viewPager.setOffscreenPageLimit(TOTAL_COUNT);
viewPager.setPageMargin(getResources().getDimensionPixelSize(R.dimen.page_margin));

##### 34.一级缓存和二级缓存是什么意思？？
静态ram缓存叫一级缓存，而把后来增加的动态RAM叫二级缓存。
RAM分两种，
一种是静态RAM，SRAM；一种是动态RAM，DRAM。前者的存储速度要比后者快得多，我们现在使用的内存一般都是动态RAM。

有的菜鸟就说了，为了增加系统的速度，把缓存扩大不就行了吗，扩大的越大，缓存的数据越多，系统不就越快了吗 

缓存通常都是静态RAM，速度是非常的快， 

但是静态RAM集成度低（存储相同的数据，静态RAM的体积是动态RAM的6倍）， 

价格高（同容量的静态RAM是动态RAM的四倍）， 

由此可见，扩大静态RAM作为缓存是一个非常愚蠢的行为， 

但是为了提高系统的性能和速度，我们必须要扩大缓存， 

这样就有了一个折中的方法，不扩大原来的静态RAM缓存，而是增加一些高速动态RAM做为缓存， 

这些高速动态RAM速度要比常规动态RAM快，但比原来的静态RAM缓存慢， 

我们把原来的静态ram缓存叫一级缓存，而把后来增加的动态RAM叫二级缓存。 

一级缓存和二级缓存中的内容都是内存中访问频率高的数据的复制品（映射），它们的存在都是为了减少高速CPU对慢速内存的访问。 
通常CPU找数据或指令的顺序是：先到一级缓存中找，找不到再到二级缓存中找，如果还找不到就只有到内存中找了


##### 35.性能优化：使用SparseArray代替HashMap<Integer,Object> 
http://blog.csdn.net/haukey/article/details/8200404	

##### 36.代码规范
http://liuzhichao.com/p/1781.html#more-1781


##### 37.        // Disallow Parent Intercept, just in case
                        ViewParent parent = getParent();
                        if (parent != null) {
                            parent.requestDisallowInterceptTouchEvent(true);
                        }



##### 38.linerlayout布局，如何把一个view指定父view的底部
	在纯属布局中，将除最底部以外的的view都设置weight为1就可以了。

##### 39.editview 左侧加drawable
如果只是在左边或者右边加图片  可以用EditeView 的一个属性；　android:drawableLeft在text的左边输出一个drawable
如果在中间或者随意加图片的话，需要你重写EditView来实现图文混排！


##### 40.加密算法

41.01-07 15:34:23.160: E/AndroidRuntime(1932): Caused by: java.lang.UnsatisfiedLinkError: Couldn't load AES: findLibrary returned null

01-07 15:37:43.240: E/AndroidRuntime(2537): java.lang.UnsatisfiedLinkError: Native method not found: com.jetsun.hbfc.core.AESCoder.decryptCNew:()Ljava/lang
/String;

01-07 15:37:43.230: D/dalvikvm(2537): No JNI_OnLoad found in /data/data/com.jetsun.hbfc/lib/libAES.so 0x4160abe0, skipping init

01-07 15:37:43.230: W/dalvikvm(2537): No implementation found for native Lcom/jetsun/hbfc/core/AESCoder;.decryptCNew:()Ljava/lang/String;


return makes pointer from integer without a cast [enabled by default]


01-07 17:51:47.520: D/dalvikvm(12438): No JNI_OnLoad found in /data/data/com.jetsun.hbfc/lib/libAES.so 0x41601a80, skipping init
01-07 17:51:47.525: I/JNIMsg(12438): jclass == NULL
01-07 17:51:47.525: I/JNIMsg(12438): step 1 : jclass Begin ok !
01-07 17:51:47.525: I/JNIMsg(12438): encryptC == NULL
01-07 17:51:47.525: I/JNIMsg(12438): step 2 : decryptC new failed 
01-07 17:51:47.525: I/JNIMsg(12438): step 2 : decryptC method prepared ok !



##### 41.jni基础
android   __android_log_print打印函数__源代码 http://blog.csdn.net/sno_guo/article/details/8143050
JNI字段描述符“([Ljava/lang/String;)V”  http://fgsink.blog.163.com/blog/static/16716997020124310169911/
jni函数讲解      http://blog.csdn.net/caimouse/article/category/661872/2
基于 Android NDK 的学习之旅----- C调用Java    http://www.cnblogs.com/luxiaofeng54/archive/2011/08/17/2142000.html
No JNI_OnLoad found in … skipping init    http://stackoverflow.com/questions/11798054/no-jni-onload-found-in-skipping-init
eclipse ndk配置详细描述    http://www.cnblogs.com/chenjiajin/archive/2012/04/12/2444188.html
基于 Android NDK 的学习之旅

##### 汇总 ndk精华

http://www.cnblogs.com/chenjiajin/archive/2012/04/12/2444188.html
http://www.cnblogs.com/luxiaofeng54/archive/2011/08/17/2142000.html
http://blog.csdn.net/caimouse/article/details/6853795
http://fgsink.blog.163.com/blog/#m=0&t=1&c=fks_084071081085086066085080094095085080086066082095095068084

##### 42.md5 aes加密
有固定的密钥key的AES加密   http://fenglingcorp.iteye.com/blog/586600
android Rsa 算法加  密明文--->公钥--->密文   密文-->密钥-->明文     http://blog.sina.com.cn/s/blog_6568e7880100x8r9.html
java加密与解密的艺术作者   http://snowolf.iteye.com/blog/379860
Android AES加密算法及其实现   http://blog.csdn.net/randyjiawenjie/article/details/6587986
AES加密解密Android版  http://www.cnblogs.com/carlosk/archive/2012/05/18/2507975.html

加密方式  AES
加密模式  AES/CBC/PKCS5Padding
加密向量 iv
secretkey 秘钥
编码方式 utf-8

##### 43.proguard的使用
代码混淆时，不混淆的部分。

##### 44.socket
Socket简单用法   http://www.cnblogs.com/harrisonpc/archive/2011/03/31/2001565.html
即时通讯  
基于xmpp openfire smack开发之openfire介绍和部署[1]  http://blog.csdn.net/shimiso/article/details/8816558
Openfire+Spark聊天Demo   http://www.apkbus.com/android-69413-1-1.html
openfire的Android客户端实现    http://download.csdn.net/detail/sky_monkey/5820879#comment

##### 45.音频编解码
FFmpeg的Android平台移植—编译篇   http://blog.csdn.net/gobitan/article/details/22750719#reply


##### 46.f5 负载均衡


##### 47. 掌上指路标 —– APP架构与导航设计  http://www.yixieshi.com/ucd/13188.html
　APP导航设计的步骤主要为以下三步：

　　1. APP框架整理：信息架构 or 任务分析

　　2. 框架层级判断： 扁平 vs 树状

　　3. 导航具体表现形式：控件形式and摆放位置


##### 48.移动App架构设计
http://blog.csdn.net/uxyheaven/article/details/38041091
移动App设计之分层架构+MVC   http://www.cnblogs.com/Logen/archive/2012/11/08/2760638.html



##### 49.Android 精品开源项目
http://blog.csdn.net/caesardadi/article/details/21091645



##### 50.使用GDB调试JNI代码 
Android NDK应用原理 http://shihongzhi.com/ndk/
NDK 开发指南---Android NDK概览  http://hualang.iteye.com/blog/1135105

##### 51.ubuntu下搜狗输入法，使用过程中突然出现   “搜狗面板程序加载失败 请重启以使用输入法”导致无法使用
解决方法：终端sogou-qimpanel &


##### 52.layout_alignBaseline的作用

##### 53.android:layout_weight的真实含义 
android:layout_weight的真实含义是:一旦View设置了该属性(假设有效的情况下)，那么该 View的宽度等于原有宽度(android:layout_width)加上剩余空间的占比！
**简单的说，就是剩余空间的权重.**
http://blog.csdn.net/yanzi1225627/article/details/24667299

##### 54.即时通讯


基础：socket
	原理：
	如何保证socket长连接 http://blog.csdn.net/chengyingzhilian/article/details/7633640
	android中对服务端的长连接【socket】 http://blog.csdn.net/yaya_soft/article/details/11778593

	1.Android 基于Socket的聊天应用(二)  http://www.cnblogs.com/-run/archive/2012/04/07/2434837.html#!comments   下载demo
	Ubuntu 14.04下MySQL服务器和客户端的安装  http://www.linuxidc.com/Linux/2014-10/107912.htm
	Ubuntu 安装mysql和简单操作   http://www.cnblogs.com/zhuyp1015/p/3561470.html
	如何在mysql中创建数据库  http://www.360doc.com/content/11/0719/18/2104556_134548635.shtml
	Java连接MYSQL 数据库的连接步骤  http://database.51cto.com/art/201006/204217.htm


	2.基于XMPP的即时聊天项目  需要google账号，目前无法登录 本项目是一套基于android+asmack+openfire+xmpp的安卓即时聊天服务端，项目直连google talk服务器，可以使用谷歌帐号登录客户端，测试需要至少两个谷歌帐号。在程序里添加好友即可聊天

	3.Android手机通过socket与pc通信 http://blog.csdn.net/tobacco5648/article/details/7742295

##### 55.ubuntu显示端口占用、正在运行的程序，以及强制关闭一个进程
	1. 显示占用某个端口的程序

	lsof -i:80
	lsof -i:5000

	2. 显示某个程序是否在运行，查看某个运行的程序

	ps -aux | grep "paster"
	ps -aux | grep apache2

	3. 杀掉一个进程，和强制杀掉一个进程

	kill 211119
	sudo kill -s 9 21119


##### 56.设置Activity进入退出动画
使用代码设定

   通过调用overridePendingTransition() 可以实时修改Activity的切换动画。但需注意的是:该函数必须在调用startActivity()或者finish()后立即调用，且只有效一次。


##### 57.滑动返回
android-swipelistview  
SwipeBackLayout
SlidingFinish

自从用了swipebacklayout， 友好度提高了许多。
但是又遇到一个问题 每个界面在滑动返回时候都能够看到桌面 ，然后才跳到我的主界面。
**解决方案：**
 主界面窗口不要设置透明 <item name="android:windowIsTranslucent">false</item>，其他界面true


##### 58.Android 虚拟键盘弹出把底部栏顶上去的解决办法
解决办法：

在AndroidManifest的相应的activity中加上：android:windowSoftInputMode="adjustPan"
http://www.linuxidc.com/Linux/2011-10/46070.htm


##### 59. 在EditText中插入表情图片 (CharacterStyle&SpannableString)   http://gundumw100.iteye.com/blog/904107

	EditText通常用于显示文字，但有时候也需要在文字中夹杂一些图片，比如QQ中就可以使用表情图片，又比如需要的文字高亮显示等等，如何在android中也做到这样呢？
	记得android中有个android.text包，这里提供了对文本的强大的处理功能。
	添加图片主要用SpannableString和ImageSpan类：
	Java代码  收藏代码

	    Drawable drawable = getResources().getDrawable(id);  
		    drawable.setBounds(0, 0, drawable.getIntrinsicWidth(), drawable.getIntrinsicHeight());  
		    //需要处理的文本，[smile]是需要被替代的文本  
		    SpannableString spannable = new SpannableString(getText().toString()+"[smile]");  
		    //要让图片替代指定的文字就要用ImageSpan  
		    ImageSpan span = new ImageSpan(drawable, ImageSpan.ALIGN_BASELINE);  
		    //开始替换，注意第2和第3个参数表示从哪里开始替换到哪里替换结束（start和end）  
	    //最后一个参数类似数学中的集合,[5,12)表示从5到12，包括5但不包括12  
		    spannable.setSpan(span, getText().length(),getText().length()+"[smile]".length(), Spannable.SPAN_INCLUSIVE_EXCLUSIVE);    
		    setText(spannable); 

##### 60.viewpager中嵌套gridview
自定义带表情键盘  android 表情,软键盘冲突解决方案（仿微博等SNS应用）    http://blog.csdn.net/jj120522/article/details/9825871
日历   android中ViewPager嵌套GridView引发的一系列UI卡顿不顺畅的问题   http://www.android100.org/html/201403/10/5840.html
Android UI开发篇之 ViewPager+九宫格布局 实现左右滑动                 http://blog.csdn.net/janice0529/article/details/17335473
ViewPager+GridView实现宫格横向滑动切换  http://download.csdn.net/detail/yefengyulu/5433913

##### 61.异常：java.lang.ClassCastException: android.view.ViewGroup$LayoutParams cannot be cast to android.view.ViewGroup$MarginLayoutParams的终极解决方式

思路：从原来的View中直接获取LayoutParams。http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2014/1117/1991.html
	今天在使用LayoutParams时出现了一个问题，我是这样用的：

	在gridview初始化的时候，为gridview添加了一个header（我用的是第三方GridView是可以添加header的）：


	headerView = new View(getActivity());
	LayoutParams params = new LayoutParams(LayoutParams.FILL_PARENT, (int)300); 
	headerView.setLayoutParams(params);     
	mGridView.addHeaderView(headerView);
	然后当程序执行到某处，我希望通过setLayoutParams来改变这个高度，于是我这样做：


	LayoutParams params = new LayoutParams(LayoutParams.FILL_PARENT, 500); 
	headerView.setLayoutParams(params);
	重点是，两个LayoutParams 都是ViewGroup的LayoutParams ，然后一执行就出现下列错误：

	java.lang.ClassCastException: android.view.ViewGroup$LayoutParams cannot be cast to android.view.ViewGroup$MarginLayoutParams

	跟android中的很多异常一样，你去仔细推敲异常本来的含义往往是百思不得其姐的，异常说的是两个是不同类型的LayoutParams ，但明明都是ViewGroup的LayoutParams。而且我确定ViewGroup的LayoutParams用在GridView的header上是可以的，因为我不执行上面的第二段代码不会报错（再次强调我用的是第三方GridView是可以添加header的）。



	然后就在stackoverflow上查找答案，虽然没找到满意的，但是有个人的回答倒是点醒了我，是不是第二段代码中又重新创建了一个LayoutParams的关系？于是我将第二段代码改成：


	**LayoutParams params = headerView.getLayoutParams();**
	params.height = 500;
	其实就是不去新建一个LayoutParams，而是从原来的View中直接获取LayoutParams。

	改完运行结果没有出现异常了。

	看来，当一个View已经有了LayoutParams，是不能再次添加一个新创建的LayoutParams的。



##### 62.android4.0的edittext屏蔽输入法时候光标显示问题  通过反射解决  http://www.eoeandroid.com/thread-248276-1-1.html
		if (android.os.Build.VERSION.SDK_INT <= 10) {
                                        mEditText.setInputType(InputType.TYPE_NULL);
                                } else {
                                        getWindow().setSoftInputMode(WindowManager.LayoutParams.SOFT_INPUT_STATE_ALWAYS_HIDDEN);
                                        try {
                                                Class<EditText> cls = EditText.class;
                                                Method setSoftInputShownOnFocus;
                                                setSoftInputShownOnFocus = cls.getMethod("setSoftInputShownOnFocus", boolean.class);
                                                setSoftInputShownOnFocus.setAccessible(true);
                                                setSoftInputShownOnFocus.invoke(mEditText, false);
                                        } catch (Exception e) {
                                                e.printStackTrace();
                                        }
                                        try {
                                                Class<EditText> cls = EditText.class;
                                                Method setShowSoftInputOnFocus;
                                                setShowSoftInputOnFocus = cls.getMethod("setShowSoftInputOnFocus", boolean.class);
                                                setShowSoftInputOnFocus.setAccessible(true);
                                                setShowSoftInputOnFocus.invoke(mEditText, false);
                                        } catch (Exception e) {
                                                e.printStackTrace();
                                        }
                                }

##### 63.自定义控件
getContext的使用

自定义android用户控件,使用回调函数实现自定义事件


##### 64.如何获取到，EditView 的 粘贴复制呢（解决）  重写editview控件，onTextContextMenuItem  。http://www.eoeandroid.com/thread-61482-1-1.html
 
Android学习笔记之通过剪切板传递数据  http://www.it165.net/pro/html/201404/11599.html

Android EditText 取消复制粘贴剪贴功能   http://www.xuebuyuan.com/2038921.html
	 在API-11以上，也就是Android 3.0以上的版本，这个操作就无效了，需要用到以下方法：

	editText.setCustomSelectionActionModeCallback(new ActionMode.Callback() 
	    editText.setImeOptions(EditorInfo.IME_FLAG_NO_EXTRACT_UI);

如何捕获Edittext的粘贴方法？http://www.apkbus.com/android-92944-1-1.html
向EditView插入qq表情，并可删除表情或文字 android开发教程 http://cache.baiducontent.com/c?m=9d78d513d99417f41efa950e494d80230e55f0744ddcc76508c3e34984102d564616f4cd27356074c4c40c7071a55e28eee47132690c7af1dd8a9f4baea68f6d6acd3034074fda17528e42f9c84427d620e707a9fa04bdfcaf6c8eaed0d0d95652d751066787f58f5b1714bd35b64b6f&p=80769a47959d18ff57ee927c1c4791&newp=c67f8f5e85cc43be43bd9b7d0b148a231610db2151d6d2176ecf&user=baidu&fm=sc&query=editview%C9%BE%B3%FD%D2%BB%B8%F6&qid=f5bf3b5b0000bd4e&p1=3

##### 65.android EditText插入字符串到光标所在位置 


	EditText mTextInput=(EditText)findViewById(R.id.input);//EditText对象

	int index = mTextInput.getSelectionStart();//获取光标所在位置

	String text="I want to input str";

	Editable edit = mTextInput.getEditableText();//获取EditText的文字

	if (index < 0 || index >= edit.length() ){

	       edit.append(text);

	}else{

	      edit.insert(index,text);//光标所在位置插入文字

	 }


##### 66.Android学习笔记：浅析自己的聊天系统的设计思想   http://www.android100.org/html/201406/09/22125.html


##### 67.java 正则表达式（Invalid escape sequence (valid ones are \b \t \n \f \r \" \' \\ ) 请问是啥原因呢？
	把你的里面的\全部替换为\\即可


##### 69.error
NewsCommentDetailActivity

01-20 11:35:28.990: E/AndroidRuntime(6166): java.lang.RuntimeException: Unable to instantiate application com.jetsun.hbfc.core.MyApplication: java.lang.NullPointerException
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.LoadedApk.makeApplication(LoadedApk.java:508)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.ActivityThread.handleBindApplication(ActivityThread.java:4245)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.ActivityThread.access$1400(ActivityThread.java:131)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1288)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.os.Handler.dispatchMessage(Handler.java:99)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.os.Looper.loop(Looper.java:137)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.ActivityThread.main(ActivityThread.java:4866)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at java.lang.reflect.Method.invokeNative(Native Method)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at java.lang.reflect.Method.invoke(Method.java:511)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:786)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:553)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at dalvik.system.NativeStart.main(Native Method)
01-20 11:35:28.990: E/AndroidRuntime(6166): Caused by: java.lang.NullPointerException
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.LoadedApk.initializeJavaContextClassLoader(LoadedApk.java:384)
01-20 11:35:28.990: E/AndroidRuntime(6166): 	at android.app.LoadedApk.getClassLoader(LoadedApk.java:327)





01-20 04:05:16.637: E/AndroidRuntime(1372): Process: com.jetsun.hbfc:webview, PID: 1372
01-20 04:05:16.637: E/AndroidRuntime(1372): java.lang.RuntimeException: Unable to instantiate application com.jetsun.hbfc.core.MyApplication: java.lang.IllegalStateException: Unable to get package info for com.jetsun.hbfc; is package not installed?
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.LoadedApk.makeApplication(LoadedApk.java:561)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.ActivityThread.handleBindApplication(ActivityThread.java:4491)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.ActivityThread.access$1500(ActivityThread.java:144)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1339)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.os.Handler.dispatchMessage(Handler.java:102)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.os.Looper.loop(Looper.java:135)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.ActivityThread.main(ActivityThread.java:5221)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at java.lang.reflect.Method.invoke(Native Method)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at java.lang.reflect.Method.invoke(Method.java:372)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:899)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:694)
01-20 04:05:16.637: E/AndroidRuntime(1372): Caused by: java.lang.IllegalStateException: Unable to get package info for com.jetsun.hbfc; is package not installed?
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.LoadedApk.initializeJavaContextClassLoader(LoadedApk.java:410)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.LoadedApk.getClassLoader(LoadedApk.java:363)
01-20 04:05:16.637: E/AndroidRuntime(1372): 	at android.app.LoadedApk.makeApplication(LoadedApk.java:554)



##### 70.解决eclipse闪退的办法           http://blog.csdn.net/ieicihc/article/details/9629991
	方法1.最好解决办法： 
	删除文件 [workspace]/.metadata/.plugins/org.eclipse.e4.workbench/workbench.xmi

	方法2.在文件eclipse/configuration/config.ini末尾加上如下一行：

org.eclipse.swt.browser.DefaultType=mozilla

但是不怎么起作用，在不断切换引用时，有时也会闪退。回来转到androidstudio，用eclipse不多了，偶尔用用没问题。

##### 71.Android WebView的前进、后退、与刷新
	mWebView.goBack();   //后退  
	mWebView.goForward();//前进
	mWebView.reload();  //刷新

    webview有自己的堆stack

##### 72.You must call removeView() on the child's parent first
	在做alertdialog是的时候报了这么一个错误：

	java.lang.IllegalStateException: 
	The specified child already has a parent. 
	You must call removeView() on the child's parent first.

	搞了许久，终于理解了。

	et1 = (EditText)findViewById(R.id.editText1);
	builder.setView(et1);  -- AlertDialog.Builder builder
	et1我写在了xml里面，这样报错，原因是一女不可二嫁。

	et1的parent即是R.layout.main 又是AlertDialog。

	自然就报错了要你removeView()了。

	解决方法有两种

	1.动态生成EditText

	et1 = new EditText(this);
	builder.setView(et1);
	2. 放在另一个xml中，用inflater

	LayoutInflater inflater = LayoutInflater.from(this);  
		    View textEntryView = inflater.inflate(R.layout.test1, null);  
		    et1 = (EditText)textEntryView.findViewById(R.id.editText1);
	builder.setView(textEntryView ); 注意这里是textEntryView ，不是et1 
    
    补充还有一种方法，如果此布局中只有该view，可以直接在xml只布局此view。


##### 73.Activity切换动画无效(android:windowIsTranslucent)影响(android:windowAnimationStyle)   http://blog.csdn.net/xuewater/article/details/36398803

	style里面设置了android:windowIsTranslucent这个属性


##### 74.Android 解决程序启动时的黑屏问题    http://blog.csdn.net/fancylovejava/article/details/39643449    
	android 界面切换黑屏处理从A切换到B的过程中出现黑屏，可以在Manifest文件中改变B的theme，在theme里添加<item name="android:windowIsTranslucent">true</item>，这样从A到B的过程中，因为B是透明的，所以背景就是A。这样的用户体验比较好


##### 75.
	atvity主题加透明属性 如下： <item name="android:windowIsTranslucent">true</item>  
  在该atvtivity中使用webview。  webview中有videos，可以播放视频，点击视频全屏后，导致其上级fragmentactivity重新加载，导致内容空白。
   
##### 76.打包过程中出现错误  Unexpected error while computing stack sizes:
java.lang.IllegalArgumentException] (Stack size becomes negative after instruction [12] invokevirtual #96 in [cn/jpush/android/a/a.<clinit>()V])

   解决办法： 如何在代码时混淆忽略 jpush-sdk-release.jar？       http://www.xuebuyuan.com/1683269.html

    请下载最新的proguard.jar，   umeng官方最新的试了也是有问题，估计兼容型的不好吧，采用http://download.csdn.net/detail/msn465780/6625061这个 ok。
    并替换你Android Sdk "tools\proguard\lib\proguard.jar"
    在你的proguard.cfg加上代码：
	-dontwarn
	cn.jpush.**
	-keep class cn.jpush.** { *; }


##### 77.android eclipse设置的断点无效的解决方案 
	1.排除 Run——Skip All Breakpoints
	2.排除断点无效的activity所在的进程是否是主进程。


##### 78.极光推送富媒体
	 推送富媒体时，推送模版其实是通知，推送文件其实是自定义消息类型
	通知 vs. 自定义消息  http://docs.jpush.cn/pages/viewpage.action?pageId=3309701
	富文本页面 Javascript 回调API  http://docs.jpush.cn/pages/viewpage.action?pageId=7536748
	Rich Push 开发指南  http://docs.jpush.cn/pages/viewpage.action?pageId=7536799


##### 79.内部跳转  Routable for Android


##### 80.fjrefox  firebug插件。chrome 自身F12都可以方便的查看并且编辑html

##### 81 带有凭证的activity 必须在一个进程中。否则凭证会为空。还有一点在调试的时候，非主进程无法和主进程跳转调试。

##### 82.apktool反编译过程中出现如下错误
	
	Exception in thread "main" brut.androlib.AndrolibException: Could not decode arsc file
		at brut.androlib.res.decoder.ARSCDecoder.decode(ARSCDecoder.java:56)
		at brut.androlib.res.AndrolibResources.getResPackagesFromApk(AndrolibResources.java:491)
		at brut.androlib.res.AndrolibResources.loadMainPkg(AndrolibResources.java:74)
		at brut.androlib.res.AndrolibResources.getResTable(AndrolibResources.java:66)
		at brut.androlib.Androlib.getResTable(Androlib.java:50)
		at brut.androlib.ApkDecoder.getResTable(ApkDecoder.java:189)
		at brut.androlib.ApkDecoder.decode(ApkDecoder.java:114)
		at brut.apktool.Main.cmdDecode(Main.java:146)
		at brut.apktool.Main.main(Main.java:77)
	Caused by: java.io.IOException: Expected: 0x001c0001, got: 0x00000000
		at brut.util.ExtDataInput.skipCheckInt(ExtDataInput.java:48)
		at brut.androlib.res.decoder.StringBlock.read(StringBlock.java:44)
		at brut.androlib.res.decoder.ARSCDecoder.readPackage(ARSCDecoder.java:102)
		at brut.androlib.res.decoder.ARSCDecoder.readTable(ARSCDecoder.java:83)
		at brut.androlib.res.decoder.ARSCDecoder.decode(ARSCDecoder.java:49)
		... 8 more


由于使用新的adt，而反编译的apktool.jar不是最新的导致。使用新的apktool.jar替换原来的就可以了。官方下载地址 https://code.google.com/p/android-apktool/。


##### 83.渠道打包工具
之前有的umeng，但是现在无法使用【因为android更新了编译的sdk版本，而umeng不在提供更新】。目前的做法是通过
gradle来打包[Gradle多渠道打包](http://blog.csdn.net/u011570979/article/details/44919389)

##### 84.genymotion快速高效的android模拟器

https://www.genymotion.com/#!/developers/user-guide#license
http://blog.csdn.net/langyuewu/article/details/39196653

需要翻墙。部分需要付费


##### 85.使用Vitamio打造自己的Android万能播放器
直播方面 可以参考我翻译的[Android如何直播RTMP流](https://github.com/ayyb1988/android-tech-frontier/blob/master/issue-10/Android%E5%A6%82%E4%BD%95%E7%9B%B4%E6%92%ADRTMP%E6%B5%81.md)
86.
Ctrl+Shift+F7 可以高亮当前元素在当前文件中的使用
Android Studio 如何提示函数用法？   先选中，然后按F2

##### 87.android 提供的很多List控件如 listview、gridview 默认都会显示一个fadingedge的东西，它在View的top和bottom处各显示一个渐变半透的阴影以达到更好的视觉效果，但是这个带来的副作用就是导致在性能不是那么强劲的机器上，一些listview，gridview的拖动会显得很不流畅，因为我们知道绘制带Alpha的图片是最耗时的。 
 
我们的优化思路就是对这个fadingedge做一些修改，当view处于滚动状态时，通过接口setVerticalFadingEdgeEnabled(false)让其不显示fadingedge，当view处于静止状态时，通过接口setVerticalFadingEdgeEnabled(true)恢复显示fadingedge。以上的listview和gridview等控件都是继承与AbsListView，所以我们直接修改framework中的AbsListView.java文件，就可以达到系统级的改动效果了。 

##### 88. 从github上clone下来swipebacklayout
编译报错查看log为 android-studio llij.ide.plugins.PluginManager - null

修改方法
tasks.withType(Compile) { options.encoding = "UTF-8" } 
改为
 tasks.withType(JavaCompile) { options.encoding = "UTF-8" } 


##### 89.Error:Execution failed for task ':xxx:compileDebugNdk'.
> NDK not configured.
  Download the NDK from http://developer.android.com/tools/sdk/ndk/.Then add ndk.dir=path/to/ndk in local.properties.
  (On Windows, make sure you escape backslashes, e.g. C:\\ndk rather than C:\ndk)
  
在androidstudio中的local.properties中添加ndk.dir= 你的ndk的路径


##### 90.Error:(8, 0) Could not find property 'ANDROID_BUILD_SDK_VERSION' on project ':ActionBar-PullToRefresh'.
dependencies {
    compile 'com.github.castorflex.smoothprogressbar:library:0.4.+@aar'
}
解决方法
I think you should also import 'SmoothProgressBar' library in your project https://github.com/castorflex/SmoothProgressBar



#####91.@+id  @id  android:id  ?android:attr

。@+id：宣告一個id值來識別控制項


。@id：透過id值引用控制項


。android:id：透過id值, 引用Android系統內部的資源


。?android:attr：引用Android預置定義樣式

#####92.
Looks like there is no way to avoid modifications made by the import plugin. All the settings it has is three checkboxes related to dependency management. I tried to uncheck all of them but still it does change my project structure.

I managed to add existing library projects manually: 
1) Copied library's directory under the root directory of my project. 
2) Referenced that library in settings.gradle by adding include ':libraryA'. 
3) Added dependency to my project's build.gradle: compile project(':libraryA').

Moreover, after that the IDE recognized that library as module and highlighted its folder in bold font whithin Project Structure.

#####93.如何从当前的activity获得根视图  或者 Android如何获取Activity的View？

((ViewGroup)findViewById(android.R.id.content)).getChildAt(0)
或者
getWindow().getDecorView().findViewById(android.R.id.content)

#####94.radiogroup中的radiobutton如何不显示图标button，并且可以等比例再用wight
	android：button="@none" 或@null
	android：drawableTop ="@drawable/xxx" 或者也设置为空

#####95.搜索也是一门艺术   浓缩搜索  详细搜索

#####96.android layoutinfater  没有显示内容  检查parent试图是否为空

#####97..Error:Execution failed for task ':app:dexDebug'.UNEXPECTED TOP-LEVEL EXCEPTION:  	com.android.dex.DexException: Multiple dex files define
Landroid/support/annotation/AnimRes;
  		at com.android.dx.merge.DexMerger.readSortableTypes(DexMerger.java:596)
  		at com.android.dx.merge.DexMerger.getSortedTypes(DexMerger.java:554)
  		at com.android.dx.merge.DexMerger.mergeClassDefs(DexMerger.java:535)
  		at com.android.dx.merge.DexMerger.mergeDexes(DexMerger.java:171)
  		at com.android.dx.merge.DexMerger.merge(DexMerger.java:189)
  		at com.android.dx.command.dexer.Main.mergeLibraryDexBuffers(Main.java:454)
  		at com.android.dx.command.dexer.Main.runMonoDex(Main.java:303)
  		at com.android.dx.command.dexer.Main.run(Main.java:246)
  		at com.android.dx.command.dexer.Main.main(Main.java:215)
  		at com.android.dx.command.Main.main(Main.java:106)

检查 Multiple dex
#####98.android动画的三种形式  tween  animition  ,frame animition ,property animition


#####99.LoopingViewPager    QuickReturn


#####100.  appcompat-v7:21.0.0': No resource found that matches the given name: attr 'android:actionModeShareDrawable'
		http://stackoverflow.com/questions/26431676/appcompat-v721-0-0-no-resource-found-that-matches-the-given-name-attr-andro

#####101.recycleview vs listview head foot  .recycleview实现gridview   新事物不要躲避，机遇。

#####102.清除Android工程中没用到的资源    http://www.cnblogs.com/angeldevil/p/3725358.html

#####103.xmlns:tools与tools:context
tools:context="activity name"这一句不会被打包进APK。只是ADT的Layout Editor在你当前的Layout文件里面设置对应的渲染上下文，说明你当前的Layout所在的渲染上下文是activity name对应的那个activity，如果这个activity在manifest文件中设置了Theme，那么ADT的Layout Editor会根据这个Theme来渲染你当前的Layout。就是说如果你设置的MainActivity设置了一个Theme.Light（其他的也可以），那么你在可视化布局管理器里面看到的背景啊控件啊什么的就应该是Theme.Light的样子。仅用于给你看所见即所得的效果而已。


#####104. android-studio下使用volley    Android working with Volley Library   http://www.androidhive.info/2014/05/android-working-with-volley-library-1/
http://blog.gssxgss.me/setup-android-studio-and-volley-usage-1/

#####105.androidstudio 导入libs后要同步一下才可以用


#####106.fragment + butterknife 的使用
 othersetting-->Compiler → Annotation Processors. Check "Enable annotation processing".


#####107. com.astuetz.PagerSlidingTabStrip$PageListener.onPageScrolled(

#####108.
E/InputEventReceiver﹕ Exception dispatching input event.
E/MessageQueue-JNI﹕ Exception in MessageQueue callback: handleReceiveCallback
E/MessageQueue-JNI﹕ java.lang.RuntimeException: native typeface cannot be made
            at android.graphics.Typeface.<init>(Typeface.java:175)
            at android.graphics.Typeface.createFromAsset(Typeface.java:149)
            at NewsFragment$1.onPageSelected(NewsFragment.java:74)

androidstudio中assert的位置和eclipse中的不同。需要注意。否则调用assert中资源会找不到而出现问题。

#####109.Custom Fonts in Android  
http://sudharti.github.io/articles/custom-fonts-android/

Typeface tf = Typeface.createFromAsset(getActivity().getAssets(), "fonts/font_name.ttf");
  Typeface tf2 = Typeface.createFromAsset(getActivity().getAssets(), "fonts/font_name2.ttf");
  
  TextView tv = (TextView) findViewById(R.id.textview);
  tv.setTypeface(tf); //Set Typeface
  
  EditText et = (EditText) findViewById(R.id.edittext);
  et.setTypeface(tf2);


#####110.PagerSlidingTabStrip  the view throws an exception if there are no tabs available to display. It would be great if the view failed gracefully or gave a  		better error message. 
https://github.com/astuetz/PagerSlidingTabStrip/issues/69

#####111.  Android开发之ScrollView中嵌套ListView的解决方案   http://blog.csdn.net/minimicall/article/details/40983331

	 重写listview的onmeasure方法   
	 @Override
	    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
		int expandSpec = MeasureSpec.makeMeasureSpec(Integer.MAX_VALUE >> 2,
		        MeasureSpec.AT_MOST);
		super.onMeasure(widthMeasureSpec, expandSpec);
	    }

	这个方法有一个同样的毛病，就是默认显示的首项是ListView，需要手动把ScrollView滚动至最顶端。
	sv = (ScrollView) findViewById(R.id.act_solution_4_sv);
	sv.smoothScrollTo(0, 0);

	int	AT_MOST	Measure specification mode: The child can be as large as it wants up to the specified size.
	int	EXACTLY	Measure specification mode: The parent has determined an exact size for the child.
	int	UNSPECIFIED	Measure specification mode: The parent has not imposed any constraint on the child.

##### 112.  java.lang.NullPointerException    at android.webkit.HTML5VideoView.isPlaying(HTML5VideoView.java:122)		    at android.webkit.HTML5VideoViewProxy$VideoPlayer.isPlaying(HTML5VideoViewProxy.java:269)
	检查清单文件对应activity的配置
	android:configChanges="orientation|screenLayout"


#####113.   Caused by: java.lang.IllegalStateException: You need to use a Theme.AppCompat theme (or descendant) with this activity.

#####114.http://jgilfelt.github.io/android-actionbarstylegenerator/
	这个网站可以在线配置action bar的样式，支持holo、support v7、sherlock 





#####115.在其它界面异常之后返回到FragmentActivity Fragment显示异常（重叠或不显示）解决方 ...

	前面专门开了个帖来问这个问题，问题描述详见：http://www.eoeandroid.com/thread-496879-1-1.html
	当然，问题没有解决掉，一直也很郁闷，今天花了点时间换了N多关键词来找，最后也忘了在哪里看到一个方法，死马当活马医的写上，居然好了。
	解决方案是，在FragmentActivity里重写onSaveInstanceState，并且去掉super.onSaveInstanceState()即可。
	原因：猜测应该是在二级界面抛了异常之后，应用在返回上级界面时会从onSaveInstanceState内读取FragmentActivity缓存的状态，所以导致Fragment全部显示（显示重叠）或者显示不出来。（只是猜测）
	@Override protected void onSaveInstanceState(Bundle outState) { }


#####116.修复Android App中出现的重复菜单项及Fragment重叠
https://typeblog.net/tech/2014/08/22/fix-duplicate-menu.html


	 fragment replace出现重叠


	一般fragment的容器都是fragment，用到的方法：

	FragmentManager fm = getActivity().getSupportFragmentManager();
	FragmentTransaction ft = fm.beginTransaction();
	ft.replace(R.id.container, fragment);
	ft.addToBackStack(null);
	ft.commit();
	replace这个方法在fragment内部直接代入布局的id是不会有问题的，但是在外部比如Activitiy中用就会出现fragment叠加的问题。

	有很多人说给每个fragment设置背景色或图片，但是我觉得额外费资源。

	其实只要改成这样就好了，但这之中的原理又有谁懂呢？

	http://stackoverflow.com/questions/12958555/android-replace-fragment-still-displays-some-of-the-replaced-fragment

	transaction.replace(((ViewGroup)(getView().getParent())).getId(), fragment);



#####117.通过activity 得到它的fM,通过tag指定到上级fragment，从而获取到其中的接口数据 yyb
        if (getActivity().getSupportFragmentManager().findFragmentByTag("videos") instanceof QuickReturnInterface) {
            mCoordinator = (QuickReturnInterface) getActivity().getSupportFragmentManager().findFragmentByTag("news");
        } else {
            throw new ClassCastException("Parent container must implement the QuickReturnInterface");
        }


#####118.内存优化相关   ANDROID内存优化(大汇总)   http://blog.csdn.net/a396901990/article/details/38707007

#####119.PagerSlidingTabStrip   Changing the title of the adapter and notifyDatasetChanged does not work. #13
	Call notifyDataSetChanged() on the PagerSlidingTabStrip instead.
	Worked for me yesterday with data loaded from a CursorLoader.


#####120.Ubuntu下的屏幕录制软件RecordMyDesktop


	安装：
	sudo apt-get install gtk-recordmydesktop

	使用：

	安装好之后该软件会在影音软件里面，打开就可以。然后可以选择需要录制的窗口，如果不选择的话就默认是用户在屏幕上的所有操作。点击“录制”就开始了，此时该软件隐藏在   上方的任务栏（红色圆圈），可以随时停止录制。得到的视频保存在主目录下，其格式为Ogg。如果需要把它转换为avi格式，可以安装软件mencoder，命令如下：

	sudo apt-get install mencoder

	然后用下面的命令转换：
	mencoder -ovc lavc -oac copy -lavcoptsvcodec=mpeg4 -o outfile.avi infile.ogv




	 ubuntu动态截图，制作GIF动画

	Ubuntu 下, 如何录制 gif 格式的屏幕截图

	1. 安装 gtk-recordmydesktop 来录制屏幕, 安装 mplayer 將视频分解成单帧图片, 安装 imagemagick 將单帧图片压缩成一张 gif:

	sudo apt-get install imagemagick mplayer gtk-recordmydesktop
	2. 命令行下执行, 录制并保存文件为 out.ogv:

	gtk-recordmydesktop
	3. 执行如下命令將 out.ogv 分解成单帧图片:

	mplayer -ao null out.ogv -vo jpeg:outdir=.
	4. 执行如下命令將单帧图片压缩成 gif 图片:

	convert *.jpg out.gif
	5. 执行如下命令將 gif 图片进行压缩:

	convert out.gif -fuzz 10% -layers Optimize optimized.gif
	Live Like You're Dying And Never Stop Tying


#####121.一个ListView中会创建很多个convertview，并不是所有的都复用的，比如同一屏显示的肯定都是不一样的convertview。

#####122.性能优化  框架的选择。volley【尽量google支持的或者原生的】  buttferty  greendao  【没有采用反射技术的，比如greendao使用的是code generation。而不是注解】
	
	为什么greenDao使用的是code generation，而不是注解？

	对于greenDao，代码生成是非常合理的。在Android平台上，基于注解的解决方式是有缺陷的：它们不得不依赖于元数据的解析和反射。特别是反射，会显著降低ORM工具的性能。另一方面，greenDao会为Android生成优化过的代码。这些生成的代码完全避免了反射。这也是greenDao如此快的主要原因。另一个优势是大小。

	greenDao的核心lib是非常小的（在100K以下，包括单元测试）。这是因为对于一些ORM的内部逻辑都在generator中，而不是在核心库中。

	greenDao包含了：DaoCore，DaoGenerator和DaoTest。DaoCore是需要你加入到android项目中的，在Apache License 2版本以下是许可的。

	DaoGenerator是java程序，负责实体的生成，DAO和其它的文件。DaoTest是单元测试用例额，确保了greenDao本身和其稳定性。

	DaoGenerator 和DaoTest 在GPL V3以下是可用的。这些许可条款可以满足大部分的开发者使用。


#####123.Lazy Loading
	lazy不是翻译成懒，差不多算延迟、推迟的意思。
	是说不在初始化时loading，而是推迟到必须loading时才进行loading。


#####124.android-stuido    File > Invalidate
问题：could not save application settings:java.util.zip.zipexception:incorrect header check 

	https://code.google.com/p/android/issues/detail?id=56190
解决
	It looks like there's a corrupted cache.
	To work around this, invoke **File > Invalidate** Caches.  If you can't start Android Studio at all, try going to the cache directory (its location depends on your platform) and delete it, then start Studio.


#####125.[Android.gitignore](https://github.com/github/gitignore/blob/master/Android.gitignore)
	.gradle
	/local.properties
	/.idea/workspace.xml
	/.idea/libraries
	.DS_Store
	/build
	# Built application files
	*.apk
	*.ap_

	# Files for the Dalvik VM
	*.dex

	# Java class files
	*.class

	# Generated files
	bin/
	gen/

	# Gradle files
	.gradle/
	build/
	/*/build/

	# Local configuration file (sdk path, etc)
	local.properties

	# Proguard folder generated by Eclipse
	proguard/

	# Log Files
	*.log


#####126.NDK With Android Studio
http://blog.csdn.net/u011570979/article/details/43966567

#####127.chrome+红杏 honx.in/i/VLMhwoIaA1yvXz7n

#####127.ANDROID仿IOS时间_ANDROID仿IOS弹出提示框
 http://dwtedx.com/itshare_297.html

#####128. Android TextView drawableLeft 在代码中实现

方法1

Drawable drawable= getResources().getDrawable(R.drawable.drawable);
/// 这一步必须要做,否则不会显示.
drawable.setBounds(0, 0, drawable.getMinimumWidth(), drawable.getMinimumHeight());
myTextview.setCompoundDrawables(drawable,null,null,null);

方法2

public void setCompoundDrawablesWithIntrinsicBounds (Drawable left,
Drawable top, Drawable right, Drawable bottom)




#####129. /* 去锯齿 */ paint.setAntiAlias(true);

#####130.android 画图之setXfermode   
http://blog.csdn.net/wm111/article/details/7299294
	setXfermode 

	设置两张图片相交时的模式 

	我们知道 在正常的情况下，在已有的图像上绘图将会在其上面添加一层新的形状。 如果新的Paint是完全不透明的，那么它将完全遮挡住下面的Paint； 

	而setXfermode就可以来解决这个问题 


	一般来说 用法是这样的 
	[java] view plaincopy

	    Canvas canvas = new Canvas(bitmap1);  
	      
	    paint.setXfermode(new PorterDuffXfermode(Mode.SRC_IN));  
	      
	    canvas.drawBitmap(mask, 0f, 0f, paint);    

#####131.   ubuntu android cordova
	Setting up PhoneGap on Ubuntu for Android app development

#####132.webview的页面都finish了居然还能听到视频播放的声音，查了下发现webview的
	onResume方法可以继续播放，
	onPause可以暂停播放，
	但是这两个方法都是在Added in API level 11添加的，所以需要用反射来完成。
	停止播放：在页面的onPause方法中使用：
	webView.getClass().getMethod("onPause").invoke(webView,(Object[])null);
	继续播放：在页面的onResume方法中使用：
	webView.getClass().getMethod("onResume").invoke(webView,(Object[])null);
	这样就可以控制视频的暂停和继续播放了。

	在webView的Activity配置里面加上：
	android:hardwareAccelerated="true"


#####133.Create new project on Android, Error: Studio Unknown host 'services.gradle.org'
	解决方法
	please try following steps:
	Go to..

	File --> settings --> HTTP Proxy [Under IDE Settings] --> Auto-detect proxy settings

	you can also use the test connection button and check with google.com if it works or not
    [关于红杏的公益代理, Android Studio以及freso的编译](http://www.liaohuqiu.net/cn/posts/about-red-apricot-and-compiling-fresco/)

#####134.ListView.setOnItemClickListener 点击无效


	如果ListView中的单个Item的view中存在checkbox，button等view，会导致ListView.setOnItemClickListener无效，

	事件会被子View捕获到，ListView无法捕获处理该事件.

	解决方法：

	在checkbox、button对应的view处加android:focusable="false"
	   android:clickable="false"android:focusableInTouchMode="false"

	其中focusable是关键

	 

	从OnClickListener调用getSelectedItemPosition()，Click 和selection 是不相关的，Selection是通过D-pad or trackball 来操作的，Click通常是点击操作的。

	 

	arg2参数才是点击事件位置的参数

#####135.listview addheader 如果有多个header，可以把多个header封装。把封装后的view作为header

#####136.emojicon
emojicon, https://github.com/rockerhieu/emojicon
emojicon, https://github.com/ankushsachdeva/emojicon

#####137.新闻评论页，如何实现盖楼，listview的高度自适应？
    控件的高度 设为wrap_content

#####138.android改变CheckBox和后面文字的间距  http://www.haodaima.net/art/1891872
	解决方法：
	1.设置android:paddingLeft="25dip",就可以了。
	2.设置checkbox的背景图片。系统默认的给checkbox加的有一个透明的背景。


#####139.volley请求超时 如何处理  http://stackoverflow.com/questions/17094718/android-volley-timeout

	myRequest.setRetryPolicy(new DefaultRetryPolicy(
		        MY_SOCKET_TIMEOUT_MS, 
		        DefaultRetryPolicy.DEFAULT_MAX_RETRIES, 
		        DefaultRetryPolicy.DEFAULT_BACKOFF_MULT));  
#####140.Listview getItemViewType的使用  对于不同xml，使用多个viewhold


#####141.Android “Only the original thread that created a view hierarchy can touch its views.”    http://stackoverflow.com/questions/5161951/android-only-the-original-thread-that-created-a-view-hierarchy-can-touch-its-vi
	thread = new Thread(){
		@Override
		public void run() {
		    try {
		        synchronized (this) {
		            wait(5000);

		            runOnUiThread(new Runnable() {
		                @Override
		                public void run() {
		                    dbloadingInfo.setVisibility(View.VISIBLE);
		                    bar.setVisibility(View.INVISIBLE);
		                    loadingText.setVisibility(View.INVISIBLE);
		                }
		            });

		        }
		    } catch (InterruptedException e) {
		        e.printStackTrace();
		    }
		    Intent mainActivity = new Intent(getApplicationContext(),MainActivity.class);
		    startActivity(mainActivity);
		};
	    };  
	    thread.start();
#####142.Java SDK提供了对上述三种压缩技术的支持：Inflater类和Deflater类直接用zlib库对数据压缩/
	解压缩，GZIPInputStream类和GZIPOutputStream类提供了对gzip格式的支持，ZipFile、Zi
	pInputStream、ZipOutputStream则用于处理zip格式的文件。

	所以，你应当根据你的具体需求，选择不同的压缩技术：如果只需要压缩/解压缩数据，你
	可以直接用zlib实现，如果需要生成gzip格式的文件或解压其他工具的压缩结果，你就必须
	用gzip或zip等相关的类来处理了。


#####143.利用volley进行http设置请求头、超时及请求参数设置(post)

	这里以post请求说明，get请求相似设置请求头及超时。

	1.自定义request，继承com.android.volley.Request

	2.构造方法实现（basecallback,为自定义的监听，实现Response.Listener,ErrorListener接口）--post请求

	 public BaseRequest(String url,String params, BaseCallback<T> callback)
	    {
		super(Method.POST, url, callback);
		this.callback = callback;
		this.params = params;
		Log.e(TAG, "request:" + params);
		setShouldCache(false);
	    }
	3.请求头设置：重写getHeaders方法

	 @Override
	    public Map<String, String> getHeaders() throws AuthFailureError
	    {
		Map<String, String> headers = new HashMap<String, String>();
		headers.put("Charset", "UTF-8");
		headers.put("Content-Type", "application/x-javascript");
		headers.put("Accept-Encoding", "gzip,deflate");
		return headers;
	    }
	设置字符集为UTF-8,并采用gzip压缩传输

	4.超时设置：重写getRetryPolicy方法

	 @Override
	    public RetryPolicy getRetryPolicy()
	    {
		RetryPolicy retryPolicy = new DefaultRetryPolicy(SOCKET_TIMEOUT, DefaultRetryPolicy.DEFAULT_MAX_RETRIES, DefaultRetryPolicy.DEFAULT_BACKOFF_MULT);
		return retryPolicy;
	    }
	5.请求参数组装：重写getBody方法

	 @Override
	    public byte[] getBody() throws AuthFailureError
	    {
		return params == null ? super.getBody() : params.getBytes();
	    }
	 

#####144.  android handler的警告Handler Class Should be Static or Leaks Occur

	在使用Handler更新UI的时候，我是这样写的：


	public class SampleActivity extends Activity {
		                                                      
	  private final Handler mLeakyHandler = new Handler() {
	    @Override
	    public void handleMessage(Message msg) {
	      // TODO
	    }
	  }
	}
	看起来很正常的，但是 Android Lint 却给出了警告：

	This Handler class should be static or leaks might occur

	意思是说：这个Handler 必须是static的，否则就会引发内存泄露。

	其实，对于这个问题，Android Framework 的工程师 Romain Guy 早已经在Google论坛上做出过解释，并且给出了他的建议写法：



	I wrote that debugging code because of a couple of memory leaks I 
	found in the Android codebase. Like you said, a Message has a 
	reference to the Handler which, when it's inner and non-static, has a 
	reference to the outer this (an Activity for instance.) If the Message 
	lives in the queue for a long time, which happens fairly easily when 
	posting a delayed message for instance, you keep a reference to the 
	Activity and "leak" all the views and resources. It gets even worse 
	when you obtain a Message and don't post it right away but keep it 
	somewhere (for instance in a static structure) for later use. 



	他的建议写法是：


	class OuterClass {
		                          
	  class InnerClass {
	    private final WeakReference<OuterClass> mTarget;
		                          
	    InnerClass(OuterClass target) {
		   mTarget = new WeakReference<OuterClass>(target);
	    }
		                          
	    void doSomething() {
		   OuterClass target = mTarget.get();
		   if (target != null) {
		        target.do();    
		   }
	     }
	}
	下面，我们进一步解释一下：

	1.Android App启动的时候，Android Framework 为主线程创建一个Looper对象，这个Looper对象将贯穿这个App的整个生命周期，它实现了一个消息队列（Message  Queue），并且开启一个循环来处理Message对象。而Framework的主要事件都包含着内部Message对象，当这些事件被触发的时候，Message对象会被加到消息队列中执行。
	2.当一个Handler被实例化时（如上面那样），它将和主线程Looper对象的消息队列相关联，被推到消息队列中的Message对象将持有一个Handler的引用以便于当Looper处理到这个Message的时候，Framework执行Handler的handleMessage(Message)方法。
	3.在 Java 语言中，非静态匿名内部类将持有一个对外部类的隐式引用，而静态内部类则不会。

	到底内存泄露是在哪里发生的呢？以下面代码为例：


	public class SampleActivity extends Activity {
		          
	  private final Handler mLeakyHandler = new Handler() {
	    @Override
	    public void handleMessage(Message msg) {
	      // ...
	    }
	  }
		          
	  @Override
	  protected void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
		          
	    // Post a message and delay its execution for 10 minutes.
	    mLeakyHandler.postDelayed(new Runnable() {
	      @Override
	      public void run() { }
	    }, 60 * 10 * 1000);
		          
	    // Go back to the previous Activity.
	    finish();
	  }
	}
	当Activity被finish()掉，Message 将存在于消息队列中长达10分钟的时间才会被执行到。这个Message持有一个对Handler的引用，Handler也会持有一个对于外部类（SampleActivity）的隐式引用，这些引用在Message被执行前将一直保持，这样会保证Activity的上下文不被垃圾回收机制回收，同时也会泄露应用程序的资源（views and resources）。

	为解决这个问题，下面这段代码中的Handler则是一个静态匿名内部类。静态匿名内部类不会持有一个对外部类的隐式引用，因此Activity将不会被泄露。如果你需要在Handler中调用外部Activity的方法，就让Handler持有一个对Activity的WeakReference，这样就不会泄露Activity的上下文了，如下所示：


	public class SampleActivity extends Activity {
		 
	  /**
	   * Instances of static inner classes do not hold an implicit
	   * reference to their outer class.
	   */
	  private static class MyHandler extends Handler {
	    private final WeakReference<SampleActivity> mActivity;
		 
	    public MyHandler(SampleActivity activity) {
	      mActivity = new WeakReference<SampleActivity>(activity);
	    }
		 
	    @Override
	    public void handleMessage(Message msg) {
	      SampleActivity activity = mActivity.get();
	      if (activity != null) {
		// ...
	      }
	    }
	  }
		 
	  private final MyHandler mHandler = new MyHandler(this);
		 
	  /**
	   * Instances of anonymous classes do not hold an implicit
	   * reference to their outer class when they are "static".
	   */
	  private static final Runnable sRunnable = new Runnable() {
	      @Override
	      public void run() { }
	  };
		 
	  @Override
	  protected void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
		 
	    // Post a message and delay its execution for 10 minutes.
	    mHandler.postDelayed(sRunnable, 60 * 10 * 1000);
		     
	    // Go back to the previous Activity.
	    finish();
	  }
	}
	总结：
	在实际开发中，如果内部类的生命周期和Activity的生命周期不一致（比如上面那种，Activity finish()之后要等10分钟，内部类的实例才会执行），则在Activity中要避免使用非静态的内部类，这种情况，就使用一个静态内部类，同时持有一个对Activity的WeakReference。

##### 146.FragmentPagerAdapter （getSupportFragmentManager() ） You must call removeView() on the child's parent
	How to solve for viewpager : The specified child already has a parent. You must call removeView() on the child's parent first
http://stackoverflow.com/questions/13559353/how-to-solve-for-viewpager-the-specified-child-already-has-a-parent-you-must
解决方法
	I had the same problem when I used

	View res = inflater.inflate(R.layout.fragment_guide_search, container);
	inside Fragment.onCreateView(...

	You must call

	View res = inflater.inflate(R.layout.fragment_guide_search, container, false);
	or

	View res = inflater.inflate(R.layout.fragment_guide_search, null);

参考：

[1]https://groups.google.com/forum/?fromgroups=#!msg/android-developers/1aPZXZG6kWk/lIYDavGYn5UJ
[2]http://www.androiddesignpatterns.com/2013/01/inner-class-handler-memory-leak.html
[3]http://stackoverflow.com/questions/11407943/this-handler-class-should-be-static-or-leaks-might-occur-incominghandler



##### 145. 使用代码为textview设置drawableLeft

	Drawable drawable= getResources().getDrawable(R.drawable.drawable);  
	/// 这一步必须要做,否则不会显示.  
	drawable.setBounds(0, 0, drawable.getMinimumWidth(), drawable.getMinimumHeight());  
	myTextview.setCompoundDrawables(drawable,null,null,null);  

##### 146.Android如何在java代码中设置margin  

	LinearLayout.LayoutParams lp = new LinearLayout.LayoutParams(LinearLayout.LayoutParams.WRAP_CONTENT, LinearLayout.LayoutParams.WRAP_CONTENT);  
	lp.setMargins(10, 20, 30, 40);  
	imageView.setLayoutParams(lp);

##### 147.出错了表现:Conversion to Dalvik format failed: Unable to execute dex: method ID not in [0, 0xffff]: 65536
	解决:谷歌出了 新的Multidex支持库  androidstudio    https://developer.android.com/tools/building/multidex.html
		android {
			    compileSdkVersion 21
			    buildToolsVersion "21.1.0"

			    defaultConfig {
				...
				minSdkVersion 14
				targetSdkVersion 21
				...

				// Enabling multidex support.
				multiDexEnabled true
			       }
			      ...
			}

			dependencies {
			  compile 'com.android.support:multidex:1.0.0'
			}



##### 148.How to get Nautilus-scripts working on Ubuntu 14.04?

	nautilus-actions-config-tool
	
	http://askubuntu.com/questions/281062/how-to-get-nautilus-scripts-working-on-ubuntu-13-04  设置好之后 nautilus -q。重启下nautilus服务生效

	http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-add-open-as-rootadministrator-to-context-menu/

##### 149. imageloader显示图片所使用的uri：
	String imageUri = "http://site.com/image.png"; // from Web
	String imageUri = "file:///mnt/sdcard/image.png"; // from SD card
	String imageUri = "content://media/external/audio/albumart/13"; // from content provider
	String imageUri = "assets://image.png"; // from assets
	String imageUri = "drawable://" + R.drawable.image; // from drawables (only images, non-9patch)
	注意：使用drawable://除非你真的需要他。时刻要注意使用本地图片加载方法：setImageResource带代替ImageLoader。
	五，有用的信息
	1，ImageLoader.getInstance().init(config); // 在应用开启的时候初始化。
	2，<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>sd卡缓存是需要写入权限
	3，ImageLoader根据ImageView的width，height确定图片的宽高。
	4，如果经常出现OOM
	   ①减少配置之中线程池的大小，(.threadPoolSize).推荐1-5；
	   ②使用.bitmapConfig(Bitmap.config.RGB_565)代替ARGB_8888;
	   ③使用.imageScaleType(ImageScaleType.IN_SAMPLE_INT)或者try.imageScaleType(ImageScaleType.EXACTLY)；
	   ④避免使用RoundedBitmapDisplayer.他会创建新的ARGB_8888格式的Bitmap对象；
	   ⑤使用.memoryCache(new WeakMemoryCache())，不要使用.cacheInMemory();
	5，内存缓存，sd卡缓存，显示图片，可以使用已经初始化过的实现；
	6，为了避免使用list，grid，scroll，你可以使用
	boolean pauseOnScroll = false; // or true
	boolean pauseOnFling = true; // or false
	PauseOnScrollListener listener = new PauseOnScrollListener(imageLoader, pauseOnScroll, pauseOnFling);
	listView.setOnScrollListener(listener);


##### 150.View's getWidth() and getHeight() returning 0
	You should use: image1.getLayoutParams().width;    http://stackoverflow.com/questions/18268915/views-getwidth-and-getheight-returning-0

##### 151.GridView的行数问题
	在gridview里边设置属性 android:numColumns="3"；意思是三列 然后在BaseAdapter的 getCount()方法 里边返回9。这样就可以平分为3行3列了


##### 152.ArrayList和数组间的相互转换   http://wanglihu.iteye.com/blog/243238

	ArrayList提供public <T> T[] toArray(T[] a)

	public static <T> List<T> asList(T... a)



##### 153.Unexpected response code 500

	网页已经被关闭
	还有就是，一般由于内部服务器错误造成的。
	  服务器关闭或者服务器升级而造成的资源无法访问
	  由于服务器太忙而造成的，此时无法处理请求。通讯量超出 Web 站 点的能力



##### 154. banner广告及view pager 的小圆点指示器  CirclePageIndicator   http://9437752.blog.51cto.com/9427752/1580984


##### 155.使用ViewPager+GridView实现横向滑动的效果  http://blog.csdn.net/developer_jiangqq/article/details/9364501

##### 156.CircleImageView  https://github.com/hdodenhof/CircleImageView

##### 157.ViewPager FragmentPagerAdapter Nullpointer   fragmentpageradapter和pageradapter的区别。使用的场景。

##### 158.unable to have ViewPager WRAP_CONTENT       http://stackoverflow.com/questions/8394681/android-i-am-unable-to-have-viewpager-wrap-content
	Overriding onMeasure of your ViewPager as follows will make it get the height of the biggest child it currently has.

	@Override 
	protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
	 
	    int height = 0;
	    for(int i = 0; i < getChildCount(); i++) {
		View child = getChildAt(i);
		child.measure(widthMeasureSpec, MeasureSpec.makeMeasureSpec(0, MeasureSpec.UNSPECIFIED));
		int h = child.getMeasuredHeight();
		if(h > height) height = h;
	    } 
	 
	    heightMeasureSpec = MeasureSpec.makeMeasureSpec(height, MeasureSpec.EXACTLY);
	 
	    super.onMeasure(widthMeasureSpec, heightMeasureSpec);
	} 


##### 159.在自定义视图布局文件中，仅支持FrameLayout、LinearLayout、RelativeLayout三种布局控件和AnalogClock、Chronometer、Button、ImageButton、ImageView、ProgressBar、TextView、ViewFlipper、ListView、GridView、StackView和AdapterViewFlipper这些显示控件，不支持这些类的子类或Android提供的其他控件。否则会引起ClassNotFoundException异常



##### 160.Android模拟器Genymotion加载ARM架构so文件   
	http://www.eoeandroid.com/thread-552875-1-1.html
	https://www.genymotion.com/#!/support?chapter=collapse-logs#faq


##### 161.Viewpager wrap_hight导致不显示。  重写ViewPager 

	 /**
	     * for bug   : unable to have ViewPager WRAP_CONTENT
	     */
	    @Override
	    protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
		int hight = 0;
		for (int i = 0; i < getChildCount(); i++) {
		    View child = getChildAt(i);
		    child.measure(widthMeasureSpec, MeasureSpec.makeMeasureSpec(0, MeasureSpec.UNSPECIFIED));
		    int h = child.getMeasuredHeight();
		    if (h > hight) hight = h;

		}
		heightMeasureSpec = MeasureSpec.makeMeasureSpec(hight, MeasureSpec.EXACTLY);
		super.onMeasure(widthMeasureSpec, heightMeasureSpec);
	    } 



##### 162.选择项有RadioGroup和另外一个button组成   点击button的时候，清除radiogroup中选中的radiobutton。调用radiogroup的clearCheck方法即可


##### 163.gridview    columnnum。上传照片

##### 164.  9.png   Error:Must have one-pixel frame that is either transparent or white. -xxx/app/src/main/res/drawable-xhdpi/icon_addpic_focused.png: libpng warning: iCCP: Not recognizing known sRGB profile that has been edited
解决方法如下
this is the problem with latest adt that is 20.0.3. you can instead rename the *.9.png to *.png and start working. i think this is the bug with the adt only, since for 18.0.0 version adt it doesnt prompts for this type of error and works fine



##### 165.    IntentRecieverLeakedException, Are you missing a call to unregisterReceiver() ? in android


	注册广播接收者有两种方式，一种在清单文件中注册。这个是长期有效的。另外一种是。在activity中注册，这种注册的生命周期在actity的生命周期内，还有第二种注册不要registerReceiver必须要和unregisterReceiver配套使用，否则会出现上述问题。
	http://stackoverflow.com/questions/9078390/intentrecieverleakedexception-are-you-missing-a-call-to-unregisterreceiver



166. SVN Ignore files in Android Studio   http://stackoverflow.com/questions/23536563/svn-ignore-files-in-android-studio

	There was nothing in the repository, until I did Share Directory on the project. It then created the folder for the project in the repository. I entered the following in Settings|Version Control|Subversion:

	File:.idea/workspace.xml
	File: .gradle
	Directory: build/
	Mask: *.iws
	Directory: .idea/libraries/
	Directory: app/build/
	File: local.properties

      下面的更彻底
	*.iml
	*.iws
	*.ipr
	.idea/
	.gradle/
	local.properties

	*/build/

	*~
	*.swp


##### 167.    packagingOptions {
        exclude 'META-INF/LICENSE.txt'
        exclude 'META-INF/NOTICE.txt'
    }


##### 168.CLEAN

Android Studio fails to debug with error org.gradle.process.internal.ExecException
Error:Execution failed for task ':app:dexDebug'.
> com.android.ide.common.process.ProcessException: org.gradle.process.internal.ExecException: Process 'command 'C:\Program Files\Java\jdk1.7.0_11\bin\java.exe'' finished with non-zero exit value 2

169.Eclipse混淆文件导入Android Studio Gradle编译报input jar file is specified twice    http://blog.csdn.net/X_i_a_o_H_a_i/article/details/41979983
原因是build.gradle文件配置了


dependencies {
    compile fileTree(include: '*.jar', dir: 'libs')

}

里面已经添加过jar包，混淆文件proguard-rules.pro里面又加了句-libraryjars libs/***.jar,将-libraryjars libs/***.jar 前面用#号注释或者直接删掉即可。


##### 170.key.java    android-stuido 中错误提示：“非法字符： \65279”    http://www.cnblogs.com/littlehb/archive/2013/04/20/3032721.html
对设置为“UTF-8”编码的文件在修改后保存时自动加入了UTF-8文件签名，即BOM（将文件以十六进制形式查看，可见文件首部为“EF BB BF”）.

解决方法：
	使用Notepad++去除BOM 【在IntelliJ IDEA 12使用，可成功】

	具体方法：先设置以UTF-8无ROM方式编码，然后打开文件，另存此文件，覆盖掉原文件。

	设置方法：格式->以UTF-8无ROM方式编码。


##### 171.LocalBroadcastManager 解决fragment中通信的问题
	最近在开发平板项目，完全是fragmentactivity+fragment的结构。看起来似乎简单，但是和以前不同的是，业务逻辑非常复杂，多处的非常规跳转，
	fragment之间的数据交换，一处更新多处更新等操作，有时玩起来都心塞。项目背景介绍完毕。
	现在有这样一个场景，项目需求是，后台可配置功能，也就是说app端所有的功能都是后台配置上去的动态生成，对应的功能界面如下图。
	能够完成在应用内的广播发送，而且比全局广播更具优势:
	1).广播只会在你的应用内发送，所以无需担心数据泄露，更加安全。
	2).其他应用无法发广播给你的应用，所以也不用担心你的应用有别人可以利用的安全漏洞
	3).相比较全局广播，它不需要发送给整个系统，所以更加高效。

	2. 使用方式
	广播注册：
	LocalBroadcastManager localBroadcastManager = LocalBroadcastManager.getInstance(getActivity());
	IntentFilter filter = new IntentFilter();
	filter.addAction(ACTION);
	myBroadcastReciver = new MyBroadcastReciver();
	localBroadcastManager.registerReceiver(myBroadcastReciver, filter);
	复制代码
	广播发送：
	Intent intent = new Inten();
	intent.setAction(SaleLeftFragment.ACTION);
	intent.putExtra(TAG, data);
	LocalBroadcastManager.getInstance(getActivity()).sendBroadcast(intent);
	复制代码
	3.使用注意
	在使用的时候，请关注以下几点:
	1).LocalBroadcastManager注册广播只能通过代码注册的方式。
	2).LocalBroadcastManager注册广播后，一定要记得取消监听。
	3).重点的重点，使用LocalBroadcastManager注册的广播，您在发送广播的时候务必使用


Fragment间的广播消息接收

	广播注册,可以写在Activity（onCreate）,也可以写在Fragment（onActivityCreated）里。

	复制代码
	LocalBroadcastManager broadcastManager = LocalBroadcastManager.getInstance(getActivity());
	IntentFilter intentFilter = new IntentFilter();
	intentFilter.addAction("android.intent.action.CART_BROADCAST");//建议把它写一个公共的变量，这里方便阅读就不写了。
	BroadcastReceiver mItemViewListClickReceiver = new BroadcastReceiver() {
		    @Override
		    public void onReceive(Context context, Intent intent){
		        System.out.println("OK");
		    }
	 };
	 broadcastManager.registerReceiver(mItemViewListClickReceiver, intentFilter);
	复制代码
	 

	 


	发送广播

	Intent intent = new Intent("android.intent.action.CART_BROADCAST");
	LocalBroadcastManager.getInstance(getActivity()).sendBroadcast(intent);


##### 172.[How can I] Change the password, so I can share it with others and let them sign
Using keytool:

	keytool -storepasswd -keystore /path/to/keystore
	Enter keystore password:  changeit
	New keystore password:  new-password
	Re-enter new keystore password:  new-password



##### 173.How to create a release signed apk file using Gradle?
http://stackoverflow.com/questions/18328730/how-to-create-a-release-signed-apk-file-using-gradle


##### 174.No activity found to handle intent action.dial
 Uri.parse("tel:" + a1)
 Android 调用系统Email --多附件
Intent.ACTION_SENDTO  无附件的发送
  Intent.ACTION_SEND  带附件的发送
  Intent.ACTION_SEND_MULTIPLE  带有多附件的发送
Intent data=new Intent(Intent.ACTION_SENDTO);    
data.setData(Uri.parse("mailto:455245521@qq.com"));    
data.putExtra(Intent.EXTRA_SUBJECT, "这是标题");    
data.putExtra(Intent.EXTRA_TEXT, "这是内容");    
startActivity(data);   


##### 175.HTML 中有用的字符实体
注释：实体名称对大小写敏感！
显示结果	描述	实体名称	实体编号
 	空格	&nbsp;	&#160;
<	小于号	&lt;	&#60;
>	大于号	&gt;	&#62;
&	和号	&amp;	&#38;
"	引号	&quot;	&#34;
'	撇号 	&apos; (IE不支持)	&#39;
￠	分	&cent;	&#162;
£	镑	&pound;	&#163;
¥	日圆	&yen;	&#165;
€	欧元	&euro;	&#8364;
§	小节	&sect;	&#167;
©	版权	&copy;	&#169;
®	注册商标	&reg;	&#174;
™	商标	&trade;	&#8482;
×	乘号	&times;	&#215;
÷	除号	&divide;	&#247;


##### 176.Generating signed release APK using Gradle   https://github.com/almalkawi/Android-Guide/wiki/Generating-signed-release-APK-using-Gradle
	 How to create a release signed apk file using Gradle?   http://stackoverflow.com/questions/18328730/how-to-create-a-release-signed-apk-file-using-gradle
	android {
	    compileSdkVersion 17

	    signingConfigs {
		releaseSigning {
		    storeFile file(System.getenv("ANDROID_KEYSTORE"))
		    storePassword System.console().readLine("\nStore password: ")
		    keyAlias System.getenv("ANDROID_KEYALIAS")
		    keyPassword System.console().readLine("Key password: ")
		}
	    }

	    buildTypes {
		release {
		    signingConfig signingConfigs.releaseSigning
		}
	    }
	}
	Now, you can generate the signed and zipaligned release APK using the Gradle task:

	./gradlew assembleRelease


##### 177.Android Studio: How to use Monitor(DDMS) tool to debug application step by step?

	Go to "Tools > Android > Android Device Monitor" in v0.8.6. That will pull up the DDMS eclipse perspective.

     dump viewhierarchy for ui automator 可以查看应用的布局，当对某个app布局感兴趣时，可以采用此种方式查看此app的布局，相当于布局反编译功能。


##### 178. 如何通过java代码设置textview字体加粗。
	textView.setTypeface(Typeface.defaultFromStyle(Typeface.BOLD));//加粗  


##### 179.qickreturn swiperefreshlayout

##### 180. viewpager中彻底性动态添加、删除Fragment   http://stackoverflow.com/questions/10396321/remove-fragment-page-from-viewpager-in-android
	viewpager在加载当前页的时候已经将pager页左右页的内容加载进内存里了，这样才保证了viewpager左右滑动的时候的流畅性；
	为了解决彻底删除fragment，我们要做的是：
	1.将FragmentPagerAdapter 替换成FragmentStatePagerAdapter，因为前者只要加载过，fragment中的视图就一直在内存中，在这个过程中无论你怎么刷新，清除都是无用的，直至程序退出； 后者 可以满足我们的需求。
	2.我们可以重写Adapter的方法--getItemPosition()，让其返回PagerAdapter.POSITION_NONE即可；



##### 181. Uri.encode


##### 182.omniplan mac

##### 183.androidstudio svn delete

##### 184.GreenDao query OR within AND  
	http://stackoverflow.com/questions/22785327/greendao-query-or-within-and

	QueryBuilder.and() and QueryBuilder.or() are used to combine WhereConditions. The resulting WhereConditions have to be used inside QueryBuilder.where() (which will combine the conditions using AND) or QueryBuilder.whereOr().

##### 185.greendao  删除某个对象

http://www.cnblogs.com/spring87/p/4364769.html
	1.public void deleteCityInfo(int cityId)
	2.{
	3.QueryBuilder<DBCityInfo> qb = cityInfoDao.queryBuilder();
	4.DeleteQuery<DBCityInfo> bd = qb.where(Properties.CityId.eq(cityId)).buildDelete();
	5.bd.executeDeleteWithoutDetachingEntities();
	6.}


##### 187. androidstudio   ctrl+shift+t 模糊搜索类
                    ctrl+o 本文件的函数
		    ctrl+g  全局搜索类 变量 函数
                   alter+insert 快速插入getset等
		Ctrl+Shift+F7 可以高亮当前元素在当前文件中的使用
		Android Studio 如何提示函数用法？   先选中，然后按F2

##### 188.Fragment的通信有关问题, 新建Fragment为何不要在构造方法中传递参数   
http://233.io/article/1057296.html

##### 189.
在理解反射的时候，不得不说一下内存。
    先理解一下JVM的三个区：堆区，栈区，和方法去（静态区）。
   堆区：存放所有的对象，每个对象都有一个与其对应的class信息。在JVM中只有一个堆区，堆区被所有的线程共享。
    栈区：存放所有基础数据类型的对象和所有自定义对象的引用，每个线程包含一个栈区。每个栈区中的数据都是私有的，其他栈不能访问。
   栈分为三部分：
        基本类型变量区、执行环境上下文、操作指令区(存放操作指令)。 
    方法区：即静态区，被所有的线程共享。方法区包含所有的class和static变量。它们都是唯一的。
 
    在启动一个java虚拟机时，虚拟机要加载你程序里所用到的类 ，这个进程会首先跑到jdk中（在jdk的jre/lib/ext文件夹里找那些jar文件），如果没有找到，会去classpath里设置的路径去找。
    在找到要执行的类时：
    1.首先将找到的类的信息加载到运行时数据区的方法区。这个过程叫做类的加载。所以一下static类型的在类的加载过程中就已经放到了方法区。所以不用实例化就能用一个static类型的方法。
    2.加载完成后，在new一个类时，首先就是去方法区看看有没有这个类的信息。如果没有这个类的信息，先装载这个类。then，加载完成后，会在堆区为new的这个类分配内存，有了内存就有了实例，而这个实例指向的是方法区的该类信息。其实就是存放了在方法区的地址。而反射就是利用了这一点。


##### 190.  Genymotion Crash after a few minutes 
 E/eglCodecCommon(2163): writeFully: failed: Broken pipe

http://stackoverflow.com/questions/23855115/genymotion-crash-after-a-few-minutes

	It's not really caused by your application, so don't worry.

	It often happens when you computer goes in sleep mode and when you come back Genymotion will throw this exception (it happens to me very often).

	In your specific case sounds like the device goes in sleep mode so a way to fix it is simply to enable "Always stay awake" in developers options.
	


##### 192. A WebView method was called on thread 'Timer-1'. All WebView methods must be called on the UI thread. Future versions of WebView may not support use on other threads.


 java.lang.IllegalStateException: Timer was canceled
            at java.util.Timer.scheduleImpl(Timer.java:561)
            at java.util.Timer.schedule(Timer.java:481)
            at com.jetsun.hbfc.activity.base.CommonWebViewActivity$3.onPageStarted(CommonWebViewActivity.java:178)

Webview reload page get force close

Change your TimerTask to the following:

new TimerTask() { 
    @Override 
    public void run() { 
        runOnUiThread(new Runnable() {
            public void run() { 
                wvNovaMenzaCammera.reload(); 
            } 
        });       
    } 
} 


##### 193.http://blog.csdn.net/xieyuooo/article/details/8607220
Timer与TimerTask的真正原理&使用介绍


##### 194.http://233.io/article/1057296.html  Fragment的通信有关问题, 新建Fragment为何不要在构造方法中传递参数


##### 195.Add a new file in Intellij doesn't add to subversion
	http://stackoverflow.com/questions/2817452/add-a-new-file-in-intellij-doesnt-add-to-subversion
		Go to File -> Settings -> Version control -> Confirmation -> When files are created You're probably looking for "Add silently".

##### 196.使用Android Studio的lint清除无用的资源文件  http://waychel.com/shi-yong-android-studiode-lintqing-chu-wu-yong-de-zi-yuan-wen-jian/

##### 197. Android应用程序release打签名包时，出现错误:"XXX" is not translated in "af" (Afrikaans), "am" (Amharic), "ar" (Arabic).....

eclipse
	http://blog.csdn.net/u012264122/article/details/39371343

androidstudio  http://stackoverflow.com/questions/20699147/gradle-build-fails-on-lint-task

	// This is important, it will run lint checks but won't abort build
	  lintOptions {
	      abortOnError false
	  }


	if abortOnError false will not resolve your problem, you can try this.

	lintOptions {
	    checkReleaseBuilds false
	}

##### 198.  
全面提高Ubuntu Linux操作系统运行速度

	1.六招让你的Ubuntu马上提速  http://article.yeeyan.org/view/205625/294577


	       Where did the startup-applications-preferences program go?  ubuntu satartup applications preference
		 http://askubuntu.com/questions/159887/where-did-the-startup-applications-preferences-program-go
		The if you can't find the program anywhere, try running gnome-session-properties from the command line (or alt+f2).

		If it's not installed, I'm sure you can install the package gnome-session-properties.

	2. 将localhost化名为主机名

		据说这个方法可以改善使用Ubuntu一段后，在GNOME中启动应用程序变慢的问题

		# vi /etc/hosts

		127.0.0.1 localhost

		127.0.1.1 Ubuntu

		===>

		127.0.0.1 localhost Ubuntu

		127.0.1.1 Ubuntu

		注:在第一行末尾加上主机名，也就是第二行的那个名字。

	3.安装preload

		可以把一些常用到的lib库和应用程序预加载到内存，以提高程序的启动速度

		# apt-get install preload

##### 199.volley由于网络访问比较慢，导致访问两次的现象  http://stackoverflow.com/questions/22428343/android-volley-double-post-when-have-slow-request?
		http://stackoverflow.com/questions/3352424/httpurlconnection-openconnection-fails-second-time

##### 200.当你想让一个高度值不足scrollview的子控件fillparent的时候，单独的定义 android:layout_height="fill_parent"是不起作用的，必须加上fillviewport属性，当子控件的高度值大于 scrollview的高度时，这个标签就没有任何意义了。

##### 201.activity FLAG_ACTIVITY_REORDER_TO_FRONT 无法startActivity  http://blog.csdn.net/mingli198611/article/details/8678513




##### 202.   Genymotion模拟器运行项目 jPush报错jpush Couldn't load jpush: findLibrary returned null  
at cn.jpush.android.api.JPushInterface.init(Unknown Source)

##### 203.androidstudio检查更新。Android Studio支持自动检查更新。之前尚未发布正式版时，一周有时会有几次更新。你可以设置检查的类型，用以控制更新类型。
	Settings --> Updates 。勾选 Check for updates in channel ，即开通了自动检查更新。你可以禁用自动检查更新。右侧的列表，是更新通道。
	Stable Channel ： 正式版本通道，只会获取最新的正式版本。
	Beta Channel ： 测试版本通道，只会获取最新的测试版本。
	Dev Channel ： 开发发布通道，只会获取最新的开发版本。
	Canary Channel ： 预览发布通道，只会获取最新的预览版本。rc  release candidates

以上4个通道中， Stable Channel 最稳定，问题相对较少， Canary Channel 能获得最新版本，问题相对较多。


204.AndroidのActivity之Listview组件快速拖动  android:fastScrollEnabled="true"  android:focusable="true" 



##### 205. Lint: How to ignore “<key> is not translated in <language>” errors?   
http://stackoverflow.com/questions/11443996/lint-how-to-ignore-key-is-not-translated-in-language-errors
To ignore this in a gradle build add this to the android section of your build file:

lintOptions {
   disable 'MissingTranslation'
}


Authentication Error errorcode: 201 uid: -1 appid -1 msg: APP被用户自己禁用
205.
ubuntu  apktool 2.0  Exception in thread "main" brut.androlib.err.UndefinedResObject


keytool -list -keystore SportsApp.keystore
##### 206.

Exception in thread "main" brut.androlib.AndrolibException: Could not decode arsc file
	at brut.androlib.res.decoder.ARSCDecoder.decode(ARSCDecoder.java:56)
	at brut.androlib.res.AndrolibResources.getResPackagesFromApk(AndrolibResources.java:491)
	at brut.androlib.res.AndrolibResources.loadMainPkg(AndrolibResources.java:74)
	at brut.androlib.res.AndrolibResources.getResTable(AndrolibResources.java:66)
	at brut.androlib.Androlib.getResTable(Androlib.java:50)
	at brut.androlib.ApkDecoder.getResTable(ApkDecoder.java:189)
	at brut.androlib.ApkDecoder.decode(ApkDecoder.java:114)
	at brut.apktool.Main.cmdDecode(Main.java:146)
	at brut.apktool.Main.main(Main.java:77)
Caused by: java.io.IOException: Expected: 0x001c0001, got: 0x00000000
	at brut.util.ExtDataInput.skipCheckInt(ExtDataInput.java:48)
	at brut.androlib.res.decoder.StringBlock.read(StringBlock.java:44)
	at brut.androlib.res.decoder.ARSCDecoder.readPackage(ARSCDecoder.java:102)
	at brut.androlib.res.decoder.ARSCDecoder.readTable(ARSCDecoder.java:83)
	at brut.androlib.res.decoder.ARSCDecoder.decode(ARSCDecoder.java:49)
	... 8 more


It seems there's some problem in building the resources while recompiling the apk. what you can do is, when you decompile your apk use this command

apktool d -f -r apkfilename.apk
here -f is to replace previous decompiled apk's code and -r is to ignore the decompiling of resources.

this would prevent the resources from being decompiled and will simply copy the same resources when you recompile the apk.


##### 207.尊敬的三星用户您好：
三星I9228手机截止目前支持升级的最新版本是安卓4.1
1.Fota方式升级：通过手机设定-（一般）-关于设备-系统更新（或软件更新）-更新。
此方式升级固件注意事项：
1).手机需设置为当前时间
2).建议升级时手机有足够的电量最好多于50%。
3).手机需要有足够的存储空间(至少1GB USB存储器)。
4).网络环境稳定（系统/固件更新版本较大，可能会消耗较多流量，建议升级时可以使用WLAN上网方式操作）。
2.Kies方式升级：在电脑中安装Kies软件，安装后手机和电脑通过USB连接，打开Kies软件，如有手机系统/固件新版本时Kies软件会有固件升级提示，点击升级即可。
1).Kies下载链接如下：
http://www.samsung.com/cn/support/usefulsoftware/KIES/JSP
注意：下载安装时手机与电脑不要连接。
若您使用的手机或平板电脑采用的是安卓4.3及以上操作系统，请下载安装Kies3版本。
2).Kies方式升级固件注意事项:
http://skp.samsungcsportal.com/integrated/popup/FaqDetailPopup3.jsp?cdsite=cn&seq=438936
3.送到三星服务中心升级：携带购机发票、包修卡和机器到三星服务中心，由专业的售后工程师帮助您升级。
具体服务中心查询请访问：http://support-cn.samsung.com/support/ServiceLocations.asp
欢迎您向我们反馈您的建议和评价： www.diaochaquan.cn/s/3Z0LE

##### 208

android sharesdk微信分享 创建应用时所需的应用签名怎么得到

根据这个页面提供的一个工具 签名生成工具
https://open.weixin.qq.com/cgi-bin/readtemplate?t=resource/app_download_android_tmpl&lang=zh_CN
Android资源下载
开发工具包
开发第三方应用所需要的库以及文件。点击下载
范例代码
包含了一个完整的范例工程。该范例的使用可以参阅Android平台上手指南：HelloWeixin@Android。点击下载
签名生成工具用于获取安装到手机的第三方应用签名的apk包。点击下载
  
可以一个字符串,类似于:
 应用签名：049a9fde46bfc5087f3825582208b248
安装这个应用可以获取本手机已经安装的某个android软件,根据软件的包名,类似于: com.demo.AppX 来查找这个软件,以及获取这个软件的 应用签名。
还有一个工具是在
http://wiki.open.qq.com/wiki/mobile/SDK下载
Android_SDK_V2.3.1 的tools目录下有一个  获取签名.apk ,这个也可以获取,但是我测试发现,只能显示一部分的本机应用,有些应用查不到,就麻烦了..


##### 209.:app:lintVitalRelease                   
Failed converting ECJ parse tree to Lombok for file /home/yyb/work/BoShiTong/trunk/HBFC/Android/Comment/HBFC-AS2/app/src/main/java/com/jetsun/hbfc/widget/ioc/AbIocView.java
java.lang.ClassCastException: lombok.ast.Annotation cannot be cast to lombok.ast.Expression

##### 210.
 Ignoring InnerClasses attribute for an anonymous inner class

##### 211.
WebView 在Android4.4的手机上onPageFinished()回调会多调用一次(具体原因待追查)
需要尽量避免在onPageFinished()中做业务操作，否则会导致重复调用，还有可能会引起逻辑上的错误.
onPageStarted和onPageFinished 会加载两次 



##### 212.Android WebView常见问题及解决方案汇总
 http://blog.csdn.net/t12x3456/article/details/13769731

##### 213.Android check network connectivity on some tablets crash

java.lang.NullPointerException
at com.xxx.Util.getNetworkState(Util.java:246)

##### 214.What is the equivalent of Eclipse “Custom debug Keystore” in Android studio?
	http://stackoverflow.com/questions/17189076/what-is-the-equivalent-of-eclipse-custom-debug-keystore-in-android-studio



##### 215.Android Studio在调试时，修改变量的值  在“Variables”窗口中，选择需要修改的变量，然后右键，选“Set Value..."。快捷键F2



##### 216.打开百度定位导致MyApplication中的初始化重新加载一遍。如果此时有自动登录等，会导致重新登录 而目前的凭证失效

##### 217.android webview和js交互json对象  。通过字符串传递。然后通过jsonobject把字符串生成json对象从中获取数据。

##### 218. Android Studio开发jni ndk
  主要有以下三块
   1. Javah生成JNI头文件     
	 需要进入到/src/mian 这个目录下 。如果不进入这个目录等会运行javah的时候会提示：  错误: 找不到 'com.lcj.ndk_demo_2.HelloNDK' 的类文件
	 javah -d jni -classpath ..\..\build\intermediates\classes\debug com.lcj.ndk_demo_2.HelloNDK 
           jni 是生成的头文件需要存放的文件夹（一般取名jni才对）
            ..\..\build\intermediates\classes\debug 是class所在目录（Build—>Make Project生成的class文件都在这里，这是一个相对路径）   
            com.lcj.ndk_demo_2.HelloNDK 是class文件的文件名（根据之前的java文件生成的）
     参考 http://wenku.baidu.com/view/105474098e9951e79b8927a3.html
   2.根据上不生成的.h文件 写.c和makefile
   3.ndk-build【这个androidstudio1.2已经集成，可以直接编译ndk，所以多一个选择】
	易出现的问题 When running the ndk-build command I get the following error:

	Android NDK: Could not find application project directory !    
	Android NDK: Please define the NDK_PROJECT_PATH variable to point to it

	解决方案

	NDK_PROJECT_PATH is an environment variable so you don't have to include in the Android.mkfile. Is nkd-build launched in the project directory?

	For more info read the docs in docs/HOWTO.html in the NDK folder where I read

	Starting with NDK r4, you can simply place the file under $PROJECT/jni/ and launch the 'ndk-build' script from your project tree.

	If you want to use 'ndk-build' but place the file to a different location, use a GNU Make variable override as:

	ndk-build NDK_APPLICATION_MK=/path/to/your/Application.mk

##### 219.Android下使用lamemp3库将PCM录音数据压缩为MP3格式  
            文章最下面有demo 很不错 通过javah修改下，可以直接用
	   来源：    http://ikinglai.blog.51cto.com/6220785/1228730


##### 220.Android Studio 不自动弹起代码提示功能解决办法 do not auto popup code completion

升级后不自动弹起代码提醒功能了，而且变量也不标注颜色，简直是气死我了，Google了各种关键词，都没办法
后来看到有个Power Save Mode，昨天看到笔记本发热厉害就给勾上了，是不是这个原因呢？
取消之后一切正常，看来是省电模式下禁用了这些功能，通过反射来实现代码的autoComplete是会增加CPU运算量。

File-->Power Save Mode  .勾掉省电模式
参考：http://blog.csdn.net/ameryzhu/article/details/14105275

##### 221. 百度地图相关  在Genymotion上启动项目时，程序抛出异常

1. 问题描述：
	1、在Genymotion上启动项目时，程序抛出异常，报错日志为：11-10 09:18:44.577: E/com.btten.base.CrashReportHandler(1298): Caused by: java.lang.UnsatisfiedLinkError: Cannot load library: load_library[1093]: Library '/system/lib/libhoudini.so' not found

2. 问题分析：
	1、鉴于Genymotion是只支持x86架构的，所以从.so文件入手找问题，项目中导入了jpush的.so配置文件，jpush官网上的解释通常都是http://docs.jpush.cn/pages/viewpage.action?pageId=7864765，新建x86、mips 、armeabi-v7a几个目录，然后把libjpush.so也复制一份过去。尝试之后发现不起作用。

3. 解决办法：
	1、网上找了很久发现如下办法，下载一个ARM Translation Installer的压缩包，安装到Genymotion上，重启下，重新运行程序，ok，问题顺利解决。简要摘抄步骤如下：
	Download the following ZIPs:
	ARM Translation Installer v1.1 Hosted by FILETRIP(Mirrors) - If you have issues flashing ARM Trnaslation, Try re-downloading from a mirror
	Download the correct GApps for your Android version:
	If you have issues flashing GApps, Try re-downloading from a mirror
	Google Apps for Android 4.4(Mirror)(Download from CM11 Links)(4.4 GApps might be buggy)
	Google Apps for Android 4.3(Mirrors)
	Google Apps for Android 4.2
	Google Apps for Android 4.1
	Next Open your Genymotion VM and go to the Homescreen
	Now Drag&Drop the Genymotion-ARM-Translation.zip onto the Genymotion VM window.
	It should say "File transfer in progress", once it asks you to flash it click 'OK'
	Now Reboot your VM using ADB or an app like ROM Toolbox. If nescessary you can simply close the VM window, but I don't recommend it.

	详情转载地址：http://forum.xda-developers.com/showthread.php?t=2528952

##### 222. 百度地图相关。E/baidumapsdk﹕ Authentication Error errorcode: -1 uid: -1 appid -1 msg: AndroidManifest.xml的application中没有meta-data标签


##### 223. 百度地图相关  百度地图去掉缩放按钮

MapView放在ScrollView中,滚动时出现黑条
http://bbs.lbsyun.baidu.com/forum.php?mod=viewthread&tid=1093
应该GLSurfaceView放在ScrollView内部的问题.1.3.5用View直接绘制没有问题.能否在下版中提供一个底层基于View绘制的MapView

版主,我在想,当滚动用截取当前地图的bitmap.(调用getCurrentMap())然后盖在GLSurface上.但getCurrentMap()操作是异步的,用android自带的View.getDrawingCache()也未能成功获取.上述不成功后,由于需求限制可以对地图不操作,尝试了下能不能再MapView完成地图加载后getCurrentMap()把截图放在ImageView中盖在MapView上,但未能找到相应的监听方法.见贴:http://bbs.lbsyun.baidu.com/viewthread.php?tid=1104&extra=page%3D1.现在改用1.3.5在做.QQ:396920165能否交流下


scrollview内嵌mapview后的滑动问题

百度地图mapview放在scrollview中滑动黑屏

后面我试下了直接用截图功能。mapview设置隐藏，然后方法没被执行。是不是在mapview 不显示的情况下。截图功能不可用？
 开始移动前截图覆盖
静态。不可拖动但是可要能点击


建议不要在scroll中使用mapview  因为本身map是用opengl绘制的，这个东西在scroll中存在性能问题，所以导致的体验效果不佳，请考虑改变实现方式。


百度map1.3.5
http://developer.baidu.com/map/reference/index.php?title=Class:android%E6%A0%B8%E5%BF%83%E7%B1%BB/MapView



静态【不可放大缩小】的mapview。点击无效


http://www.cnblogs.com/trinea/archive/2012/11/14/2770433.html



##### 224.Android自定义DataTimePicker（日期选择器）    http://blog.csdn.net/wwj_748/article/details/38778631

##### 225.Content-Type:       application/x-www-form-urlencoded;  
可以通过mitmproty分析 

https://www.imququ.com/post/four-ways-to-post-data-in-http.html

四种常见的 POST 提交数据方式

application/x-www-form-urlencoded
multipart/form-data
text/xml
application/json
text/xml


##### 226.androidstudio 升级后无法使用git svn等代码管理工具。
vcs -->Enable Version Control Integration 选择git/subversion 即可

##### 227.androidstudio 升级后发现 编写代码自动提醒功能没了。
原因在于打开了File--->Power Saved Mode，关闭即可。

##### 228.dshow 音频采集

##### 229.kill －SIGKILL PID
强行中止(经常使用杀掉)一个进程标识号为324的进程：
　　#kill －9 324
　　(2)解除Linux系统的死锁
　 　在Linux中有时会发生这样一种情况：一个程序崩溃，并且处于死锁的状态。此时一般不用重新启动计算机，只需要中止(或者说是关闭)这个有问题的程序 即可。当kill处于X-Window界面时，主要的程序(除了崩溃的程序之外)一般都已经正常启动了。此时打开一个终端，在那里中止有问题的程序。比 如，如果Mozilla浏览器程序出现了锁死的情况，可以使用kill命令来中止所有包含有Mozolla浏览器的程序。首先用ps命令查找该程序的 PID，然后使用kill命令停止这个程序：
　　#kill －SIGKILL XXX
　　其中，XXX是包含有Mozolla浏览器的程序的进程标识号。
　　(3)使用命令回收内存
　　我们知道内存对于系统是非常重要的，回收内存可以提高系统资源。kill命令可以及时地中止一些"越轨"的程序或很长时间没有相应的程序。例如，使用top命令发现一个无用(Zombie)的进程，此时可以使用下面命令：
　　#kill －9 XXX
　　其中，XXX是无用的进程标识号。
　　然后使用下面命令：
　　#free
　　此时会发现可用内存容量增加了。
　　(4)killall命令
　　Linux下还提供了一个killall命令，可以直接使用进程的名字而不是进程标识号，例如：
　　# killall -HUP inetd
  
#####230.android导入eclipse项目后，出现如下问题

1.Error:The project is using an unsupported version of the Android Gradle plug-in (0.12.2). The recommended version is 1.2.3.

classpath 'com.android.tools.build:gradle:1.2.3'

在build.gradle 根据提示把
    dependencies {
        classpath 'com.android.tools.build:gradle:0.12.+'
    }

修改为
    dependencies {
        classpath 'com.android.tools.build:gradle:1.2.3'
    }

2.上面修改后会出现如下错误：

Error:Unable to load class 'org.codehaus.groovy.runtime.typehandling.ShortTypeHandling'.
Possible causes for this unexpected error include:You are using JDK version 'java version "1.7.0_71"'. Some versions of JDK 1.7 (e.g. 1.7.0_10) may cause class loading errors in Gradle.
Please update to a newer version (e.g. 1.7.0_67).

明明用的就是jdk1.7.0_71[比1.7.0_67还新] 却提示不对，问题起始不在jdk这而是 gradle-wrapper.properties

distributionUrl=http\://services.gradle.org/distributions/gradle-1.12-all.zip  估计用的是jdk1.7.0.10

把    distributionUrl=http\://services.gradle.org/distributions/gradle-1.12-all.zip
修改为 distributionUrl=https\://services.gradle.org/distributions/gradle-2.2.1-all.zip

ok 经过上面两步，从studio导入eclipse项目的正常使用。

#####231.android 注释模板
Settings-->Editor-->File and Code Templates-->Includes

#####232.shape中子节点的常用属性
1. ```<gradient>  渐变```

android:startColor  起始颜色
android:endColor  结束颜色
android:angle  渐变角度，0从上到下，90表示从左到右，数值为45的整数倍默认为0；
android:type  渐变的样式 liner线性渐变 radial环形渐变 sweep  

例如：
```
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    type="rectangle">
    <gradient
        android:angle="270"
        android:endColor="#9f36a0"
        android:startColor="#65216a" />
</shape>
```
2.```<corners > 圆角```
android:radius  圆角的半径 值越大角越圆

android:topRightRadius  右上圆角半径

android:bottomLeftRadius 右下圆角角半径

android:topLeftRadius 左上圆角半径

android:bottomRightRadius 左下圆角半径
如果你把4个角设成为90的话，那么改图片是一个圆！
3.```<solid >  填充```
android:color  填充的颜色

4.```<stroke > 描边```
android:width 描边的宽度
android:color 描边的颜色
android:dashWidth 表示'-'横线的宽度
android:dashGap 表示'-'横线之间的距离

参考 http://blog.csdn.net/cs_li1126/article/details/11781577

#####
#####233. GestureOverlayView

#####234.Animation lInAnim = AnimationUtils.loadAnimation(mActivity, R.anim.push_left_in);
#####235.  使用volley 错误时，无法看到详细的信息。
可以有两种方式处理

**方法1**.抓包  通过Fiddler抓包，在ubuntu系统下通过mitmproty来抓包。或者android4.4chrome浏览器--工具--检查设备来抓包。

**方法2**.
参考 [Android: How handle message error from the server using Volley?](http://stackoverflow.com/questions/21867929/android-how-handle-message-error-from-the-server-using-volley)
在gsonrequest中重写parseNetworkError 如下：
//In your extended request class 
```
@Override 
protected VolleyError parseNetworkError(VolleyError volleyError){
        if(volleyError.networkResponse != null && volleyError.networkResponse.data != null){
                VolleyError error = new VolleyError(new String(volleyError.networkResponse.data));
                volleyError = error;
            } 
 
        return volleyError;
    } 
} 
```
还要提示一点排查错误信息可以通过androidstudio的筛选 error volley。来直观的看到错误的状态码。
NetworkError
ClientError
ServerError
 AuthFailureError
 ParseError
 NoConnectionError
 TimeoutError
 
 **知其然，还要知其所以然**
 
 BasicNetwork.java 中函数 performRequest执行错误时会抛出错误。
 	throw new ServerError(networkResponse);
 
 networkResponse的类如下：
 public class NetworkResponse {
    public final int statusCode;
    public final byte[] data;
    public final Map<String, String> headers;
    public final boolean notModified;
    ......
    }
 所以重写gsongrequest中的 方法parseNetworkError。通过networkResponse的data获得更详细的错误信息信息。
 
#####236. url编码
遇到一个很奇怪的问题，同一个url在手机端请求 返回400【页面不存在】 而把这个url放在pc浏览器请求却是好的。
最后发现是url中有个空格 。在app上没有进行url.encode 导致。至于pc上请求没问题是自动做了url编码处理。
切记 请求的url有特殊字符 如空格 加号等，一定要url编码。


#####237. How to add a header to a listView which is inside SwipeRefreshLayout?
http://stackoverflow.com/questions/27048416/how-to-add-a-header-to-a-listview-which-is-inside-swiperefreshlayout
https://code.google.com/p/android/issues/detail?id=80227
上述是2014年12月份报的android自身 bug。先已经修改

android.widget.ListView{41ad4e90 VFED.VC. .F...... 0,0-720,1110 #7f090078 app:id/listview}


#####238. 定义键盘 会遇到“当按返回键界面退出，但虚拟键盘没有消失的现象”针对这个问题，可以在onpause中强制隐藏它。代码如下。
        InputMethodManager imm = (InputMethodManager) getSystemService(Context.INPUT_METHOD_SERVICE);
        imm.hideSoftInputFromWindow(et_content.getWindowToken(), 0);

#####239. 代码混淆导致问题，快速定位
在代码混淆打包时，屏蔽了用到的第三方库，以及常规的android混淆屏蔽，但生成的apk，运行还是会崩溃。事出必有因，后来分析找到原因是**使用greendao自动生成的java-gen下package中的内容没有屏蔽代码混淆，导致存储数据库时，报**a(SourceFile:) NullPointerException ****
混淆打包apk，运行崩溃 总结如下：

我们在打包时，debug版本没问题，但混淆后release版本有时会出现异常崩溃，
比如：**a(SourceFile:) NullPointerException **

针对这种情况，可以通过抓UncaughtExceptionHandler崩溃日志或者第三方比如云测工具查看崩溃的原因。在androidstudio下还有一种更好的方式。

在androidstudio中可以设置debug下也混淆，通过android log直观的、快速的定位问题所在

```
 signingConfigs {
            release {

            }

            debug{

            }
   }

    }

    buildTypes {
        release {
            // 不显示Log
            buildConfigField "boolean", "LOG_DEBUG", "false"
            minifyEnabled true
            // 移除无用的resource文件
            shrinkResources true
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
            signingConfig signingConfigs.release  //使用上述签名信息

         }
        }
        debug {
            minifyEnabled true
            // 移除无用的resource文件
            shrinkResources true
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
            signingConfig signingConfigs.debug
        }
    }
```
#####240 通过gif展示一个效果是否直观，Ubuntu平台gif动画录制工具可以使用命令行，录制的效果很好，并且录制gif大小很小。
byzanz-record --duration=30 --x=0 --y=50 --width=500  out.gif
参数说明 --duration 录制的时长  --x录制开始的x坐标   --y录制开始的y坐标 --width 宽度  out.gif 输出文件名

#####241.微信开放平台申请流程  http://bbs.mob.com/thread-95-1-4.html
命令操作如下
	
keytool -list -keystore keystore文件路径 得到对应app的秘钥  把:去掉，大写转小写即可。

#####242.编译ijkplayer时，报错 NDK r10: Fix make-standalone-toolchain.sh "<<<" bashism

这个是android官方问题 
把for ABI in $(tr ',' ' ' <<< $ABIS); do 修改为 for ABI in $(echo "$ABIS" | tr ',' ' '); do

https://code.google.com/p/android/issues/detail?id=74145
#####243.ubuntu nginx rtmp流媒体服务器的安装
Setup Nginx-RTMP on Ubuntu 14.04  
英文文档 https://www.vultr.com/docs/setup-nginx-rtmp-on-ubuntu-14-04
中文文档 http://www.cnblogs.com/cocoajin/p/4353767.html

nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
80端口被占用解决方法：

sudo fuser -k 80/tcp
sudo service nginx start

#####242.ubuntu查看占用某端口的程序   查看端口使用情况，使用netstat命令。
 查看已经连接的服务端口（ESTABLISHED netstat -a 查看所有的服务端口（LISTEN，ESTABLISHED） netstat -ap  
 查看8080端口，则可以结合grep命令：netstat -ap | grep 8080   
 
	1. 显示占用某个端口的程序
	lsof -i:80
	lsof -i:5000
	2. 显示某个程序是否在运行，查看某个运行的程序
	ps -aux | grep "paster"
	ps -aux | grep apache2

#####243.架构师编写详细设计的重要性。
详细设计，这是考验技术专家设计思维的重要关卡，详细设计说明书应当把具体的模块以最’干净’的方式(黑箱结构）提供给编码者，使得系统整体模块化达到最大；一份好的详细设计说明书，可以使编码的复杂性减低到最低，实际上，严格的讲详细设计说明书应当把每个函数的每个参数的定义都精精细细的提供出来，从需求分析到概要设计到完成详细设计说明书，一个软件项目就应当说完成了一半了。换言之，一个大型软 件系统在完成了一半的时候，其实还没有开始一行代码工作。
#####244.http请求的url含有中字符时，需要Uri编码。Uri.encoder()
#####245.使用androidstudio时，不知道什么原因svn不见了  
[Android Studio missing Subversion plugin](http://stackoverflow.com/questions/23680809/android-studio-missing-subversion-plugin)

Please make sure that the "SubversionIntegration" plugin is enabled in Preferences > Plugins

#####246.Error:Execution failed for task ':app:dexDebug'.> com.android.ide.common.process.ProcessException: org.gradle.process.internal.ExecException: Process 'command '/home/xxx/tools/android/jdk1.7.0_71/bin/java'' finished with non-zero exit value 2

**检查下是否多次引用同一个jar包**
以下情况
1. module下jar包版本不同

2. 同一个module 在libs中包含乐.jar，而在src下又把相应的source页加入了

3. gradle中是否重复编译，

比如 
已经加了compile fileTree(include: ['*.jar'], dir: 'libs')
然而在下面又加一句compile files('libs/xxx.jar')

参考 [Error:Execution failed for task ':app:dexDebug'. com.android.ide.common.process.ProcessException](http://stackoverflow.com/questions/28917696/errorexecution-failed-for-task-appdexdebug-com-android-ide-common-process)

#####246.android handler的警告Handler Class Should be Static or Leaks Occur
在使用Handler更新UI的时候public class SampleActivity extends Activity {
                                                              
  private final Handler mLeakyHandler = new Handler() {
    @Override
    public void handleMessage(Message msg) {
      // TODO
    }
  }
}会包上述warning 会导致内存泄露 
原因在于匿名内部类handler持有activity的引用，当activity finish后 handler还没有处理完，导致activity的view和resource资源不能得到释放，导致内存泄露
针对这个问题google官方给出了正确的做法
通过静态内部类 包含activity的弱引用来处理。
public class SampleActivity extends Activity {
         
  /**
   * Instances of static inner classes do not hold an implicit
   * reference to their outer class.
   */
  private static class MyHandler extends Handler {
    private final WeakReference<SampleActivity> mActivity;
         
    public MyHandler(SampleActivity activity) {
      mActivity = new WeakReference<SampleActivity>(activity);
    }
         
    @Override
    public void handleMessage(Message msg) {
      SampleActivity activity = mActivity.get();
      if (activity != null) {
        // ...
      }
    }
  }
         
  private final MyHandler mHandler = new MyHandler(this);
         
  /**
   * Instances of anonymous classes do not hold an implicit
   * reference to their outer class when they are "static".
   */
  private static final Runnable sRunnable = new Runnable() {
      @Override
      public void run() { }
  };
         
  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
         
    // Post a message and delay its execution for 10 minutes.
    mHandler.postDelayed(sRunnable, 60 * 10 * 1000);
             
    // Go back to the previous Activity.
    finish();
  }
}

参考[android handler的警告Handler Class Should be Static or Leaks Occur](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2014/1106/1922.html)

#####247.androidstudio不同tab切换  ctrl+tab

#####248.androidstudio 如何自动import用到的类或接口？
	For Windows/Linux, you can go to File -> Settings -> Editor -> General -> Auto Import -> Java and make the following changes:
	
	change Insert imports on paste value to All
	
	markAdd unambigious imports on the fly option as checked
	On a Mac, do the same thing in Android Studio -> Preferences

参考[What is the shortcut to Auto import all in Android Studio?](http://stackoverflow.com/questions/16615038/what-is-the-shortcut-to-auto-import-all-in-android-studio/16616085#16616085)

#####249.Android NDK: Could not find application project directory !  Android NDK: Please define the NDK_PROJECT_PATH variable to point to it.    
    /home/cenuser/android/android-ndk-r7b/build/core/build-local.mk:130: *** Android NDK: Aborting    .  Stop.
    
    cd到jni目录。或者 ndk-build -C your_project_path
#####250 .Why do I want to avoid non-default constructors in fragments?  fragment设置参数正确的做法


	Make a bundle object and insert your data (in this example your Category object). Be careful, you can't pass this object directly into the bundle, unless it's serializable. I think it's better to build your object in the fragment, and put only an id or something else into bundle. This is the code to create and attach a bundle:
	
	Bundle args = new Bundle();
	args.putLong("key", value);
	yourFragment.setArguments(args);
	After that, in your fragment access data:
	
	Type value = getArguments().getType("key");
	That's all.
	
#####251. ubuntu下删除.svn的方法

	find -type d -name '.svn' -exec rm -rfv {} \;

	参考 http://blog.csdn.net/zhaoyu7777777/article/details/9445717

#####252. Fatal : Could not read from remote repository.
git配置使用，已经把公钥发给发给服务端，在终端命令行也是可以正常的pull push，但是在androidstudio push或者pull的时候确出现上述错误
解决方式 
    setting --> Version Control -->Git ,In the SSH executable dropdown, choose Native

#####253. ubuntu获取证书指纹的命令
keytool -list -keystore xxx.keystore
#####254. mac 命令行安装软件
通过brew安装，相当于ubuntu中得apt-get
首先安装brew
curl -LsSf http://github.com/mxcl/homebrew/tarball/master | sudo tar xvz -C/usr/local --strip 1  
然后就可以使用brew安装软件了
比如 使用brew安装软件  brew install wget  
#####255.代码混淆时 报如下错误 Error:Execution failed for task ':app:proguarxxxRelease'.
> java.io.IOException: Can't read [/libs/xxx.jar] (No such file or directory)
http://stackoverflow.com/questions/26028171/android-studio-proguard-java-io-ioexception-bin-classes-no-such-file-or-d

解答   **proguard-android.txt文件中不用在指定 -injars, -outjars, or -libraryjars  or libs.**

The Android Gradle plugin already specifies all input and output for you, so you must not specify -injars, -outjars, or -libraryjars.

Moreover, the file proguard-android.txt in the Android SDK specifies all generic Android settings for you, so you shouldn't specify them again.

Essentially, your file proguard-rules.txt can be empty, except for any application-specific settings to make sure any reflection continues to work

#####256.Android中如何设置RadioButton在文字的右边，图标在左边
解决方法  ：
第一步：
android:button="@null"这条语句将原来系统的RadioButton图标给隐藏起来。
第二步：
 android:drawableRight="@android:drawable/btn_radio"这条语句
参考 http://blog.csdn.net/sunnyfans/article/details/7901592

#####257.java报“非法字符: \65279 ”错误的解决方法

众所周知，在跨程序的工程中，统一编码是至关重要的，而目前最普遍的则是统一采用“utf8”编码方案。 
但是在采用utf8方案的时候，请注意编辑器的自作聪明。 
比如editplus。 
原因就在于某些编辑器会往utf8文件中添加utf8标记（editplus称其为签名），它会在文件开始的地方插入三个不可见的字符（0xEF 0xBB 0xBF，即BOM），它的表示的是 Unicode 标记（BOM）。 
参考 http://hyl198611.iteye.com/blog/1336981
#####258.手机root后 还会出现下述情况Android: adb: copy file to /system (Permission denied)
解决方式，需要remount /system
mount -o remount,rw /system
#####259.androidstudio 手动添加assets文件 路径在哪
	XXX\src\main\assets  
#####260.android双击back退出
```java
public class MainActivity extends Activity {


    private Toast toast;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        toast = Toast.makeText(getApplicationContext(), "确定退出？", 0);

    }
    public void onBackPressed() {
        quitToast();
    }

    private void quitToast() {
        if(null == toast.getView().getParent()){
            toast.show();
        }else{
            System.exit(0);
        }
    }
}
```

或者
```java
private Toast toast;
 protected void onCreate(Bundle savedInstanceState) {
 	...
         toast = Toast.makeText(this, "再按一次退出应用", Toast.LENGTH_SHORT);
        toast.setGravity(Gravity.BOTTOM, 0, ConversionUtil.dip2px(this, 150));
 }
@Override 
public void onBackPressed() { 
    if (doubleBackToExitPressedOnce) { 
        if(toast!=null){
            toast.cancel();
        }
        super.onBackPressed(); 
        return; 
    } 
 
    this.doubleBackToExitPressedOnce = true;
    toast.show();
 
    new Handler().postDelayed(new Runnable() {
 
        @Override 
        public void run() { 
            doubleBackToExitPressedOnce=false;                        
        } 
    }, 2000); 
}  
```
参考 [Android关于双击退出应用的问题](http://segmentfault.com/q/1010000002921663)
