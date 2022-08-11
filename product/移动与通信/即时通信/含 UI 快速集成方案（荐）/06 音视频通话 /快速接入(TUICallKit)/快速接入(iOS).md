本文将介绍如何用最短的时间完成 TUICallKit 组件的接入，跟随本文档，您将在一个小时的时间内完成如下几个关键步骤，并最终得到一个包含完备 UI 界面的视频通话功能。

## 环境准备
iOS 9.0 (API level 16) 及更高。


[](id:step1)
## 步骤一：开通服务
TUICallKit 是基于腾讯云 [即时通信 IM](https://cloud.tencent.com/document/product/269/42440) 和 [实时音视频 TRTC](https://cloud.tencent.com/document/product/647/16788) 两项付费 PaaS 服务构建出的音视频通信组件。您可以按照如下步骤开通相关的服务并体验 7 天的免费试用服务：

1. 登录到 [即时通信 IM 控制台](https://console.cloud.tencent.com/im)，单击**创建新应用**，在弹出的对话框中输入您的应用名称，并单击**确定**。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/1105c3c339be4f71d72800fe2839b113.png">
2. 单击刚刚创建出的应用，进入**基本配置**页面，并在页面的右下角找到**开通腾讯实时音视频服务**功能区，单击**免费体验**即可开通 TUICallKit 的 7 天免费试用服务。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/667633f7addfd0c589bb086b1fc17d30.png">
3. 在同一页面找到 **SDKAppID** 和**密钥**并记录下来，它们会在后续的[步骤四：登录 TUI 组件](#step4)中被用到。
<img width="640" src="https://qcloudimg.tencent-cloud.cn/raw/e435332cda8d9ec7fea21bd95f7a0cba.png">


[](id:step2)
## 步骤二：导入组件
使用 CocoaPods 导入组件，具体步骤如下：
1. 在您的 `Podfile` 文件中添加以下依赖。
```
pod 'TUICallKit'
```
2. 执行以下命令，安装组件。
```bash
pod install
```
如果无法安装 TUICallKit 最新版本，执行以下命令更新本地的 CocoaPods 仓库列表。
```bash
pod repo update
```

[](id:step3)
## 步骤三：完成工程配置
使用音视频功能，需要授权麦克风和摄像头的使用权限。在 App 的 Info.plist 中添加以下两项，分别对应麦克风和摄像头在系统弹出授权对话框时的提示信息。

```
<key>NSCameraUsageDescription</key>
<string>CallingApp需要访问您的相机权限，开启后录制的视频才会有画面</string>
<key>NSMicrophoneUsageDescription</key>
<string>CallingApp需要访问您的麦克风权限，开启后录制的视频才会有声音</string>
```
<img width="900" src="https://qcloudimg.tencent-cloud.cn/raw/7f91f3f8defa5a0650f08b8acf960219.png">


[](id:step7)
## 步骤四：更多特性

### 一、悬浮窗功能
如果您的业务需要开启悬浮窗功能，您可以在 TUICallKit 组件初始化时调用以下接口开启该功能：
 <dx-codeblock>
:::  Objective-C Objectivec
[[TUICallKit createInstance] enableFloatWindow:YES];
:::
::: Swift
TUICallKit.createInstance().enableFloatWindow(true)
:::
</dx-codeblock>

### 二. 通话状态监听
如果您的业务需要 **监听通话的状态**，例如通话开始、结束，以及通话过程中的网络质量等等，可以监听以下事件：
<dx-codeblock>
:::  Objective-C Objectivec
[[TUICallEngine createInstance] addObserver:self];

- (void)onCallBegin:(TUIRoomId *)roomId callMediaType:(TUICallMediaType)callMediaType callRole:(TUICallRole)callRole {
  
}
- (void)onCallEnd:(TUIRoomId *)roomId callMediaType:(TUICallMediaType)callMediaType callRole:(TUICallRole)callRole totalTime:(float)totalTime {
  
}
- (void)onUserNetworkQualityChanged:(NSArray<TUINetworkQualityInfo *> *)networkQualityList {
  
}
:::
::: Swift
TUICallEngine.createInstance().add(self)

public func onCallBegin(roomId: TUIRoomId, callMediaType: TUICallMediaType, callRole: TUICallRole) {
        
}
public func onCallEnd(roomId: TUIRoomId, callMediaType: TUICallMediaType, callRole: TUICallRole, totalTime: Float) {
        
}
public func onUserNetworkQualityChanged(networkQualityList: [TUINetworkQualityInfo]) {
        
}
:::
</dx-codeblock>

### 三、自定义铃音
如果您需要自定义来电铃音，可以通过如下接口进行设置：
<dx-codeblock>
:::  Objective-C Objectivec
[[TUICallKit createInstance] setCallingBell:filePath];
:::
::: Swift
TUICallKit.createInstance().setCallingBell(filePath: filePath)
:::
</dx-codeblock>
