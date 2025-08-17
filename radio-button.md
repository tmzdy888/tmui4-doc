
## 单选按钮组 xRadioButton

***

#### 介绍

类似单选导航按钮式或者叫分割选择按钮。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-radio-button/x-radio-button.uvue**

#### 使用

<x-radio-button></x-radio-button>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 数据 | RADIO_BUTTON[] | () : RADIO_BUTTON[] => {<br>    return [] as RADIO_BUTTON[]<br>} |
| modelValue | 当前选中的id值 | string | "" |
| bgColor | 背景 | string | "#f3f5f8" |
| darkBgColor | 暗黑时的背景，如果不提供读取页面暗黑背景 | string | "" |
| activeColor | 激活的按钮块背景 | string | "white" |
| darkActiveColor | 激活的按钮块暗黑背景，如果不提供inputDarkColor | string | "" |
| activeFontColor | 激活时的文字颜色,默认取全局主题色。 | string | "" |
| fontColor | 文字颜色，暗黑时取白色 | string | "#333333" |
| fontSize | 文字大小 | string | "16" |
| height | 按钮组高度 | string | "40" |
| space | 四周内间隙 | string | "2" |
| round | 圆角,空值时读取全局配置。 | string | "" |
| textStyle | 文本样式，可修改文字的样式。 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : string | 变换时触发。 |
| click | - | 点击按钮时触发. |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/radio-button

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
			<x-text font-size="18" class=" text-weight-b mb-8">单选按钮 RadioButton</x-text>
			<x-text  color="#999999" >样式可以随意定制。</x-text>
		</x-sheet>
		<x-sheet><x-radio-button text-style="font-weight:bold;" :list="list"></x-radio-button></x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">改变颜色和样式</x-text>
		</x-sheet>
		<x-sheet>
			<x-radio-button v-model="active" height="44" round="4" space="2" fontSize="16" bg-color="primary" font-color="#ffffff" active-font-color="primary" :list="list"></x-radio-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">为菜单加上图标</x-text>
		</x-sheet>
		<x-sheet>
			<x-radio-button round="32" space="1" font-size="12" v-model="active" :list="list2"></x-radio-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">当作图标控告选项</x-text>
		</x-sheet>
		<x-sheet>
			<view style="width: 200px;">
				<x-radio-button  round="6" space="2" font-size="18" v-model="active" :list="list3"></x-radio-button>
			</view>
		</x-sheet>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { RADIO_BUTTON } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			return {
				active:"2",
				list:[
					{id:"1",title:"苹果"} as RADIO_BUTTON,
					{id:"2",title:"香蕉"} as RADIO_BUTTON,
					{id:"3",title:"李子"} as RADIO_BUTTON,
					{id:"4",title:"蕉子李"} as RADIO_BUTTON,
				] as RADIO_BUTTON[],
				list2:[
					{id:"1",title:"系统设置",icon:"settings-4-fill"} as RADIO_BUTTON,
					{id:"2",title:"打印设置",icon:"printer-fill"} as RADIO_BUTTON,
					{id:"3",title:"订单管理",icon:"price-tag-2-fill"} as RADIO_BUTTON,
				] as RADIO_BUTTON[],
				list3:[
					{id:"1",title:"",icon:"settings-4-fill"} as RADIO_BUTTON,
					{id:"2",title:"",icon:"printer-fill"} as RADIO_BUTTON,
					{id:"3",title:"",icon:"price-tag-2-fill"} as RADIO_BUTTON,
				] as RADIO_BUTTON[]
			};
		}
	}
</script>

<style lang="scss">

</style>

		
