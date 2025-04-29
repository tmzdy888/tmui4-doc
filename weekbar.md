
## 时间周 xWeekbar

***

#### 介绍

样式丰富,非常精美,能够适应不同设计要求.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-weekbar/x-weekbar.uvue**

#### 使用

<x-weekbar></x-weekbar>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| startDate | 开始的日期 | string | "1900-1-1" |
| endDate | 结束的日期 | string | "2100-1-1" |
| format | 格式展示在组件上的日期. | string | "DD" |
| cn | 周上面显示的中文名称. | string[] | () : string[] => ['一', '二', '三', '四', '五', '六', '日'] as string[] |
| color | 背景 | string | "white" |
| darkColor | 暗黑时的背景,如果不提供使用sheet暗黑背景 | string | "" |
| fontColor | 字号颜色 | string | "#333333" |
| fontSize | 字号颜色 | string | "14" |
| fontDarkColor | 暗黑时的字号颜色 | string | "#fbfbfb" |
| fontActiveColor | 激活时的字号颜色,不区分暗黑 | string | "white" |
| mode | 选中的样式.<br>rect和circular,none三种 | string | "rect" |
| rectRound | mode为rect时的选中背景圆角 | string | "5" |
| round | 组件圆角 | string | "0" |
| activeBgColor | 激活时的背景,不区分暗黑,不填充默认是全局主题色 | string | "" |
| topHeight | 上部分标题的高 | string | "32" |
| bottomHeight | 下部分日期的高. | string | "42" |
| padding | 左右,上下的间隙 | string[] | () : string[] => ['4', '8'] as string[] |
| showAction |  | boolean | true |
| actionIcon |  | string | 'arrow-left-s-line' |
| actionSize | 操作栏的图标大小 | string | '24' |
| actionColor | 操作栏的图标颜色 | string | '#bebebe' |
| actionDarkColor | 操作栏的图标暗黑颜色 | string | '#bebebe' |
| emptyValueSelected | 当前modelValue为空时,这里设置为false时,默认进来<br>不会选中当前日期. | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **date** : string | 时间切换时触发 |
| update:modelValue | **date** : string | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| left | 左边操作栏按钮 | - |
| right | 右边操作栏按钮 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/weekbar

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
		<x-sheet :margin="['0']" :round="['0']">
			<x-text font-size="18" class=" text-weight-b mb-8">时间周 xWeekbar</x-text>
			<x-text color="#999999" >
				样式丰富,非常精美,能够适应不同设计要求.
			</x-text>
		</x-sheet>
		<x-weekbar></x-weekbar>
		<x-sheet :margin="['0','8','0','0']" :round="['0']">
			<x-text font-size="18" class=" text-weight-b ">无操作栏及圆模式</x-text>
		</x-sheet>
		<x-weekbar :showAction="false" mode="circular" :padding="['0','4']"></x-weekbar>
		<x-sheet :margin="['0','8','0','0']" :round="['0']">
			<x-text font-size="18" class=" text-weight-b ">无背景模式</x-text>
		</x-sheet>
		<x-weekbar :showAction="false" color="transparent" fontActiveColor="primary" mode="none" :padding="['0','0']"></x-weekbar>
		<x-sheet :margin="['0']" :round="['0']">
			<x-text font-size="18" class=" text-weight-b ">个性化</x-text>
		</x-sheet>
		<x-weekbar :showAction="false" 
		color="#fff60a" 
		fontDarkColor="black"
		darkColor="#fff60a" activeBgColor="black" mode="circular" :padding="['0','4']"></x-weekbar>
		<x-sheet :margin="['0']" :round="['0']">
			<x-text font-size="18" class=" text-weight-b ">个性化(默认不选中)</x-text>
		</x-sheet>
		<x-weekbar
		actionIcon="arrow-left-circle-line"
		rectRound="8"
		color="error" 
		darkColor="error" 
		fontColor="rgba(255,255,255,0.7)" 
		fontDarkColor="rgba(255,255,255,0.8)" 
		activeBgColor="#6b0902" 
		mode="rect" 
		actionDarkColor="rgba(255,255,255,0.4)"
		actionColor="rgba(255,255,255,0.5)"
		bottomHeight="50"
		topHeight="32"
		:padding="['4','8']"
		:emptyValueSelected="false"
		>
		</x-weekbar>
		<view style="height: 50px;"></view>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>

</script>

<style>

</style>
		
