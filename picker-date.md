
## 日期选择器 xPickerDate

***

#### 介绍

日期选择，可以控制显示精确到秒。默认的开始时间为当前时间的上一年，结束时间为默认当前时间
使用时，建议不要显示过多年份以防卡太多数据。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker-date/x-picker-date.uvue**

#### 使用

<x-picker-date></x-picker-date>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前时间,与modelStr不同，此提供的值必须是正常的时间格式<br>否则报错，无法运行。可以提供以下合法格式：<br>YYYY,YYYY-MM,YYYY-MM-DD,YYYY-MM-DD HH,YYYY-MM-DD HH:mm,YYYY-MM-DD HH:mm:ss | string | "" |
| modelStr | 当前时间经过format格式化后输出的值。<br>此值不会处理输入，只输出显示。 | string | "" |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题 | string | "请选择时间" |
| cancelText | 取消按钮的文本 | string | "取消" |
| confirmText | 确认按钮的文本 | string | "确认" |
| start | 开始时间，请提供正确的时间格式 | string | "" |
| end | 结束时间，请提供正确的时间格式 | string | "" |
| type | 精确到的级别<br>year:年<br>month:年月<br>day:年月日<br>hour:年月日小时<br>minute:年月日小时分钟<br>second:年月日小时分钟秒 | ModelType | "day" |
| format | 输出时间格式，只对v-model:modelStr有效<br>如果桢同步对vmodel:modelValue有效需要设置formatSyncValue为true<br>有效格式：<br>YYYY年<br>MM月<br>DD日<br>hh小时<br>mm分钟<br>ss秒 | string | "YYYY-MM-DD" |
| formatSyncValue | 是否将format格式化的v-model:modelStr同步到v-model:modelValue<br>默认false,注意：如果开启了同步，你要确保format的值是正常的时间值<br>正常兼容以下时间格式：<br>YYYY,YYYY-MM,YYYY-MM-DD,YYYY-MM-DD HH,YYYY-MM-DD HH:mm,YYYY-MM-DD HH:mm:ss | boolean | false |
| cellUnits | 上方的单位名称 | string[] | () : string[] => ['年', '月', '日', '时', '分', '秒'] as string[] |
| lazyContent | 是否懒加载内部内容。<br>当前你的列表内容非常多，且影响打开的动画性能时，请务必<br>设置此项为true，以获得流畅视觉效果。如果选择数据较少没有必要打开<br>要兼容微信就必须打开为true,非微信可以设置为false | boolean | true |
| zIndex | 层级 | number | 1100 |
| showClose |  | boolean | true |
| disabled | 是否禁用弹出 | boolean | false |



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

/pages/biaodan/picker-date

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
			<x-text font-size="18" class=" text-weight-b mb-8">日期选择器 PickerDate</x-text>
			<x-text color="#999999">日期选择，可以控制显示精确到秒。默认的开始时间为当前时间的上一年，结束时间为默认当前时间</x-text>
		</x-sheet>
		
	
		<x-sheet>
			<x-picker-date v-model="modelValue" :formatSyncValue="true" start="2020-1-1" end="2024-12-5" v-model:model-str="nowVal" type="minute"
				format="YYYY-MM-DD hh:mm">
				<x-button :block="true">打开时间</x-button>
			</x-picker-date>

			<x-sheet :margin="['0','24','0','0']" color="#f5f5f5" dark-color="#333">
				<x-text color="#999999">选中的值：{{modelValue}}</x-text>
				<x-text color="#999999">经format的值：{{nowVal}}</x-text>
			</x-sheet>
		</x-sheet>
		<x-sheet>
			<x-button skin='thin' :block="true" @click="modelValue = '2024-3-21'">赋值2024-3-21</x-button>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">内嵌日期选择器 xDateView</x-text>
			<x-date-view ></x-date-view>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">精确到秒</x-text>
		</x-sheet>
		<x-sheet>
			<x-picker-date type="second">
				<x-button :block="true">打开时间</x-button>
			</x-picker-date>
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
				modelValue: "2024-10-06 10:10:10",
				
			};
		},
		methods: {
			
		},
	}
</script>

<style lang="scss">

</style>
		
