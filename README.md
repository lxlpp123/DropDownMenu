## 简介
扩展的思路 可以看我的[简书](http://www.jianshu.com/p/719267a0df32)

## 下载
[demo.apk](app/build/outputs/apk/app-debug.apk)

## 特色
* 支持多级菜单
* 你可以完全自定义你的菜单样式，我这里只是封装了一些实用的方法，Tab的切换效果，菜单显示隐藏效果等
* 非用popupWindow实现，无卡顿
 
## 截图
<div style="display:inline;"><img src="dropdown_demo.gif" width="332"></div>

## 扩展

箭头居中而不是居最右<br>
<img src="http://upload-images.jianshu.io/upload_images/1682632-a7d108a623dabb17.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">

icon方向属性<br>
<img src="http://upload-images.jianshu.io/upload_images/1682632-67fed77c933c62c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">
<img src="http://upload-images.jianshu.io/upload_images/1682632-a9830a6500806c6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">

分隔线高度属性<br>
<img src="http://upload-images.jianshu.io/upload_images/1682632-14683c5a45292208.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">
<img src="http://upload-images.jianshu.io/upload_images/1682632-74b76c2474762382.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">

为popupWindows集合的view增加了对LayoutParams的支持<br>
<img src="http://upload-images.jianshu.io/upload_images/1682632-e65f5c4edefc1b1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="700">
<img src="http://upload-images.jianshu.io/upload_images/1682632-86ef98adaf6c8d44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">

支持手动添加非下拉tabView<br>
<img src="http://upload-images.jianshu.io/upload_images/1682632-54018e2db4c6bc13.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="350">

## 使用
注意：`此布局需要作为根布局才可能覆盖内容区域`

* 样式扩展
添加名为tab_item.xml到你的布局文件，在要显示内容的TextView上设置id为R.id.tv_tab。tab_item.xml中 任意布局即可。<br>
tab_item.xml
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="0dp"
    android:layout_height="wrap_content"
    android:layout_weight="1"
    android:gravity="center">
    <TextView
        android:id="@+id/tv_tab"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:drawablePadding="7dp"
        android:gravity="center"
        android:paddingBottom="12dp"
        android:paddingLeft="5dp"
        android:paddingRight="5dp"
        android:paddingTop="12dp"
        android:textColor="#26a8e0" />
</LinearLayout>
```
* 手动添加非下拉tabView
tab_text.xml设置样式/也可以代码生成，加载控件添加到DropDownMenu中<br>
tab_text
```xml
<TextView
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:drawablePadding="7dp"
    android:gravity="center"
    android:paddingBottom="12dp"
    android:paddingLeft="5dp"
    android:paddingRight="5dp"
    android:paddingTop="12dp"
    android:textColor="#26a8e0"
    xmlns:android="http://schemas.android.com/apk/res/android" />
```
调用添加,在setDropDownMenu之后添加
```java
...
//init dropdownview
 mDropDownMenu.setDropDownMenu(Arrays.asList(headers), popupViews, contentView);
 //测试tabView扩展功能
 TextView textView= (TextView) getLayoutInflater().inflate(R.layout.tab_text,null);
 textView.setLayoutParams(new LinearLayout.LayoutParams(0, ViewGroup.LayoutParams.WRAP_CONTENT, 1.0f));
 textView.setText("所有");
 mDropDownMenu.addTab(textView,0);
 textView.setOnClickListener(new View.OnClickListener() {
       @Override
       public void onClick(View view) {
           mDropDownMenu.closeMenu();
       }
   });
```

如果你要了解更多，可以直接看源码  <a href="https://github.com/keyboard3/DropDownMenu/blob/master/app/src/main/java/com/yyy/djk/dropdownmenu/MainActivity.java">Example</a>

## 关于我

简书 [keyboard3](http://www.jianshu.com/users/62329de8c8a6/latest_articles)<br>
邮箱 keyboard3@icloud.com

# 致谢

- 感谢 [dongjunkun/DropDownMenu](https://github.com/dongjunkun/DropDownMenu) 
