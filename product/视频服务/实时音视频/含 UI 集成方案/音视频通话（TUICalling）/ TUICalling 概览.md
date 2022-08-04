<style>
    .card-container {
        width: 380px;
        display: block;
        float: left;
        padding-left: 15px;
        padding-right: 15px;
        box-sizing: border-box;
    }

    .card {
        border-radius: 10px;
        padding-top: 10px;
        padding-left: 10px;
        padding-right: 10px;
        padding-bottom: 10px;
        margin-top: 30px;
        border: 1px solid #ebeef5;
        background-color: #fff;
        overflow: hidden;
        box-shadow: 0 2px 12px 0 rgb(0 0 0 / 10%);
        text-align: center;
    }

    .markdown-text-box img {
        box-shadow: none;
    }


    .titlename {
                color:#191919;
        position: relative;
        top: -2px;
                font-weight: bolder;
                font-size: larger;
    }
        
        @media (max-width: 768px){
                .card-container,
                .scene-card-container{
                        width: 100%;
                }
                .scene-card > div{
                        width: 100%!important;
                        margin-left: 0!important;
                }
                img {
        box-shadow: none;
    }
        }
</style>

## 组件介绍

TUICalling 是腾讯云推出一款音视频通话 UI 组件，通过在项目中集成 TUICalling 组件，您只需要编写几行代码就可以为您的应用添加“一对一音视频通话”场景，并且支持离线唤起能力。TUICalling  支持Android、iOS、Web、小程序、Flutter、UniApp 等多个平台，基本功能如下图所示：

