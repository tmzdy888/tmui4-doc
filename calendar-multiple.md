
## 多选日历 xCalendarMultiple

***

#### 介绍

可以单选和多选，无限循环滚动，目前4.67dev以下版本使用可能会有性能风险，请关注后续官方针对性的优化。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.2.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-calendar-multiple/x-calendar-multiple.uvue**

#### 使用

<x-calendar-multiple></x-calendar-multiple>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 同步当前时间v-model<br>不想受控:model-value | Array | [] as string[] |
| model | 范围选择模式<br>day:天数多选，通过multipleMax可以设置允许选择的天数<br>range:天数的范围选择，起始和终止<br>week:按周次选择范围（未开放）<br>quarter:按季度选择范围（未开放）<br>year:按年（未开放） | union | 'day' |
| multipleMax | 多选模式时，允许选择的最大天数。 | number | -1 |
| disabledDays | 禁用的日期字符串如"2023-12-12"<br>它与下面的start，end不冲突。 | Array | [] as string[] |
| startDate | 允许选择的开始日期 | string | '1900-1-1' |
| vertical | 是否上下切换日历 | boolean | false |
| endDate | 允许选择的结束日期 | string | '2100-1-1' |
| currentDate | 当前显示的月份，默认以modalValue中的第一项为初始月<br>如果为空，显示本月，可以控制这里切换显示的日期 | string | '' |
| dateStyle | 设置指定日期的样式<br>数据类型见：xCalendarDateStyle_type | Array | [] as xCalendarDateStyle_type[] |
| format | 同步vmodel时格式化模板 | string | 'YYYY-MM-DD' |
| color | 选中的主题色，默认空值，取全局主题色<br>如果提供了dateStyle，以dateStyle为准 | string | '' |
| fontColor | 默认的文字颜色<br>如果提供了dateStyle，以dateStyle为准 | string | '#333333' |
| fontDarkColor | 默认的暗黑文字颜色<br>如果提供了dateStyle，以dateStyle为准 | string | '#ffffff' |
| activeFontColor | 默认选中时的文字颜色<br>如果提供了dateStyle，以dateStyle为准 | string | '#ffffff' |
| rangColor | 范围选中时,范围中间的选中颜色,<br>如果为空,为color的透明度0.5; | string | '' |
| rangFontColor |  | string | '' |
| headBgColor | 头的背景颜色，默认为透明 | string | 'transparent' |
| headFontColor | 头的文字颜色，提供了后暗黑失效会以这个为准。 | string | '' |
| headStyle | 头部自定义样式。 | string | '' |
| renderOnly | 循环渲染时，是否只渲染当前面板（如果你在pad等10年前的低端机上渲染日历有压力请打开此值为true)<br>关闭后可以提升滑动体验。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : string[] | 时间变化时触发 |
| click | **value** : string | 当前日历面板的日期被点击时触发 |
| currentChange | **value** : string | 当前激活面板月份改变时触发（就是当前看到的月份面板） |
| update:modelValue | **value** : string[] | 同步当前的选中的日期绑定 |
| update:currentDate | **value** : string | 同步当前查看的月份日期，请以日期形式提供值 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| header | 日历头，隐藏使用空插槽，将隐藏，如果想自定，请通过ref函数来翻页控制日历走向。 | - |
| footer | 日历尾部 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| next | - | - | 下月 |
| prev | - | - | 上月 |
| setCurrentMonth | - | - | 设置日历返回到本月 |
| clear | - | - | 清空选择 |


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
			<x-text color="#999999">支持多选，范围,如果需要单天选择请前往xCalendarView组件{{currentDate}}</x-text>
		</x-sheet>
		<x-sheet :padding="['0']">
			<x-calendar-multiple style="border-radius: 12px;" @change="onchange" v-model:currentDate="currentDate" :disabledDays="['2024-5-31']" :date-style="dateStyle" headBgColor='rgb(5, 121, 255)' headFontColor='white' v-if="show" v-model="dates"></x-calendar-multiple>
			<view class="px-12 pb-12">
				<x-button @click="setdate" skin='thin' :block="true" >赋值</x-button>
			</view>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">范围选择</x-text>
			<x-text color="#999999">下面的范围选择限制了只能最多选择20天,如果要不限制设置multipleMax为0即可</x-text>
		</x-sheet>
		<x-sheet :padding="['0']">
			<x-calendar-multiple @change="onchange" currentDate="2024-5-1"  v-if="show" :multipleMax="20" model='range' v-model="dates2"></x-calendar-multiple>
			<view class="px-12 pb-12">
				<x-button @click="fuzhi" skin='thin' :block="true" >赋值</x-button>
			</view>
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
				dateStyle: [] as xCalendarDateStyle_type[],
				currentDate:"",
				show:false
			}
		},
		onReady() {
			this.show = true;
		},
		methods: {
			fuzhi(){
				this.dates2=['2024-5-1','2024-5-19']
				
			},
			onchange(dates:string[]){
				console.log(dates)
			},
			setdate() {
				this.dates = ['2024-5-1','2024-5-8']
				this.currentDate = "2024-5-1"
				nextTick(()=>{
					this.dateStyle = [
						{ date: '2024-5-3', color: '#00aa7f', label: '推荐', fontColor: 'white' } as xCalendarDateStyle_type,
						{ date: '2024-5-20', label: '完成', fontColor: 'orange' } as xCalendarDateStyle_type,
						{ date: '2024-5-21', label: '爆满', fontColor: 'red' } as xCalendarDateStyle_type,
						{ date: '2024-5-31', label: '禁用' } as xCalendarDateStyle_type,
						{ date: '2024-5-18', dot: true } as xCalendarDateStyle_type,
						{ date: '2024-5-17', dot: true, dotColor: "orange", dotLabel: "36" } as xCalendarDateStyle_type,
						{ date: '2024-5-1', dot: true, dotColor: "#52c428", dotLabel: "假", label: "劳动节", fontColor: "#52c428" } as xCalendarDateStyle_type,
						{ date: '2024-5-4', dot: true, dotColor: "#aa55ff", dotLabel: "休", label: "劳动节", fontColor: "#52c428" } as xCalendarDateStyle_type,
					] as xCalendarDateStyle_type[]
				})
			}
		}
	}
</script>

<style>

</style>

		
