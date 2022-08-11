本文将介绍如何用最短的时间完成 TUICallKit 组件的接入，跟随本文档，您将在一个小时的时间内完成如下几个关键步骤，并最终得到一个包含完备 UI 界面的视频通话功能。

## 环境准备
- 最低兼容 Android 4.1（SDK API Level 16），建议使用 Android 5.0 （SDK API Level 21）及以上版本。
- Android Studio 3.5 及以上的版本（Gradle 3.4.0 及以上的版本）。
- Android 4.1 及以上的手机设备。

[](id:step1)
## 步骤一：开通服务
TUICallKit 是基于腾讯云 [即时通信 IM](https://cloud.tencent.com/document/product/269/42440) 和 [实时音视频 TRTC](https://cloud.tencent.com/document/product/647/16788) 两项付费 PaaS 服务构建出的音视频通信组件。您可以按照如下步骤开通相关的服务并体验 7 天的免费试用服务：

1. 登录到 [即时通信 IM 控制台](https://console.cloud.tencent.com/im)，单击**创建新应用**，在弹出的对话框中输入您的应用名称，并单击**确定**。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/1105c3c339be4f71d72800fe2839b113.png">
2. 单击刚刚创建出的应用，进入**基本配置**页面，并在页面的右下角找到**开通腾讯实时音视频服务**功能区，单击**免费体验**即可开通 TUICallKit 的 7 天免费试用服务。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/99a6a70e64f6877bad9406705cbf7be1.png">
3. 在同一页面找到 **SDKAppID** 和 **密钥(SecretKey)** 并记录下来，它们会在后续的 [步骤四：登录 TUI 组件](#step4) 中被用到。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/e435332cda8d9ec7fea21bd95f7a0cba.png">


[](id:step2)
## 步骤二：下载并导入组件
在 [Github](https://github.com/tencentyun/TUICalling) 中克隆/下载代码，然后拷贝 Android 目录下的 tuicallkit 子目录到您当前工程中的 app 同级目录中，如下图：
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/5184b651c273ff1727065866cc45cd9a.png">
[](id:step3)
## 步骤三：完成工程配置
1. 在工程根目录下找到 `setting.gradle` 文件，并在其中增加如下代码，它的作用是将 [步骤二](#step2) 中下载的 tuicallkit 组件导入到您当前的项目中：
```java
include ':tuicallkit'
```
2. 在 app 目录下找到 `build.gradle` 文件，并在其中增加如下代码，它的作用是声明当前 app 对新加入的 tuicallkit 组件的依赖：
```java
api project(':tuicallkit')
```
> ? TUICallKit 工程内部已经默认依赖：`TRTC SDK`、`IM SDK`、`tuicallengine` 以及公共库 `tuicore`，不需要开发者单独配置。如需进行版本升级，则修改`tuicallkit/build.gradle`文件即可。
3. 由于我们在 SDK 内部使用了Java 的反射特性，需要将 SDK 中的部分类加入不混淆名单，因此需要您在 `proguard-rules.pro` 文件中添加如下代码：
``` 
-keep class com.tencent.** { *; }
```

>! TUICallKit 会在内部帮助您动态申请相机、麦克风、读取存储权限等，如果因为您的业务问题需要删减，可以请修改`tuicallkit/src/main/AndroidManifest.xml`。

[](id:step4)


[](id:step7)
## 步骤四：更多特性
### 一、悬浮窗功能
如果您的业务需要开启悬浮窗功能，您可以在 TUICallKit 组件初始化时调用以下接口开启该功能：
```java
TUICallKit.createInstance(context).enableFloatWindow(true);
```

### 二、通话状态监听
如果您的业务需要 **监听通话的状态**，例如通话开始、结束，以及通话过程中的网络质量等等，可以监听以下事件：
```java
TUICallEngine.createInstance(context).addObserver(new TUICallObserver() {
    @Override
    public void onCallBegin(TUICommonDefine.RoomId roomId, TUICallDefine.MediaType callMediaType, TUICallDefine.Role callRole) {
    }
    public void onCallEnd(TUICommonDefine.RoomId roomId, TUICallDefine.MediaType callMediaType,TUICallDefine.Role callRole, long totalTime) {
    }
    public void onUserNetworkQualityChanged(List<TUICommonDefine.NetworkQualityInfo> networkQualityList) {
    }
});
```

### 三、自定义铃音
如果您需要自定义来电铃音，可以通过如下接口进行设置：
```java
TUICallKit.createInstance(context).setCallingBell(filePath);
```
