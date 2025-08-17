
## 词云 TextCloud

***

#### 介绍

实验性的组件。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-text-cloud/x-text-cloud.uvue**

#### 使用

<x-text-cloud></x-text-cloud>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽度，可任意单位 | string | '100%' |
| height | 高度，可任意单位 | string | '300rpx' |
| backgroundColor | 背景颜色 | string | 'transparent' |
| list | 数据 | TEXTCLOUD_ITEM_INFO[] | () : TEXTCLOUD_ITEM_INFO[] => [] as TEXTCLOUD_ITEM_INFO[] |
| color | 文本颜色，如果的数据中不指定统一使用这里的值。 | string | 'primary' |



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

/pages/zhanshi/text-cloud

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
			<x-text font-size="18" class=" text-weight-b mb-8">词云 TtextCloud</x-text>
			<x-text color="#999999" >把文字集中一起随机绘制，权重高的会突显变大，并居中显示。</x-text>
		</x-sheet>
		<x-sheet>
			<x-text-cloud :list="list"></x-text-cloud>
		</x-sheet>
		<x-sheet>
			<x-text-cloud :list="list2"></x-text-cloud>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { TEXTCLOUD_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			return {
				list: [
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 60, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '666', weight: 20, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '乱', weight: 30, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 20, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 80, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '世界观', weight: 40, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 20, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '666', weight: 10, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '乱', weight: 60, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 5, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '贵', weight: 10, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
					{ text: '我是词', weight: 10, color: '#e1e1e1' },
					{ text: '世界观', weight: 100, color: 'red' },
					{ text: '你好', weight: 30, color: '#e1e1e1' },
					{ text: '好', weight: 1, color: '#e1e1e1' },
					{ text: '棒', weight: 10, color: '#e1e1e1' },
					{ text: '牛逼', weight: 4, color: '#e1e1e1' },
				] as TEXTCLOUD_ITEM_INFO[],
				list2: [
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 60, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '666', weight: 20, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '乱', weight: 30, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 20, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 80, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '世界观', weight: 40, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 20, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '666', weight: 10, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '乱', weight: 60, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 5, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '贵', weight: 10, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
					{ text: '我是词', weight: 10, color: '#bababa' },
					{ text: '世界观', weight: 100, color: 'green' },
					{ text: '你好', weight: 30, color: '#bababa' },
					{ text: '好', weight: 1, color: '#bababa' },
					{ text: '棒', weight: 10, color: '#bababa' },
					{ text: '牛逼', weight: 4, color: '#bababa' },
				] as TEXTCLOUD_ITEM_INFO[]

			};
		}
	}
</script>

<style lang="scss">

</style>
		
