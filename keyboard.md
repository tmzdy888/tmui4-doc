
## 密码键盘 xKeyboard

***

#### 介绍

密码键盘，如果你只是要单纯的数字键盘见x-keyboard-number

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-keyboard/x-keyboard.uvue**

#### 使用

<x-keyboard></x-keyboard>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前输入的值 | string | "" |
| maxLen | 最大长度 | number | 9 |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题,默认：安全键盘请放心输入 | string | "" |
| color | 主按钮色，空值取全局主题 | string | "" |
| btnColor | 按钮背景 | string | 'white' |
| bgColor | 键盘背景 | string | 'info' |
| fontColor | 文字颜色 | string | '#3b3b3b' |
| hold | 点击确认是否保持键盘不收起 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **** : undefined | 值变化时触发 |
| update:modelShow | - | 变量控制打开状态<br>等同v-model:model-show |
| confirm | - | 点击确认时触发 |
| cancel | - | 关闭取消时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽,默认触发打开选择器。你的默认布局可以放置在这里。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/keyboard

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
		<x-text font-size="18" class=" text-weight-b mb-8">数字键盘 KeyboardNumber</x-text>
		<x-text color="#999999" >允许小数点，整数，最大长度的控制,可定制性强</x-text>
		
		<x-sheet dark-color="#333" :margin="['0','16']" color="#f5f5f5">
			<x-text>输入的值：{{price}}</x-text>
		</x-sheet>
		<x-keyboard-number :max="100" v-model="price">
			<x-button :block="true">打开默认键盘(控制最大100)</x-button>
		</x-keyboard-number>
		<x-keyboard-number :digit="false" :max="100" v-model="price">
			<x-button class="mt-20" :block="true">整数键盘</x-button>
		</x-keyboard-number>
		
	</x-sheet>
	

	<x-sheet>
		<x-text font-size="18" class=" text-weight-b mb-24">通过属性定制不同样式键盘</x-text>
		<x-keyboard-number btn-color="white" v-model="price">
			<x-button  class="mb-24" color="info" darkColor="#333" :block="true">打开白色键盘</x-button>
		</x-keyboard-number>
		<x-keyboard-number bg-color="#111111" btn-color="#232323" font-color="#f0f0f0" v-model="price">
			<x-button color='success' :block="true">打开黑色键盘</x-button>
		</x-keyboard-number>
	</x-sheet>
	
	<x-sheet>
		<x-text font-size="18" class=" text-weight-b mb-24">密码键盘</x-text>
		
		<x-keyboard v-model="password">
			<x-button darkColor="#333" color="info" :block="true">打开密码键盘</x-button>
		</x-keyboard>
		
	</x-sheet>

	
	<x-sheet>
		<x-text font-size="18" class=" text-weight-b mb-24">身份证键盘</x-text>
		<x-keyboard-idcard>
			<x-button darkColor="#333" :block="true">打开身份证键盘</x-button>
		</x-keyboard-idcard>
	</x-sheet>
	
	<x-sheet>
		<x-text font-size="18" class=" text-weight-b mb-24">车牌键盘</x-text>
		<x-keyboard-car>
			<x-button darkColor="#333" :block="true">打开车牌键盘</x-button>
		</x-keyboard-car>
	</x-sheet>
	
	
	<view style="height: 50px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				price:'',
				password:''
			};
		}
	}
</script>

<style lang="scss">

</style>

		
