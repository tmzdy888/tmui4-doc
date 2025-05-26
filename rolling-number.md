
## 数字翻滚 xRollingNumber

***

#### 介绍

是否小数点，取决与你的的endVal目标值，如果它带小数点，那动画也是相应带小数点。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-rolling-number/x-rolling-number.uvue**

#### 使用

<x-rolling-number></x-rolling-number>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| fontSize | 文字大小 | string | "32" |
| fontColor | 文字颜色 | string | "black" |
| darkFontColor | 暗黑时的文字颜色，如果为空取白 | string | "" |
| startVal | 起始值 | number | 0 |
| endVal | 目标值（当前需要显示的值） | number | 0 |
| duration | 动画速率。控制翻滚动的动画效果。 | number | 600 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | **value** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/rolling-number

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
			<x-text font-size="18" class=" text-weight-b mb-8">数字翻滚 xRollingNumber</x-text>
			<x-text color="#999999" >
				是否小数点，取决与你的的endVal目标值，如果它带小数点，那动画也是相应带小数点。
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">小数</x-text>
			<x-rolling-number :endVal="endVal"></x-rolling-number>
			<x-button class="mt-32" :block="true" @click="endVal=endVal+12">增加+12</x-button>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">整数,让动画时间加长点{{endVal2}}</x-text>
			<x-rolling-number :endVal="endVal2" :duration="1100"></x-rolling-number>
			<x-button class="mt-32" :block="true" @click="endVal2=endVal2+122">增加+122</x-button>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {

		data() {
			return {
				endVal:2023.2,
				endVal2:1998,
			};
		},
		onLoad() {
			
		}
	}
</script>

<style lang="scss">

</style>

		
