---
layout: post
title: "《第一行代码——Android》《Android编程权威指南》笔记"
date: 2015-06-04 18:00:25 +0800
comments: true
categories:
- Android
- note
- develop
---
本文是Yifen同学在接触Android开发时候随便记录的笔记。
<!-- more -->
 《Android编程权威指南》就是那本Big Nerd Ranch出的书。这个小公司一直在做IT职业培训，顺带着出教材。跟《第一行代码》比较的话，我觉得第一行代码只是手把手地教你怎么敲代码，却不知其然。BNR的书在使用每一个函数的时候都会将其使用方法列出来，在我看来是非常有必要的。
 
 另外完全可以忽视在前言中所说的，希望阅读着能有 Java 经验云云。只需要有一本手头书可以随时查阅即可。在我看来，面对对象的函数式编程方法和 C++ 大同小异。可能到后头会需要 Thinking in Java，但也应该是后面的事了。
 
 我个人觉得 BNR 的书比第一行代码更适合入门。而通读完BNR的书后，下一步就是大量阅读开源项目的代码，以及通过接触实际项目来弥补实战不足。另外因为BNR第一版的书仍然是停留在用 Eclipse 的时期，所以仍需要通过阅读比较新的项目来获得up to date的感觉。
 
 除了《权威指南》这一本小书之外，Yifen 同学在入门 Android 开发时还使用了Udacity 的`Developing Android App`系列课程。笔记也一并记录。
 
 以上。
 
## Actionbar 类的版本差异

旧版本的 Android 里，Menu 需要点击实体或者虚拟的菜单键唤出。但是到了现在的Android 版本已经取消了 Menu 键，不论是实体键还是虚拟键都去掉了Menu的功能，转而变成了多窗口按钮，而把Menu整合到了Actionbar中。造成的影响包括了在创建空白Activity 时候会变成 `extend ActionBarActivity`，而不是书中的`extend Activity`。无伤大雅。

## 实例变量的声明

直接举例，在 ManiActivity 中声明一个 Button 的时候：

{% highlight Java linenos%}
private Button mTrueButton;
{% endhighlight %}

命名时前面加一个小写的 m 是 Android 命名习惯。Thanks to Android Studio的自动导包功能，已经不再需要像Eclipse时代再额外进行导包。

## 制作Nine patch图片

Nine patch 图片用于 App 中需要用到对话窗口时候的悬浮气泡中。为了避免气泡图被过度拉伸而通过划分边界的方法部分拉伸。

书中使用的编辑器不是 Android studio，故而很多的操作都是使用 Eclipse。在制作Nine patch 图片的时候书中的方法是：

>在Android sdk目录下有一个tools文件夹,在这个文件夹中找到draw9patch.bat文件, 我们就是使用它来制作 Nine-Patch 图片的。

但其实在Android Studio中已经有了更直接的方法。参照这个[链接](http://stackoverflow.com/questions/16602582/convert-png-images-to-9-patch-in-android-studio)，直接对drawable中的图片进行右键，选择`Create 9-patch file`就可以进行编辑。

## 关于签名方法，release key和debug key

8 月 31 日更新

上周在 Google Play market 上发布了自己的第一个 app，也清楚了应该怎么打包 apk 文件。个人感觉如果不是最终版本确定的话，不要轻易生成 release apk。之前的都用 debug 供于内测即可。可以发布在 Fir 上。

## 设置setter和getter

Android Studio 中是自带有 setter 和 getter 的 generator 的，快捷键是 `Cmd+n`。唤出后选择`Getter and Setter`就可以。

![setter and getter](http://7vijxa.com1.z0.glb.clouddn.com/setterandgetter.png)

不过根据这个[链接](https://www.jetbrains.com/idea/help/code-style-java.html#jcode_generation)，还需要设定setter和getter的前缀。在`Editor>Code Style>Java`里。

![prefix](http://7vijxa.com1.z0.glb.clouddn.com/prefix.png)
这样生成的setter和getter就不会有m和s。

## 启动另一个Activity
原来启动另一个Activity是依靠系统的ActivityManager来进行的。利用`startActivity(intent)`这个函数，传入activity的intent id。在启用startActivity的时候，会先检查是否在AndroidManifest中有注册过这个Activity。

## 启动另一个Fragment
这一部分BNR的书有在第十章的地方讲解到，但是第一次看很难看懂。

## 使用ScrollView instead of ListView
这个内容是在看Udacity的课程developing android app的时候，从拓展材料上看到的。ListView会使用自己的列表呈现方式，Udacity推荐的是使用ScrollView，放弃ListView。在ScrollView里面放进LinearLayout。ListView会根据需要展示的列表项进行动态加载，而不是一股脑儿地全部加载，从而节省设备性能和储存空间。其实也很有道理，屏幕看不到的地方，就算加载出来了也完全没有用处。另外ListView是2010年的I/O大会上推出的。

## 使用Uri.Builder方法
在Developing Android App里面使用的一种构造Ulr的方法，用来传递参数，避免Url的直接引用，增加可拓展性。具体的文档在[这里](http://developer.android.com/reference/android/net/Uri.Builder.html) 。