![](https://qcloudimg.tencent-cloud.cn/raw/08f914b45857743fd05dfaa28e2adb72.png)


>! **特别说明，基于开发者反馈和市场需求调研、 2022年08月 TUICalling 推出了新的两组API：TUICallKit、TUICallEngine 分别面向含 UI 集成Calling用户，以及无UI集成的Calling用户， 两组新的API在功能特性更加强大。同时我们整合TRTC和IM两个腾讯云的重磅产品，推出了专属 TUICallKit、TUICallEngine的音视频通话套餐，欢迎大家使用！**

#### 功能优势
- 接入方便：提供带 UI 的开源组件，节省90%开发时间，快速上线音视频通话应用；
- 多平台互通：各平台的TUICalling 组件间均支持相互拨打、接听、挂断等，互联互通；
- 大小窗切换：主叫方和被叫方自由切换本地的视频窗口；
- 离线推送：支持Android&iOS离线推送，被叫用户 App 不在线时收到电话通知；

#### 适用场景
两人或多人进行音视频通话，覆盖游戏社交、在线客服、视频客服、在线问诊、保险咨询等场景。

## 服务开通
**新版本的视频通话 SDK需要配合专属的音视频通话套餐**，新的套餐整合了腾讯云 [实时音视频 TRTC](https://cloud.tencent.com/document/product/647/16788) 和 [即时通信 IM](https://cloud.tencent.com/document/product/269/42440) 等两个基础的通信 PaaS 服务，一站式开通音视频通话相关服务，详细的开通流程请参考：[**两分钟开通 TUICalling 服务**]()。

### 音视频通话套餐详情
<table>
  <tr>
    <th width="100px" style="text-align:center">功能模块</th>
    <th width="100px" style="text-align:center">功能详情</th>
    <th width="100px" style="text-align:center"> 体验版</th>
    <th width="100px" style="text-align:center"> 基础版</th>
	  <th width="100px" style="text-align:center"> 进阶版</th>
    <th width="100px" style="text-align:center"> 尊享版</th>
  </tr>
   <td rowspan='4' style="text-align:center">音视频通话 UI </td>
   </tr>
	  <td style="text-align:left">微信同款UI设计</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
	<tr>
    <td style="text-align:left">悬浮窗</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
	<tr>
    <td style="text-align:left">自定义铃音</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
<td rowspan='9' style="text-align:center">音视频通话 SDK</td>
	<tr>
    <td style="text-align:left">1V1 通话</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">群组通话</td>
    <td style="text-align:center">-</td>
    <td style="text-align:center">-</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">中途呼叫/加入通话</td>
    <td style="text-align:center">-</td>
    <td style="text-align:center">-</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">视频通话切换语音通话</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">离线推送</td>
    <td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">多端登录</td>
    <td style="text-align:center">-</td>
    <td style="text-align:center">-</td>
		<td style="text-align:center">-</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left">AI 降噪</td>
    <td style="text-align:center">-</td>
    <td style="text-align:center">-</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
  </tr>
  <tr>
    <td style="text-align:left"> 弱网优化 </td>
    <td style="text-align:center">-</td>
    <td style="text-align:center">-</td>
		<td style="text-align:center">&#10003;</td>
    <td style="text-align:center">&#10003;</td>
</table>

## Demo 体验
<div style="position: relative; box-sizing: border-box;  padding-bottom: 10px; margin-bottom: 10px; overflow:hidden;display: flex">
        <div class="card-container">
            <div class="card">
                            <img src="https://main.qcloudimg.com/raw/b0211b0870806899009a17a4216ea65c.svg" data-nonescope="true">
                                <p class="titlename">Android</p>
                <div style="width: 100px; margin: auto;">
                <p style="color:#586376;"><img style="width:100px; max-width: inherit;" src="https://qcloudimg.tencent-cloud.cn/raw/078fbb462abd2253e4732487cad8a66d.png" /></p>
                </div>
                </div>
</div>
<div class="card-container">
            <div class="card">
                            <img src="https://main.qcloudimg.com/raw/613f2e15bed7c8297110676b52784b71.svg" data-nonescope="true">
                                <p class="titlename">iOS</p>
                <div style="width: 100px; margin: auto;">
                <p style="color:#586376;"><img style="width:100px; max-width: inherit;" src="https://qcloudimg.tencent-cloud.cn/raw/b1ea5318e1cfce38e4ef6249de7a4106.png" /></p>
                </div>
                            </div>
</div>
<div class="card-container">
            <div class="card">
                <div>
                            <img src="https://main.qcloudimg.com/raw/98394fa5d669de7fb7a187565d138cdb.svg" data-nonescope="true">
                             <p class="titlename">Web</p>
                <div style="width: 100px; margin: auto;">
                                <p style="height: 107.53px;display: flex; justify-content: center;
                                align-items: center;"><input type="button" value="基础聊天" style="height: 30px;width: 110px;background-color: #006eff;
    color: #fff;border: 1px solid #006eff;line-height: 30px;text-align: center;display: inline-block;cursor: pointer;outline: 0 none;
    box-sizing: border-box;text-decoration: none;font-size: 12px;vertical-align: middle;white-space: nowrap;border-radius: 15px;"  onclick="window.open('https://web.sdk.qcloud.com/im/demo/latest/index.html')" /></p>
                </div>
            </div>
                </div>
        </div>
			<div class="card-container">
            <div class="card">
                            <img src="https://main.qcloudimg.com/raw/b0211b0870806899009a17a4216ea65c.svg" data-nonescope="true">
                                <p class="titlename">Uni-APP（Android）</p>
                <p style="color:#586376;"><img style="width:100px; max-width: inherit;" src="https://qcloudimg.tencent-cloud.cn/raw/c1fed062d91cd95fdfb57059edcd5890.png" /></p>
            </div>
        </div>
				  <div class="card-container">
            <div class="card">
                            <img src="https://qcloudimg.tencent-cloud.cn/raw/af07e321883032c9796848d189a80f5e.png" data-nonescope="true">
                                <p class="titlename">微信小程序</p>
                <p style="color:#586376;"><img style="width:100px; max-width: inherit;" src="https://qcloudimg.tencent-cloud.cn/raw/46f2c76de9ef98e7eda34cc838c01d32.png" /></p>
            </div>
        </div>
</div>
</div>
</div>
</div>

## SDK 下载

<div style="position: relative; box-sizing: border-box;  padding-bottom: 10px; margin-bottom: 10px; overflow:hidden">
        <div class="card-container">
            <div class="card">
                 <img src="https://main.qcloudimg.com/raw/b0211b0870806899009a17a4216ea65c.svg" data-nonescope="true">
                <p class="titlename">Android  TUICalling</p>
                <p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速接入</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
                <a style="margin-left: 10px;" href=""><b>常见问题</b></a>
            </div>
        </div>
				<div class="card-container">
            <div class="card">
                 <img src="https://main.qcloudimg.com/raw/613f2e15bed7c8297110676b52784b71.svg" data-nonescope="true">
                <p class="titlename">iOS  TUICalling</p>
                <p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速接入</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
                <a style="margin-left: 10px;" href=""><b>常见问题</b></a>
            </div>
        </div>
				<div class="card-container">
						<div class="card">
                 <img src="https://main.qcloudimg.com/raw/7e2651085e3e3c6e32190e401a6dfd32.svg" data-nonescope="true">
                <p class="titlename">Web  TUICalling</p>
                <p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速接入</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
                <a style="margin-left: 10px;" href=""><b>常见问题</b></a>
            </div>
        </div>
				<div class="card-container">
						<div class="card">
                 <img src="https://main.qcloudimg.com/raw/af07e321883032c9796848d189a80f5e.png" data-nonescope="true">
                <p class="titlename">小程序  TUICalling</p>
                <p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速接入</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
                <a style="margin-left: 10px;" href=""><b>常见问题</b></a>
            </div>
        </div>
			  <div class="card-container">
						<div class="card">
                 <img src="https://main.qcloudimg.com/raw/e9d18b164152f08bc0694c01e966daea.png" data-nonescope="true">
                <p class="titlename">Uni-APP（客户端） TUICalling</p>
                <p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
								<a style="margin-left: 10px;" href=""><b>跑通示例</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速集成</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
            </div>
        </div>
				<div class="card-container">
						<div class="card">
                 <img src="https://main.qcloudimg.com/raw/e9d18b164152f08bc0694c01e966daea.png" data-nonescope="true">
                <p class="titlename">Uni-APP（小程序）TUICalling</p>
								<p style="color:#586376;">类“微信” UI，支持 1V1 通话、群组通话、悬浮窗、离线推送等特性，功能强大。</p>
                <a style="margin-left: 10px;" href=""><b>Github </b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32175"><b>快速接入</b></a>
                <a style="margin-left: 10px;" href="https://cloud.tencent.com/document/product/647/32166"><b>API 参考</b></a>
                <a style="margin-left: 10px;" href=""><b>常见问题</b></a>
            </div>
        </div>
</div>

## 开源建设
除上述 TUICalling 新版本之外，腾讯云音视频团队还基于 TRTC+IM 两个核心 SDK 封装了一个开源版本的通话解决方案，既原来的TUICalling API、TRTCCalling API，方便开发者更好的理解音视频通话的业务流程，详见 [**这里**](https://github.com/tencentyun/TUICalling)，欢迎了解~