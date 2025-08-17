
## 底部导航 xTabbar

***

#### 介绍

可定义凸起按钮。通过全局状态设置选中项，放于任何页面可自动选中。组件的镂空因平台而有兼容差异，sdk不支持相关api

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-tabbar/x-tabbar.uvue**

#### 使用

<x-tabbar></x-tabbar>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 未选中时的颜色 | string | "#b9b9b9" |
| selectedColor | 选中时的颜色，空值取全局主题 | string | "" |
| bgColor | 背景,如果你为空，会读取全局的亮色tabbar背景 | string | "white" |
| darkBgColor | 暗黑时的背景，如果为空，取全局的底部导航背景色。 | string | "" |
| showTopBorder | 显示顶部边线，暗黑时取全局的borderDarkColor | boolean | true |
| borderColor | 边线颜色 | string | "#f0f0f0" |
| fontSize | 文字大小 | string | "11px" |
| iconSize | 图标大小 | string | "28px" |
| autoTabbarHeight | 导航的整体高度，请使用v-model:autoTabbarHeight="x"<br>来获取当前的高度。外部要去变更值。这个只是对外输出，<br>给您 外部放在底部占位用，省得你们要一屏时计算高。外部最好computed使用，因为是异步的 | number | 0 |
| outIndex | 需要向外凸起的项目索引。<br>-1表示不凸起 | number | 2 |
| outBgColor | 凸起的背景色 | string | "primary" |
| outIconColor | 凸起的图标颜色 | string | "white" |
| isOutSpace | 是否开启凸起背景镂空，截止sdk 4.31 ios有bug官方已经知晓在修复 | boolean | true |
| outReserve | 是否反向凸起就是不镂空，但在凸起的底层会被绘制背景。false是镂空，true表示反向包住。<br>截止sdk 4.31 ios有bug官方已经知晓在修复 | boolean | false |
| position | 是否悬浮在底部,不可动态修改<br>fixed悬浮，relative静态布局。 | string | 'fixed' |
| linearGradient | 渐变背景，如果提供，上面的背景和暗黑背景将失效。<br>仅支持:to bottom,to right,to left,to top<br>例：['to right','#ff667f','#ff5416'] | string[] | () : string[] => [] as string[] |
| list | 如果你提供了本地的list数据，那么全局的list将不会被采用，你需要自己管理激活引，<br>跨页面时需要你自己设置当前页面的索引，因为变量索引是无法跨页面的。 | TABBAR_ITEM_INFO[] | () : TABBAR_ITEM_INFO[] => [] as TABBAR_ITEM_INFO[] |
| activeIndex | 当前激活的索引,如果你提供了本地索引，那全局的索引将失效。<br>跨页面时需要你自己设置当前页面的索引，因为变量索引是无法跨页面的。<br>仅当月list不为空时有效。 | number | -1 |
| zIndex | 层级 | number | 20 |
| firstRenderTimeout | 首次渲染等待时长<br>如果你在首页或者第一页使用时，如果渲染异常，请通过调节这个值来使用其正常<br>主要是针对安卓ios。对web不起效<br>如果是次页，时间不需要太长。时间长短时你页面渲染时长而定。<br>页面元素过多，排版较长时可能需要设置超过350ms，正常的次页100-150ms即可。 | number | 300 |
| isCanvasRender | 是否开启canvas渲染引擎，开启后，可以得到<br>异形的镂空效果。比view渲染的更精致好看。开启后前面的firstRenderTimeout要注意阅读<br>两种渲染版本请自行选择使用。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | **index** : number | 项目被点击时触发。 |
| change | **index** : number | 切换项目时触发。 |
| update:autoTabbarHeight | **height** : number | 同步组件高给外部使用，请使用v-model:autoTabbarHeight<br>组件高度 = 安全栏高度 + 导航栏高度,外部最好computed使用，因为是异步的 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| out | 凸起图标插槽。 | **active** : boolean<br>**active** : number<br>**size** : boolean<br>**size** : number<br> |
| item | 子项目插槽，以便完全自定义化样式。 | **isactive** : number<br>**isactive** : boolean<br>**isactive** : number<br>**selfindex** : number<br>**selfindex** : boolean<br>**selfindex** : number<br>**children** : number<br>**children** : boolean<br>**children** : number<br>**activeindex** : number<br>**activeindex** : boolean<br>**activeindex** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/tabbar

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view style="flex:1;display: flex;flex-direction: column;">
		<scroll-view class="flex-1" :scroll-y="true">
			<x-sheet>
				<x-text font-size="18" class=" text-weight-b mb-8">底部导航 xTabbar</x-text>
				<x-text  color="#999999" >本组件使用全局来控制选中荐和数据，因此在在各个页面放置本组件后。不需要再赋值当前选中项和数据了。解决以往很多同学不会用的问题。</x-text>
			</x-sheet>
			
			<x-sheet :margin="['12']">
				<x-text font-size="18" class=" text-weight-b mb-8">凸起</x-text>
				<x-text  color="#999999" >使用时-1表示关闭</x-text>
				<view class="mt-20 flex flex-row">
					<x-button @click="outIndex=2" class="mr-20">打开凸起</x-button>
					<x-button @click="outIndex=-1" >关闭凸起</x-button>
				</view>
			</x-sheet>
		
			<x-sheet :margin="['12']">
				<x-text font-size="18" class=" text-weight-b mb-8">个性化，开启isCanvasRender</x-text>
				<x-text  color="#999999" >使用插槽name=item可以动态修改更个性化的底部导航样式。</x-text>
			</x-sheet>
			<x-tabbar :outIndex="outIndex" :is-canvas-render="false" class="mb-24" color="rgba(0,0,0,0.64)"  out-bg-color="#16ee9c" selected-color="#000000" :linear-gradient="['to right','#20f8be','#1cd86b']" position="relative" >
			</x-tabbar>
			<x-tabbar :outReserve="true" :outIndex="1"  class="mb-24" color="rgba(0,0,0,0.64)"  out-bg-color="#ffffff" out-icon-color="#16ee9c" selected-color="#000000" :linear-gradient="['to right','#20f8be','#1cd86b']" position="relative" >
			</x-tabbar>
			<x-sheet :margin="['12']">
				<x-text font-size="18" class=" text-weight-b">个性化，关闭isCanvasRender</x-text>
				<x-text  color="#999999" >非isCanvasRender渲染，没有镂空等异形渲染效果。效果没有开启的好看。请自行选择使用效果。</x-text>
			</x-sheet>
			<x-tabbar :isCanvasRender="false"   class="mb-24" color="#fff" out-icon-color="#921fff" out-bg-color="#ffffff" selected-color="#ff0" :linear-gradient="['to right','#921fff','#2952ff']" position="relative" >
			</x-tabbar>
			<x-sheet :margin="['12']">
				<x-text font-size="18" class=" text-weight-b mb-8">关于占位问题</x-text>
				<x-text  color="#999999" >
					组件通过v-model:autoTabbarHeight="autoTabbarHeight"来对外输入占位高度。
					例本页面就是通过属性控制占位达到一屏效果，请下拉体验。
					也要可以通过xStore.xTabbarConfig.tabaarHeight读取
					当前高：{{tabbaerHeight}}
				</x-text>
			</x-sheet>
			<x-sheet v-for="index in 12" :key="index">
				<x-text>{{index+1}} / 24向下滑动页面，占位一屏。</x-text>
			</x-sheet>
			
			<!-- 占位 -->
			<view :style="{height:autoTabbarHeight+'px'}"></view>
			
			<x-tabbar :outIndex="outIndex" v-model:autoTabbarHeight="autoTabbarHeight" color="#808080" >
				<template v-slot:item="{isactive,children,selfindex}">
					<text v-if="selfindex!=2" :style="{color:(isactive as boolean)?_color:'#808080'}">
						{{(children as TABBAR_ITEM).title}}
					</text>
				</template>
			</x-tabbar>
		</scroll-view>
		
	</view>
	
