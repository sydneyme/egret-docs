通过 `Egret` 引擎制作的游戏，不仅可以发布成 `Html5` 网页项目，还可以发布成原生项目。

## 发布设置前的准备工作

- 安装最新版本的launcher
- 确认引擎版本
    - 引擎版本必须为***5.1.6及以上***
- 发布 iOS 需要安装Xcode
    - 建议版本: 9.0或以上
    - 后续需要在 Xcode 中完成发布项目的修改和功能接入
- 发布安卓需要安装 Android Studio
	- 建议版本: 3.0或以上
	- 后续需要在 Android Studio 中完成发布项目的修改和功能接入

## 发布Android工程

### 发布项目

- 在launcher的项目面板找到需要发布Android工程的Egret项目，点击发布设置

![](./p0.png)

- 点击左侧的Android按钮，在右侧页面中，输入应用名称、应用包名，点击确定。

![](./p1.png)


## 发布iOS工程

### 发布项目

- 在launcher的项目面板找到需要发布iOS工程的Egret项目，点击发布设置

![](./p0.png)

- 点击左侧的iOS按钮，在右侧页面中，输入应用名称、应用包名，点击确定。

![](./p2.png)

- 如果勾选`使用Hybrid方案`，该项目会使用 iOS 系统的 webview 来运行游戏

## 工程设置

### 设置游戏地址
Android：

```java
nativeAndroid.initialize(gameUrl);
```

iOS:

```objective-c
[_native startGame:gameUrl];
```

launcher创建的默认工程会将游戏资源放到assets/game目录下，这时会从assets目录加载游戏。如果不需要将游戏放到应用里，请删除assets/game目录。

### 其它设置

可以通过修改nativeAndroid.config或_native.config的属性更改工程设置。

属性说明：

- showFPS 是否显示fps面板
- fpsLogTime log在屏幕上停留时间，单位是秒，-1为永久显示
- disableNativeRender 是否禁用原生渲染加速
- clearCache 是否清理缓存，设置为true时每次启动都会清理缓存，方便调试
- loadingTimeout 加载index的超时时间。默认为0，不设置超时
- preloadPath 设置预加载目录，详见“热更新方案说明”

## 注意

Native 仅支持 webgl 渲染模式。