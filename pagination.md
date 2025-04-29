
## 翻页器 xPagination

***

#### 介绍

复杂和简便两种模式

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-pagination/x-pagination.uvue**

#### 使用

<x-pagination></x-pagination>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前页码 | number | 1 |
| disabled | 是否彬 | boolean | false |
| pageSize | 每页的数量 | number | 10 |
| total | 总条数 | number | 0 |
| maxButtons | 中间显示最多页码数量<br>注意它不是只整体页码是指多的时候中间的数量<br>如果不能理解请根据demo查看。 | number | 3 |
| minButtons | 最小显示数量<br>如果总页小于此值，直接输出所有页码，上方的maxButtons失效。 | number | 5 |
| showTotal | 是否显示总数（当simple开启时有效） | boolean | false |
| color | 当前默认背景 | string | "#f5f5f5" |
| darkColor | 暗黑时如果空值取sheet暗黑背景 | string | "" |
| activeColor | 选中时的按钮背景，如果空值取全局color | string | "" |
| btnWidth | 按钮宽，这里是最小宽 | string | "38" |
| btnHeight | 按钮高 | string | "38" |
| fontSize | 字号 | string | "14" |
| fontColor | 字号颜色 | string | "#333333" |
| fontDarkColor | 暗黑时的字号颜色 | string | "#ffffff" |
| activeFontColor | 激活时字号颜色 | string | "#FFFFFF" |
| activeFontDarkColor | 激活时暗黑的字号颜色 | string | "#ffffff" |
| round | 按钮圆角 | string | "6" |
| simple | 是否开启简单型模式。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 页码切换时触发<br>@@param {number} current 当前页码 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/pagination

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
			<x-text font-size="18" class=" text-weight-b mb-8">翻页器 xPagination</x-text>
			<x-text color="#999999" class="text-size-b mb-20">
				提供简单和复杂两种类型
			</x-text>
			<x-pagination v-model="current as number" :total="1000" @change="pageChange"></x-pagination>
		</x-sheet>
	
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-20">自定中间按钮最小数量</x-text>
			<x-pagination :total="50" :max-buttons="2"></x-pagination>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-20">简单型</x-text>
			<x-pagination :simple="true" :total="1000" :max-buttons="2"></x-pagination>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>
	import {ref} from "vue"
	const current = ref<number>(5)
	const pageChange = (index:number)=>{
		console.log("页码",index)
	}
	
</script>

<style>
		
</style>

		
