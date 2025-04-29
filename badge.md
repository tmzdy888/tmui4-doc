
## 角标 xBadge

***

#### 介绍

角标

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-badge/x-badge.uvue**

#### 使用

<x-badge></x-badge>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| fontSize | 文字大小，可数字或者带单位 | string | "9" |
| bgColor | 背景颜色，合法和颜色值及主题名称 | string | "error" |
| fontColor | 文字颜色，合法和颜色值及主题名称 | string | "white" |
| dot | 是否显示为点，优先级小于count,label | boolean | true |
| count | 是否显示为文本数字，优先级小于label | number | 0 |
| maxCount | 为数字时大于此值显示+号 | number | 99 |
| label | 是否显示为文本，优先级最大 | string | "" |
| position | 位置 | string | "right" |
| offset | 偏移 | number[] | () : number[] => [0, 0] as number[] |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认内容区域,你的正常内容放置在标签内 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/badge

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
			<x-text font-size="18" class=" text-weight-b mb-8">角标 Badge</x-text>
			<x-text color="#999999" >
				另外：安卓布局需要你使用flex布局，并且内容层需要有宽度值防止让角标的内容断行
			</x-text>
		</x-sheet>
		<x-sheet  class="flex flex-row flex-row-center-center flex-wrap ">

			<view class="flex-1 flex flex-row flex-row-center-center ">
				<x-badge >
					<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
				</x-badge>
			</view>
			<view class="flex-1 flex flex-row flex-row-center-center">
				<x-badge bg-color="danger" :count="1" >
					<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
				</x-badge>
			</view>
			
			<view class="flex-1 flex flex-row flex-row-center-center">
				<x-badge bg-color="success" label="HOT" >
					<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
				</x-badge>
			</view>
			<view  class="flex-1 flex flex-row flex-row-center-center">
				<x-badge bg-color="primary" :count="150" >
					<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
				</x-badge>
				
			</view>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">左上，右上，左下，右下，上中，下中</x-text>
			<x-text color="#999999" >
				另外：安卓布局需要你使用flex布局，并且内容层需要有宽度值防止让角标的内容断行
			</x-text>
		</x-sheet>

		<x-sheet class="flex flex-row flex-row-center-center flex-wrap ">

			<x-badge position="left" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
			<x-badge position="right" bg-color="danger" :count="36" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
			<x-badge position="bottomLeft" bg-color="success" label="HOT" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
			<x-badge position="bottomRight" bg-color="primary" :count="150" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
			<x-badge position="top" bg-color="success" label="HOT" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
			<x-badge position="bottom" bg-color="error" :count="150" >
				<view style="width: 100rpx;height:100rpx;background: #f3f3f3;"></view>
			</x-badge>
		</x-sheet>

		<x-sheet >
			<x-text font-size="18" class=" text-weight-b ">应用在其它组件上</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-center">

			<x-badge label="50%SALE" >
				<x-button size="normal">按钮</x-button>
			</x-badge>
			<x-badge label="HOT" >
				<view style="width:64rpx">
					<x-icon name="movie-2-fill"></x-icon>
				</view>
			</x-badge>
			<x-badge>
				<view style="width:42rpx">
					<x-icon name="settings-5-fill"></x-icon>
				</view>
			</x-badge>

		</x-sheet>

		<view class="py-32"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad(){
		}
	}
</script>

<style lang="scss">

</style>
		
