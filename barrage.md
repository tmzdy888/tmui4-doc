
## 弹幕 Barrage

***

#### 介绍

弹幕，当前版本比较初级。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-barrage/x-barrage.uvue**

#### 使用

<x-barrage></x-barrage>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| layerHeight | 弹幕的总高度。如果你的容器高小于此高会被裁切。 | string | "" |
| list | 字符数组 | string[] | () : string[] => [] as string[] |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认内容插槽，内容的高度至少要大于弹幕整体的layerHeight高度。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/barrage

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view>
		<x-sheet color="primary">
			<x-barrage :list="list" layerHeight="160rpx">
				<x-sheet :margin="['0']" >
					<x-text font-size="18" class=" text-weight-b mb-8">弹幕 Barrage</x-text>
					<x-text color="#999999" >
						主要是营销使用，比如安蕾尔活动的滚动，互动等。
						本弹幕是比较初级的，不支持暂停，重播，因为牵涉计算滚动位置（耗性能），因此初版本采用自然动画。如果要重设内容，只需要重新赋值即可，位置和内容会自动更新。
						如果有需求，将使用绘制来重新改写模板。
					</x-text>
					<x-button class="mt-32" :block="true" @click="restart">重新播放</x-button>
				</x-sheet>
			</x-barrage>
		</x-sheet>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					"老子6666",
					"陈**已购买1万大礼包",
					"李世民来了哦",
					"哦豁~",
					"那个甄姬太坏了，巴不得早点死！",
					"我看Xui非常好用。推荐",
					"TMUI.DESIGN",
					"大家都是VIP8，躁起来！！！",
					"不错。",
					]
			};
		},
		onLoad() {
			
		},
		methods: {
			restart() {
				this.list = [
					"老子6666",
					"陈**已购买1万大礼包",
					"李世民来了哦",
					"哦豁~",
					"那个甄姬太坏了，巴不得早点死！",
					"我看Xui非常好用。推荐",
					"TMUI.DESIGN",
					"大家都是VIP8，躁起来！！！",
					"不错。",
					]
			}
		},
	}
</script>

<style lang="scss">

</style>

		
