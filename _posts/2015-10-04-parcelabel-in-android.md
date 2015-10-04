---
layout: post
title: "Parcelable in Android"
date: 2015-10-03 11:58:25 +0800
comments: true
categories:
- Android
- note
- develop

---

最近在嘗試讀透蘑菇飯的源代碼，同時嘗試在蘑菇飯的項目基礎上進行飯否客戶端的二次開發。蘑菇飯的代碼在我看來是非常乾淨而且優美的，項目結構非常分明，就連我這種剛接觸開發的新手也感覺能從中獲益。在項目中可以隨處看到 LogUtil 函數，封裝良好的功能函數以及對 abstract 類的復用。

本篇博文嘗試在閱讀蘑菇飯代碼過程中記錄一些零散筆記，包括對一些 Android 開發時會遇到的工具以及具體使用方法，更有自己嘗試二次開發時使用的代碼和工具。這篇即是記錄一下 Android 裡頭對 Parcel 的使用。

Parcel 的中文可以譯成「打包」「包裹」，當然在 Android 開發裡頭不能直接如此生硬翻譯。在不同的 Activity 裡進行數據傳遞時，首先會想到的便是用 Bundle 中的 args，再利用 Intent 進行傳遞。但這種方法不適合於一個 Object 中含有多個變量的情況。設想一下，一條 Twitter status 中，不僅包含用戶信息（ screenName, userId, etc），還會包含 status content, create time, source 等。在 HomeTimeline Activity 中點擊單獨的 Item 跳轉到詳情頁時，兩個 Activity 之間的信息傳遞就必須要使用 Parcel 先對 Object 進行「打包」的操作了。

例如新項目中的 Parging 類：

{% highlight Java linenos %}
public class Paging implements Parcelable {

    public int page;
    public int count;
    public String sinceId;
    public String maxId;
    public boolean trim;
}
{% endhighlight %}

此處先對 Paging 類中的物件進行聲明。如果要對 Paging 類進行 Parcel 處理，需要在 constructor 中對 Paging 進行 implements Parcelable 處理。同時應該在接下來的編碼中對 describeContent, writeToParcel, 進行重新定義（ 即是 Override ），並對 createFromParcel 的函數內容進行聲明。這些都是在 Google 的 [文檔](http://developer.android.com/reference/android/os/Parcel.html) 中有明確寫明的。

而上面提到的這些函數的內容都比較固定且統一，敲進去編輯器即可。有沒有方便一些的方法呢？畢竟這些函數都是「固定且統一的」。

有。我在 Github 上發現了這個 repo: [sockeqwe/ParcelablePlease](https://github.com/sockeqwe/ParcelablePlease)

在 Gradle 裡添加相應依賴後，並安裝相關的 Android Studio 插件，就可以在編輯器裡用 command + n 快捷鍵快速喚出 ParcelablePlease 的選項，點擊後便可由編輯器自己生成上面提到的函數。在此之前，需要在 Paging 的上面進行 Parcelable 的 annotation：

{% highlight Java linenos %}
@ParcelablePlease
public class Paging implements Parcelable
{% endhighlight %}

就基本完成了 Paging 類的 Parcel 化函數聲明。插件會自行生成一個 PagingParcelablePlease 的對象，此時 Android Studio 可能會出現 can't resolve symbole 的報錯提示。刷新下 Gradle 即可。之後再自行補充剩餘部分，就可以完成 Parcel 的過程。

