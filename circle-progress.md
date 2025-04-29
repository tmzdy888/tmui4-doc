
## 圆形进度环 xCircleProgress

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

**@/uni_modules/tmx-ui/components/x-circle-progress/x-circle-progress.uvue**

#### 使用

<x-circle-progress></x-circle-progress>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| size | 可以是px,rpx,纯数字符串。默认以rpx为单位。 | string | "60" |
| lineWidth | 可以是px,rpx,纯数字符串。默认以rpx为单位。 | string | "3" |
| color | 圆环背景颜色,暗黑时取inputDarkColor | string | "info" |
| activeColor | 当前激活的进度颜色，空值读取全局值。 | string | "" |
| modelValue | 当前的值,以百分比为值0-100<br>等同v-model=""<br>您直接:model-value="xx"也是一样可以改变值。 | number | 30 |
| labelFontSize | 中间文本字号 | string | "16" |
| labelUnit | 数字的单位。 | string | "%" |
| showLabel | 是否显示中间文本。 | boolean | false |
| labelColor | 中间文本的颜色。 | string | "#333333" |
| darkLabelColor | 中间文本的暗黑颜色。空值是取白色 | string | "" |
| duration | 进度条动画的时间,单位ms。<br>请不要设置的过慢，否则会有停顿感。 | number | 300 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认文本插槽 | **current** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/circle-progress

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
			<x-text font-size="18" class=" text-weight-b mb-8">圆形进度环 xCircleProgress</x-text>
			<x-text  color="#999999" >样式灵活多变。性能好。</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-row flex-row-center-center">
				<x-circle-progress :model-value="testValue"></x-circle-progress>
				<x-circle-progress lineWidth="6" activeColor="success" class="mx-16"
					:model-value="testValue"></x-circle-progress>
				<x-circle-progress class="mr-32" lineWidth="10" color="error" activeColor="danger"
					:model-value="testValue"></x-circle-progress>
					<x-circle-progress activeColor="warn" :model-value="testValue"></x-circle-progress>
			</view>
			<view class="flex flex-row mt-32  flex-row-center-center">
				<x-button @click="add">增加</x-button>
				<x-button color="error" class="mx-16" @click="sur">减少</x-button>
			</view>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">尺寸，显示文本</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-row flex-row-center-center">
				<x-circle-progress lineWidth="20" size="100" :show-label="true"
					:model-value="testValue"></x-circle-progress>
				<x-circle-progress lineWidth="20" class="ml-32" size="100" :show-label="true" color="error"
					activeColor="danger" :model-value="testValue"></x-circle-progress>
			</view>

		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				testValue: 64
			};
		},
		methods: {
			add() {
				let abs = this.testValue + 10;
				if (abs > 100) {
					abs = 100
				}
				this.testValue = abs
			},
			sur() {
				let abs = this.testValue - 10;
				if (abs < 0) {
					abs = 0
				}
				this.testValue = abs
			}
		},
	}
</script>

<style lang="scss">

</style>
		
