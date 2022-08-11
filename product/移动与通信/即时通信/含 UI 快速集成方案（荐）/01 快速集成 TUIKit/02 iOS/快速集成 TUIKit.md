### 开发环境要求
- Xcode 10 及以上
- iOS 9.0 及以上

### CocoaPods 集成
TUIKit 从 5.7.1435 版本开始支持模块化集成，您可以根据自己的需求选择所需模块集成。

1. 根据实际业务需求在 Podfile 中添加对应的 TUI 组件，比如需要聊天功能，可以添加 `pod 'TUIChat'`，需要会话列表功能，可以添加 `pod 'TUIConversation'`，需要音视频通话功能，可以添加 `pod 'TUICalling'`，TUI 组件之间相互独立，添加或删除均不影响工程编译。
```
# 防止 TUI 组件里的 *.xcassets 与您项目里面冲突。
install! 'cocoapods', :disable_input_output_paths => true  

# TUI 组件依赖了静态库，需要屏蔽如下设置，如果报错，请参考常见问题说明。
# use_frameworks!

# 集成聊天功能
pod 'TUIChat'
# 集成会话功能
pod 'TUIConversation'
# 集成关系链功能
pod 'TUIContact'
# 集成群组功能
pod 'TUIGroup'
# 集成搜索功能（需要购买旗舰版套餐）
pod 'TUISearch'
# 集成音视频通话功能
pod 'TUICalling'
```
2. 执行以下命令，安装 TUI 组件。
```bash
pod install
```
 如果无法安装 TUIKit 最新版本，执行以下命令更新本地的 CocoaPods 仓库列表。
```bash
 pod repo update
```
**TUI 组件集成后效果**：<br>
 <img src="https://qcloudimg.tencent-cloud.cn/raw/083905832dcc7f8cc1d14ddaf15232e9.jpg" width = "400"/>


## 快速搭建
常用的聊天软件都是由会话列表、聊天窗口、好友列表、音视频通话等几个基本的界面组成，参考下面步骤，您仅需几行代码即可在项目中快速搭建这些 UI 界面。

### 步骤一：组件登录
```objectivec
#import "TUILogin.h"
// 您可以在用户 UI 点击登录的时候登录 UI 组件
- (void)loginSDK:(NSString *)userID userSig:(NSString *)sig succ:(TSucc)succ fail:(TFail)fail {
    // SDKAppID 可以在 即时通信 IM 控制台中获取
    // userSig生成见 GenerateTestUserSig.h
    [TUILogin login:SDKAppID userID:userID userSig:sig succ:^{
        NSLog(@"-----> 登录成功");
    } fail:^(int code, NSString *msg) {
        NSLog(@"-----> 登录失败");
    }];
}
```

### 步骤二：构建会话列表

会话列表只需要创建 `TUIConversationListController` 对象即可。会话列表会从数据库中读取最近联系人，当用户点击联系人时，`TUIConversationListController` 将该事件回调给上层。

```java
@implementation ConversationController // 您自己的 ViewController
- (void)viewDidLoad {
    [super viewDidLoad];
    // 创建 TUIConversationListController
    TUIConversationListController *conv = [[TUIConversationListController alloc] init];
    conv.delegate = self;
    // 把 TUIConversationListController 添加到自己的 ViewController
    [self addChildViewController:conv];
    [self.view addSubview:conv.view];
}

- (void)conversationListController:(TUIConversationListController *)conversationController didSelectConversation:(TUIConversationCell *)conversation
{
    // 会话列表点击事件，通常是打开聊天界面
}
@end
```

### 步骤三：构建聊天窗口

初始化聊天界面时，上层需要传入当前聊天界面对应的会话信息，示例代码如下：

```java
@implementation ChatViewController // 您自己的 ViewController
- (void)viewDidLoad {
   // 创建会话信息
   TUIChatConversationModel *data = [[TUIChatConversationModel alloc] init];
   data.userID = @"userID";    
   // 创建 TUIC2CChatViewController
   TUIC2CChatViewController *vc = [[TUIC2CChatViewController alloc] init];  
   [vc setConversationData:data];
   // 把 TUIC2CChatViewController 添加到自己的 ViewController
   [self addChildViewController:conv];
   [self.view addSubview:conv.view];
}
@end
```
`TUIC2CChatViewController` 会自动拉取该用户的历史消息并展示出来。

### 步骤四：构建通讯录界面

通讯录界面不需要其它依赖，只需创建对象并显示出来即可。

```java
@implementation ContactController // 您自己的 ViewController
- (void)viewDidLoad {    
   // 创建 TUIContactController
   TUIContactController *vc = [[TUIContactController alloc] init];
   // 把 TUIContactController 添加到自己的 ViewController
   [self addChildViewController:conv];
   [self.view addSubview:conv.view];
}
@end
```

### 步骤五：构建音视频通话功能
TUIKit 组件支持在聊天界面对用户发起音视频通话，仅需要简单几步就可以快速集成，详情请参考 [接入音视频通话]()。
  
>? 更多实操教学视频请参见：[极速集成 TUIKit（iOS）](https://cloud.tencent.com/edu/learning/course-3130-56699)。


## 常见问题
1. 提示 "target has transitive dependencies that include statically linked binaries" 如何处理？
如果在 pod 过程中出现该错误，是因为 TUIKit 使用到了第三方静态库，需要在 podfile 中注释掉 `use_frameworks!`。
如果在某种情况下，需要使用 `use_frameworks!`，则请使用 cocoapods 1.9.0 及以上版本进行 `pod install`，并修改为：
```
use_frameworks! :linkage => :static
```
如果您使用的是 swift，请将头文件引用改成 @import 模块名形式引用。

## 交流与反馈
欢迎加入 QQ 群进行技术交流和反馈问题。
<img src="https://qcloudimg.tencent-cloud.cn/raw/ca5f8724cd5a9002abc454f80bf3df12.png" alt="" style="zoom:50%;"/>