---

layout: page
title: "MinicatX--蘑菇饭X"
permalink: /project/android/minicatx/
hide: true

---

## 蘑菇饭X

**[蘑菇饭X](https://github.com/Anthonyeef/minicatx)** 是饭否客户端 **[蘑菇饭](https://github.com/mcxiaoke/minicat)** 的改进版本。因原项目已经不再维护，所以对其稍加修改，希望能够有更好的刷饭体验。

### 为什么不自己写一个？
饭否依然使用 OAuth 1.0a 协议。在搜索了网上能够找到的 OAuth 解决方案都蛮繁琐的，自己也没有多少时间。故转而直接在现有项目上面进行修改。

### 当前进度

- 2015.11.20 项目启动。
  - 修改 LoginLayout。更新了原项目中全部第三方 Library 至最新版本。
- 2015.11.21
  - 解决新第三方 Library 中各种函数的冲突，更新了已经 deprecated 的方法；
  - 修改了 ActionBar 样式，增加了 FloatingActionButton 支持；
- 2015.11.22
    - 将饭否 Timeline 列表全部修改成卡片式。修改了卡片布局，背景，divider；
