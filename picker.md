
## 选择器 xPicker

***

#### 介绍

组件采用数组id式选择，非索引。考虑到实际实用中多以id为交互提交数据。因此摒弃了传统的索引选项

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker/x-picker.uvue**

#### 使用

<x-picker></x-picker>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 数据项同x-picker-view的PICKER_ITEM_INFO | PICKER_ITEM_INFO[] | () : PICKER_ITEM_INFO[] => [] as PICKER_ITEM_INFO[] |
| modelValue | 当前选中项的id值 | string[] | () : string[] => [] as string[] |
| modelStr | 当前选中项的回显文本等同v-model:model-str<br>请不要更改此值，此值只对外输出显示。<br>如果空值，将内部首次递归渲染回显文本。如果你后台返回，就不会计算。<br>因此如果对性能有要求的请务必让后台在首次显示时先回显文本，<br>这样内部在第一次时不会递归计算回显文本，提高性能。 | string | "" |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题 | string | "" |
| cancelText | 取消按钮的文本 | string | "" |
| confirmText | 确认按钮的文本 | string | "" |
| lazyContent | 是否懒加载内部内容。<br>当前你的列表内容非常多，且影响打开的动画性能时，请务必<br>设置此项为true，以获得流畅视觉效果。如果选择数据较少没有必要打开<br>注意:由于要兼容微信,此属性从1.1.9开始必须打开,除非不用微信小程序可以关闭. | boolean | true |
| cellUnits | 显示在顶部的单位名称 | string[] | () : string[] => [] as string[] |
| unitsFontSize |  | string | '12' |
| modelStrJoin | 自动同步modelstr拼接时的符号. | string | "," |
| zIndex | 层级 | number | 1100 |
| showClose |  | boolean | false |
| disabled | 是否禁用弹出 | boolean | false |
| widthCoverCenter | 宽屏时是否让内容剧中显示<br>并限制其宽为屏幕宽，只展示中间内容以适应宽屏。 | boolean | false |
| customWrapStyle | 自定义容器背景层样式 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cancel | - | 取消时触发 |
| confirm | - | 确认触发 |
| change | **ids** : string[] | 滑动变换时触发 |
| update:modelShow | - | 变量控制打开状态<br>等同v-model:model-show |
| update:modelStr | - | 等同v-model:model-str<br>只对外输出当前回选区的选中项的文本，不要外部改变此值。 |
| update:modelValue | - | 点击确认时同步。等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽,默认触发打开选择器。你的默认布局可以放置在这里。 | **label** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/picker

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
			<x-text font-size="18" class=" text-weight-b mb-8">选择器 Picke</x-text>
			<x-text color="#999999" class="text-size-b">
				这是xPickerView封装的弹出式，详细可见xPickerView文档
			</x-text>
		</x-sheet>
		<x-sheet>

			<x-picker @change="change" v-model="selecteds" v-model:model-str="(str as string)" :list="list">
				<x-button :block="true">打开选项</x-button>
			</x-picker>

			<x-sheet :margin="['0','24']" color="#f5f5f5" dark-color="#333">
				<x-text color="#999999">选中的值：{{selecteds.join(',')}}</x-text>
				<x-text color="#999999">选中的值回显文本：{{str}}</x-text>
			</x-sheet>
			<x-button :block="true" @click="fuzhi">赋值</x-button>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">customWrapStyle定义外观</x-text>
			
		</x-sheet>
		<x-sheet>
			<x-picker customWrapStyle="margin:16px;width:auto;border-radius:16px;" @change="change" v-model="selecteds" v-model:model-str="(str as string)" :list="list">
				<x-button :block="true">打开选项</x-button>
			</x-picker>
		</x-sheet>
		
		<view style="height: 50px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts">
	import { PICKER_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	const items = [
		{
			title: '江西',
			id: "9-1",
			children: [
				{
					title: '南昌',
					id: "132",
					children: [
						{ title: '青山湖区', id: "1-2" } as PICKER_ITEM_INFO,
						{ title: '高新区', id: "1-3", disabled: true } as PICKER_ITEM_INFO,
						{ title: '红谷滩区', id: "1-4" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
				{

					title: '九江', id: "222",
					children: [
						{ title: '2青山湖区', id: "1-32" } as PICKER_ITEM_INFO,
						{ title: '2高新区', id: "1-33" } as PICKER_ITEM_INFO,
						{ title: '3红谷滩区', id: "1-34" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],
				} as PICKER_ITEM_INFO,
			] as PICKER_ITEM_INFO[],
		} as PICKER_ITEM_INFO,
		{
			title: '安徽',
			id: "10-13",
			children: [
				{
					title: '5南昌',
					id: "3",
					children: [
						{ title: '5青山湖区', id: "1-52" } as PICKER_ITEM_INFO,
						{ title: '5高新区', id: "1-53" } as PICKER_ITEM_INFO,
						{ title: '5红谷滩区', id: "1-54" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
				{
					title: '5南昌',
					id: "36",
					children: [
						{ title: '6青山湖区', id: "61-52" } as PICKER_ITEM_INFO,
						{ title: '6高新区', id: "61-53" } as PICKER_ITEM_INFO,
						{ title: '6红谷滩区', id: "61-54" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
			] as PICKER_ITEM_INFO[],
		} as PICKER_ITEM_INFO,

	] as PICKER_ITEM_INFO[];
	export default {
		data() {

			return {
				list: items,
				// '10-1', '1', '1-3'
				selecteds: [] as string[],
				str: ""

			};
		},
		methods: {
			change(ids : string[]) {
				console.log(ids)
			},
			fuzhi() {
				this.selecteds = ['10-13', '36', '61-53']

			}
		},
	}
</script>

<style lang="scss">

</style>
		
