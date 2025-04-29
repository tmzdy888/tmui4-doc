
## 横向滚动 xScrollx

***

#### 介绍

需要明确内部宽，否则无法左右导航滚动。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-scrollx/x-scrollx.uvue**

#### 使用

<x-scrollx></x-scrollx>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽，不能设置为auto,需要一个具体的宽度值<br>否则无法左右滚动。 | string | '100%' |
| height | 高 | string | 'auto' |
| scrollbarWidth | 下面横向小条宽,px单位 | number | 100 |
| scrollbarHeight | 下面横向小条高,px单位 | number | 6 |
| showScrollBar | 是否显示底部横线指示 | boolean | true |
| scrollPosBarWidth | 内部小指示条的宽,px单位 | number | 20 |
| scrollPosBgColor | 下面滚动指示条的轨道背景 | string | "#f3f5f8" |
| darkScrollPosBgColor | 下面滚动指示条的轨道暗黑背景<br>不填充的话取输入框的暗黑背景 | string | "" |
| scrollPosColor | 下面滚动指示条的活动背景<br>不填写的话取全局的color | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 当前滚指示内部的小条的位置 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/scrollx

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
			<x-text font-size="18" class=" text-weight-b mb-8">横向滚动 xScrollx</x-text>
			<x-text color="#999999">用于内容导航时滚动指示</x-text>
		</x-sheet>

		<x-sheet>
			<x-scrollx scrollPosColor="warn" :scrollbarWidth="50" :scrollPosBarWidth="10">
				<view class="flex flex-row flex-row-center-start nowrap">
					<x-grid width="400" :col="4" icon-color="primary" dark-icon-color="primary">
						<x-grid-item icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
						<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
						<x-grid-item icon="price-tag-2-fill" text="活动日历"></x-grid-item>
						<x-grid-item icon="wallet-3-fill" text="领淘金币"></x-grid-item>
						<x-grid-item icon="gift-fill" text="会员福利"></x-grid-item>
						<x-grid-item icon="coupon-5-fill" text="省钱卡"></x-grid-item>
						<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
						<x-grid-item icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
					</x-grid>
					<x-grid width="400" :col="4" icon-color="primary" dark-icon-color="primary">
						<x-grid-item icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
						<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
						<x-grid-item icon="price-tag-2-fill" text="活动日历"></x-grid-item>
						<x-grid-item icon="wallet-3-fill" text="领淘金币"></x-grid-item>
						<x-grid-item icon="gift-fill" text="会员福利"></x-grid-item>
						<x-grid-item icon="coupon-5-fill" text="省钱卡"></x-grid-item>
						<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
						<x-grid-item icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
					</x-grid>
				</view>
			</x-scrollx>
		</x-sheet>

		<x-sheet>
			<x-scrollx>
				<x-image class="mr-10" v-for="(item,index) in 6" :key="index" width="100" height="100"
					:src="`https://store.tmui.design/api_v2/public/random_picture?random=183${index}`"></x-image>
			</x-scrollx>
		</x-sheet>
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

<style >
	

</style>
		
