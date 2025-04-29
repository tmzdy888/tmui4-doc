
## 消息条 xSnackbar

***

#### 介绍

消息条是可以在上方或者正文累加显示，新的消息在旧的前面。而不会只显示一条，会自动消失。支持6个方向的弹出

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-snackbar/x-snackbar.uvue**

#### 使用

<x-snackbar></x-snackbar>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| offset | 距离顶/底的偏移量。 | string | '12px' |
| block | 是否让消息条横屏占满，默认是根据内容自动宽。 | boolean | false |
| content | 消息数据<br>注意，id一定要提供且是数字，可以随意，只要相对上一次变更下，就会触发<br>显示新的消息条。这种显示的方式就是避免你们引用ref方式来调用方法，相对更简单。 | SNACKBAR_INFO | () : SNACKBAR_INFO => {<br>    return {<br>        background: "",<br>        color: "",<br>        fontSize: "",<br>        content: "",<br>        id: -1,<br>        icon: ""<br>    } as SNACKBAR_INFO<br>} |
| duration | 多少毫秒后销毁 | number | 2500 |
| position | 出现的位置<br>top:正上方<br>top-left:左上方<br>top-right:右上角<br>bottom-right:右下角<br>bottom-left:左下角<br>bottom:正下方 | string | 'bottom' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/snackbar

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
			<x-text font-size="18" class=" text-weight-b mb-8">消息条 Snackbar</x-text>
			<x-text color="#999999">
				位置可以在顶或者底，并且不需要ref函数来实现，我创新的通过使用变量id更改来发送新的消息条。
				消息条是无限累加在旧消息条的前面,并且现在支持6个方向的弹出.
			</x-text>
		</x-sheet>
		<x-snackbar position="top" :content="content"></x-snackbar>
		<x-sheet>
			<x-button :block="true" @click="randMsg">随机一条顶部消息</x-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">可以设置为横幅尺寸和自定样式</x-text>
		</x-sheet>
		<x-snackbar :block="true" :content="content2"></x-snackbar>
		<x-sheet>
			<x-button color="warn" :block="true" @click="randMsg2">随机一条底部消息</x-button>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="uts" setup>
	import { SNACKBAR_INFO } from '@/uni_modules/tmx-ui/interface.uts';
	const content = ref<SNACKBAR_INFO>({
		id: -1,//-1表示 不显示。
		content: ""
	})
	const content2 = ref<SNACKBAR_INFO>({
		id: -1,//-1表示 不显示。
		content: ""
	})
	const randMsg = () => {
		content.value = {
			id: content.value.id + 1,
			content: "测试标题" + content.value.id.toString()
		} as SNACKBAR_INFO
	}
	const randMsg2 = () => {
		content2.value = {
			id: content2.value.id + 1,
			content: "可以随意定义颜色可以随意定义颜色" + content2.value.id.toString(),
			background: 'red',
			icon: "close-circle-line"
		} as SNACKBAR_INFO
	}
</script>

<style lang="scss">

</style>
		
