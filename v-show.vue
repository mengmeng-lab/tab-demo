<template>
  <div>
      <div class="tab">
        <ul class="tab_button">
            <li 
	            v-for="(item,index) in tabList" 
	            :key="index" 
	            :class="{active:currentClass==index}" 
	            @click="toggleTab(index)"  // 只传一个参数用来控制选中tab的样式以及选中tab对应内容块的显示
            >{{item}}</li>
        </ul>
    </div>
    <div>  // 三个tab对应内容块
        <div class="tab_con" v-show="currentTab==0">
            firstTab
        </div>
        <div class="tab_con" v-show="currentTab==1">
            secondTab
        </div>
        <div class="tab_con" v-show="currentTab==2">
            thirdTab
        </div>
    </div>
  </div>
</template>

<script>

export default {
name: 'Home',
props: {},
data() {
    return {
        currentTab: 0,
        currentClass: 0,
        tabList:[ 'firstTab', 'secondTab', 'thirdTab']
    };
},
methods: {
    toggleTab(current){
        this.currentTab = current;
        this.currentClass = current;
    }
}
}
</script>
<style scoped>
.tab_button li{width: 220px; height: 84px; border: 1px solid #999; background: transparent; cursor: pointer; display: inline-block; margin-left: 24px; border-radius: 8px;
font: bold 24px/84px 'Microsoft Yahei'; color: #333; text-align: center;}
.tab_button li.active{ border: 1px solid #f3ae19; color: #f3ae19}
.tab_con{ width: 714px; height: 400px; background: #ccc; color: #333; margin-left: 64px; font-size: 64px; text-align: center; line-height: 400px;}
</style>

