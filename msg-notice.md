
## 消息通知 xMsgNotice

***

#### 介绍

本组件可以通过左右拖拉关闭消息，往左拉，左关闭，右拉右关闭，有阻尼回弹效果，可单独设置。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-msg-notice/x-msg-notice.uvue**

#### 使用

<x-msg-notice></x-msg-notice>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 打开和关闭状态<br>等同v-model,如果使用:modelValue将不受控. | boolean | true |
| duration |  | number | 450 |
| threshold | 当滑动时小于此值，会回弹到原位。而不执行关闭 | number | 64 |
| round | 圆角,空值时取全局的drawr圆角。 | string | "" |
| position | 显示位置top,bottom | string | "bottom" |
| offset | 距离边界的偏移量 | string | "12px" |
| bgColor | 背景 | string | "white" |
| darkBgColor | 暗黑的背景，如果不提供，读取sheetDarkColor | string | "" |
| clickClose | 点击组件是否关闭通知 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 组件点击事件 |
| update:modelValue | - | 等同v-model,<br>在使用时，要选同步关闭，再同步打开这样循环，<br>类似于ref方法on,off方式。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/msg-notice

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
			<x-text font-size="18" class=" text-weight-b mb-8">也可变量控制</x-text>
			<view class="flex flex-row flex-row-center-between">
				<x-button width="48%" @click="onClick(true)">打开底部消息条</x-button>
				<x-button width="48%" @click="onClick(false)" color="error">关闭询问消息条</x-button>
			</view>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">消息通知 xMsgNotice</x-text>
			<x-text color="#999999" >
				本组件可以通过左右,上下拖拉关闭消息，往向不同方向拉手势,会向指定方向关闭，有阻尼回弹效果，可单独设置。
			</x-text>
		</x-sheet>
		<x-msg-notice :model-value="true" position="top">
			<x-sheet color='primary' :margin="['0']">
				<x-text color="white" class="text-size-g text-weight-b">左右或者向上拉可关闭</x-text>
				<x-text color="white" class="text-size-m text-grey mt-10  line-8">本组件可以通过左右,上下拖拉关闭消息，往向不同方向拉手势,会向指定方向关闭，有阻尼回弹效果，可单独设置。</x-text>
			</x-sheet>
		</x-msg-notice>
		<x-msg-notice v-model="show">
			<x-sheet>
				<x-text class="text-size-g text-weight-b">消息通知 xMsgNotice</x-text>
				<x-text class="text-size-m text-grey mt-10  line-8">本组件可以通过左右,上下拖拉关闭消息，往向不同方向拉手势,会向指定方向关闭，有阻尼回弹效果，可单独设置。</x-text>
			</x-sheet>
		</x-msg-notice>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				show: false
			};
		},
		methods: {
			onClick(isshow : boolean) {
				this.show = isshow;

			}
		},
	}
</script>

<style lang="scss">

</style>
		
