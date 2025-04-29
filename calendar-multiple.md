
## 日历多选 xCalendarMultiple

***

#### 介绍

日历面板，支持指定日期新式设置，角标，底部文本设置等支持多选

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-calendar-multiple/x-calendar-multiple.uvue**

#### 使用

<x-calendar-multiple></x-calendar-multiple>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 同步当前时间v-model<br>不想受控:model-value | string[] | ():string[]=>[] as string[] |
| model | 范围选择模式<br>day:天数多选，通过multipleMax可以设置允许选择的天数<br>range:天数的范围选择，起始和终止<br>week:按周次选择范围（未开放，请使用x-between-date）<br>quarter:按季度选择范围（未开放，请使用x-between-date）<br>year:按年（未开放，请使用x-between-date） | string | 'day' |
| multipleMax | 多选模式时，允许选择的最大天数。 | number | 0 |
| disabledDays | 禁用的日期字符串如"2023-12-12"<br>它与下面的start，end不冲突。 | string[] | () : string[] => {<br>    return [] as string[]<br>} |
| startDate | 允许选择的开始日期 | string | "1900-1-1" |
| endDate | 允许选择的结束日期 | string | "2100-12-31" |
| dateStyle | 设置指定日期的样式<br>数据类型见：xCalendarDateStyle_type | xCalendarDateStyle_type[] | () : xCalendarDateStyle_type[] => [] as xCalendarDateStyle_type[] |
| format | 同步vmodel时格式化模板 | string | "YYYY-MM-DD" |
| color | 选中的主题色，默认空值，取全局主题色 | string | "" |
| rangColor | 范围选中时,范围中间的选中颜色,<br>如果为空,为color的透明度0.5; | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 变化时触发，切换月份时，也会变更日期，但与vmodel的日期是不一定相等的，vmodel是选中的日期。 |
| update:modelValue | - | 点击日期时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/calendar-multiple

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
			<x-text font-size="18" class=" text-weight-b mb-8">日历多选 xCalendarMultiple</x-text>
			<x-text color="#999999">支持多选，范围,如果需要单天选择请前往xCalendarView组件</x-text>
		</x-sheet>
		<x-sheet>
			<x-calendar-multiple  v-if="show" v-model="dates"></x-calendar-multiple>
			<x-button @click="dates=['2024-7-1','2024-7-20']" skin='thin' :block="true" >赋值</x-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">范围选择</x-text>
			<x-text color="#999999">下面的范围选择限制了只能最多选择20天,如果要不限制设置multipleMax为0即可</x-text>
		</x-sheet>
		<x-sheet>
			<x-calendar-multiple  v-if="show" :multipleMax="20" model='range' v-model="dates2"></x-calendar-multiple>
			<x-button @click="fuzhi" skin='thin' :block="true" >赋值</x-button>
		</x-sheet>
		<view style="height:16px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts">
	import { xCalendarDateStyle_type } from "@/uni_modules/tmx-ui/interface.uts"
	import { xConfig } from "@/uni_modules/tmx-ui/config/xConfig.uts"
	export default {
		data() {
			return {
				dates:[] as string[],
				dates2:[] as string[],
				show:false
			}
		},
		onReady() {
			this.show = true;
		},
		methods: {
			fuzhi(){
				this.dates2=['2024-5-1','2024-5-19']
				
			}
		}
	}
</script>

<style>

</style>

		
