
## 水印 xWatermark

***

#### 介绍

适合需要保密，版权的页面使用，可自行调整透明度，颜色值等，方便打标签。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-watermark/x-watermark.uvue**

#### 使用

<x-watermark></x-watermark>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| label | 水印文字 | string | "XUI DESIGN" |
| color | 水印颜色 | string | "rgba(0,0,0,0.05)" |
| darkColor | 暗黑时的水印颜色 | string | "rgba(255,255,255,0.05)" |
| fontSize | 文字大小 | string | "18" |
| gap | 渲染的水印之间的间隙，单位px | number | 40 |



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

/pages/zhanshi/watermark

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
			<x-text font-size="18" class=" text-weight-b mb-8">水印 Watermark</x-text>
			<x-text color="#999999" >可以控制，颜色，内容，但不支持图片。和uniapp x不支持图片有关系。</x-text>
		</x-sheet>

		<x-watermark :label="label"></x-watermark>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				label: "XUI DESIGN"
			};
		}
	}
</script>

<style lang="scss">

</style>
		
