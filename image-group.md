
## 图集 xImageGroup

***

#### 介绍

主要是为了一些需要快速图片排版集的展示，比如评论图集，详情列表图集等，快速开发时使用。方便快捷。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-image-group/x-image-group.uvue**

#### 使用

<x-image-group></x-image-group>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 图片列表<br>只要包含有url字段即可。<br>label需要在图片显示的文本字段，如果没有不要出现此字段<br>如果提供了temp缩略图，会优先展示temp字段，预览时采用url原图<br>{url:string,label?:string,temp?:string} | UTSJSONObject[] | () : UTSJSONObject[] => [] as UTSJSONObject[] |
| model | 显示的模式见：https://doc.dcloud.net.cn/uni-app-x/component/image.html | string | "scaleToFill" |
| height | 图片高,不要使用auto，%， | string | "100" |
| width | 图片宽,不要使用auto，可以%值 | string | "33.33%" |
| gutter | 间隙 | string | "2" |
| labelModel | inset表示文本在图片上<br>ouuter表示文本在正文展示<br>不要动态修改 | string | "inset" |
| labelFontSize | 如果有文字显示文字的大小 | string | "14" |
| labelFontColor | 如果有文字，显示文字的颜色 | string | "white" |
| darkLabelFontColor | 如果有文字，显示文字的颜色，暗黑时为空时取白 | string | "" |
| preview | 是否预览图片 | boolean | true |
| round |  | string | '0' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 图片项目被点击 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/image-group

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
			<x-text font-size="18" class=" text-weight-b mb-8">图集 xImageGroup</x-text>
			<x-text color="#999999" class="mb-12">主要是为了一些需要快速图片排版集的展示，比如评论图集，详情列表图集等，快速开发时使用。方便快捷</x-text>
			<x-image-group round="6" :list="list"></x-image-group>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">宽允许百分比，方便响应式</x-text>
			<x-image-group round="6"  width="50%" :list="list3"></x-image-group>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">允许显示label在图片上</x-text>
			<x-image-group round="6"  :list="list2"></x-image-group>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">label在图片下上</x-text>
			<x-image-group height="140" labelModel="outter" label-font-color="#333" dark-label-font-color="#afafaf" :list="list2"></x-image-group>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				list: [
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18a32' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18f33' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18c43' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=1843' } as UTSJSONObject,
				] as UTSJSONObject[],
				list3: [
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=1a8a32' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18ff33' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18ff33' } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18ac43' } as UTSJSONObject,
				] as UTSJSONObject[],
				list2: [
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=18d32', label: "原生开发通常指的是为特定平台（如iOS或Android）使用该平台" } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=183s3', label: "使用该平台" } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=184f3', label: "通常指的是为特定平" } as UTSJSONObject,
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=184x3', label: "该平" } as UTSJSONObject,
				] as UTSJSONObject[]
			};
		}
	}
</script>

<style lang="scss">

</style>
		
