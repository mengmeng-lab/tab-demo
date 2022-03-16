<template>
	<view class="shenhe-container">
		<view class="tab-container">
			<u-tabs-swiper ref="uTabs" 
			:current="current" :list="navList" 
			:is-scroll="false" 
			swiperWidth="750"
			height="80"
			:activeColor="'#000'"
			:inactiveColor="'#8A8A8A'"
			:fontSize = "29"
			:bold = "false"
			:barWidth = "101"
			:barHeight= "4"
				@change="tabsChange">
			</u-tabs-swiper>
		</view>
		<swiper style="height: 100%;" :current="swiperCurrent" @transition="transition"
			@animationfinish="animationfinish">
			<swiper-item class="swiper-item">
				<scroll-view scroll-y style="height: 100%; width: 100%;">
					<view class="swiper-div">
						1
					</view>
				</scroll-view>
			</swiper-item>
			<swiper-item class="swiper-item">
				<scroll-view scroll-y style="height: 100%; width: 100%;">
					<view class="swiper-div">
						2
					</view>
				</scroll-view>
			</swiper-item>
			<swiper-item class="swiper-item">
				<scroll-view scroll-y style="height: 100%; width: 100%;">
					<view class="swiper-div">
						3
					</view>
				</scroll-view>
			</swiper-item>
		</swiper>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList: [{
					name: '审核中'
				}, {
					name: '审核失败'
				}, {
					name: '审核成功'
				}],
				current: 0, // tabs组件的current值，表示当前活动的tab选项
				swiperCurrent: 0, // swiper组件的current值，表示当前那个swiper-item是活动的

			}
		},
		components: {

		},
		methods: {
			// tabs通知swiper切换
			tabsChange(index) {
				this.swiperCurrent = index;
			},
			// swiper-item左右移动，通知tabs的滑块跟随移动
			transition(e) {
				let dx = e.detail.dx;
				this.$refs.uTabs.setDx(dx);
			},
			// 由于swiper的内部机制问题，快速切换swiper不会触发dx的连续变化，需要在结束时重置状态
			// swiper滑动结束，分别设置tabs和swiper的状态
			animationfinish(e) {
				let current = e.detail.current;
				this.$refs.uTabs.setFinishCurrent(current);
				this.swiperCurrent = current;
				this.current = current;
			},
		}
	}
</script>

<style lang="scss" scoped>
	.shenhe-container {
		display: flex;
		flex-direction: column;
		height: 100%;
		background-color: pink;
		.tab-container {
			height: 80rpx;
		}
		.swiper {
			flex: 1rpx;
			height: 2rpx;
		}
	}
</style>

