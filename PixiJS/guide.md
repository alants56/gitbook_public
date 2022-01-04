# Guide



**1. 创建一个画板**

```html
<div id='template'/>
```

```js
const app = new PIXI.Application({backgroundColor : 0xFFFFFF,width:width, height:height});
let dom = document.getElementById("template");

dom.addEventListener('contextmenu', (e)=>{
  e.preventDefault();
})

dom.appendChild(app.view);
```



**2.加载远程图片资源到舞台**

```js
let loader = new PIXI.Loader();
loader.add({url:imgUrl}, {crossOrigin: true}).load(()=>{
  const template = new PIXI.Sprite(
    PIXI.utils.TextureCache[this.imgUrl],
  );
  
  //缩放比例
  template.scale.x = scale;
  template.scale.y = scale;
  //位置
  template.x = 0;
  template.y = 0;
  app.stage.addChild(template);
});
```



**3.在加载的图片上添加鼠标响应事件**

```js
template.on('pointerdown', (event)=>{console.log(event)})
  .on('pointerup', ()=>{})
  .on('pointerupoutside', ()=>{})
  .on('pointerover',()=>{})
  .on('pointerout',()=>{})
  .on('pointermove', (event)=>{console.log(event)})
```