</template>

<script>
	import { TABBAR_ITEM_INFO,NAVIGATE_TYPE,TABBAR_ITEM } from "@/uni_modules/tmx-ui/interface.uts"
	import { xStore } from "@/uni_modules/tmx-ui/index.uts"

	export default {
		data() {
			return {
				autoTabbarHeight:0,
				outIndex:2,
				list:[
					{title:"首页",icon:"home-smile-2-line",selectedIcon:"home-smile-2-fill",dotType:'dot'} as TABBAR_ITEM_INFO,
					{title:"分类",icon:"drive-line",selectedIcon:"drive-fill"} as TABBAR_ITEM_INFO,
					{title:"购物车",icon:"shopping-basket-line",selectedIcon:"shopping-basket-fill"} as TABBAR_ITEM_INFO,
					{title:"统计",icon:"bar-chart-2-line",selectedIcon:"bar-chart-2-fill",dotLabel:'99+',} as TABBAR_ITEM_INFO,
					{title:"我的",icon:"group-line",selectedIcon:"group-fill"} as TABBAR_ITEM_INFO
				] as TABBAR_ITEM_INFO[]
			};
		},
		computed:{
			_color():string {
				return xStore.xConfig.color
			},
			tabbaerHeight():number{
				return xStore.xTabbarConfig.tabaarHeight
			}
		},
		beforeMount() {
			xStore.xTabbarConfig.list = this.list;
		},
		methods:{

			changBadge(){
				this.list[3]!.dotLabel = '2'
			}
		}
	}
</script>

<style lang="scss">

</style>

		
