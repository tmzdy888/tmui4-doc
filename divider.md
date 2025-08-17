
## 分割线 xDivider

***

#### 介绍

横和竖向，内容左，中，右。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-divider/x-divider.uvue**

#### 使用

<x-divider></x-divider>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| align | 对齐方式 | string | "center" |
| label | 文本 | string | "" |
| color | 线的颜色 | string | "#f5f5f5" |
| darkColor | 线的暗黑颜色，如果不提供取全局的borderDarkColor | string | "" |
| lineWidth | 线粗细度。 | string | "1" |
| height | 竖向时的高度 | string | "10" |
| labelColor | 文本颜色 | string | "#a2a2a2" |
| model | 线条样式 | string | "solid" |
| fontSize | 字体大小 | string | "11" |
| vertical | 是否是竖向 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认文本插槽。建议通过属性label填写，如果你有特殊要求可以 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/divider

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
			<x-text font-size="18" class=" text-weight-b ">分割线 Divider</x-text>
		</x-sheet>
		<x-sheet>
			<x-divider></x-divider>
			<x-divider class="mt-16" darkColor='error' color="error"></x-divider>
			<x-divider class="mt-16" darkColor='success' color="success"></x-divider>
		</x-sheet>
		<x-sheet>
			<x-divider label="标题测试"></x-divider>
		</x-sheet>
		<x-sheet>
			<x-divider align="right" label="标题测试"></x-divider>
		</x-sheet>
		<x-sheet>
			<x-divider align="left" label="左侧"></x-divider>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">竖向</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row ">
			<x-divider :vertical="true" height="50px"></x-divider>
			<x-divider :vertical="true" darkColor='success' color="success" height="50px" class="ml-16"></x-divider>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">

</style>
		
