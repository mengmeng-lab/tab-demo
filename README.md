# tab-demo
tab切换动画切换

一、vue中tab切换
1.v-show控制内容切换
简单版原理：用点击事件改变num值作为开关，控制tab样式和内容显示隐藏。和组件切换原理类似，适合tab内容少，可以直接放在同一个页面
2.组件切换
利用vue里的 :is属性和keep-alive缓存
3.路由切换
通过router-link实现，对地址栏和数据请求友好，但是tab按钮和内容块不在一个页面，需要跳转
4.ui组件
vant组件自带tab切换，使用不够灵活
<van-tabs v-model:active="active">
  <van-tab title="标签 1">内容 1</van-tab>
  <van-tab title="标签 2">内容 2</van-tab>
  <van-tab title="标签 3">内容 3</van-tab>
  <van-tab title="标签 4">内容 4</van-tab>
</van-tabs>

二、uniapp移动端中的tab切换以及左右动画滑动
u-tabs-swiper的使用，全屏选项卡
