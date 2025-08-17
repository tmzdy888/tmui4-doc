
## 步进器 xStepper

***

#### 介绍

可整数，小数

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-stepper/x-stepper.uvue**

#### 使用

<x-stepper></x-stepper>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前值，可v-model | number | 0 |
| max | 最大值 | number | 100 |
| width | 组件宽 | string | "auto" |
| min | 最小值 | number | 0 |
| autoHideBtn | 开启后自动隐藏限制的按钮<br>最小时隐藏减号按钮 | boolean | false |
| disabled | 是否禁用整个组件 | boolean | false |
| disabledInput | 是否禁用输入框 | boolean | false |
| step | 步进值 | number | 1 |
| decimalLen | 如果进步值是小数位需要设置此值 | number | 0 |
| btnColor | 按钮的颜色 | string | "info" |
| darkBtnColor | 按钮的暗黑颜色<br>空值读取全局的Input暗黑背景色 | string | "" |
| bgColor | 输入框的背景色 | string | "info" |
| inputStyle | 输入框的自定样式<br>可以写背景字体等样式 | string | '' |
| darkBgColor | 输入框的暗黑背景色<br>空值读取全局的Input暗黑背景色 | string | "" |
| btnWidth | 按钮的宽 | string | "36" |
| height | 输入框及按钮的高 | string | "36" |
| round | 按钮的圆角。 | string | "4" |
| splitBtn | 是否按钮与输入框独立开来<br>不和输入框粘一起。 | boolean | false |
| btnFontColor | 按钮文本颜色，暗黑时取白色 | string | "#333333" |
| fontColor | 文本颜色,暗黑时取白色 | string | "#333333" |
| fontSize | 文本文字大小 | string | "14" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **** : number | 输入值或者点击按钮时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/stepper

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
			<x-text font-size="18" class=" text-weight-b mb-8">步进器 Stepper</x-text>
			<x-text color="#999999" >可整数，小数步进</x-text>
		</x-sheet>
		
		<x-sheet class="flex flex-row">
			<x-stepper width="110" ></x-stepper>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">达到界定值时自动隐藏按钮</x-text>
		</x-sheet>
		<x-sheet class="">
			<x-stepper :autoHideBtn="true" :max="5" width="110" ></x-stepper>
			<view class="py-10"></view>
			<x-stepper :autoHideBtn="true"  darkBtnColor="primary" btn-color="primary" btn-font-color="white" font-color="primary" :splitBtn="true" :model-value="0" width="110" ></x-stepper>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">小数点</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row">
			<x-stepper :decimal-len="1" :step="0.1" width="110" ></x-stepper>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">圆角类型</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row">
			<x-stepper :splitBtn="true" :model-value="50" width="110" ></x-stepper>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">更换颜色</x-text>
		</x-sheet>
		<x-sheet class="">
			<x-stepper darkBtnColor="primary" btn-color="primary" btn-font-color="white" font-color="primary" :splitBtn="true" :model-value="10" width="110" ></x-stepper>
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
		
