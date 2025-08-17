
## 头像组 xAvatarGroup

***

#### 介绍

平铺和堆叠方式。如果想要单头像建议使用：xSheet+xImage配合，+xBadge达到效果，因此我不再提供单头像组件，没有意义。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-avatar-group/x-avatar-group.uvue**

#### 使用

<x-avatar-group></x-avatar-group>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 头像列表,也可以是文本数组，也可以是空字符串数组 | string[] | () : string[] => [] as string[] |
| size | 不允许使用auto,%只能数字或者带单位的数字2px,2rpx这种 | string | '32' |
| maxCount | 最多显示几个头像。 | number | 5 |
| round | 圆角 | string | '16' |
| gutter | 平铺或者堆叠时的间隙或者前推差值。<br>不允许使用auto,%只能数字或者带单位的数字2px,2rpx这种 | string | '16' |
| model | 显示类型见：<br>https://doc.dcloud.net.cn/uni-app-x/component/image.html#%E5%B1%9E%E6%80%A7 | string | "scaleToFill" |
| count | 显示在最后一个时，显示的数字。如果为0取list的长度 | number | 0 |
| showCount | 是否显示最后一个数字头像 | boolean | true |
| flat | 是否平铺，如果否就是堆叠。是就是正常排列。 | boolean | false |
| bgColor | 如果为文本头像时的背景 | string | "#f5f5f5" |
| darkBgColor | 如果为文本头像时的暗黑背景<br>空时默认取inputDarkBgcolor | string | "" |
| fontColor | 如果为文本头像时的文字颜色 | string | "#a6a6a6" |
| darkFontColor | 如果为文本头像时的暗黑背景<br>空时默认取inputDarkBgcolor | string | "#ffffff" |
| fontSize | 字号 | string | "14" |
| randomBgColor | 文本头像时，是否随机背景色 | boolean | false |
| placeIcon | 如果当图片或者文本为空时的图片占位符<br>可以是图片地址或者图标名称 | string | 'user-3-fill' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | **index** : number**src** : string | 头像被点击时 |
| moreClick | - | 最后一个数字头像more被点击时 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| more | more更多插槽，如果使用了这个插槽moreClick事件会丢失，请自己写在自己的布局上。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/avatar-group

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
			<x-text font-size="18" class=" text-weight-b mb-8">头像组 xAvatarGroup</x-text>
			<x-text color="#999999">
				平铺和堆叠方式。如果想要单头像建议使用：xSheet+xImage配合，+xBadge达到效果，因此我不再提供单头像组件，没有意义。
			</x-text>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">堆叠</x-text>
			<x-avatar-group :list="list" :max-count="8"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">平铺</x-text>
			<x-avatar-group :list="list" :flat="true" :max-count="8" gutter="3"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">控制圆角及显示数量</x-text>
			<x-avatar-group :list="list" round="4" :flat="true" :max-count="8" :count="1000" gutter="3"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">文本头像</x-text>
			<x-avatar-group :list="list2" round="4" :flat="true" :max-count="8" :count="1000" gutter="3"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">文本头像随机颜色</x-text>
			<x-avatar-group :randomBgColor="true" :list="list2" round="4" :flat="true" :max-count="8" :count="1000" gutter="3"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">头像与文本混搭,空时图标占位</x-text>
			<x-avatar-group :randomBgColor="true" :list="list3" round="4" :flat="true" :max-count="8" :count="1000" gutter="3"></x-avatar-group>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">插槽定制more</x-text>
			<x-avatar-group :list="list" round="4" :flat="true" :max-count="4" :count="1000" gutter="3">
				<template v-slot:more>
					<x-sheet class="flex flex-center" width="32" height="32" :round="['4']" :margin="['0']" :padding="['0']" color="primary">
						<x-icon color="white" name="add-line"></x-icon>
					</x-sheet>
				</template>
			</x-avatar-group>
		</x-sheet>
		<view style="height: 32px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>
		const list = [
			"https://store.tmui.design/api_v2/public/random_picture?random=183",
			"https://store.tmui.design/api_v2/public/random_picture?random=13",
			"https://store.tmui.design/api_v2/public/random_picture?random=8",
			"https://store.tmui.design/api_v2/public/random_picture?random=83",
			"https://store.tmui.design/api_v2/public/random_picture?random=18",
			"https://store.tmui.design/api_v2/public/random_picture?random=3",
			"https://store.tmui.design/api_v2/public/random_picture?random=8",
			"https://store.tmui.design/api_v2/public/random_picture?random=83",
			"https://store.tmui.design/api_v2/public/random_picture?random=18",
			"https://store.tmui.design/api_v2/public/random_picture?random=3",
		] as string[]
		const list2 = [
			"同名自定义",
			"Dclound",
			"ak",
			"sk",
			"国家",
			"天清色",
			"漂亮",
			"相爱一家人",
			"北京",
			"厉害了我的哥",
			"呃",
		] as string[]
		const list3 = [
			"同名自定义",
			"https://store.tmui.design/api_v2/public/random_picture?random=8",
			"",
			"sk",
			"https://store.tmui.design/api_v2/public/random_picture?random=3",
			"",
			"漂亮",
			"https://store.tmui.design/api_v2/public/random_picture?random=3",
			"北京",
			"https://store.tmui.design/api_v2/public/random_picture?random=83",
			"呃",
		] as string[]
</script>

<style>
		
</style>

		
