
## 布局 xRow

***

#### 介绍

内部标签只可旋转x-col子组件。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-row/x-row.uvue**

#### 使用

<x-row></x-row>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| col | 默认列数,请不要动态修改此值。 | number | 12 |
| justify | 子元素左右对齐排列 | string | "start" |
| align | 子元素上下对齐排列<br>是align-items：值 | string | "flex-start" |
| wrap | 是否自动断行. | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 内部标签只可旋转x-col子组件。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/chongyong/row

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
		<x-sheet >
			<x-text font-size="18" class="text-weight-b mb-8">布局 xRowCol</x-text>
			<x-text color="#999999" >响应式布局，快速生成排版布局,默认12列布局，可以自行更改列的总数。</x-text>
		</x-sheet>

		<x-row class="mx-12 mb-12">
			<x-col style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">3</x-text></x-col>
			<x-col style="background-color: #55b2eb;" _class="py-15"><x-text class="text-align-center " color="white">3</x-text></x-col>
			<x-col style="background-color: #7de6a4;" _class="py-15"><x-text class="text-align-center " color="white">3</x-text></x-col>
			<x-col style="background-color: #d2b29c;" _class="py-15"><x-text class="text-align-center " color="white">3</x-text></x-col>
		</x-row>
		<x-row class="mx-12 mb-12">
			<x-col :span="6" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">6</x-text></x-col>
			<x-col :span="4" style="background-color: #55b2eb;" _class="py-15"><x-text class="text-align-center " color="white">4</x-text></x-col>
			<x-col :span="2" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">2</x-text></x-col>
		</x-row>
		<x-row class="mx-12 mb-12">
			<x-col :span="2" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">2</x-text></x-col>
			<x-col :span="4" style="background-color: #55b2eb;" _class="py-15"><x-text class="text-align-center " color="white">4</x-text></x-col>
			<x-col :span="6" style="background-color: #60cdff;" _class="py-15"><x-text class="text-align-center " color="white">6</x-text></x-col>
		</x-row>
		<x-sheet>
			<x-text font-size="18" class="text-weight-b">嵌套使用</x-text>
		</x-sheet>
		<x-row class="mx-12 mb-12">
			<x-col :span="6" style="background-color: #ffffff;" _class="py-15">
				<x-row>
					<x-col :span="6" style="background-color: #e7c4ac;" _class="py-15"><x-text class="text-align-center " color="white">6</x-text></x-col>
					<x-col :span="6" style="background-color: #dea496;" _class="py-15"><x-text class="text-align-center " color="white">6</x-text></x-col>
				</x-row>
			</x-col>
			<x-col :span="6" style="background-color: #ececec;" _class="py-15">
				<x-row>
					<x-col :span="4" style="background-color: #f8d2b9;" _class="py-15"><x-text class="text-align-center " color="white">4</x-text></x-col>
					<x-col :span="4" style="background-color: #e7c4ac;" _class="py-15"><x-text class="text-align-center " color="white">4</x-text></x-col>
					<x-col :span="4" style="background-color: #d2b29c;" _class="py-15"><x-text class="text-align-center " color="white">4</x-text></x-col>
				</x-row>
			</x-col>
		</x-row>
		<x-sheet>
			<x-text font-size="18" class="text-weight-b">自动断行形成列</x-text>
		</x-sheet>
		<x-row class="mx-12 mb-12">
			<x-col :span="12" style="background-color: #1692ff;" _class="py-15"><x-text class="text-align-center " color="white">12</x-text></x-col>
			<x-col :span="12" style="background-color: #1384e6;" _class="py-15"><x-text class="text-align-center " color="white">12</x-text></x-col>
			<x-col :span="12" style="background-color: #1171c5;" _class="py-15"><x-text class="text-align-center " color="white">12</x-text></x-col>
		</x-row>
		<x-sheet>
			<x-text font-size="18" class="text-weight-b">对齐,设置24列</x-text>
		</x-sheet>
		<x-row :col="24" class="mx-12 mb-12" justify="space-between">
			<x-col :span="11" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">11</x-text></x-col>
			<x-col :span="11" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">11</x-text></x-col>
		</x-row>
		<x-row :col="24" class="mx-12 mb-12" justify="space-between">
			<x-col :span="7" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">7</x-text></x-col>
			<x-col :span="7" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">7</x-text></x-col>
			<x-col :span="7" style="background-color: #1587eb;" _class="py-15"><x-text class="text-align-center " color="white">7</x-text></x-col>
		</x-row>
		<view style="height:40px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		computed:{
			
		}
	}
</script>

<style lang="scss">

</style>

		
