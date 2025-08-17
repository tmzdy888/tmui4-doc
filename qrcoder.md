
## 二维码 xQrcoder

***

#### 介绍

本组件使用UTS原生代码绘制，性能非常高，如果你是在1.1.9之前版本请使用x-qrcoder-s原生插件获得高性能。从1.1.9版本后请
使用组件绘制QR码来获得更高性能和更多样式配置。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-qrcoder/x-qrcoder.uvue**

#### 使用

<x-qrcoder></x-qrcoder>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 窗口宽 | string | '250px' |
| height | 宽器高，这将影响条码的高度 | string | '250px' |
| color | 码颜色 | string | "primary" |
| bgColor | 码背景颜色 | string | "white" |
| posColor | 码的定位点颜色,不填写和原前景一致 | string | "" |
| text | 条码内容 | string | "https://xui.tmui.design" |
| logo | 是否绘制Logo到qr上。 | string | "" |
| logoBgColor | 是否绘制Logo到qr上。 | string | "#fff" |
| logoSize | logo大小。 | string | "50px" |
| padding | 边距 | number | 2 |
| mode | 绘制的样式目前提供<br>rect ：普通码矩形<br>circular ：小圆点<br>line ：线条<br>rectSmall ：小方格 | string | "rect" |



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

/pages/qita/qrcoder

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
			<x-text font-size="18" class=" text-weight-b mb-8">二维码 Qrcoder</x-text>
			<x-text color="#999999" >
				本组件绘制QR码性能非常高和以及更多的样式配置。并且不依赖第三方插件完全自绘制。提供了四种类型。
			</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-center ">
				<x-qrcoder mode="rectSmall" ref="qxqr" :text="text" :logo="logo"></x-qrcoder>
			</view>
			<x-input class="my-16" v-model="text"></x-input>
			<view class="flex flex-row flex-row-center-between mb-16">
				<x-button width="48%" @click="addLogo">添加Logo</x-button>
				<x-button width="48%" @click="logo=''">去除Logo</x-button>
			</view>
			<x-button :block="true" @click="getImgQr">查看码图片</x-button>
			
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">修改颜色，尺寸，样式</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row-center-center flex-row">
			<x-qrcoder width="105px" height="105px" color="red"></x-qrcoder>
			<x-qrcoder class="mx-5" width="105px" mode="line" height="105px" ></x-qrcoder>
			<x-qrcoder  pos-color="error" width="105px" mode="circular" height="105px" color="black"></x-qrcoder>
		</x-sheet>
		<view style="height:100px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				logo: "",
				text:"https://tmui.design"
			};
		},
		methods: {
			addLogo() {
				this.logo = "/static/tmui4xLibs/static/empty.png"
			},
			getImgQr(){
				let el = this.$refs["qxqr"] as XQrcoderComponentPublicInstance
				el!.getQrImg((imgstr:string)=>{
					if(imgstr=='') return;
					uni.previewImage({
						current:imgstr,
						urls:[imgstr] as string[]
					})
				})
			}
		},
	}
</script>

<style lang="scss">

</style>
		
