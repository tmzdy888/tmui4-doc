
## 链接 xLink

***

#### 介绍

链接可以打开指定的页面,也可以打开外链(打开外链依赖于x-openweb插件,加密用户请联系发你源码自行源码编译)
微信小程序无法打开外链,微信小程序正式版本pc版本可以打开外链,真机手机仅可打开应用内页面.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-link/x-link.uvue**

#### 使用

<x-link></x-link>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| href | 需要打开的链接,可以是页面地址也可以是网页链接地址. | string | "" |
| color | 空值时取全局主题 | string | "" |
| fontSize | 字号,rpx,px,单位均可 | string | "15" |
| line | 是否需要下划线 | boolean | false |
| openType | 打开方式,如果是网页链接将启动新的窗口打开. | NAVIGATE_TYPE | "navigate" |
| prefix | 前缀图标名称 | string | "links-line" |
| suffix | 后缀图标名称 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击事件 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，仅可放置文本 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/link

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
			<x-text font-size="18" class=" text-weight-b mb-8">链接 xLink</x-text>
			<x-text color="#999999" >
				链接可以打开指定的页面,也可以打开外链(打开外链依赖于x-openweb插件,加密用户请联系发你源码自行源码编译)
			</x-text>
		</x-sheet>
		
		<x-sheet>
			<x-link href="/pages/index/button">打开应用内页面</x-link>
		</x-sheet>
		<x-sheet>
			<x-link href="https://tmui.design">打开外部链接</x-link>
		</x-sheet>
		<x-sheet>
			<x-link href="/pages/index/button" prefix='' :line="true">下划线</x-link>
		</x-sheet>
		<x-sheet>
			<x-link href="/pages/index/button" prefix='' suffix="share-circle-line">后缀图标</x-link>
		</x-sheet>
		<x-sheet>
			<x-link color="success" font-size="21" href="/pages/index/button" prefix='' suffix="share-circle-line">颜色及字号</x-link>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>
		
</script>

<style>
		
</style>

		
