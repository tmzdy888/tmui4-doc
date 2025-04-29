
## 日历 xCalendar

***

#### 介绍

日历面板，支持指定日期新式设置，角标，底部文本设置等暂不同时支持多选，因为不支持联合类型后期需要分开组件使用。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-calendar-view/x-calendar-view.uvue**

#### 使用

<x-calendar-view></x-calendar-view>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 同步当前时间v-model<br>不想受控:model-value | string | "" |
| disabledDays | 禁用的日期字符串如"2023-12-12"<br>它与下面的start，end不冲突。 | string[] | () : string[] => {<br>    return [] as string[]<br>} |
| startDate | 允许选择的开始日期 | string | "2020-1-1" |
| endDate | 允许选择的结束日期 | string | "2040-12-31" |
| dateStyle | 设置指定日期的样式<br>数据类型见：xCalendarDateStyle_type | xCalendarDateStyle_type[] | () : xCalendarDateStyle_type[] => [] as xCalendarDateStyle_type[] |
| format | 同步vmodel时格式化模板 | string | "YYYY-MM-DD" |
| color | 选中的主题色，默认空值，取全局主题色 | string | "" |
| hideHeader | 隐藏顶部操作栏，可自己定义顶部工具要栏 | boolean | false |
| disabledSwiper | 禁用日历切换，会提高性能，因为只渲染一个层，可以手动切换日历 | boolean | false |
| disabled | 禁止用户操作选中,相当于仅展示日历 | boolean | false |
| vertical | 是否上下切换日历 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 变化时触发 |
| update:modelValue | - | 点击日期时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/calendar-view

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
			<x-text font-size="18" class=" text-weight-b mb-8">日历 xCalendar</x-text>
			<x-text color="#999999">日历面板，支持指定日期样式设置，角标，底部文本设置等</x-text>
			<x-text color="#999999">注意区别：appx端是canvas绘制，h5是view节点，因此appx端右角标文件只能限制2个字符，英文3个字符</x-text>
		</x-sheet>
		<x-sheet :padding="['0']" :margin="['12','0','12','12']"
			:linear-gradient="_isDark?([] as string[]):['bottom','#d1eaed','#effdff']">
			<x-calendar-view v-if="show" :date-style="dateStyle" :disabled-days="['2024-5-31']" v-model="date"></x-calendar-view>
			<view class="pa-32">
				<x-button :block="true" @click="setdate">设置日期样式数据</x-button>
			</view>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b ">禁用头，尾，禁用用户操作和切换，可以实现自定日历。</x-text>
		</x-sheet>
		<x-sheet :padding="['0']" >
			<x-calendar-view v-if="show" :disabled="true" :hideHeader="true" :disabledSwiper="true"></x-calendar-view>
		</x-sheet>
		
		<view style="height:50px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { xCalendarDateStyle_type } from "@/uni_modules/tmx-ui/interface.uts"
	import { xConfig } from "@/uni_modules/tmx-ui/config/xConfig.uts"
	export default {
		data() {
			return {
				date: "2024-2-26",
				dateStyle: [] as xCalendarDateStyle_type[],
				show:false
			};
		},
		computed: {
			_isDark() : boolean {
				return xConfig.dark == 'dark'
			}
		},
		onReady() {
			this.show = true;
		},
		methods: {
			setdate() {
				this.date = "2024-5-8"
			
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
			}
		},
	}
</script>

<style lang="scss">

</style>
		
