
## 瀑布流 xWaterfall

***

#### 介绍

可以通过columnu来控制排版列数，默认是2列排版。可以无限加载不卡,全异步流加载.使用时请参考demo布局,已精心为你规划如何提高性能.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-waterfall/x-waterfall.uvue**

#### 使用

<x-waterfall></x-waterfall>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| column | 瀑布流的列数<br>不可动态动态更改。 | number | 2 |
| listCount | 用来刷新数据的，你可以通过你的外面list.length来传递进来<br>比如为0时，自动清空瀑布流数据。 | number | 0 |
| gutter | 间距,单位不能为%比，可以是数字字符，带rpx,px等单位<br>默认的数字符单位是全局的unit单位。 | string | '8' |
| isResize | 是否响应尺寸监测。设置为false可以关闭<br>关闭后能增加性能。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 只能放置直接子节点x-waterfall-item | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| pushChild | - | - | - |
| nextRender | - | - | - |
| removeChild | - | - | - |


#### 示例页面路径

/pages/zhanshi/waterfall

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
			<x-text font-size="18" class=" text-weight-b mb-8">瀑布流 xWaterfall</x-text>
			<x-text color="#999999">可以通过columnu来控制排版列数，默认是2列排版。另外理论上子节点数量不限制的，渲染也不会卡,全为异步加载,请根据demo布局你的长列表瀑布流.不要在子节点中布局自定义节点,请完全使用原生节点.</x-text>

		</x-sheet>
		<view class="px-8" >
			<x-waterfall  :list-count="list.length">
				<x-waterfall-item v-for="(item,index) in list" :order="index" :key="index">
					<template v-slot:default="col">
						<view class="pa-8" :style="{borderRadius:'6px',backgroundColor:bgColorOfView}">
							<image style="width:100%;height:120px":src="`https://store.tmui.design/api_v2/public/random_picture?random=18${index}`"></image>
							<text class="mt-16" :style="{color:textColorOfView,fontSize:'15px',lineHeight:'1.4'}" >{{item}}</text>
						</view>
					</template>
				</x-waterfall-item>
			</x-waterfall>
		</view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { xStore, xDate } from "@/uni_modules/tmx-ui/index.uts"
	export default {
		data() {
			return {
				strs: '今年4月15日是第九个全民国家安全教育日。《环球时报》记者观察发现，今年“4·15”前后，国更加隐蔽。除国家安全传统领域外，关乎国计国家安全问题专家在接受《环球时报》记者采访时表示，反间也是广大人民群众的义务。',
				list: [] as string[],
				loading: false
			};
		},
		onLoad() {
			this.randomData();
		},
		onReachBottom() {
			if (this.loading) return;
			this.onloadata();
		},
		onPullDownRefresh() {
			this.list = [] as string[]
			this.$forceUpdate()
			this.onloadata();
		},
		computed:{
			bgColorOfView() : string {
				return xStore.xConfig.dark == 'dark'?xStore.xConfig.sheetDarkColor:'white'
			},
			textColorOfView() : string {
				return xStore.xConfig.dark == 'dark'?'white':'#333333'
			},
		},
		methods: {
			randomData() {

				let total = this.list.length;
				for (let i = 0; i < 12; i++) {
					let start = Math.max(0, Math.min(Math.random() * this.strs.length, this.strs.length))
					this.list.push((total + i).toString() + this.strs.substring(start))
				}
			},
			onloadata() {
				let _this = this;
				uni.showLoading({ title: '...', mask: true })
				_this.loading = true;
				setTimeout(function () {
					_this.randomData();
					_this.loading = false;
					uni.hideLoading()
					uni.stopPullDownRefresh()
				}, 1000);

			}
		}
	}
</script>

<style lang="scss">

</style>
		
