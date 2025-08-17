
## 选择器容器 xPickerView

***

#### 介绍

这是非官方pickerView封装,由于我是自行开发的，
                因此比较好的能控制动画，回弹，阻尼，禁用项等
                如果你不喜欢这个样式可以修改源码，比官方的更好更改样式。
                组件采用数组id式选择，非索引。考虑到实际实用中多以id为交互提交数据。因此摒弃了传统的索引选项

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker-view/x-picker-view.uvue**

#### 使用

<x-picker-view></x-picker-view>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 数据项<br>格式类型为：PICKER_ITEM_INFO | PICKER_ITEM_INFO[] | () : PICKER_ITEM_INFO[] => [] as PICKER_ITEM_INFO[] |
| listPro | 数据项,这是内部使用的以提高数据的转换性能。如果你确定你提供的是这个类型，可以赋值此值，避免转换时间。<br>格式类型为：X_PICKER_X_ITEM<br>数据如果超过1mb不要去转换，最后直接从后台提供string然后直接JSON.getArray<X_PICKER_X_ITEM>(data)赋值到值。<br>这样性能在安卓上可以提高到好多。 | X_PICKER_X_ITEM[] | () : X_PICKER_X_ITEM[] => [] as X_PICKER_X_ITEM[] |
| modelValue | 当前选中项的id值 | string[] | () : string[] => [] as string[] |
| modelStr | 当前选中项的标题文本组 | string | "" |
| cellUnits | 显示在顶部的单位名称 | string[] | () : string[] => [] as string[] |
| unitsFontSize |  | string | '12' |
| fontSize | 项目的字体号大小 | string | "16" |
| duration |  | number | 300 |
| threshold |  | number | 0.9 |
| modelStrJoin | 自动同步modelstr拼接时的符号. | string | "," |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **ids** : string[] | 选项变化时触发 |
| update:modelStr | - | 等同v-model:model-str<br>只对外输出当前回选区的选中项的文本，不要外部改变此值。 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/picker-view

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
			<x-text font-size="18" class=" text-weight-b mb-8">选择器容器 PickerView</x-text>
			<x-text  color="#999999" class="text-size-b">
				组件采用数组id式选择，非索引。考虑到实际实用中多以id为交互提交数据。因此摒弃了传统的索引选项
			</x-text>
		</x-sheet>

		<x-sheet>
			<x-picker-view v-model:model-str="selectedStr" @change="change" v-model="selecteds" :list="list"></x-picker-view>
			<x-sheet :margin="['0','24','0','0']" color="#f5f5f5" dark-color="#333">
				<x-text color="#999999">选中的值：{{selecteds.join(',')}}</x-text>
				<x-text color="#999999">选中项的文本：{{selectedStr}}</x-text>
			</x-sheet>
		</x-sheet>
		<view style="height:50px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts">
	import { PICKER_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			const items = [
				{
					"title": "1江西",
					"id": "1",
					"children": [
						{
							"title": "1南昌",
							"id": "1-1",
							"children": [
								{
									"title": "11青山湖区",
									"id": "1-1-1"
								} as PICKER_ITEM_INFO,
								{
									"title": "11高新区",
									"id": "1-1-2"
								} as PICKER_ITEM_INFO,
								{
									"title": "11红谷滩区",
									"id": "1-1-3"
								} as PICKER_ITEM_INFO
							] as PICKER_ITEM_INFO[]
						} as PICKER_ITEM_INFO,
						{
							"title": "1九江",
							"id": "1-2",
							"disabled": true
						} as PICKER_ITEM_INFO,
						{
							"title": "1赣州",
							"id": "1-3",
						} as PICKER_ITEM_INFO,
						{
							"title": "1吉安",
							"id": "1-4"
						} as PICKER_ITEM_INFO,
						{
							"title": "1抚州",
							"id": "1-5"
						} as PICKER_ITEM_INFO
					] as PICKER_ITEM_INFO[]
				},
				{
					"title": "2湖南",
					"id": "2",
					"children": [
						{
							"title": "21长沙",
							"id": "2-1",
							"children": [
								{
									"title": "21雨花区",
									"id": "2-1-2"
								} as PICKER_ITEM_INFO,
								{
									"title": "21芙蓉区",
									"id": "2-1-3"
								} as PICKER_ITEM_INFO,
								{
									"title": "21开福区",
									"id": "2-1-4"
								} as PICKER_ITEM_INFO
							] as PICKER_ITEM_INFO[]
						} as PICKER_ITEM_INFO,
						{
							"title": "2株洲",
							"id": "2-2",
							"disabled": true
						} as PICKER_ITEM_INFO,
						{
							"title": "2湘潭",
							"id": "2-3"
						} as PICKER_ITEM_INFO,
						{
							"title": "2衡阳",
							"id": "2-4"
						} as PICKER_ITEM_INFO,
						{
							"title": "2郴州",
							"id": "2-5"
						} as PICKER_ITEM_INFO
					] as PICKER_ITEM_INFO[]
				} as PICKER_ITEM_INFO,
				{
					"title": "3广东",
					"id": "3",
					"children": [
						{
							"title": "3广州",
							"id": "3-1",
							"children": [
								{
									"title": "31天河区",
									"id": "3-1-2"
								} as PICKER_ITEM_INFO,
								{
									"title": "31白云区",
									"id": "3-1-3"
								} as PICKER_ITEM_INFO,
								{
									"title": "31黄埔区",
									"id": "3-1-4"
								} as PICKER_ITEM_INFO
							] as PICKER_ITEM_INFO[]
						} as PICKER_ITEM_INFO,
						{
							"title": "3深圳",
							"id": "3-2",
							"disabled": true
						} as PICKER_ITEM_INFO,
						{
							"title": "3珠海",
							"id": "3-3"
						} as PICKER_ITEM_INFO,
						{
							"title": "3佛山",
							"id": "3-4"
						} as PICKER_ITEM_INFO,
						{
							"title": "3惠州",
							"id": "3-5"
						} as PICKER_ITEM_INFO
					] as PICKER_ITEM_INFO[]
				}
			] as PICKER_ITEM_INFO[];
			return {
				list: items,
				selecteds: ["2","2-1","2-1-2"],
				selectedStr:""

			};
		},
		methods: {
			change(ids : string[]) {
				// console.log(ids)
			}
		},
	}
</script>

<style lang="scss">

</style>
		
