
## 汽泡菜单 xPopover

***

#### 介绍

汽泡菜单,警告:如果你弹出的内容比如文本,它会自动宽和高,是个特殊组件在web上,此类需要固定下宽.
建议内容要自己写个固定宽或者高性能更好。另外sdk4.57开始，在微信端你的菜单内容最好不要动态更改导致宽和高动态变化，在微信端只会记录首次的
内容区域的宽和高（触发插槽不限制），如果确实在微信端要动态变更内容可以vif整体组件或者改变key来刷新组件解决。非微信端无此限制。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-popover/x-popover.uvue**

#### 使用

<x-popover></x-popover>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| position | 弹出的位置。<br>'bc'\|'br'\|'bl'\|'tr'\|'tc'\|'tl'<br>底中\|底右\|底左\|顶右\|顶中\|顶左 | xPopopverPosType | 'bc' |
| keyName | 如果你的弹出层内容是异步加载。<br>你需要刷新下此key以刷新位置。如果你是vif一来切换或者显示前内容是固定的，则不需要刷新此值。 | number | 0 |
| modelValue | 变量控制是否显示菜单，等同v-model=""<br>如果你想默认显示，但不受变量控制由内部自行处理可以:model-value="true"即可 | boolean | false |
| isClickClose | 点击弹出的内容是否允许关闭。 | boolean | true |
| round | 容器圆角。ios如果不设置，你内容圆角没有用。 | string | '16' |
| maskBgColor | 遮罩背景,默认是透明 | string | "rgba(0,0,0,0)" |
| showTriangle | 是否显示指示的三角形。 | boolean | false |
| triangleColor | 三角指示的背景色 | string | 'white' |
| triangleDarkColor | 三角指示的暗黑背景色,空取sheet暗黑背影色 | string | '' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽触发区域，点击此插槽内容可显示菜单。 | - |
| menu | 菜单弹出区域的插槽，弹出内容可以在这里自由布局。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/popover

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
			<x-text font-size="18" class=" text-weight-b mb-8">汽泡菜单 Popover</x-text>
			<x-text color="#999999">
				方向由上三个和下三个方位共6个。不提供左和右，因为在移动端用处不大。采用插槽布局弹出内容灵活自由度极高。同时可以插槽触发以及变量控制关闭。
				警告:如果你弹出的内容比如文本,它会自动宽和高,是个特殊组件在web上,此类需要固定下宽.
			</x-text>
		</x-sheet>

		<x-sheet class="flex flex-row flex-row-center-between">
			<x-popover :show-triangle="true" position="bl">
				<x-button color="error" round="64" :iconBtn="true" icon="menu-unfold-fill"></x-button>
				<template #menu>
					<view style="width:140px">
						<x-cell v-for="(item,index) in menuCount" :key="index" :show-bottom-border="index!=menuCount-1"
							:card="false" :title="'菜单-'+item"></x-cell>
					</view>

				</template>
			</x-popover>
			<x-popover mask-bg-color="rgba(0,0,0,0.3)" :show-triangle="true" triangle-color="black" triangle-dark-color="black">
				<x-button round="64" :iconBtn="true" icon="menu-line"></x-button>
				<template #menu>
					<view style="width:140px">
						<x-cell color="black" dark-color="black" bottom-border-color="#1f1f1f" title-color="white" icon-color="white"
							v-for="(item,index) in menuCount" :key="index" :show-bottom-border="index!=menuCount-1"
							:card="false" :title="'菜单-'+item"></x-cell>
					</view>

				</template>
			</x-popover>
			<x-popover :show-triangle="true" position="br" triangle-color="success" triangle-dark-color="success">
				<x-button round="64" color="success" :iconBtn="true" icon="more-2-line"></x-button>
				<template #menu>
					<view style="width:140px">
						<x-cell color="success" icon-color="white" dark-color="success" linkColor="white" linkDarkColor="white" titleColor="white" bottomBorderColor="rgba(255,255,255,0.1)" v-for="(item,index) in menuCount" :key="index" :show-bottom-border="index!=menuCount-1"
							:card="false" :title="'菜单-'+item"></x-cell>
					</view>
				</template>
			</x-popover>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">默认弹出</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-center">

			<x-popover position="bc" v-model="show" :show-triangle="true" triangle-color="#333" triangle-dark-color="#333">
				<text class="text-red">点击我也能打开菜单</text>
				<template #menu>
					<view style="width:180px">
						<x-cell url="text" color="#333" dark-color="#333" title-color="white" icon-color="white"
							v-for="(item,index) in menuCount" :key="index" bottom-border-color="#474747"
							:show-bottom-border="index!=menuCount-1" :card="false" :title="'菜单-'+item"></x-cell>
					</view>
				</template>
			</x-popover>
			<!-- <x-button class="ml-32" @click="show=true">变量控制</x-button> -->
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">弹出方向</x-text>
		</x-sheet>
		<x-sheet>
			<view class="flex flex-row flex-row-center-between mb-32">
				<x-popover position="bl">
					<x-text>底左对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333" :margin="['0']">
							<x-text>菜单可随意布局</x-text>
							<x-button>任意布局哦</x-button>
						</x-sheet>
					</template>
				</x-popover>
				<x-popover>
					<x-text>底中对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333" :margin="['0']" ><x-text >菜单可随意布局</x-text></x-sheet>
						
					</template>
				</x-popover>
				<x-popover position="br">
					<x-text>底右对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333" width="120" :margin="['0']">
							<x-text>菜单可随意布局</x-text>
						</x-sheet>
					</template>
				</x-popover>
			</view>
			<view class="flex flex-row flex-row-center-between">
				<x-popover position="tl">
					<x-text>上左对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333" :margin="['0']"><x-text>菜单可随意布局</x-text></x-sheet>
					</template>
				</x-popover>
				<x-popover position="tc">
					<x-text>上中对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333" :margin="['0']"><x-text>菜单可随意布局</x-text></x-sheet>
					</template>
				</x-popover>
				<x-popover position="tr">
					<x-text>上右对齐</x-text>
					<template #menu>
						<x-sheet dark-color="#333"  width="120"  :margin="['0']"><x-text>菜单可随意布局</x-text></x-sheet>
					</template>
				</x-popover>
			</view>

		</x-sheet>
		
		<view style="height: 100px;"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				menuCount: 4,
				show: true
			};
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">

</style>
		
