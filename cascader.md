
## 极联器 xCascader

***

#### 介绍

极联选择器，单选模式。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-cascader/x-cascader.uvue**

#### 使用

<x-cascader></x-cascader>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽,可以为auto | string | 'auto' |
| height | 高，不可为auto。 | string | '150' |
| list | 数据结构 | Array |  |
| modelValue | 当前选中项的id | string |  |
| fontSize | 项目文字大小id | string | "18" |
| itemTextColor | 选项项目未选中的文字颜色 | string | "#333333" |
| darkItemTextColor | 选项项目未选中的暗黑文字颜色，空值是取白色 | string | "" |
| itemActiveColor | 选项项目选中的文字颜色，空值取全局主题 | string | "" |
| sliderContentBgColor | 内容区域背景颜色 | string | 'rgba(0,0,0,0)' |
| showCurrentBtn | 是否在有下级的项目上显示选择本级按钮.<br>当用户选中了本级时就同选择最后一项一样会触发confirm及同步vmodel值 | boolean |  |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **ids** : String[] | 选中触发时变化，只要路径变化了就会触发 |
| cellClick | **item** : CASCADER_TREE_ITEM**parentIndex** : number**childrenIndex** : number | 点击项目时触发 |
| confirm | **id** : String**ids** : String[] | 最后一项时触发,或者选择本级时触发 |
| update:modelValue | **id** : String | 等同v-model,或者选择本级时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| header | 顶部头菜单导航插槽,你可以完全写自己的导航样式 | **menus** : CASCADER_ITEM_INFO[]<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/cascader

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
			<x-text font-size="18" class=" text-weight-b mb-8">极联器 xCascader</x-text>
			<x-text color="#999999" >极联选择器，单选,暂不支持多选。不支持异步加载数据（后期实现）</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">单选（可无限级）</x-text>
			<x-divider ></x-divider>
			<x-cascader :showCurrentBtn="true" v-model="selecteds1" :list="list" height="200"></x-cascader>
			<x-sheet color="#f5f5f5" dark-color="#333" :margin="['0','16']">
				<x-text color="#999999">选中的值：{{selecteds1}}</x-text>
			</x-sheet>
			<x-button class="mt-32" @click="selecteds1 = '1-4-1'" :block="true">动态赋值</x-button>
		</x-sheet>
		
		

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { CASCADER_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			const items = [
				{ title: '广东省', id: "199" } as CASCADER_ITEM_INFO,
				{
					title: '江西',
					id: "1-1",
					children: [
						{
							title: '南昌',
							id: "1",
							children: [
								{ title: '青山湖区', id: "1-2" } as CASCADER_ITEM_INFO,
								{ title: '高新区', id: "1-3" } as CASCADER_ITEM_INFO,
								{ title: '红谷滩区', id: "1-4" } as CASCADER_ITEM_INFO,
								{

									title: '东湖区', id: "1-5",

									children: [
										{ title: '三级-青山湖区', id: "1-2-1" } as CASCADER_ITEM_INFO,
										{ title: '三级-高新区', id: "1-3-1" } as CASCADER_ITEM_INFO,
										{ title: '三级-红谷滩区', id: "1-4-1" } as CASCADER_ITEM_INFO,
										{ title: '三级-东湖区', id: "1-5-1" } as CASCADER_ITEM_INFO,
									] as CASCADER_ITEM_INFO[],

								} as CASCADER_ITEM_INFO,
							] as CASCADER_ITEM_INFO[],

						} as CASCADER_ITEM_INFO,
						{ title: '九江', id: "2" } as CASCADER_ITEM_INFO,
						{ title: '赣州', id: "8", disabled: true } as CASCADER_ITEM_INFO,
						{ title: '吉安', id: "9" } as CASCADER_ITEM_INFO,
						{ title: '抚州', id: "10" } as CASCADER_ITEM_INFO,
					] as CASCADER_ITEM_INFO[],
				} as CASCADER_ITEM_INFO,
				{
					title: '江苏',
					id: "4-1",
					children: [
						{ title: '常熟', id: "4" } as CASCADER_ITEM_INFO,
						{ title: '苏州', id: "5" } as CASCADER_ITEM_INFO,
						{ title: '小上海', id: "6" } as CASCADER_ITEM_INFO,
					] as CASCADER_ITEM_INFO[],
				} as CASCADER_ITEM_INFO,
				{ title: '安徽(被禁用)', disabled: true, id: "7" } as CASCADER_ITEM_INFO,
				{ title: '湖南', id: "99" } as CASCADER_ITEM_INFO,
			] as CASCADER_ITEM_INFO[];
			return {
				list: items,
				selecteds1: "",
				selecteds: [] as string[]
			};
		},
		onReady() {
			
		}
	}
</script>

<style lang="scss">

</style>
		
