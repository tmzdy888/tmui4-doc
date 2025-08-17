
## 思维导图 xTreeFlat

***

#### 介绍

主要用来展示平面树平面结构,思维导图的展示

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-tree-flat/x-tree-flat.uvue**

#### 使用

<x-tree-flat></x-tree-flat>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| canvasWidth | 画板宽,总宽不要小于节点展开后的宽,可以尽量设置大点 | number | 800 |
| canvasHeight | 画板高,总高不要小于节点展开后的高,可以尽量设置大点 | number | 800 |
| width | 组件宽 | string | '100%' |
| height | 组件高,不能为auto | string | '600' |
| list | 动态数据 | Array | [] as XTREEFLAT_NODES[] |
| opts |  | union | null as XTreeFlatOpts|null |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| init | - | 引擎初始化完成,可以进行通过ref来异步设置数据 |
| change | - | 当list数据被编辑变动时触发 |
| click | **** : item:XTREEFLAT_CHILDREN | 当前节点被点击时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| setData | - | - | - |


#### 示例页面路径

/pages/qita/tree-flat

#### 示例源码

<template>
	<!-- #ifdef APP -->
	<scroll-view style="flex:1">
	<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
			<navigation-bar :background-color="xThemeConfigNavBgColor"
				:front-color="xThemeConfigNavFontColor"></navigation-bar>
		</page-meta>
		<!-- #endif -->
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">思维导图 xTreeFlat</x-text>
			<x-text color="#999999">
				这是一个横向布局的思维导图,可以用来展示结构或组织架构或流程,纯原生绘制,性能高
			</x-text>
		</x-sheet>
		<view class="flex-1">
			<!-- :list="nodes"  -->
			<x-tree-flat :opts="opts" ref="xmind" @init="oninit" height="100%"></x-tree-flat>
		</view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>
	import { XTreeFlatOpts,XTREEFLAT_NODES } from '@/uni_modules/tmx-ui/interface';
	import mockDatalist from "./mock.uts"
	const xmind = ref<XTreeFlatComponentPublicInstance | null>(null)
	const opts = { lineWidth:2 } as XTreeFlatOpts
	const oninit = () => {
		console.warn("导图引擎启动成功，可以设置数据了")
		xmind.value!.setData(mockDatalist)
	}
</script>

<style>
	/* #ifdef MP */
	page,
	body {
		height: 100vh;
		display: flex;
		flex-direction: column;
	}

	/* #endif */
</style>
		
