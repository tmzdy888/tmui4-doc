
## 条码 xBarcode

***

#### 介绍

本条码暂只开发了cdoebar,ean13两种。ean13是国际通用码，也是国内商品的码，
我严格按照编码规则进行开发，所以提供商品码时，一定要准确。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-barcode/x-barcode.uvue**

#### 使用

<x-barcode></x-barcode>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 窗口宽 | string | 'auto' |
| height | 宽器高，这将影响条码的高度 | string | '140px' |
| pading | 上下间隙，单位是px | number | 20 |
| color | 条码颜色 | string | "black" |
| encode | 目前我仅开发两种常见的国内格式<br>codebar正常的数字字符条码<br>ean13国际通用物品编码，也是国内的商品码以69开头。 | string | "ean13" |
| text | 条码内容 | string | "" |



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

/pages/qita/barcode

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
			<x-text font-size="18" class=" text-weight-b mb-8">条码 xBarcode</x-text>
			<x-text color="#999999" >
				本条码暂支持：codebar,ean13 两种
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">ean13国内，国际商品码</x-text>
			<x-text color="#999999" class="mb-12">
				可使用淘宝等软件扫描识别
			</x-text>
			<x-sheet dark-color="#dcdcdc" :padding="['0']" :margin="['0']">
				<x-barcode encode="ean13" text="6970980210024"></x-barcode>
			</x-sheet>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">codebar，常规条码</x-text>
			<x-text color="#999999" class="mb-12">
				需要专用的识别软件或者条码器识别，见：https://products.aspose.app/barcode/zh-hans/recognize#
			</x-text>
			
			<x-sheet dark-color="#dcdcdc" :padding="['0']" :margin="['0']">
				<x-barcode encode="codebar" text="6970980210024"></x-barcode>
			</x-sheet>
		</x-sheet>
		
		<view style="height:50px"></view>
		
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
		
