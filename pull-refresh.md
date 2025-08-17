
## 下拉刷新 xPullRefresh

***

#### 介绍

请注意内容下拉内置了mode模式即可以是listview,也可以是scrollview组件进行渲染,请了解各自功能.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-pull-refresh/x-pull-refresh.uvue**

#### 使用

<x-pull-refresh></x-pull-refresh>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| height | 高，可以是百分比，px,rpx等单位数字或者字符串。 | string | '100%' |
| pullHeight | 下拉区域触发刷新的高度 | number | 60 |
| color | 图标颜色,空值时，取全局主题色。 | string | "" |
| textColor | 文字颜色,空值时，取全局主题色。 | string | "" |
| modelValue | 当前是否在刷新中,如果默认是true，表示一进入就触发刷新，然后你需要手动复位完成这个刷新状态。<br>请在事件refresh中设置本状态为false来结束刷新。 | boolean | false |
| modelBottomStatus | 底部的刷新状态，true刷新中，false结束刷新，不在刷新中。 | boolean | false |
| mode | 内部使用哪种组件来渲染列表<br>可用值:listview,scrollview | string | "scrollview" |
| showScrollbar | 是否显示滚动条 | boolean | true |
| disabledPull | 是否禁用下拉刷新 | boolean | false |
| disabledBottom | 是否禁用触底刷新 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| refresh | - | 下拉触发了刷新。请在事件refresh中设置本状态modelValue为false来结束刷新。 |
| bottomRefresh | - | 触底刷新，请在事件中来结束当前的刷新状态。 |
| update:modelBottomStatus | - | 等同v-model:model-bottom-status="" |
| scroll | - | 滚动的时候触发 |
| scrollDirection | - | 滚动的时候触发 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |
| pull | - | - |
| bottom | - | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| setScrollTop | **top** : number | - | 设置滚动距离 |
| setScrollIntoView | **id** : string | - | 设置滚动距离 |


#### 示例页面路径

/pages/fankui/pull-refresh

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view class="flex-1">

		<x-tabs  :is-item-center="true" width="100%" :list="list3"></x-tabs>
		<view style="position: relative;flex:1;">
			<view 
			v-if="scrootop>0"
			:style="{
				position: 'absolute',
				marginTop:menuPosition+'px',
				width: '100%'
			}" class="floatMenu">
			<x-text color="white" >内悬浮菜单</x-text>
			</view>
			<x-pull-refresh :showScrollbar="false" @scroll="scrollingEvt" @scrollDirection="onScrollDirection" style="flex:1" v-model="isfresh"
				v-model:model-bottom-status="bottomFresh" @refresh="load" @bottomRefresh="bottomLoad">
				<view class="floatMenu" style="z-index:8">
					<x-text color="white">内悬浮菜单</x-text>
				</view>
				<view>
					<x-sheet>
						<x-text font-size="18" class=" text-weight-b mb-8">下拉刷新 PullRefresh</x-text>
						<x-text color="#999999">
							可以完全自主定义样式和刷新提示文字，请通过插槽配置，插槽数据已返回当前状态管理。
							可以自己定义宽和高放置在局部布局中实现局部下拉和触底刷新。
						</x-text>
					</x-sheet>
				</view>
				<view v-for="(item,index) in 8" :key="index" :type="1">
					<x-sheet height="250">
						<x-text>下拉查看下拉刷新,上拉查看触底刷新 - {{item}}</x-text>
					</x-sheet>
				</view>
			</x-pull-refresh>
		</view>

		<!-- 下面是listview示例 -->
		<!-- 固定到父元素顶部的元素 -->
		<!-- <x-tabs  :is-item-center="true" width="100%" :list="list3"></x-tabs>
		<view style="position: relative;flex:1;">
			<text 
			v-if="scrootop>0"
			:style="{
				position: 'absolute',
				marginTop:menuPosition+'px',
				width: '100%'
			}" class="floatMenu">内悬浮菜单</text>
			<x-pull-refresh :showScrollbar="false" mode="listview" @scroll="scrollingEvt" @scrollDirection="onScrollDirection" style="flex:1" v-model="isfresh"
				v-model:model-bottom-status="bottomFresh" @refresh="load" @bottomRefresh="bottomLoad">
				<list-item>
					<text class="floatMenu" style="z-index:8">内悬浮菜单</text>
				</list-item>
				<list-item>
					<x-sheet>
						<x-text font-size="18" class=" text-weight-b mb-8">下拉刷新 PullRefresh</x-text>
						<x-text color="#999999">
							可以完全自主定义样式和刷新提示文字，请通过插槽配置，插槽数据已返回当前状态管理。
							可以自己定义宽和高放置在局部布局中实现局部下拉和触底刷新。
						</x-text>
					</x-sheet>
				</list-item>
				<list-item v-for="(item,index) in 8" :key="index" :type="1">
					<x-sheet height="250">
						<x-text>{{scrollDirection}}下拉查看下拉刷新,上拉查看触底刷新 - {{item}}</x-text>
					</x-sheet>
				</list-item>
			</x-pull-refresh>
		</view> -->
	</view>
