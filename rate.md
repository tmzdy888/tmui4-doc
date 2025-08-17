
## 评分 xRate

***

#### 介绍

评分组件，只读和禁用等属性

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-rate/x-rate.uvue**

#### 使用

<x-rate></x-rate>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前分值，等同v-model | number | 0 |
| count | 最大评分数量 | number | 5 |
| color | 选中的颜色，默认空值取全局值 | string | "" |
| unColor | 未选中的颜色 | string | "#cacaca" |
| darkUnColor | 未选中的暗黑背景颜色<br>空时取InputDark表单颜色 | string | "#8b8b8b" |
| size | 尺寸 | string | "21" |
| space | 间隙 | string | "4" |
| icon | 选中的图标 | string | "star-fill" |
| unicon | 未选中的图标 | string | "star-line" |
| readonly | 是否只读状态 | boolean | false |
| disabled | 是否禁用状态 | boolean | false |
| showScore | 是否显示右侧评分值 | boolean | false |
| fontSize | 右侧文本分值文本的字号 | string | "14" |
| half | 是否开启半星<br>开启半星后，自定的unicon和icon失效。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 评分变换时触发 |
| update:modelValue | - | 同步当前分值，等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| score | 文本分值的右侧插槽 | **score** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/rate

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
			<x-text font-size="18" class=" text-weight-b ">评分 Rate</x-text>
		</x-sheet>
		<x-sheet>
			<x-rate></x-rate>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">设置总评分数量</x-text>
		</x-sheet>
		<x-sheet>
			<x-rate :model-value="6" :count="10"></x-rate>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">开启半星</x-text>
		</x-sheet>
		<x-sheet>
			<x-rate :half="true" :model-value="2.5" size="32" :count="5"></x-rate>
		</x-sheet>
		
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">只读</x-text>
		</x-sheet>
		<x-sheet>
			<x-rate color="#f4a64c" :model-value="5" :readonly="true"></x-rate>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">显示右侧评分值</x-text>
		</x-sheet>
		<x-sheet>
			<x-rate color='success' :model-value="5" :show-score="true"></x-rate>
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
		
