---

layout: page
title: "MinicatX--蘑菇饭X"
permalink: /project/android/minicatx/
hide: true

---

## 蘑菇饭X

**[蘑菇饭X](https://github.com/Anthonyeef/minicatx)** 是饭否客户端 **[蘑菇饭](https://github.com/mcxiaoke/minicat)** 的改进版本。因原项目已经不再维护，所以对其进行修改，希望能够有更好的刷饭体验。

### 为什么不自己写一个？
饭否依然使用 OAuth 1.0a 协议。在搜索了网上能够找到的 OAuth 解决方案都蛮繁琐的，自己也没有多少时间。故转而直接在现有项目上面进行修改。

### 当前进度

#### 2015.11.20 项目启动。
- 修改 LoginLayout。更新了原项目中全部第三方 Library 至最新版本。

#### 2015.11.21
  - 解决新第三方 Library 中各种函数的冲突，更新了已经 deprecated 的方法；
  - 修改了 ActionBar 样式，增加了 FloatingActionButton 支持；

#### 2015.11.22
  - 将饭否 Timeline 列表全部修改成卡片式。修改了卡片布局，背景，divider；

#### 2015.11.28

  - 在项目中去掉了就的 Support v4 library，并加入了最新的 design library。解决了新 design library 与旧代码中的冲突，并将原本的 AbstractActivity 改成 extend 自  AppCompatActivity。

  - 将旧代码中 TabIndicator 部分砍掉，将旧的 ActionBar 方法用新的 Toolbar 替换；
  - Layout 中增加 CoordinatorLayout，同时将原本用第三方库实现的 FloatingActionButton 用 design 库中的原生 FAB 代替。
  - 修改了原项目中的 theme，特别是 theme(v21) 部分。继承自 Theme.Compat，并修改了里头的 attr 名。
  - **发现的问题：**
      - 因新的 CoordinatorLayout 中， Toolbar 和 Tablayout 在列表划动过程中的响应行为只有在列表是 RecyclerView 时才会被触发。原项目中使用了 mcxiaoke 自己定义的一个 listview 类（ EndlessListView)，如果强制修改成 RecyclerView 会非常麻烦（需要修改许多的监听器和相应时间，同时也要实现 RecyclerView 的 ViewHolder 等。
        - 同样的问题也存在在 FAB 上。FAB 的 fade in 和 fade out 方法依赖于  CoordinatorLayout 中的 behavior，该 behavior RecyclerView 或者是一个嵌套在其中的 ScrollView。
        为了能实现 tab 和 toolbar 在列表滑动时候的相应行为，决定下星期动手自己写 Toolbar 和 tab 布局。

#### 2015.11.29

  - 用 NavigationView 替代了原项目中用 Fragment 自定义的 Drawer。
