
## 查看更多 xMore

***

#### 介绍

让内容超过指定高时自动隐藏内容.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-more/x-more.uvue**

#### 使用

<x-more></x-more>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 组件宽度 | string | "auto" |
| height | 被关闭时的高度。 | string | "60" |
| modelValue | 当前打开的状态 | boolean | false |
| activeColor | 激活后的文本色,默认是读取全局色 | string | "" |
| unActiveColor | 未激活后的文本色 | string | "#a6a6a6" |
| text | 打开和关闭状态的文本 | string[] | () : string[] => ["展开更多", "收起更多"] |
| maskBgColor | 遮罩的渐变的背景色 | string[] | () : string[] => ['rgba(255, 255, 255, 1)', 'rgba(255, 255, 255, 0.3)'] |
| darkMaskBgColor | 暗黑时遮罩的渐变的背景色 | string[] | () : string[] => ['rgba(24, 24, 24, 1.0)', 'rgba(24, 24, 24, 0.3)'] |
| disabled | 是否禁用展开。 | boolean | false |
| showMoreBtn | 是否显示开启和关闭按钮,<br>因为各个手机屏幕可能不一样,可能会根据行数自行决定是否<br>要显示展开和关闭按钮,请通过此自行判断. | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **opened** :  boolean  | 状态切换时变换 |
| click | - | 点击展开的按钮时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/more

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
			<x-text font-size="18" class=" text-weight-b mb-8">查看更多 xMore</x-text>
			<x-text  color="#999999" >更多信息展示使用,在使用时注意内部不要放动态异步加载内容。</x-text>
		</x-sheet>
		<x-sheet>
			<x-more >
				<x-text class="line-10">
					随后，行刑者用一根管子放出温水顺着死刑犯的手臂往下流。并在地上放置一个铁盆，让水流到盆里的声音“嘀哒嘀哒“作响，给罪犯造成是自己流血的错觉。
					随着水流越来越慢，水温越来越低，声音越来越小。
					没过多久，罪犯就断气而身亡。尸检发现，罪犯死于心脏麻痹。
					随后，行刑者用一根管子放出温水顺着死刑犯的手臂往下流。并在地上放置一个铁盆，让水流到盆里的声音“嘀哒嘀哒“作响，给罪犯造成是自己流血的错觉。
					随着水流越来越慢，水温越来越低，声音越来越小。
					没过多久，罪犯就断气而身亡。尸检发现，罪犯死于心脏麻痹。
				</x-text>
				<x-image src="https://store.tmui.design/api_v2/public/random_picture?random=vsf"></x-image>
			</x-more>
			<x-divider class="my-24"></x-divider>
			<x-more :disabled="true" :text="['付费解锁','关闭详情']">
				<x-text class="line-10">
					禁用无法打开
					随后，行刑者用一根管子放出温水顺着死刑犯的手臂往下流。并在地上放置一个铁盆，让水流到盆里的声音“嘀哒嘀哒“作响，给罪犯造成是自己流血的错觉。
					随着水流越来越慢，水温越来越低，声音越来越小。
					没过多久，罪犯就断气而身亡。尸检发现，罪犯死于心脏麻痹。
					随后，行刑者用一根管子放出温水顺着死刑犯的手臂往下流。并在地上放置一个铁盆，让水流到盆里的声音“嘀哒嘀哒“作响，给罪犯造成是自己流血的错觉。
					随着水流越来越慢，水温越来越低，声音越来越小。
					没过多久，罪犯就断气而身亡。尸检发现，罪犯死于心脏麻痹。
				</x-text>
				<x-image src="https://store.tmui.design/api_v2/public/random_picture?random=vsf"></x-image>
			</x-more>
			<x-divider class="my-24"></x-divider>
			<x-more height="80">
				<x-text font-size="18" class=" text-weight-b mb-8">可以设置高度</x-text>
				<x-text class="line-10">
					并在地上放置一个铁盆，让水流到盆里的声音“嘀哒嘀哒“作响，给罪犯造成是自己流血的错觉。
					随着水流越来越慢，水温越来越低，声音越来越小。
				</x-text>
				<x-image src="https://store.tmui.design/api_v2/public/random_picture?random=666df"></x-image>
			</x-more>
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
		
