| 如果有bug请用最新版本 | [ ![Download](https://api.bintray.com/packages/zhongrui/mylibrary/CropBitmap/images/download.svg) ](https://bintray.com/zhongrui/mylibrary/CropBitmap/_latestVersion) |
|--------|----|
# 仿QQ头像裁剪  
 

   
    

![github](https://github.com/zhongruiAndroid/CropBitmap/blob/master/app/src/main/res/drawable/clipbitmap2.gif "github")  

## [Demo.apk下载](https://raw.githubusercontent.com/zhongruiAndroid/CropBitmap/master/app/sampledata/app.apk "apk文件")
    

| 属性           | 类型      | 说明                                                                  |
|----------------|-----------|-----------------------------------------------------------------------|
| maskColor      | color | 遮罩层颜色(默认#60000000)                                |
| borderColor     | color | 裁剪框内部边框颜色(默认白色)                               |
| radius        | dimension     | 裁剪框圆角(默认为最大值，裁剪框高度的一半)                                                        |
| maxScale    | float     | 图片最大放大倍数(默认3)                                                      |
| doubleClickScale    | float | 双击图片放大倍数(默认1.8,最大值不超过maxScale)

  
```xml
<com.github.cropbitmap.LikeQQCropView
    android:id="@+id/likeView"
    android:layout_width="match_parent"
    android:layout_height="0dp"
    android:layout_weight="1"
    android:background="@color/white"
    />
```


#### 设置Bitmap
```java
LikeQQCropView likeView=findViewById(R.id.likeView);

//如果传入的bitmap过大,此方法有OOM的可能
likeView.setBitmap(Bitmap bitmap);

//以下方法很安全,做了防止OOM的压缩

/**设置压缩之后的宽和高*/
likeView.setBitmap(多参);

/**[推荐该方法]设置压缩之后的高度(宽度自适应)*/
likeView.setBitmapForHeight(多参);

/**[推荐该方法]设置压缩之后的宽度(高度自适应)*/
likeView.setBitmapForWidth(多参);

/**设置压缩的缩放倍数(偶数),图片缩小一半传2,缩小4倍传4*/
likeView.setBitmapForScale(多参);
```
#### 对Bitmap的操作
```java
/**水平翻转*/
likeView.horizontalFlip();

/**垂直翻转*/
likeView.verticalFlip();

/**垂直+水平翻转*/
likeView.verticalAndHorizontalFlip();

/**裁剪*/
likeView.clip();

/**图片位置重置*/
likeView.reset();

/**设置遮罩层*/
likeView.setMaskColor(color);

/**设置裁剪框内部边框颜色*/
likeView.setBorderColor(color);

/**设置裁剪框圆角*/
likeView.setRadius(radius);

/**设置图片最大放大倍数*/
likeView.setMaxScale(3);

/**设置双击图片放大倍数*/
likeView.setDoubleClickScale(1.8);

/**获取裁剪框宽度*/
likeView.getClipWidth();
```
### 如果手机相册里面的图片出现旋转的情况
```java
likeView.setBitmapForWidth(filePath,1080);

int degree = likeView.readPictureDegree("filePath");

Bitmap oldBitmap = likeView.getBitmap();
Bitmap rotateBitmap = likeView.rotateBitmap(degree, oldBitmap);

likeView.setBitmap(rotateBitmap);

/*或者使用下面4种方法,自动判断是否需要旋转图片*/
likeView.setBitmapForHeightToRotate(filePath,height);
likeView.setBitmapForWidthToRotate(filePath,width);
likeView.setBitmapToRotate(filePath,width,height);
likeView.setBitmapForScaleToRotate(filePath,4);
```
<br/>
<br/>

| 最新版本号 | [ ![Download](https://api.bintray.com/packages/zhongrui/mylibrary/CropBitmap/images/download.svg) ](https://bintray.com/zhongrui/mylibrary/CropBitmap/_latestVersion) |
|--------|----|
  



```gradle
implementation 'com.github:MyCropBitmap:版本号看上面'
```
