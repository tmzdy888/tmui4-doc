
## 进度条 xProgress

***

#### 介绍

使用，允许设置min,max值，如果你的双向绑定的vale值超过min,max的合法值，将会被转换为正确值。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-progress/x-progress.uvue**

#### 使用

<x-progress></x-progress>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| min | 最小值 | number | 0 |
| max | 最大值 | number | 100 |
| modelValue | 当前的值<br>等同v-model="" | number | 0 |
| color | 进度条激活时的颜色<br>为空时，取全局配置的值 | string | "" |
| bgColor | 背景颜色 | string | "info" |
| darkBgColor | 暗黑背景颜色，如果不设置取inputDarkColor | string | "" |
| showLabel | 是否显示进度条上的label文本 | boolean | false |
| labelColor | 文本颜色 | string | "white" |
| labelFontSize | 文本文字大小 | string | "10" |
| size | 进度条的大小 | string | "4" |
| round | 圆角。<br>为空值时，取全局的统一值 | string | "" |
| duration | 动画持续的时间 | number | 350 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| update:modelValue | - | 等同v-model=""<br>如果你的双向绑定的vale值超过min,max的合法值，将会被转换为正确值。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认标签文本插槽，需要设置:showLabel="true" | **value** : number<br>**value** : number<br>**percentage** : number<br>**percentage** : number<br> |
| right | 右插槽 | **value** : number<br>**value** : number<br>**percentage** : number<br>**percentage** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/progress

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
			<x-text font-size="18" class=" text-weight-b mb-8">进度条 Progress</x-text>
			<x-text color="#999999" >
				主题，圆角风格可全局统一配置
			</x-text>
		</x-sheet>
		
		<x-sheet>
			<x-progress v-model="val" class="mb-12"></x-progress>
			<x-progress v-model="val" class="mb-12" color="danger"></x-progress>
			<x-progress v-model="val" color="error"></x-progress>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">显示label</x-text>
		</x-sheet>
		<x-sheet>
			<x-progress v-model="val" class="mb-12" size="12" :show-label="true"></x-progress>
			<x-progress v-model="val" size="12" :show-label="true" color="danger"></x-progress>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">设置圆角</x-text>
		</x-sheet>
		<x-sheet>
			<x-progress v-model="val" class="mb-12" round="0"></x-progress>
			<view>
				<x-progress v-model="val" round="0" color="error"></x-progress>
			</view>
		</x-sheet>
		
		<x-sheet style="display: flex;flex-direction: row;">
			<x-button class="mr-32"  @click="val = val+10">增加</x-button>
			<x-button color="error" @click="val = val-10">减少</x-button>
		</x-sheet>
		
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">设置右插槽，显示内容</x-text>
		</x-sheet>
		<x-sheet >
			<x-progress :model-value="50" round="0" :max="150">
				<template #right="{percentage,value}">
					<x-text font-size="12" class="ml-12">{{percentage}}%,{{value}}元</x-text>
				</template>
			</x-progress>
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
				val:50,
			};
		},
		onLoad() {
			
		}
	}
</script>

<style lang="scss">

</style>

		
