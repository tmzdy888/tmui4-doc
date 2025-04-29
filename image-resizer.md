
## 图片裁剪 xImageResizer

***

#### 介绍

兼容PC操作，可双指缩放，单指平移，翻转，也可支持电脑端滚轮缩放，鼠标平移，裁剪框四角缩放，功能齐全，操作方便。
web端裁剪后返回的是Base64数据，其它端是文件连接。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-image-resizer/x-image-resizer.uvue**

#### 使用

<x-image-resizer></x-image-resizer>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| cropWidth | 裁剪框宽，px单位，裁剪后的图片不是这个大小，而是按比例缩放 | number | 300 |
| cropHeight | 裁剪框高，px单位，裁剪后的图片不是这个大小，而是按比例缩放 | number | 300 |
| compress | 压缩质量0-1 | number | 1 |
| src | 待裁剪的图片，任意地址，网络（web要注意跨域），本地地址，相对地址均可。 | string | 'http://gips1.baidu.com/it/u=1971954603,2916157720&fm=3028&app=3028&f=JPEG&fmt=auto?w=1920&h=2560' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| confirm | - | 确认时返回文件<br>ios,安卓返回的是缓存文件路径<br>web返回的是Bolb文件对象<br>微信返回的是base64图片数据 |
| cancel | - | 取消裁剪时触 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/image-resizer

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view class="imgresize" style="flex:1;background-color:#000000">
		<x-image-resizer :compress="0.5" class="imgresize" @confirm="confirm" @cancel="oncancel" 
		src="https://cdn.tmui.design/xui/tmui4.0banner1.jpg"
		></x-image-resizer>
	</view>
</template>

<script setup lang="ts">
const confirm = (path:string)=>{
	console.log(path)
}
const oncancel = ()=>{
	uni.navigateBack()
}
</script>


<style>
	/* #ifdef MP-WEIXIN */
	page,body,html{
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		background-color: black;
	}
	/* #endif */
	.imgresize{
		width: 100%;
		height: 100%;
		/* #ifdef MP-WEIXIN */
		height: 100vh;
		/* #endif */
	}
</style>


		
