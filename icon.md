
## 图标 xIcon

***

#### 介绍

图标使用的是开源图标:[https://remixicon.com/](https://remixicon.com/)，版本是：4.5.0 ，使用时，不用带ri-前缀。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-icon/x-icon.uvue**

#### 使用

<x-icon></x-icon>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| name | 图标名称，不带ri-前缀<br>也可以是本地或者远程图片 | string | "home-3-fill" |
| fontSize | 图标大小,单位任意,比如"12",12px,12rpx | string | "16" |
| fontFamily | 自定义图标字体，前提是<br>你要在appuvue中已经安装好字体文件，<br>否则无法使用。<br>要让自定图标生效你需要配合code属性一起使用 | string | "remixicon" |
| code | 图标的16进制字符串，注意不含u<br>比如：ea0c，ea14这种，<br>如果你提供了code优化解析这，那么name将失效，如果你是纯字体图标使用<br>你可以使用这个属性，可以提供性能和自己定义的图标会比较方便。 | string | "" |
| color | 图标颜色 | string | "black" |
| darkColor | 暗黑时的文本颜色，如果你不提供，将自动反转。<br>自动反转是根据亮度反转，色相不变。 | string | "" |
| spin | 是否旋转动画 | boolean | false |
| rotation | 旋转角度 | number | 0 |
| duration | 动画时间 | number | 1500 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/chongyong/icon

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
			<x-text font-size="18" class="text-weight-b mb-8">图标 Icon</x-text>
			<x-text color="#999999" class="line-8">使用开源图标remixicon：https://remixicon.com/</x-text>
			<x-text color="error" class="line-8">name:只要名称就行，不要ri-前缀，比如router-line</x-text>
		</x-sheet>

		<x-sheet class="flex flex-row flex-row-center-between">
			<x-icon name="chat-3-line"></x-icon>
			<x-icon name="chat-3-fill"></x-icon>
			<x-icon name="contrast-drop-2-fill"></x-icon>
			<x-icon name="circle-line"></x-icon>
			<x-icon name="smartphone-line"></x-icon>
			<x-icon name="git-repository-private-fill"></x-icon>
			<x-icon name="mouse-fill"></x-icon>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">旋转 Rotation</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-start">
			<x-icon color="primary" font-size="32" name="arrow-up-line"></x-icon>
			<x-icon color="primary" :rotation="90" font-size="32" name="arrow-up-line"></x-icon>
			<x-icon color="primary" :rotation="180" font-size="32" name="arrow-up-line"></x-icon>
			<x-icon color="primary" :rotation="270" font-size="32" name="arrow-up-line"></x-icon>

		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">颜色 color</x-text>
			<x-text color="#999999" class="  ">更多属性见文档</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-between">
			<x-icon color="red" font-size="32" name="information-line"></x-icon>
			<x-icon color="primary" font-size="32" name="gps-line"></x-icon>
			<x-icon color="orange" font-size="32" name="headphone-line"></x-icon>
			<x-icon color="tea" font-size="32" name="rocket-fill"></x-icon>
			<x-icon color="green" font-size="32" name="mic-2-line"></x-icon>
			<x-icon color="blue" font-size="32" name="image-circle-line"></x-icon>
			<x-icon color="moccasin" font-size="32" name="plane-line"></x-icon>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">动画 Spin</x-text>
		</x-sheet>
		<x-sheet >
			<x-icon :spin="true" font-size="64" color="red" name="loader-4-fill" ></x-icon>
		</x-sheet>

		<view class="py-32"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>


<script lang="uts">
	export default {
		data() {
			return {
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>
		
