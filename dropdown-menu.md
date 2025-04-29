
## 下拉菜单 xDropdownMenu

***

#### 介绍

下拉菜单，标签内只能放置子项目x-dropdown-item

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-dropdown-menu/x-dropdown-menu.uvue**

#### 使用

<x-dropdown-menu></x-dropdown-menu>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| position | 位置，<br>static \| fixed<br>静态 \| 展开后悬浮在顶部。 | string | "fixed" |
| offsetTop | 顶部的偏移量，针对你们自定标题导航时可能需要让出顶部位置。<br>数字字符，prx,px等单位<br>如果position=static此属性失效。 | string | "0" |
| modelValue | 当前激活的索引<br>-1表示关闭。提供值时请大于-1,<br>如果不想要变量控制，些值 可不提供。交由内部自行处理。<br>当你想要用变量控制开关时可v-model="索引"来控制关闭和打开。 | number | -1 |
| height | 菜单栏的高度 | string | "44" |
| width | 宽度 | string | "auto" |
| color | 背景颜色 | string | "white" |
| darkColor | 暗黑时的背景颜色 | string | "" |
| zIndex | 层级 | number | 88 |
| hidnMask | 对于要把此组件嵌套在fiexd中时,并且position为static时<br>请一定设置为true,否则在web端会出现层级混乱(这是css dom规则所定)<br>为了全平台对齐请嵌套组件时一定注意使用事项. | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 切换菜单时触发 |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，只能放置子项目x-dropdown-item | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/dropdown-menu

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
			<x-text font-size="18" class=" text-weight-b mb-8">下拉菜单 dropdownMenu</x-text>
			<x-text color="#999999" >
				提供static和fiexd两种位置方式。内容完全通过插槽自由布局。x-dropdown-menu 中的render="true"后动画会消失
			</x-text>
		</x-sheet>
		<x-dropdown-menu @change="onchange" v-model="activeIndex">
			<x-dropdown-item  title="按销量" key-name="xiaoliang">
				<x-text class="mb-32">因自由度非常高，你可以自由布局最大高度是否滚动内容。</x-text>
				<!-- -1表示关闭 -->
				<x-button @click="activeIndex=-1" :block="true">关闭</x-button>
			</x-dropdown-item>
			<x-dropdown-item :title="menus" key-name="wiff">
				<x-text>自己添加scrollview等实现页脚功能.</x-text>
			</x-dropdown-item>
			<x-dropdown-item title="硬盘容量" key-name="yingpan">
				<x-text>内容层的高度是自动高。不需要额外设置。</x-text>
			</x-dropdown-item>
			<x-dropdown-item title="综合" key-name="zhonghe" :isBtn="true" icon="sort-desc" active-icon="sort-asc">
				<x-text>内容层的高度是自动高。不需要额外设置。</x-text>
			</x-dropdown-item>
		</x-dropdown-menu>


		<x-sheet :margin="['0','24']">
			<x-text font-size="18" class=" text-weight-b ">正文是静态，弹出时，菜单不会置顶在页面顶部。</x-text>
		</x-sheet>

		<x-dropdown-menu position="static">
			<x-dropdown-item title="按距离">
				<x-text>这里由用户自由布局内容，实现逻辑。</x-text>
			</x-dropdown-item>
			<x-dropdown-item title="综合条件">
				<x-text>你还可以实现更多更复杂的功能.</x-text>
			</x-dropdown-item>
			<x-dropdown-item title="所有项目">
				<x-text>完全插槽实现灵活度极高。</x-text>
			</x-dropdown-item>
		</x-dropdown-menu>

	<view style="height:580px"></view>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				activeIndex: -1,
				remove: true,
				menus:"网络类型"
			};
		},
		onLoad() {
		
		},
		methods: {
			onchange(index : number, keyName : string, status : boolean) {
				console.log('当前索引：', index, ';当前项目标识：', keyName, ';当前开关状态：', status)
			}
		},
	}
</script>

<style lang="scss">

</style>
		
