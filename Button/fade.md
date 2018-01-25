类似文字游戏按钮点击一下背景色逐渐往左移动的样式。

### wxml

```html
<view class='buttonType'>
    <view class='buttonBox' ></view>
    <view class='buttonBg' animation="{{animationData}}"></view>
    <view class='buttonText' bindtap='buttonText' >a modest village</view>
</view>
```

### wxss

```css
.buttonType{
  width: 100%;
  height:60%;
  padding: 50rpx;
  overflow: hidden;
}

.buttonBox{
  position: absolute;
  border: 1rpx solid black;
  width: 320rpx;
  height: 80rpx;
  z-index: 2;
}

.buttonBg{
  position: absolute;
  background-color: yellowgreen;
  width: 319rpx;
  height: 80rpx;
  margin: 1rpx 0 0 1rpx;
  z-index: 1;
}

.buttonText{
  position:absolute;
  z-index: 3;
  width: 320rpx;
  height: 80rpx;
  text-align: center;
  line-height: 80rpx;
}
```

### js

```js
//获取应用实例
const app = getApp()

Page({
  data: {
    animationData:{},
    buttonLoad:false
  },
  //事件处理函数
  onLoad: function () {
  },

  buttonText:function(){
    var self = this
    var buttonLoad = self.data.buttonLoad
    var waitTime = 3000
    if (!buttonLoad){
      console.log('tap!')
      var animation = wx.createAnimation({
        duration: waitTime,
        timingFunction: 'linear',
        transformOrigin: "0% 50% 0"
      })

      animation.scaleX(0).step()
      self.setData({
        buttonLoad:true
      })
      animation.scaleX(1).step({ duration:0});
      self.setData({
        animationData: animation.export(),
      })
      setTimeout(function(){
        self.setData({
          buttonLoad: false
        })
      }, waitTime)
    }
  }
  
})
```
