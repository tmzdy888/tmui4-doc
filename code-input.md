
## 验证码输入框 xCodeInput

***

#### 介绍

验证码输入框，截止4.22安卓会自动拉起系统键盘，ios无法使用系统键盘。目前仅配合我的组件键盘可以全局兼容。已向官方返回Input的bug

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-code-input/x-code-input.uvue**

#### 使用

<x-code-input></x-code-input>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| autoFocus | 进入时自动获取焦点，并弹出系统自带的键盘(需要useSysKeyborad=true)。 | boolean | false |
| useSysKeyborad | 是否使用系统自带的键盘。，如果为false你需要自行配置输入键盘<br>比如使用我的keyborad键盘组件。 | boolean | true |
| modelValue | 当前输入的值 | string | "" |
| maxlength | 最大长度 | number | 4 |
| gutter | 间距 | string | "8" |
| width | 验证码框的宽 | string | "50" |
| height | 验证码框的高 | string | "50" |
| fontColor | 当前输入项激活时的文字颜色同时也是高亮时的背景色。<br>默认取全局主题 | string | "" |
| darkFontColor | 暗黑时的主题色，不填写等同fontColor | string | "" |
| fontSize | 文字大小 | string | "21" |
| round | 圆角 | string | "8" |
| bgColor | skin = fill时的背景 | string | "#f0f0f0" |
| darkBgColor | skin = fill时的暗黑背景 | string | "#272727" |
| borderColor | skin = outline时的边线颜色 | string | "" |
| darkBorderColor | skin = outline时的暗黑边线颜色 | string | "" |
| unBorderColor | skin = outline时的边线颜色[非激活时] | string | "#e3e3e3" |
| unDarkBorderColor | skin = outline时的暗黑边线颜色[非激活时] | string | "#2c2b2c" |
| skin |  | string | "outline" |
| placeShape | 待输入时的占位形状<br>line线型<br>round圆形<br>空值表示不需要占位符号 | string | "round" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击框时触发 |
| confirm | - | 输入长度等于指定长度时触发 |
| change | - | 变动时触发 |
| update:modelValue | - | 等同vmodel，可与我的keyborad键盘配合使用。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/code-input

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
			<x-text font-size="18" class=" text-weight-b mb-8">验证码输入 xCodeInput</x-text>
			<x-text  color="#999999" >提供了两种方式，自带输入框输入，以及配合我的keyborad键盘。</x-text>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">自动拉起系统键盘</x-text>
			<x-code-input @confirm="ok" gutter="4" :maxlength="6" width="45" :autoFocus="true"></x-code-input>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-12">关闭系统键盘使用组件键盘</x-text>
			<x-code-input place-shape="line" @click="showkey=true" @confirm="showkey = false" v-model="value" :useSysKeyborad="false" skin="fill"></x-code-input>
		</x-sheet>
		
		
		
		<x-keyboard-number :max-len="4" v-model:modelShow="showkey" v-model="value"></x-keyboard-number>
		<view style="height: 400px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				value:"",
				showkey:false
			}
		},
		methods: {
			ok(){
				uni.showToast({
					title:"验证成功",
					mask:true
				})
			}
		}
	}
</script>

<style>

</style>

		
