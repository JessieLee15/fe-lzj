# 微信公众号接入方案（主要支付）

## 支付
https://pay.weixin.qq.com/wiki/doc/api/external/jsapi.php?chapter=7_1

支付场景的交互细节：
1. 用户打开商户网页选购商品，发起支付，在网页通过JavaScript调用getBrandWCPayRequest接口，发起微信支付请求，用户进入支付流程。
2. 用户成功支付点击完成按钮后，商户的前端会收到JavaScript的返回值。商户可直接跳转到支付成功的静态页面进行展示。
3. 商户后台收到来自微信开放平台的支付成功回调通知，标志该笔订单支付成功。

注：（2）和（3）的触发不保证遵循严格的时序。JS API返回值作为触发商户网页跳转的标志，但商户后台应该只在收到微信后台的支付成功回调通知后，才做真正的支付成功的处理。

### 流程
1. 支付来源：

微信商户平台（pay.weixin.qq.com）设置您的公众号支付支付目录；【商户平台-->产品中心-->开发配置】

公众号支付在请求支付的时候会校验请求来源是否有在商户平台做了配置

2. 授权域名： 

微信公众号（mp.weixin.qq.com）设置网页授权域名：【公众号设置-->功能设置-->网页授权域名】

目的：获取openid （被授权的域名才是一个有效的获取openid的域名）

即授权回调域名（允许获取用户基本信息即回调域名）

3. 支付实现流程：

![官方图](../img/other/wepay/wepay.png)



4. 使用微信接口，有几个授权字段需要关注：
  1. open_id: 
  2. jsapi_ticket是公众号用于调用微信JS接口的临时票据
  3. access_tocken（注意这个key有两种，普通接口用的和支付接口用的。支付接口比较特殊）
    1. 普通：https://developers.weixin.qq.com/doc/offiaccount/Basic_Information/Get_access_token.html
    2. 支付：https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/Wechat_webpage_authorization.html


因此，前端基本只需关注普通接口使用：

使用到wexin-sdk的地方：wx.config参数通过后端接口```/common/weixin/getjsconfig```获得
1. locate (index.js main中)
2. scan（serch.js 二维码扫描）
3. 自定义分享（wexin-custom-share.js）
4. voice（search-voice.js）
5. getNetworkType（log.js）


普通接口授权确认：
1. appid与公众号一对一
2. 对应的AppSecret，与appid一对一
