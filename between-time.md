
## 时间区间选择 xBetweenTime

***

#### 介绍

快速的时间区间选择器，方便时间选择自动判断前后时间大小并校正。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-between-time/x-between-time.uvue**

#### 使用

<x-between-time></x-between-time>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前时间,与modelStr不同，此提供的值必须是正常的时间格式<br>否则报错，无法运行。 | string[] | () : string[] => [] as string[] |
| modelStr | 当前时间经过format格式化后输出的值。<br>此值不会处理输入，只输出显示。 | string | "" |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题 | string | "请选择时间" |
| start | 开始时间，请提供正确的时间格式 | string | "" |
| end | 结束时间，请提供正确的时间格式 | string | "" |
| type | 精确到的级别,这里只是展示，具体的返回值还是完整的值。<br>year:年<br>month:年月<br>day:年月日<br>hour:年月日小时<br>minute:年月日小时分钟<br>second:年月日小时分钟秒 | ModelType | "day" |
| format | 输出时间格式，只对v-model:modelStr及输入框展示有效<br>因此它可能不是一个标准时间，比如YY SS ,所以不能作为modelValue使用<br>有效格式：<br>YYYY年<br>MM月<br>DD日<br>hh小时<br>mm分钟<br>ss秒 | string | "YYYY-MM-DD" |
| cellUnits | 上方的单位名称 | string[] | () : string[] => ['年', '月', '日', '时', '分', '秒'] as string[] |
| quickDate | 快速时间区间选择，如果直接填写数字字符，会以你提供的数字最近多少来天来算。<br>d:本日<br>w:本周<br>m:本月<br>y:本年<br>q:本季度<br>7:最近7天，后面的依此类推，数字的就是最近xx天。<br>px:前x年，p+[x]数字依此类推，表示前x年,如：p1,p2... | string[] | () : string[] => ['d', 'w', 'm', 'y', 'q'] as string[] |
| lazyContent | 是否懒加载内部内容。<br>当前你的列表内容非常多，且影响打开的动画性能时，请务必<br>设置此项为true，以获得流畅视觉效果。如果选择数据较少没有必要打开<br>要兼容微信,必须设置为true,非微信可以为false | boolean | true |
| drawerSize | 如果你的快捷选择较多可能会让高度不足，需要自行设置下高。 | string | '540' |
| disabledClear | 是否禁用清除按钮，默认不禁用，允许用户清空选择。点确认，以清空选项数据 | boolean | false |
| disabled | 是否禁用弹出 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cancel | - | 取消时触发 |
| confirm | - | 确认触发 |
| change | **date** : string | 滑动变换时触发 |
| dateClick | - | 快速日期被选中时触发 |
| update:modelShow | - | 变量控制打开状态<br>等同v-model:model-show |
| update:modelStr | - | 经格式化后的值。等同v-model:model-str |
| update:modelValue | - | 点击确认时同步。等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽,默认触发打开选择器。你的默认布局可以放置在这里。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/between-time

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
			<x-text font-size="18" class=" text-weight-b mb-8">时间区间选择 xBetweenTime</x-text>
			<x-text color="#999999">快速的时间区间选择器，方便时间选择自动判断前后时间大小并校正。</x-text>
		</x-sheet>
		
		<x-sheet>
		
			<x-between-time start="2020-1-9" end="2026-5-26" v-model="newdata" v-model:model-str="nowVal">
				<x-button :block="true">打开时间</x-button>
			</x-between-time>

			<x-sheet :margin="['0','24']" color="#f5f5f5" dark-color="#333">
				<x-text color="#999999">选中的值：{{newdata}}</x-text>
				<x-text color="#999999">经format的值：{{nowVal}}</x-text>
			</x-sheet>
			<x-button skin='thin' :block="true" @click="newdata = ['2024-3-21','2026-1-13']">赋值</x-button>
		</x-sheet>
	
		<x-sheet>
			<x-text font-size="18" class="text-weight-b mb-20">设置快捷按钮</x-text>
			<x-between-time :quick-date="['d','y','7','30','p1','p2']" start="2020-1-9" end="2026-5-26" v-model="newdata" v-model:model-str="nowVal">
				<x-button :block="true">打开时间</x-button>
			</x-between-time>
		
		</x-sheet>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts">
	export default {
		data() {

			return {
				nowVal: "",
				newdata:[] as string[]
			};
		},
		methods: {

		},
	}
</script>

<style lang="scss">

</style>
		
