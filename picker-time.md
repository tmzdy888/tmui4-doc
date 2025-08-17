
## 时间选择器 xPickerTime

***

#### 介绍

这是单独显示和控制选择时分秒选择器。如果你需要年月日到秒的全部选择请参考x-picker-date。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker-time/x-picker-time.uvue**

#### 使用

<x-picker-time></x-picker-time>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前时间,与modelStr不同，此提供的值必须是正常的时间格式xx:xx:xx<br>否则报错，无法运行。 | string | "" |
| modelStr | 当前时间经过format格式化后输出的值。<br>此值不会处理输入，只输出显示。 | string | "" |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题 | string | "" |
| cancelText | 取消按钮的文本 | string | "" |
| confirmText | 确认按钮的文本 | string | "" |
| start | 开始时间：请提供正确的时间格式xx:xx:xx | string | "" |
| end | 结束时间：请提供正确的时间格式xx:xx:xx | string | "" |
| type | 精确到的级别<br>hour:小时<br>minute:小时分钟<br>second:小时分钟秒 | string | "second" |
| format | 输出时间格式，只对v-model:modelStr有效<br>有效格式：<br>hh小时<br>mm分钟<br>ss秒 | string | "hh:mm:ss" |
| cellUnits | 上方的单位名称,'年', '月', '日', '小时', '分钟', '秒数' | string[] | () : string[] => [] as string[] |
| zIndex | 层级 | number | 1100 |
| showClose |  | boolean | false |
| disabled | 是否禁用弹出 | boolean | false |
| widthCoverCenter | 宽屏时是否让内容剧中显示<br>并限制其宽为屏幕宽，只展示中间内容以适应宽屏。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cancel | - | 取消时触发 |
| confirm | - | 确认触发 |
| change | **date** : string | 滑动变换时触发 |
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

/pages/biaodan/picker-time

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
			<x-text font-size="18" class=" text-weight-b mb-8">时间选择器 PickerTime</x-text>
			<x-text color="#999999" >这是单独显示和控制选择时分秒选择器。如果你需要年月日到秒的全部选择请参考x-picker-date。</x-text>
		</x-sheet>

		<x-sheet>
			<x-picker-time start="08:00:00" end="20:30:30" v-model="nowVal" v-model:model-str="date" format="hh时mm分ss秒">
				<x-button :block="true">打开时间</x-button>
			</x-picker-time>

			<x-sheet :margin="['0','12']" dark-color="#333">
				<x-text color="#999999">选中的值：{{nowVal}}</x-text>
				<x-text color="#999999">经format的值：{{date}}</x-text>
			</x-sheet>
		</x-sheet>
		<x-sheet>
			<x-button skin='thin' :block="true"  @click="nowVal = '12:14:30'">赋值12:14:30</x-button>
		</x-sheet>
	
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts">
	export default {
		data() {

			return {
				date: "",
				nowVal: "10:00:01"

			};
		},
		methods: {

		},
	}
</script>

<style lang="scss">

</style>
		