</template>

<script>
	import { TABS_ITEM_INFO,TABS_ITEM } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			return {
				isfresh: false,
				bottomFresh: false,
				scrollDirection: 'down',
				menuPosition: -50,          // 菜单的初始位置
				lastScrollTop: 0,         // 上次滚动位置
				initialMenuTop: 0,        // 菜单初始位置
				isMenuFixed: false,       // 菜单是否固定
				scrootop:0,
				list3: [
					{ title: "全部" } as TABS_ITEM_INFO,
					{ title: "被禁用", disabled: true } as TABS_ITEM_INFO,
					{ title: "已删除" } as TABS_ITEM_INFO,
					{ title: "审核中" } as TABS_ITEM_INFO,
					{ title: "审核失败" } as TABS_ITEM_INFO,
					{ title: "售后中" } as TABS_ITEM_INFO,
					{ title: "已处理已处理" } as TABS_ITEM_INFO,
					{ title: "已处理2" } as TABS_ITEM_INFO,
					{ title: "已已处理处理3" } as TABS_ITEM_INFO,
					{ title: "已已处理处理4" } as TABS_ITEM_INFO,
					{ title: "已处理5" } as TABS_ITEM_INFO,
					{ title: "已处理8" } as TABS_ITEM_INFO,
				] as TABS_ITEM_INFO[],
			};
		},
		computed: {

		},
		methods: {
			scrollingEvt(evt : UniScrollEvent) {
				const scrollTop = evt.detail.scrollTop;
				const threshold = 50;  // 触发悬浮的阈值
				this.scrootop = scrollTop
				// 计算滚动方向
				const isScrollingUp = scrollTop < this.lastScrollTop;
				const isScrollingDown = scrollTop > this.lastScrollTop;
				if(this.lastScrollTop<=0||scrollTop<=0){
					this.menuPosition = -50;
					this.lastScrollTop = scrollTop;
					return;
				}
				if (isScrollingDown) {
					this.menuPosition = -50;
				} else if (isScrollingUp) {
					
					// 往上推
					if(this.lastScrollTop<=0){
						this.menuPosition = -50;
					}else{
						if(scrollTop<=threshold/2){
							this.menuPosition = -50;
						}else if(scrollTop>threshold/2&&scrollTop<threshold){
							this.menuPosition = this.lastScrollTop -threshold;
						}else{
							this.menuPosition = 0;
						}
						
					}
					
				}

				this.lastScrollTop = scrollTop;
			},
			onScrollDirection(type : string) {
				this.scrollDirection = type;
			},
			load() {

				let t = this;
				setTimeout(function () {
					t.isfresh = false;
				}, 2500);
			},
			bottomLoad() {
				let t = this;

				setTimeout(function () {
					t.bottomFresh = false;
				}, 2500);
			}
		}
	}
</script>

<style lang="scss">
	.floatMenu {
		top: 0px;
		left: 0px;
		background-color: rgb(5, 121, 255);
		z-index: 999;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: 50px;
	}
</style>
		
