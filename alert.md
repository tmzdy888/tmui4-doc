
## 警告 xAlert

***

#### 介绍

样式丰富常用警告提醒

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-alert/x-alert.uvue**

#### 使用

<x-alert></x-alert>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| status | 类型<br>warn:警告<br>success:成功<br>error:错误<br>info:信息<br>primary:正常主题 | string | "primary" |
| icon | 警告图标,不填写取status默认图标<br>填写以填写为准 | string | "" |
| iconSize | 警告图标大小 | string | "20" |
| closeIcon |  | string | "close-line" |
| showClose | 显示还是隐藏关闭按钮 | boolean | true |
| fontSize | 文字大小 | string | "15" |
| color | 主题色，如果不填写以status为准 | string | "" |
| fontColor | 文字颜色，如果不填写以status为准 | string | "" |
| darkColor | 暗黑主题颜色，如果不填写自动计算 | string | "" |
| fontDarkColor | 暗黑文字颜色，如果不填写自动计算 | string | "" |
| skin | 它是建立在你没有提供color时才有效。<br>如果提供了color是以你color为背景最终色。<br>thin浅色模式，<br>normal标准背景色 | string | "thin" |
| round | 圆角<br>数组数字时<br>[全部]<br>[顶左，顶右，底右，底左]<br>[顶左，底右]<br>[顶左，顶右，底右]<br>空数组时取全局值 | string[] | () : string[] => [] |
| border | 边线<br>数组数字时<br>数组数字时<br>[全部]<br>[左，上，右，下]<br>[左右，上下]<br>[左，上，右]<br>空数组时取全局值 | string[] | () : string[] => [] |
| borderColor | 边框颜色<br>格式同border边线。<br>空数组时取全局值 | string[] | () : string[] => [] |
| darkBorderColor | 如果不填写，自动计算 | string[] | () : string[] => [] |
| borderStyle | 边线类型，默认solid,可以为none | string | 'solid' |
| margin | 间隙[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值 | string[] | () : string[] => ['16', '0', '16', '16'] as string[] |
| padding | 内间隙[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值 | string[] | () : string[] => ['16', '12'] as string[] |
| height | 自定义高度，可以是数字，单位或者百分比,auto | string | "auto" |
| width | 宽，单位合法即可数字，字符串带单位，百分比,auto | string | "auto" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| close | - | 关闭时触发 |
| click | - | 组件被点击时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| left | 左边图标插槽 | - |
| default | 默认插槽内容 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/alert

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
			<x-text font-size="18" class=" text-weight-b mb-8">警告 xAlert</x-text>
			<x-text color="#999999">
				样式丰富，用于警告信息的提醒。
			</x-text>
		</x-sheet>
		<x-alert>默认为thin浅色样式，可以自适应暗黑</x-alert>
		<x-alert skin='normal'>也可以把skin改成normal变成纯背景</x-alert>
		<x-alert icon="building-fill" skin='normal' color="#000000">也可以把skin改成normal变成纯背景</x-alert>
		<x-alert icon="building-fill" skin='normal' color="#dee3e7">也可以把skin改成normal变成纯背景</x-alert>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">可以使用默认的状态来管理颜色</x-text>
		</x-sheet>
		<x-alert icon="file-word-2-fill" status="success" skin='normal'>自定义图标</x-alert>
		<x-alert status="error" skin='normal'>错误提醒</x-alert>
		<x-alert status="warn" closeIcon="arrow-right-line" skin='normal'>警告提醒</x-alert>
		<x-alert icon="money-cny-circle-fill" color="#728398" skin='normal'>自定义背景色</x-alert>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">比如改些圆角，边线啥的,样式丰富请自行设计</x-text>
		</x-sheet>
		<x-alert status="warn" skin='normal' :round="['6']">警告提醒</x-alert>
		<x-alert status="error" skin='normal' :round="['12','0']">改下圆角</x-alert>
		<x-alert :border="['2']" >加个小边框</x-alert>
		<x-alert :border="['2']" :showClose="false"  :borderColor="['#89c0ff']" :darkBorderColor="['#3b5066']">加个小边框,隐藏关闭</x-alert>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>

</script>

<style>

</style>
		
