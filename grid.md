
## 宫格 xGrid

***

#### 介绍

内部只可放置x-grid-item。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-grid/x-grid.uvue**

#### 使用

<x-grid></x-grid>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| col | 显示几列 | number | 3 |
| itemHeight | 项目高度 | string | '70' |
| itemBgColor | 统一设置子组件的背景 | string | 'white' |
| bgColor | 整体宫格的背景 | string | 'transparent' |
| darkBgColor | 整体宫格的背景暗黑，如果为空，读取全局sheetDark | string | 'transparent' |
| width | 整体宽度 | string | 'auto' |
| iconColor | 图标颜色 | string | '#333333' |
| darkIconColor | 暗黑时图标颜色 | string | '#FFFFFF' |
| textColor | 文字颜色，暗黑时取白。 | string | '#888888' |
| fontSize | 文字大小 | string | '13' |
| iconSize | 图标大小 | string | '25' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽内只可放置x-grid-item | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/grid

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
			<x-text font-size="18" class=" text-weight-b mb-8">宫格 Grid</x-text>
			<x-text color="#999999" >快速导航布局</x-text>
		</x-sheet>
		<x-sheet>
			<x-grid :col="4" icon-color="primary" dark-icon-color="primary">
				<x-grid-item  icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
				<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
				<x-grid-item icon="price-tag-2-fill" text="活动日历"></x-grid-item>
				<x-grid-item icon="wallet-3-fill" text="领淘金币"></x-grid-item>
				<x-grid-item icon="gift-fill" text="会员福利"></x-grid-item>
				<x-grid-item icon="coupon-5-fill" text="省钱卡"></x-grid-item>
				<x-grid-item icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
				<x-grid-item icon="money-cny-circle-fill" text="摇现金"></x-grid-item>
			</x-grid>
		</x-sheet>
		<x-sheet>
			<x-grid :col="3" item-height="90" text-color="#333333">
				<x-grid-item iconColor="danger" icon="money-cny-circle-fill" text="摇现金">
					<x-badge label="HOT" bg-color="orange">
						<x-icon name="money-cny-circle-fill" color="danger" font-size="25" class="mb-5"></x-icon>
						<x-text font-size="13">摇现金</x-text>
					</x-badge>
					
				</x-grid-item>
				<x-grid-item iconColor="error" icon="shopping-bag-fill" text="百亿补贴"></x-grid-item>
				<x-grid-item iconColor="warn" icon="price-tag-2-fill" text="活动日历"></x-grid-item>
				<x-grid-item iconColor="parisviolet" icon="wallet-3-fill" text="领淘金币"></x-grid-item>
				<x-grid-item >
					<x-badge :count="36">
						<x-icon name="gift-fill" color="australiangold" font-size="25" class="mb-5"></x-icon>
						<x-text  font-size="13">会员福利</x-text>
					</x-badge>
				</x-grid-item>
				<x-grid-item iconColor="success" icon="coupon-5-fill" text="省钱卡"></x-grid-item>
			</x-grid>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="uts" setup>

	
</script>

<style>

</style>

		
