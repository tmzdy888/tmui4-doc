
## 列表 xCell

***

#### 介绍

card为true时，圆角可统一全局配置和动态全局配置，保持所有页面列表样式统一，免于一个一个配置。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-cell/x-cell.uvue**

#### 使用

<x-cell></x-cell>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| icon | 左图标 | string | "" |
| avatarRound | 左侧图标、头像圆角。默认为8 | string | "8" |
| color | 背景的主题色 | string | 'white' |
| darkColor | 暗黑背景的主题色，空值时取sheetDarkColor | string | '' |
| iconColor | 图标色,空值时取全局主题值。 | string | "" |
| title | 标题 | string | "标题" |
| titleColor | 标题颜色 | string | "black" |
| darkTitleColor | 暗黑标题颜色，如果不填写取白 | string | "white" |
| titleSize | 标题大小 | string | "16" |
| iconSize | 图标大小 | string | "24" |
| label | 右边文本 | string | "" |
| labelColor | 右边文本颜色 | string | "#bfbfbf" |
| labelSize | 右侧label文字大小 | string | "13" |
| desc | 标题正文的简介文本 | string | "" |
| showBottomBorder | 是否显示下边线 | boolean | true |
| bottomBorderInsert | 是否让下边线显示居右，不贯穿到左边。 | boolean | false |
| bottomBorderColor | 下边线的颜色。如果你设定了的话。<br>暗黑的边颜色失效，采用你自定的颜色。 | string | "" |
| link | 是否显示链接状态，有点按效果。包括出现右边跳转指示。<br>关闭的话，事件反应和跳转会更快。<br>如果true右侧箭头图标会显示 | boolean | true |
| linkColor | 右指示图标的颜色 | string | '#bfbfbf' |
| linkDarkColor | 右指示图标的暗黑颜色 | string | '#bfbfbf' |
| url | 需要跳转的页面地址。<br>如果填写了右侧箭头图标会显示<br>跳转时如果失败会回退到switchTab跳转。 | string | "" |
| card | 是否是卡片模式 | boolean | true |
| round | 卡片模式圆角,不填写采用全局的cardRadius属性值. | string | "" |
| leftSize | 左边图标区域宽和高的大小。 | string | '32' |
| minHeight | 最小高度，主要是用来统一风格高度不至于让点击范围过小<br>如果你需要紧凑型可以设置为auto | string | "55" |
| disabled | 是否禁用url跳转，当link为true或者url需要跳转时<br>如果禁用，点击时不会触发跳转。 | boolean | false |
| padding | 内间隙[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值 | string[] | () : string[] => ['12','0'] as string[] |
| margin | margin 同sheet原理<br>[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值cellMargin | string[] | () : string[] => [] as string[] |
| rightWidth | 右侧label宽，插槽时，这个属性不会生效<br>以你自己布局宽为准。 | string | "100" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 整个列表被点击 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| avatar | 头像图标 | **icon** : string<br> |
| default | 默认标题插槽 | - |
| desc | 简介 | **desc** : string<br> |
| label | 右边文字 | **label** : string<br> |
| right | 右插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/cell

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
			<x-text font-size="18" class=" text-weight-b mb-8">列表组 Cell</x-text>
			<x-text color="#999999">
				插槽丰富方便自定义自己的样式
			</x-text>
		</x-sheet>

		<x-cell :link="false" url="/pages/index/button" icon="apps-line" title="常见组件库"></x-cell>
		<x-cell title="应用设置" url="/pages/index/icon" icon="price-tag-3-line" label="+￥32非卡片模式非卡片模式非卡片模式非卡片模式" label-color="red"
			icon-color="red"></x-cell>
		<x-cell title="聊天介绍" url="/pages/index/tag" icon="message-3-line" label="tmx测试" icon-color="green"></x-cell>

		<x-sheet :margin="['16']">
			<x-text font-size="18" class=" text-weight-b ">非卡片模式 Cell</x-text>
			<x-text color="#999999">
				底边线可以左对齐或者右内对齐。
			</x-text>
		</x-sheet>

		<x-sheet :padding="['0']">
			<x-cell :bottomBorderInsert="true" :card="false" url="/pages/index/button" icon="color-filter-line"
				desc="UTS版本tmui组件库,高质量库" title="常见组件库"></x-cell>
			<x-cell title="价格设置" :bottomBorderInsert="true" :card="false" url="/pages/index/icon" icon="server-line"
				label="+￥32" label-color="red" icon-color="red"></x-cell>
			<x-cell title="书签读书" :bottomBorderInsert="true" :card="false" icon="book-marked-line" url="/pages/index/tag"
				label="tmx测试" icon-color="orange"></x-cell>
			<x-cell title="标签页面" :bottomBorderInsert="true" :card="false" :show-bottom-border="false" icon="gift-line"
				url="/pages/index/tag" label="tmx测试" icon-color="success"></x-cell>
		</x-sheet>




		<view class="py-32"></view>
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
		onLoad() {

		}
	}
</script>

<style lang="scss">

</style>
		
