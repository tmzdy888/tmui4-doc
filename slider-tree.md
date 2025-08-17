
## 侧边分类 xSliderTree

***

#### 介绍

侧边分类选择，可多选，单选模式。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-slider-tree/x-slider-tree.uvue**

#### 使用

<x-slider-tree></x-slider-tree>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽 | string | "auto" |
| height | 高是必填，不可为auto。 | string | "100%" |
| activeTextColor | 侧边选中的文字颜色，空值取全局主题 | string | "" |
| textColor | 侧边未选中时的文字颜色 | string | "#888888" |
| itemTextColor | 选项项目未选中的文字颜色 | string | "#333333" |
| itemActiveColor | 选项项目选中的文字颜色，空值取全局主题 | string | "" |
| sliderBgColor | 左侧边栏背景颜色 | string | "#f5f5f5" |
| darkSliderBgColor | 左侧边栏暗黑背景颜色<br>如果不提供，自动读取全局的backgroundColorContentDark背景色 | string | "" |
| sliderContentBgColor | 右内容区域背景颜色 | string | "white" |
| darkSliderContentBgColor | 右内容区域暗黑背景颜色<br>如果不提供读取sheet窗口的暗黑背景 | string | "" |
| sliderWidth | 侧边栏宽 | string | "100" |
| list |  | SLIDER_TREE_ITEM_INFO[] | () : SLIDER_TREE_ITEM_INFO[] => [] as SLIDER_TREE_ITEM_INFO[] |
| modelValue | 当前选中项的id数组 | string[] | () : string[] => [] as string[] |
| multiple | 每级是否允许多选 | boolean | false |
| fontSize | 文字大小 | string | "16" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 选中变换时触发 |
| update:modelValue | - | 更新当前的值，等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/slider-tree

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
			<x-text font-size="18" class=" text-weight-b mb-8">侧边分类 xSliderTree</x-text>
			<x-text color="#999999" >侧边分类选择，可多选，单选模式。</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">单选（可无限级）</x-text>
			<x-divider class="my-24"></x-divider>
			<x-slider-tree :model-value="['1-3']" height="280" :list="list"></x-slider-tree>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">多选（可无限级）</x-text>
			<x-divider class="my-24"></x-divider>
			<x-slider-tree v-model="selecteds" :multiple="true" height="280px" :list="list"></x-slider-tree>
			<x-button class="mt-24" @click="selecteds = ['1-3-1','10']" :block="true">动态赋值</x-button>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { SLIDER_TREE_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			const items = [
				{
					title: '江西',
					id: "1-1",
					children: [
						{
							title: '南昌',
							id: "1",
							children: [
								{ title: '青山湖区', id: "1-2" } as SLIDER_TREE_ITEM_INFO,
								{ title: '高新区', id: "1-3" } as SLIDER_TREE_ITEM_INFO,
								{ title: '红谷滩区', id: "1-4" } as SLIDER_TREE_ITEM_INFO,
								{

									title: '东湖区', id: "1-5",

									children: [
										{ title: '三级-青山湖区', id: "1-2-1" } as SLIDER_TREE_ITEM_INFO,
										{ title: '三级-高新区', id: "1-3-1" } as SLIDER_TREE_ITEM_INFO,
										{ title: '三级-红谷滩区', id: "1-4-1" } as SLIDER_TREE_ITEM_INFO,
										{ title: '三级-东湖区', id: "1-5-1" } as SLIDER_TREE_ITEM_INFO,
									] as SLIDER_TREE_ITEM_INFO[],

								} as SLIDER_TREE_ITEM_INFO,
							] as SLIDER_TREE_ITEM_INFO[],

						} as SLIDER_TREE_ITEM_INFO,
						{ title: '九江', id: "2" } as SLIDER_TREE_ITEM_INFO,
						{ title: '赣州', id: "8", disabled: true } as SLIDER_TREE_ITEM_INFO,
						{ title: '吉安', id: "9" } as SLIDER_TREE_ITEM_INFO,
						{ title: '抚州', id: "10" } as SLIDER_TREE_ITEM_INFO,
					] as SLIDER_TREE_ITEM_INFO[],
				} as SLIDER_TREE_ITEM_INFO,
				{
					title: '江苏',
					id: "4-1",
					children: [
						{ title: '常熟', id: "4" } as SLIDER_TREE_ITEM_INFO,
						{ title: '苏州', id: "5" } as SLIDER_TREE_ITEM_INFO,
						{ title: '小上海', id: "6" } as SLIDER_TREE_ITEM_INFO,
					] as SLIDER_TREE_ITEM_INFO[],
				} as SLIDER_TREE_ITEM_INFO,
				{ title: '安徽(被禁用)', disabled: true, id: "7" } as SLIDER_TREE_ITEM_INFO,
				{ title: '湖南', id: "99" } as SLIDER_TREE_ITEM_INFO,
			] as SLIDER_TREE_ITEM_INFO[];
			return {
				list: items,
				selecteds: [] as string[]
			};
		}
	}
</script>

<style lang="scss">

</style>
		
