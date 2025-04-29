
## 卡片 xCard

***

#### 介绍

圆角，主题可统一全局配置风格。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-card/x-card.uvue**

#### 使用

<x-card></x-card>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| padding | 内容的内边距。 | string | "16" |
| titleSize | 标题文字大小 | string | "18" |
| btnColor | 按钮颜色 | string | "" |
| color | 标题颜色 | string | "#333333" |
| bgColor | 背景颜色 | string | "#ffffff" |
| darkBgColor | 暗黑背景颜色，如果为空，取sheetDarkColor | string | "" |
| btns | 底部按钮数组。<br>如果不满意风格布局请使用插槽footer来布局 | string[] | () : string[] => [] as string[] |
| subtitle | 副标题 | string | "" |
| title | 标题 | string | "" |
| statusIcon | 右边的小图标，如果你是想显示状态，日期请使用对应插槽 | string | "more-fill" |
| content | 中间内容。如果有大量内容<br>请直接在默认插槽(标签内)内布局 | string | "" |
| image | 头部图片地址。 | string | "" |
| imageHeight | 头图片高度 | string | "150" |
| round | 圆角请不要动态更改此会，默认为空<br>取全局设置的风格值。 | string | "" |
| shadow | 请不要动态更改些投影值 | string | "0 3px 10px rgba(0, 0, 0, 0.05)" |
| btnSize |  | string | "small" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 卡片被点击 |
| status | - | 右边状态小图标被点击 |
| action | - | 底部按钮被点击<br>@@param {number} index - 按钮索引值 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| image | 图片插槽 | - |
| title | 标题插槽 | - |
| statusIcon | 状态右边小图标插槽 | - |
| subtitle | 副标题插槽 | - |
| default | 默认内容插槽 | - |
| footer | 底部插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/card

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
			<x-card class="mx-16 my-8"
			 
			image="https://store.tmui.design/api_v2/public/random_picture?random=183"
			title="我就是无法将你移除脑海" subtitle="Girl it's more than I dare to think about" :btns="['付款','详细']"
			content="女孩 我奢望的远不止于此 There's a dark secret in me 我还有个不为人知的秘密 Don't leave me locked in your heart 不要将我锁入你的心里"
			>
			</x-card>
			<x-card class="mx-16 mb-8"
			dark-bg-color="#333"
			title="我就是无法将你移除脑海" subtitle="自定义暗黑背景" :btns="['操作']"
			>
			</x-card>
			<x-card class="mx-16 mb-8"
			title="我就是无法将你移除脑海" subtitle="Girl it's more than I dare to think about" :btns="['操作']"
			>
				<x-image src="https://store.tmui.design/api_v2/public/random_picture?random=18366"></x-image>
				<x-text>
					Girl it's more than I dare to think about
					女孩 我奢望的远不止于此
				</x-text>
			</x-card>
			<x-card class="mx-16 mb-8" 
			status-icon="" title="Tmui4.0x" subtitle="Girl it's more than I dare to think about" :btns="['操作']"
			>
			</x-card>
		<view class="pa-16"></view>
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

		
