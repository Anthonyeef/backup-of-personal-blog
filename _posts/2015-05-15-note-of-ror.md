---
layout: post
title: "Ruby on Rails学习笔记"
date: 2015-05-15 12:39:54 +0800
comments: true
categories:
- develop
- 2015
- Ruby On Rails
---
记录一些学习Ruby on Rails时候的笔记。
<!-- more -->

##关于淘宝源
因为国内的网络原因，所以会导致在rails new project的时候出现长时间的卡顿以及失败的结果。具体terminal会给出来的反馈是：

{% highlight ruby linenos %}
Gem::RemoteFetcher::FetchError: Errno::ECONNRESET: Connection reset by peer - SSL_connect (https://rubygems.org/gems/rake-10.4.2.gem)
An error occurred while installing rake (10.4.2), and Bundler cannot continue.
Make sure that `gem install rake -v '10.4.2'` succeeds before bundling.
run bundle exec spring binstub --all
bundler: command not found: spring
Install missing gem executables with `bundle install`
{% endhighlight %}

从上面可以看到是被墙了。没有办法安装rake编译元件。之前以为可以用 Shadowsocks 全局代理避免这种情况发生，后来知道 gem 这样的 cli 默认不会走系统的 Shadowsocks。
所以更换了[淘宝的ruby源](https://ruby.taobao.org/)，并且在新建项目的时候带上-B指令：

{% highlight ruby linenos %}
rails new blog -B
{% endhighlight %}

这样避免了自动的bundle install。在新建完成项目后，进Gemfile文件修改第一行的source为https://ruby.taobao.org/。
经过漫长等待后就可以了。
国内的网络环境，有时真是烦人。

（To be continue）