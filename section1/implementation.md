# Implementation


## [Material Design 實作 | Android Developer](https://developer.android.com/design/material/index.html)

- [Getting Started](https://developer.android.com/training/material/get-started.html)
  - Key
    - Review the [material design specification](http://www.google.com/design/spec/material-design/introduction.html).
    - Apply the material [**theme**](https://developer.android.com/training/material/theme.html) to your app.
      - System widgets that let you set their color palette
      - Touch feedback animations for the system widgets
      - Activity transition animations

    - Create your **layouts** following material design guidelines.
      - Baseline grids
      - Keylines
      - Spacing
      - Touch target size
      - Layout structure

    - Specify the **elevation** of your views to cast shadows.
    - Use system **widgets** for lists and cards.
    - Customize the **animations** in your app.

  - [Maintaining Compatibility](https://developer.android.com/training/material/compatibility.html)

- [Materialize your App - Antonio Leiva](http://antonioleiva.com/materialize-app/)

---

## Toolbar

- [Material Design Everywhere: Using AppCompat 21](http://antonioleiva.com/material-design-everywhere/)
  - set ActionBar compatibility
  - Specify the Material Theme
    - extends Theme.AppCompat
      - `values/themes.xml`: 向下相容，一般設置
      - `values-v21/themes.xml`: 再overriding, 使用Lollipop 的轉場動畫

    - 在 AndroidManifest.xml 設定 theme

  - Setting the Toolbar
    - 變到layout 裡了: The most important difference is that this toolbar is now part of our layout, so that we can play with it in any way we consider: animations, drawer overlay, etc.
    - 在Activity 裡指明這個toolbar 就是ActionBar

- [ANDROID – TOOLBAR STEP BY STEP](http://blog.mosil.biz/2014/10/android-toolbar/)




## 實作NavigationDrawer + Toolbar

- [ToolBar & Navigation Drawer, DrawerLayout](http://www.google.com/design/spec/layout/structure.html%23structure-toolbars)
  - [ANDROID – TOOLBAR 上的 NAVIGATION DRAWER](http://blog.mosil.biz/2014/10/navigation-drawer-on-toolbar/)
  - [****[Material Design] 使用 Toolbar + DrawerLayout 快速實現高大上菜單側滑**](http://chenqichao.me/2014/12/08/108-Android-Toolbar-DrawerLayout-01/)
  - [Pattern: Naviagtion](http://www.google.com/design/spec/patterns/navigation-drawer.html)

- [Fragment + Navigation Drawer](https://github.com/codepath/android_guides/wiki/Fragment-Navigation-Drawer)
  - 如果想要Drawer 是整個左邊，設定 `android:fitsSystemWindows`
  - Making Status Bar Translucent: `<item name="android:windowTranslucentStatus">true</item>`
  - Fragment Drawer
    - Model, Adapter
    - `drawer_nav_item.xml`

- 重點
  - Build.gradle: Appcombat-v7
  - Xml
    - Include `Toolbar`
    - Include `DrawerLayout { <Main> <Drawer> }`
    - Theme
      - `<style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar" >`
      - `<style name="DrawerArrowStyle" parent="Widget.AppCompat.DrawerArrowToggle">`, `spinBars`

  - src/main
    - `setSupportActionBar(toolbar)`
    - `ActionBarDrawerToggle`
    - `drawerLayout.setDrawerListener(drawerToggle)`


## SwipeRefreshLayout

- [[Android] 使用](http://blog.tonycube.com/2014/09/android-swiperefreshlayout-pull-to.html) [SwipeRefreshLayout 製作下拉更新 (Pull to Refresh)](http://blog.tonycube.com/2014/09/android-swiperefreshlayout-pull-to.html)
  - `OnRefreshListener -> onRefresh() { swipe_refresh_layout.setRefreshing(true); }`
  - `if (firstVisibleItem == 0) { laySwipe.setEnabled(true); } else { … }`
  - 更新時顯示的動態橫條顏色: `setColorSchemeResources()`

- [Implementing Swipe to Refresh, an Android Material Design UI Pattern](http://www.bignerdranch.com/blog/implementing-swipe-to-refresh/)
  - `compile 'com.android.support:support-v4:21.0.+'`

- [【SwipeRefreshLayout】Google官方下拉刷新组件](http://blog.csdn.net/jabony/article/details/22890793)
