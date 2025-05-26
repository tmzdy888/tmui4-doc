
## 浮球 xFloatButton

***

#### 介绍

可以左右四个角定位放置，自动靠边吸咐，也可自由拖动放置。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-float-button/x-float-button.uvue**

#### 使用

<x-float-button></x-float-button>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| duration |  | number | 650 |
| threshold | 松开后，如果是吸附adsorption为true的话，吸附在两边的位置时的距离边界的距离。<br>单位为px,左右的安全距离. | number | 12 |
| thresholdTop | 单位为px,顶部的安全距离 | number | 0 |
| thresholdBottom | 单位为px,底部的安全距离 | number | 12 |
| round | 圆角,空值时取全局的drawr圆角。 | string | "64" |
| offset | 自己定义位置:以可视范围内的左上角算起。如何自己定义位置时<br>需要计算屏幕坐标时请使用uni.getWindowInfo()<br>来获取可视屏幕的宽和高定位你自己需要的自由位置<br>可以v-model:offset="[x,y]"来动态更改其位置。<br>我预置了以下几种常见模式：<br>[-1,-1]会在右下角。会让出threshold边界距离<br>[-2,-2]会在左下角。会让出threshold边界距离<br>[-3,-3]会在左上角。会让出threshold边界距离<br>[-4,-4]会在右上角。会让出threshold边界距离<br>[-5,-5]会在底部居中。会让出threshold边界距离 | number[] | () : number[] => [-1, -1] as number[] |
| bgColor | 背景,支持渐变值如:linear-gradient(to left, #FFED46, #FF7EC7)<br>默认空值，取全局主题值。 | string | "" |
| width | 宽 | string | '50px' |
| height | 高 | string | '50px' |
| adsorption | 是否开启吸附在两边。<br>如果设置为false,可以自由拖动在屏幕上。 | boolean | true |
| disabled | 是否禁止拖动。 | boolean | false |
| zIndex | 层级 | number | 87 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击组件时触发 |
| longpress | - | 长按组件时触发大于500ms |
| change | **postion** : number[] | 当前的位置，等同v-model:offset |
| update:offset | - | 动态修改当前的位置<br>等同v-model:offset具体见offset属性那。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 请在插槽内自由布局你的样式及功能块。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/float-button

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
			<x-text font-size="18" class=" text-weight-b mb-8">浮球 FloatButton</x-text>
			<x-text color="#999999">
				提供自由拖动，吸附功能，预设四个位置，请参阅文档。
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">双向绑定位置</x-text>
			<x-text color="#999999">
				请拖动橙色自由球：{{offsets.join(",")}}
			</x-text>
		</x-sheet>
		<x-float-button>
			<view class="flex flex-center" style="width:100%;height:100%">
				<x-icon color="white" font-size="30" name="phone-fill"></x-icon>
			</view>
		</x-float-button>
		<x-float-button bg-color="success" :offset="[-2,-2]">
			<view class="flex flex-center" style="width:100%;height:100%">
				<x-icon color="white" font-size="30" name="bluetooth-line"></x-icon>
			</view>
		</x-float-button>
		<x-float-button :disabled="true" bg-color="linear-gradient(to left, #FFED46, #FF7EC7)" :offset="[-5,-5]">
			<view class="flex flex-center" style="width:100%;height:100%">
				<x-icon color="white" font-size="30" name="forbid-line"></x-icon>
			</view>
		</x-float-button>
		<x-float-button @click="onclik" bg-color="error" :offset="[-3,-3]">
			<view class="flex flex-center" style="width:100%;height:100%">
				<x-icon color="white" font-size="30" name="add-line"></x-icon>
			</view>
		</x-float-button>
		<x-float-button :adsorption="false" bg-color="danger" :offset="[-4, -4]" @change="moveChange">
			<view class="flex flex-center" style="width:100%;height:100%">
				<x-icon color="white" font-size="30" name="sketching"></x-icon>
			</view>
		</x-float-button>
		
		<view style="height:1500px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				offsets: [] as number[]
			};
		},
		methods:{
			onclik(){
				console.log('click')
			},
			moveChange(xy:number[]){
				// this.offsets = xy;
			}
		}
	}
</script>

<style lang="scss">

</style>
		
