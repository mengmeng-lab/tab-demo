<template>
  <div>
      <div class="tab">
        <ul class="tab_button">
            <li 
	            v-for="(item,index) in tabList"    // 循环语句写tab按钮
	            :key="index" 
	            :class="{active:currentClass==index}"   // 设置选中按钮的样式
	            @click="toggleTab(item.tab_con,index)"  //  点击切换tab，传参绑定选中tab的样式和内容
            >
            {{item.title}}  // 按钮的文字
            </li>
        </ul>
    </div>
    <div class="tab_con">
        <keep-alive>   // keep-alive 内容会被缓存，不会一直渲染dom元素
            <firstTab :is="currentTab"></firstTab>   // is绑定选中tab的内容
        </keep-alive>
    </div>
  </div>
</template>

<script>
//  引入三个tab内容组件
import firstTab from './firstTab'
import secondTab from './secondTab'
import thirdTab from './thirdTab' 

export default {
	name: 'Home',
	props: {},
	data() {
	    return {
	        currentTab: 'firstTab',  // 默认选中tab
	        currentClass: 0,  // 默认选中按钮样式
	        tabList:[
	            {
	                title: 'firstTab',  // tab文字
	                tab_con: 'firstTab'  // tab对应内容块
	            },
	            {
	                title: 'secondTab',
	                tab_con: 'secondTab'
	            },
	            {
	                title: 'thirdTab',
	                tab_con: 'thirdTab'
	            }
	        ]
	    };
	},
	methods: {
	    toggleTab(tab_con,currentClass){
	        this.currentTab = tab_con;  // 选中tab内容块展示
	        this.currentClass = currentClass;  // 选中tab样式
	    }
	},
	components: {
		firstTab,
		secondTab,
		thirdTab
	},
}
</script>
<style scoped>
.tab_button li{width: 220px; height: 84px; border: 1px solid #999; cursor: pointer; display: inline-block; margin-left: 24px; border-radius: 8px; font: bold 24px/84px 'Microsoft Yahei'; color: #333; text-align: center;}
.tab_button li.active{ border: 1px solid #f3ae19; color: #f3ae19}  // 选中tab 样式
</style>

