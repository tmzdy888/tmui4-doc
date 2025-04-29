
## 空状态 xEmpty

***

#### 介绍

主要用于列表加载页面或者空状态页面时使用。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-empty/x-empty.uvue**

#### 使用

<x-empty></x-empty>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| loading | 加载状态 | boolean | true |
| empty | 是否为空 | boolean | false |
| error | 错误状态 | boolean | false |
| more | 是否有更多数据状态 | boolean | false |
| moreLabel | 没有数据时的提示，用于加载更多数据时 | string | "没有更多数据啦" |
| errorLabel | 列表加载出错时 | string | "出错啦~" |
| btnLabel | 按钮文本 | string | "点击重试" |
| btnColor | 按钮颜色，默认取全局值 | string | "" |
| btnTextColor | 按钮文本颜色，默认自动 | string | "" |
| title | 空或者加载出错时的标语 | string | "当前没有数据" |
| src | 图片路径 | string | "/static/tmui4xLibs/static/empty.png" |
| showBtn | 是否显示重试按钮 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 刷新按钮被点击时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 按钮位置的插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/empty

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
			<x-text font-size="18" class=" text-weight-b mb-8">空状态 xEmpty</x-text>
			<x-text color="#999999" >主要用于列表加载页面或者空状态页面时使用,这是根据实际页面加载场景时最常用的状态设计。包括：错误，加载，空，没有更多。综合展现</x-text>
			<x-text color="#999999" >使用时本组件应该放在列表数据的后面。</x-text>
	
			<view class="mt-32 flex flex-row">
				<x-button class="flex-1" @click="loading=true;empty=false;error=false;more=false" >加载中</x-button>
				<x-button class="ml-12 flex-1 " @click="loading=false;empty=true;error=false;more=false" >空时</x-button>
				<x-button class="ml-12 flex-1" @click="loading=false;empty=false;error=true;more=false" >出错时</x-button>
				<x-button class="ml-12 flex-1" @click="loading=false;empty=false;error=false;more=true" >没有了</x-button>
			</view>
		</x-sheet>

		<x-empty :loading="loading" :empty="empty" :error="error" :more="more"></x-empty>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				loading: true,
				empty: false,
				error: false,
				more: false
			};
		}
	}
</script>

<style lang="scss">

</style>
		
