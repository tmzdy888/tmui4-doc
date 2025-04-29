
## 标签输入框 xInputTag

***

#### 介绍

可通过键盘或者按钮，输入框输入字段回车保存标签词

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-input-tag/x-input-tag.uvue**

#### 使用

<x-input-tag></x-input-tag>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| bgColor | 输入框背景及标签背景 | string | "#f5f5f5" |
| darkBgColor | 输入框的暗黑背景色<br>空值读取全局的Input暗黑背景色 | string | "" |
| btnColor | 右边按钮主题色，空取全局主题色 | string | "" |
| fontSize | 文本大小 | string | "16" |
| fontColor | 文本颜色，暗黑时取白 | string | "#333333" |
| width | 宽 | string | "auto" |
| height | 高 | string | "40" |
| round | 圆角 | string | "" |
| placeholder | 输入提示词 | string | "请输入，确认键盘添加" |
| modelValue | 双向绑定 | string[] | () : string[] => [] as string[] |
| postion | 标签在内还是在外 | POSITIONTYPE | "out" |
| showBtn | postion为in时,可以控制隐藏按钮. | boolean | true |
| btnText | 添加按钮的文本 | string | "添加标签" |
| confirmType | 设置键盘右下角按钮的文字，仅在 type为text 时生效。 | string | 'done' |
| maxCount | 最佳输入标签数量,只有用户主动输入才会触发此限制<br>你代码赋值不会限制.-1表示不限制 | number | -1 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : string[] | 标签变化时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| tag | 标签插槽，如果对标签样式不喜欢可通过此修改。 | **tags** : string[]<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/input-tag

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
			<x-text font-size="18" class=" text-weight-b mb-8">标签输入框 xInputTag</x-text>
			<x-text color="#999999" >用来自定分类时使用</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">默认标签在输入框内</x-text>
			<x-input-tag v-model="keywords"></x-input-tag>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">让标签在输入框内</x-text>
			<x-input-tag postion="in" placeholder="输入,确认添加" v-model="keywords"></x-input-tag>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				keywords: ['测试标签', '权限设置', '产品销售']
			};
		}
	}
</script>

<style lang="scss">

</style>
		
