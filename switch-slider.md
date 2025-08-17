
## 左滑菜单 xSwitchSlider

***

#### 介绍

常用于对话聊天，订单列表等一些隐藏式按钮设计场景。如果子菜单无法定宽或者被挤夺请写style:flex-shrink: 0;避免。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-switch-slider/x-switch-slider.uvue**

#### 使用

<x-switch-slider></x-switch-slider>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| custonmStyle | 被拖动层的自定义样式 | string | "" |
| custonmMenuStyle | 菜单容器层自定义样式 | string | "" |
| width | 宽度 | string | "100%" |
| height | 高度，单位随意 | string | "50" |
| disabled | 是否禁用 | boolean | false |
| threshold | 当滑动时小于此值，会回弹到原位。 | number | 15 |
| duration | 当打开或者松开时的动画时间 | number | 450 |
| status | 当前打开状态 | boolean | false |
| borderColor | 下边线的颜色 | string | "#f5f5f5" |
| borderDarkColor | 下边线暗黑的颜色,如果不提供,取全局borderDarkColor | string | "" |
| eventNone | 让拖动层内容失去响应，会导致顶层里面的内容无法触发事件响应<br>但好处是：拖动更流畅，没有断断续续。请自行根据场景打开和关闭。<br>false关闭让内容响应事件，true让内容失去响应。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| disabledScrollChange | - | 提供这个函数是因为如果你把此组件套在了scroll中<br>你在ios端根本 无法去阻止 底部的scrollview的滚动，这大概官方是解决不了的<br>冒泡 事件。我只能绕开。<br>此函数会发现是否禁用你外部滚动的指示。 |
| click | - | 活动区域被点击时触发。 |
| open | - | 打开菜单时触发 |
| close | - | 关闭时触发 |
| start | - | 触发时触发 |
| end | - | 触摸结束时触发 |
| move | - | 触摸中时触发 |
| update:status | - | 等同v-model:status * |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，你的顶层布局可以在这里。 由于vue 的diff机制,去掉5ms的延迟。内容层会失去事件响应。请通过组件的@click | - |
| menu | 菜单插槽 | **status** : boolean<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| open | - | - | 打开 |
| close | - | - | 关闭 |


#### 示例页面路径

/pages/fankui/switch-slider

#### 示例源码

<template>
	<!-- #ifdef APP -->
	<scroll-view style="flex:1">
	<!-- #endif -->
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">左滑菜单 SwitchSlider</x-text>
			<x-text color="#999999">
				通过插槽可完全自定义布局，自由度非常高。如果子菜单无法定宽或者被挤夺请写style:flex-shrink: 0;避免。
			</x-text>
		</x-sheet>
		<x-sheet :padding="['0px']">
			<x-switch-slider
			:status="item.getBoolean('opened')"
			@open="onopen(index)"
			@close="onclose(index)"
			height="64" @disabledScrollChange="disablechange" @click="onclick(index)"
				v-for="(item,index) in testList" :key="index" :disabled="item.getBoolean('disabled')">
				<x-cell leftSize='40' min-height="64" :showBottomBorder="false" :card="false"
					:title="item.getString('title')" :desc="item.getString('subtext')" icon='F264'>
					
					<template #avatar>
						<x-sheet :margin="['0']" :round="['8']" :padding="['0']" color="primary" width="100%" height="100%" class="felx flex-center">
							<x-icon font-size="24" code="F264" color="white"></x-icon>
						</x-sheet>
					</template>
					
				</x-cell>
				<template #menu>
					<view class="flex flex-row flex-row-center-end" style="height: 100%;">
						<view @click="share" class="flex flex-row flex-row-center-center"
							style="width:110px;background:black;height: 100%;">
							<text class="text-white">分享</text>
						</view>
						<view @click="remvoe" class="flex flex-row flex-row-center-center"
							style="width:110px;background:red;height: 100%;">
							<text class="text-white">删除</text>
						</view>
					</view>
				</template>
			</x-switch-slider>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">双向绑定</x-text>
		</x-sheet>

		<x-sheet :padding="['0px']" >
			<x-switch-slider
			v-model:status="(showLeft as boolean)"
			height="64"
			>
				<x-sheet :round="['0']" :margin="['0']" :padding="['24','0']" height="64" class="flex flex-row flex-row-center-start">
					<x-text>
						双向绑定{{showLeft}}
					</x-text>
					
				</x-sheet>
				
				<template #menu>
					<view class="flex flex-row flex-row-center-end" style="height: 100%;">
						<view class="flex flex-row flex-row-center-center"
							style="width:110px;background:black;height: 100%;">
							<text class="text-white">分享</text>
						</view>
						<view class="flex flex-row flex-row-center-center"
							style="width:110px;background:red;height: 100%;">
							<text class="text-white">删除</text>
						</view>
					</view>
				</template>
			</x-switch-slider>
		</x-sheet>

		<view style="height: 1500px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				showLeft:false,
				disabledScoll: false,
				testList: [] as UTSJSONObject[]
			};
		},
		beforeMount() {
			for (let i = 0; i < 6; i++) {
				this.testList.push({
					id: Math.random().toString(16).substring(0, 12),
					index: i,
					disabled: i == 1,
					title: i == 1 ? "被禁用" : ("我是对话标题+" + i.toString()),
					subtext: "演示手动管理关闭状态",
					opened:false
				} as UTSJSONObject)
			}

		},
		onLoad() {

		},
		methods: {

			onopen(index:number){
				let oldlist = this.testList.slice(0)
				oldlist = oldlist.map((el:UTSJSONObject,from:number):UTSJSONObject =>{
					if(from!=index){
						el.set("opened",false)
					}else{
						el.set("opened",true)
					}
					return el;
				})
				this.testList = oldlist.slice(0)
			},
			onclose(index:number){
				
			},
			remvoe() {
				console.log('remove')
			},
			share() {
				console.log('share')
			},
			onclick(index : number) {
				uni.showToast({ title: "你点击了：" + index.toString() })
			},
			disablechange(disabled : boolean) {
				this.disabledScoll = disabled;
			}
		}
	}
</script>

<style lang="scss">

</style>
		
