
## 手势库 xFinger

***

#### 介绍

多方向的手势库,包括旋转，捏合，轻扫，双击等手势

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-finger/x-finger.uvue**

#### 使用

<x-finger></x-finger>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| swiperDiff | 滑动多长距离，识别并触发滑动的方向 | number | 50 |
| dbClickDiff | 定义双击的时间间隔触发时机 | number | 300 |
| clickDiff | 定义单击click的时间间隔触发时机 | number | 50 |
| longDiff | 定义长按的时间间隔触发时机 | number | 800 |
| disabled | 是否禁用 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| start | - | 触摸开始 |
| move | **evt** : object | 触摸移动时触发 |
| end | **evt** : object | 触摸结束 |
| cancel | **evt** : object | 触摸结束 |
| doubleClick | - | doubleClick |
| longPress | - | 长按事件 |
| swiper | **evt** : object | 滑动时触发 |
| click | **evt** : object | 单击 |
| pinch | **evt** : object**** : undefined | 缩放事件 |
| rotate | **evt** : object**** : undefined | 旋转事件 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | **x** : number<br>**x** : number<br>**x** : string<br>**y** : number<br>**y** : number<br>**y** : string<br>**type** : number<br>**type** : number<br>**type** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/finger

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
			<x-text font-size="18" class=" text-weight-b mb-8">手势库 Finger</x-text>
			<x-text color="#999999" >
				提供高性能手势判断事件，自定义强，可自定义，长按，单击，双击,的时长及间隔。也可自定义滑动方向的间距判断。
			</x-text>
		</x-sheet>
		
		
		<view class="white round-10 pa-12 mx-16 mb-12 ">
			<x-finger @swiper="mSwiper" @start="mStart" @move="mMove" @end="mEnd" @click="mClick"
				@doubleClick="mdbClick" @longPress="mlongClick" @rotate="rotate" @pinch="pinch">
			
				<template v-slot:default="{x,y,type}">
					<view style="width:100%;height:100px;background-color: rgba(0, 0, 0, 0.1);">
					
					</view>
				</template>
			</x-finger>
			<text class="mt-12">
				其它事件：{{diff}}
			</text>

			<text>
				滑动事件：{{swiperDiff}}
			</text>
			<text>
				缩放：{{pinth}}
				旋转：{{rotaValue}}
			</text>
		</view>


		<view class="white round-10 pa-12 mx-16 mb-12 ">
			<x-finger>
				<template v-slot:default="{x,y,type}">
					<view :style="{height:'200px',width:'100%',background: 'green',left:x+'px',top:y+'px'}">
						<text>
							请在此滑动,查看被移动的信息
							X:{{x}}
						</text>
						<text>
							请在此滑动,查看被移动的信息
							Y:{{y}}
						</text>
					</view>
				</template>
			</x-finger>
		</view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="uts">
	// import {xOverflay} from "../../uni_modules/x-core"
	export default {
		data() {
			return {
				diff: "",
				swiperDiff: "",
				pinth: 0,
				rotaValue: 0,
				_x: 0,
				_y: 0,
			};
		},
		onLoad() {
		},
		methods: {
			mSwiper(evt : UTSJSONObject) {
				this.swiperDiff = JSON.stringify(evt)
			},
			mStart(evt : UTSJSONObject) {
	
				this.diff = JSON.stringify(evt)
			},
			mMove(evt : UTSJSONObject) {
				this.diff = JSON.stringify(evt)
			},
			mEnd(evt : UTSJSONObject) {
				this.diff = JSON.stringify(evt)
			},
			mClick(evt : UTSJSONObject) {
				this.diff = JSON.stringify(evt)
			},
			mdbClick(evt : UTSJSONObject) {
				this.diff = JSON.stringify(evt)
			},
			mlongClick(evt : UTSJSONObject) {
				this.diff = JSON.stringify(evt)
			},
			pinch(evt : UTSJSONObject) {
				this.pinth = evt.getNumber('scale')!
			},
			rotate(evt : UTSJSONObject) {
				this.rotaValue = evt.getNumber('angle')!
			},
		}
	}
</script>

<style lang="scss" scoped>

</style>
		
