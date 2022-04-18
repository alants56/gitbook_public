## 1.Electron企微扫码登录

>  思路：通过webview显示企微的登录二维码，然后监听webview中的跳转事件，取出回掉中的auth_code，阻止其跳转，然后在Electron应用内进行登录



1. 首先在配置中开启webview

```js
webPreferences:{
	//...
	webviewTag: true, //开启webview
	//...
}
```

2. 通过**isWeixinLogin**控制是否是企业微信登录，**oauthUrl**你的企微登录URL，**httpreferrer**你的源地址。

```vue
<div v-if="isWeixinLogin">
	<webview id="weixinWebview" :src="oauthUrl" :httpreferrer="httpreferrer" class="webview-wrapper"></webview>
</div>
```

> 注意httpreferrer必须设置，否则企微回返回“校验请求来源错误”。



3. 监听webview中的路由跳转事件，拿到**auth_code**

```js
showQrCode() {
  this.$nextTick(()=>{
  	const webview = document.getElementById('weixinWebview')
  	webview.addEventListener('will-navigate',this.handleLogin)
	})
}

handleLogin(event) {
  console.log("handleLogin",event);
  //检查是否是企微扫码登录的回调信息
  if (this.check(event.url)) {
    //通过URL就可以拿到auth_code，并阻止webview跳转,然后根据auth_code进行验证登录
    event.preventDefault();
    event.stopPropagation();
    this.isWeixinLogin = false;
    this.loginByWeixin(event.url);
  }
}

```



## 2.Electron钉钉扫码登录

>  思路：类似于企微登录，但是有一些区别，通过div显示登录二维码，然后通过webview进行跳转，最后监听webview中的跳转事件，取出回调中的code，阻止其跳转，然后在Electron应用内进行登录

1. 创建钉钉登录二维码

```vue
<div v-if="isDingdingLogin">
  <div id="login_container" ref="webView"/>
</div>
  
```

2. 首先监听window的'message'来自钉钉的登录事件，然后将其URL在自定义的webview中显示

```js
mounted() {
    let handleMessage = (event)=>{
      if (event.origin == 'https://login.dingtalk.com') {
        this.webview = document.createElement('webview');
          this.webview.httpreferrer = this.httpreferrer; //源地址，同上述httpreferrer的作用
          this.webview.src = this.oauthUrl;
          this.$refs.webView.appendChild(this.webview);
          this.webview.addEventListener('did-start-navigation',this.handleLogin);
      }
    }
    if (typeof window.addEventListener != 'undefined') {
        window.addEventListener('message', handleMessage, false);
      } else if (typeof window.attachEvent != 'undefined') {
        window.attachEvent('onmessage', handleMessage);
      }
    
    // 显示二维码
    this.$nextTick(() => {
        let obj = DDLogin({
          id: 'login_container',//这里需要你在自己的页面定义一个HTML标签并设置id
          goto: this.gotoUrl, //请参考钉钉扫码登录
          style: 'border:none;background-color:#FFFFFF;',
          width: '365',
          height: '400',
        });
    });
 }
```

3. 接下来监听webview中的'did-start-navigation'事件，拿到**code**

```js
handleLogin(event) {
  console.log("handleLogin",event);
  //检查是否是钉钉扫码登录的回调信息
  if (this.check(event.url)) {
    //通过URL就可以拿到code，并阻止webview跳转,然后根据code进行验证登录
    event.preventDefault();
    event.stopPropagation();
    this.isDingdingLogin = false;
    this.loginByDingding(event.url);
  }
}
```

