
## 返回顶部 xBacktop

***

#### 介绍

在uvue页面中，根节点一定是scroll-view并且设置为flex:1才可滚动到顶部。详见：https://doc.dcloud.net.cn/uni-app-x/api/page-scroll-to.html

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-backtop/x-backtop.uvue**

#### 使用

<x-backtop></x-backtop>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| round | 圆角,空值时取全局的drawr圆角。 | string | "50px" |
| offset | 向下滚动页面时，如果超过此值显示返回顶部按钮。 | number | 100 |
| bgColor | 背景,支持渐变值如:linear-gradient(to left, #FFED46, #FF7EC7)<br>默认空值，取全局主题值。 | string | "" |
| width | 高度 | string | '50px' |
| height | 宽度 | string | '50px' |
| color | 图标颜色。 | string | "white" |
| icon | 图标 | string | "skip-up-fill" |
| iconSize | 图标大小 | string | '30' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击组件时触发。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认图标插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/backtop

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
			<x-text font-size="18" class=" text-weight-b mb-8">返回顶部 xBacktop</x-text>
			<x-text color="#999999" >请往下滚动100px，触发显示返回顶部按钮，请注意观察右下角。</x-text>
			<view style="height: 1600px;"></view>
		</x-sheet>
		<x-backtop></x-backtop>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">

</style>
		
