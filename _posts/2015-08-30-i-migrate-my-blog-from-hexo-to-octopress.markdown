---
layout: post
title: "I migrate my blog from Hexo to Octopress，and finally back to Jekyll"
date: 2015-08-30 19:20:43 +0800
comments: true
categories: 
- Life
- 2015
- blog
- develop
---

Here is a test for the new blog framework. I decided to change my blog today, in order to make it looks better. All I expected was a clean, simple, and with high readbility blog framework. Of course the easy use is also considered.
<!-- more -->

Hexo is great. Hexo is popular now and the my last theme looks clean and great. However I still felt there is something lost. I think Octopress, a more traditional and old school static blog framework, should have more theme to choose from, and may fit my need. But after I migrating to Octopress I found it difficult to keep the project page style coincedent to the blog page style, so I changed again to Jekyll.

So here is it.

然后现在测试一下中文显示效果。我挺满意这个 one colum 的博客样式，看起来清爽，可以专注在内容上。

测试代码块：

{% highlight Java linenos%}
public static final URL = "https://anthonyeef.github.io/";
int MAX_METHOD = 65536;
{% endhighlight %}

测试一下引用：

>"Talk is cheap, show me the code."

看来就算是老牌的博客框架 Octopress，对于挑剔的人来说，也是很难一下子找到称心的 theme。我前后看了不少的 theme，但有的太花哨，有的字体太乱，容易让人失去注意力。有一个什么都好，但是明显制作者是设计师写的代码不多，所以一到代码块显示的部分就整个崩坏了。是真的崩坏，我并没有夸张……最后我选定了现在你所看到的这个 theme。但在测试的时候我发现，在 safari 中 header 和 subtitle 的字体，到了 Chrome 中就变成了另外一个。这样奇妙的变化让我觉得很好玩。打开 sass 文件，想看一下到底是为什么，发现应该是那个 font-family 在不同浏览器下会自己选择 prefer 的字体。我本来想或许这样也好。用 Mac 的 safari 看到的我的博客内容，是中规中矩的 Helvetica Neua，到了 Chrome 上打开，就会变成好看一些的衬线字体 Cardo。不同来源的人看到的内容是不一样的，这样的概念看起来很棒。

（后来更换成 Jekyll 后选择了现在的这个主题，发现稍微调整以及添加少量代码后，看起来更加舒服了。也就不多赘言了。）

但强迫症为了保证在不同设备上一致的阅读体验，加上我自己就是两个浏览器混和使用的人，就手一抖都强制成统一的字体了 XD。

静态文件都放在了七牛上。如果觉得打开速度较慢，应该是因为有些地方使用了 Google font，国内的访问速度会因为不可言说的原因而慢下来……

最后附上几张图，分别是在 Chrome Safari 以及在 Chrome 的调试工具下模拟移动设备看到的新博客效果：

![Chrome 的效果](http://7vijxa.com1.z0.glb.clouddn.com/Screen%20Shot%202015-08-31%20at%2009.25.13.png)

![Safari 的效果](http://7vijxa.com1.z0.glb.clouddn.com/Screen%20Shot%202015-08-31%20at%2009.25.24.png)

可以看到现在看到的是没有太大区别的，最多是字体之间的间距，以及字型加粗的程度有些许差别。

![Chrome 上模拟 Nexus 5](http://7vijxa.com1.z0.glb.clouddn.com/Screen%20Shot%202015-08-31%20at%2009.24.29.png)

![Chrome 上模拟 Nexus 6](http://7vijxa.com1.z0.glb.clouddn.com/Screen%20Shot%202015-08-31%20at%2009.24.06.png)

##比较 Jekyll, Octopress 和 Hexo

就我所了解的而言，三种博客框架中，最早出现的是 Jekyll。我一开始尝试在 Github page 上搭建博客时，记得读到的文档就是推荐使用 Jekyll 作为博客框架。但对那时的我来说，对 Git 工作流并不像现在这么熟练，Github page 生成网页的过程也了解得不多。使用 Jekyll 搭建博客在那时显得无比晦涩艰辛。后来无意中发现了 Hexo，发觉 Hexo 的命令是如此地简单直白。也许跟开发者是台湾人有关，对中文的支持也出乎意料的好。那段时间一定是 Hexo 在华人技术圈迅速流行的时候，因为后来我发现越来越多我看到的，刚刚进入技术圈的年轻人，博客所用的框架绝大多数都是 Hexo，主题往往是「Next」等简约而又考虑到了响应式的主题。

估计这也是我开始渐渐厌倦 Hexo 的原因吧。感觉没那么特别了。不再有刚见到的时候「眼前一亮」的感觉。

应该说，Hexo 的开发者开发 Hexo 是为了超越 Octopress。之前看到那个台湾开发者的博文，解释了 Hexo 命名的起因。Octo 是八进制的前缀，Hexo 是十六进制的前缀（此处待考查确认）。从命名上就可以看到，开发者是将 Hexo 视为 Octopress 的进化版本，在开发和推广过程中，也尽量地希望能够避免 Octopress 的覆辙。Hexo 的作者在项目主页就建了一个 gallery 推荐一些优秀的 theme，这一点比起 Octopress 无疑考虑得更好。

搭建一个博客并不难，所需要的只是看懂文档，以及一些必要的 Git 知识。维护一个博客才更需要花时间和精力。

如果你在你的设备上看到我的博客显示效果跟上面的截图有较大差异，feel free to contact me :)
