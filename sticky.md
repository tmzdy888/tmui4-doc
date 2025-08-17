
## 粘性布局 Sticky

***

#### 介绍

可以同时存在多个悬停，多个悬停时，还支持触发距离悬停的设置，
在复杂页面需要多个菜单吸附时非常有用。并且配合切换change事件做到更复杂的布局。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-sticky/x-sticky.uvue**

#### 使用

<x-sticky></x-sticky>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| top | 顶部的偏移量 | string | "0" |
| left | 左边的偏移量。 | string | "0" |
| diffTop | 触发距离，默认0，意思是组件距离顶部多远时触发悬停。<br>对于需要多个悬停时此属性非常有用。<br>这个值不允许使用%单位，可以是：px,rpx,数字（默认是rpx） | string | '0' |
| zIndex | 层级 | number | 88 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **** : undefined**isFixed** : boolean | 当触发悬停切换时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，你要悬停的布局放在这里。 | **status** : boolean<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/sticky

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
			<x-text font-size="18" class=" text-weight-b mb-8">粘性布局 Sticky</x-text>
			<x-text  color="#999999" >当滚动到元素时自动吸附在顶部</x-text>
			<x-text  color="#999999" >您应该避免被嵌套的内容不能含有fixed,absolute布局的元素，会影响对齐和裁剪。</x-text>
		</x-sheet>
		<x-sticky>
			<template v-slot="status">
				<x-sheet color="primary" height="40px" :padding="['12','0']" :margin="['16','0']"
					class="flex flex-row flex-row-center-start">
					<text class="text-white">滚动页面我会被自动吸顶</text>
				</x-sheet>
			</template>
		</x-sticky>
		<x-sheet v-for="item in 3" :key="item" height="100px"></x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">存在多个吸附时</x-text>
			<x-text  color="#999999" >可以利用diff-top设置差值，来吸附到上一个 吸附元素的后面，避免钻到上个元素的下方。</x-text>
		</x-sheet>
		<x-sticky top="40px" diff-top="40px">
			
			<template v-slot="status">
				<x-sheet color="success" :padding="['12','12']" :margin="['16','0']">
					<text class="text-white">我会被吸附在上面元素的后面，这对布局非常有用</text>
				</x-sheet>
			</template>
		</x-sticky>
		<x-sheet v-for="item in 10" :key="item" height="100px"></x-sheet>
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
		},
		methods:{
			
			
		}
	}
</script>

<style lang="scss">

</style>
		
