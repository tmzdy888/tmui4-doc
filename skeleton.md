
## 骨架屏 xSkeleton

***

#### 介绍

样式灵活多变。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-skeleton/x-skeleton.uvue**

#### 使用

<x-skeleton></x-skeleton>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| height | 高，单位允许%，auto,'数字',rpx,px | string | '12' |
| width | 宽，单位允许%，auto,'数字',rpx,px | string | "auto" |
| color | 背景颜色 | string | '#e4e4e4' |
| darkColor | 暗黑背景颜色 | string | '#323232' |
| round | 圆角 | string | "3" |
| duration | 动画间隔 | string | '900ms' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/skeleton

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
			<x-text font-size="18" class="text-weight-b mb-8">骨架屏 xSkeleton</x-text>
			<x-text color="#999999">骨架屏就是一个单view，允许你自由组合骨架效果，建议单独使用本组件自己封装一个想要的骨架效果。</x-text>
			<x-text color="#999999">由于每个人的app占位样式不一样，我认为这种非常自由式的组合非常符合扩展。</x-text>
		</x-sheet>
		<x-sheet>
			<x-skeleton></x-skeleton>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class="text-weight-b ">动手组合一个骨架</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-row">
				<x-skeleton width="50" height="50" round="50"></x-skeleton>
				<view class="flex-1 ml-8">
					<x-skeleton class="mb-8" v-for="item in 6" :key="item"></x-skeleton>
				</view>
			</view>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class="text-weight-b ">再组合一个吧</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-row flex-row-center-between">
				<view v-for="item1 in 3" :key="item1" style="width:30%">
					<x-skeleton height="50"></x-skeleton>
					<view class="mt-8">
						<x-skeleton height="10" class="mb-8" v-for="item in 3" :key="item"></x-skeleton>
					</view>
				</view>
			</view>
		</x-sheet>
		<view style="height:50px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>

</style>
		
