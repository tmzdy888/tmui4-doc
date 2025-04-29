
## 滑动验证 xSlideVerify

***

#### 介绍

可以防止机器人刷新页面，防止恶意注册，防止恶意评论等

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-slide-verify/x-slide-verify.uvue**

#### 使用

<x-slide-verify></x-slide-verify>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽，允许使用auto,百分比，数字，带单位的字符串 | string | 'auto' |
| height | 高不允许使用auto | string | '50' |
| color | 未激活背景色 | string | '#e9ecf0' |
| activeColor | 激活时的状态背景色，空取全局 | string | '' |
| darkColor | 暗黑时的未激活背景色 | string | '#21232c' |
| successColor | 验证通过时的背景色 | string | 'success' |
| failColor | 验证失败时的背景色 | string | 'error' |
| btnColor | 按钮背景 | string | 'white' |
| btnDarkColor | 暗黑按钮背景，如果为空取sheetDarkColor | string | '#3b3e4d' |
| btnFontColor | 空取全局主题色 | string | "" |
| btnFontSize | 按钮上的图标大小 | string | "20" |
| verifyPos | 验证正确的位置<br>0-100是百分比，让用户滑动到哪个位置触发验证正确。 | number | 100 |
| showVerifyBox | 是否显示目标指示框 | boolean | false |
| tipsText | 默认的提示验证文本 | string | "请拖动到指定位置" |
| tipsTextSuccess | 失败时的文本 | string | "验证成功" |
| tipsTextFail | 成功时的文本 | string | "验证失败" |
| tipsTextColor | 底部提示文本颜色 | string | "#b8b8b8" |
| round | 圆角 | string | "25" |
| resetAuto | 验证失败时，是否自动重置 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| start | - | 开始拖动验证时触发 |
| success | - | 验证成功时触发 |
| fail | - | 验证失败时触发 |
| completed | - | 用户拖放结束时触发 |
| reset | - | 重置时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| activeLabel | 激活时的标签插槽 | - |
| btn | 拖动时的按钮插槽 | - |
| target | 目标虚拟框位置的插槽 | - |
| label | 未激活时的标签插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| reset | - | - | - |


#### 示例页面路径

/pages/qita/slide-verify

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
			<x-text font-size="18" class=" text-weight-b mb-8">滑动验证 xSlideVerify</x-text>
			<x-text color="#999999">
				可以防止机器人刷新页面，防止恶意注册，防止恶意评论等
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-slide-verify></x-slide-verify>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">显示指示框并设定目标值</x-text>
			<x-slide-verify ref='verify' :verifyPos="50" :showVerifyBox="true"></x-slide-verify>
			<x-button @click="reset" class="mt-20" :block="true">重置</x-button>
		</x-sheet>
		
		<x-sheet color="primary">
			<x-text color="white" font-size="18" class=" text-weight-b mb-8">改变样式</x-text>
			<x-slide-verify activeColor="warn" :verifyPos="80" :showVerifyBox="true" round="0"></x-slide-verify>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup lang="uts">
	
	const verify = ref<XSlideVerifyComponentPublicInstance|null>(null)
const reset = () => {
	if(verify.value==null) return;
	verify.value?.reset?.()
}
</script>

<style>

</style>
		
