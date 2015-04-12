# RecyclerView & CardView

RecyclerView 可以想成是進階版的 ListView，CardView 的話則是長的像是一塊卡片，通常有大圖 + 文字的一種 view。

一般的用法是，使用 RecyclerView 來包住一個一個的 CardView，就像我們以前會用 ListView 包住一行行的 row 一樣。

## Ref

- [RecyclerView in Android: The basics](http://antonioleiva.com/recyclerview/)
- [A Guide to Android RecyclerView and CardView](http://www.binpress.com/tutorial/android-l-recyclerview-and-cardview-tutorial/156)
- [Creating Lists and Cards | Android Developer](https://developer.android.com/training/material/lists-cards.html)


## Concept


### RecyclerView.Adapter

重新 inflate view 對於 Android 來說是很耗資源的，以前 ListView 並沒有強制要求 convertView 這種 recycle 的概念。現在則有正式的 API 開出來讓大家 @Override 了。其中，當我們在 `extends RecyclerView.Adapter` 時，就會多出以下

- `onCreateViewHolder`: Newly inflate view
- `onBindViewHolder`: Re-used convertView

Add / Remove item: notifyItemInserted(position), 跟 notifyDataSetChanged 不太一樣。


### LayoutManager

一些設定，像是 Vertical 或是 Horizontal。直接使用 LinearLayoutManager 即可。

### ItemAnimator

adding and removing items 的一些動畫，據說不好寫，原生的就挺好用。
