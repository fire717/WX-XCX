长文本点击展开和折叠

![button](../img/)

### wxml

```html
<view class='text-box'>
    <view class="{{isFold ?'textFlod':'textExtend' }}" >
      {{summary}}
    </view>
    <view class="buttonFlod" bindtap="flodFn">
      {{isFold ?'全文':'折叠' }}
    </view>
</view>
```

### wxss

```css
.textFlod{
  height: 160rpx;
  overflow: hidden;
}
.textExtend{

}
.buttonFlod{
  color: #5CACEE;
}
```

### js

```js
Page({
  data: {
    summary:'一部关于AlphaGo的纪录片定于4月21日在纽约翠贝卡电影节首映。该部纪录片由格雷格执导，演员表有李世石，樊麾，黄士杰，哈萨比斯和席尔瓦。影片时长90分钟。这部电影全方位展示了人机大战的过程，更尽可能多的揭示了人类思维的工作方式和人工智能未来的工作方式。',
    isFold:true,
  },
  //事件处理函数
  onLoad: function () {
  },

  flodFn: function () {
    var self = this
    var isFold = self.data.isFold
    self.setData({
      isFold: !isFold
    });
  }
  
})
```
