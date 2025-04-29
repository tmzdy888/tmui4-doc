
## 侧边菜单 xSliderMenu

***

#### 介绍

左边菜单选择，右边内容区域

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-slider-menu/x-slider-menu.uvue**

#### 使用

<x-slider-menu></x-slider-menu>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽 | string | "auto" |
| height | 高是必填，不可为auto。 | string | "100%" |
| showScrollbar | 是否显示滚动条 | boolean | false |
| activeTextColor | 侧边选中的文字颜色，空值取全局主题 | string | "" |
| textColor | 侧边未选中时的文字颜色 | string | "#888888" |
| fontSize | 侧边菜单文字大小 | string | "16" |
| itemTextColor | 选项项目未选中的文字颜色 | string | "#333333" |
| itemActiveColor | 选项项目选中的文字颜色，空值取全局主题 | string | "" |
| sliderBgColor | 左侧边栏背景颜色 | string | "#f5f5f5" |
| darkSliderBgColor | 左侧边栏暗黑背景颜色<br>如果不提供，自动读取全局的backgroundColorContentDark背景色 | string | "" |
| sliderContentBgColor | 右内容区域背景颜色 | string | "white" |
| darkSliderContentBgColor | 右内容区域暗黑背景颜色<br>如果不提供读取sheet窗口的暗黑背景 | string | "" |
| sliderWidth | 侧边栏宽 | string | "100" |
| list |  | SLIDER_TREE_ITEM_INFO[] | () : SLIDER_TREE_ITEM_INFO[] => [] as SLIDER_TREE_ITEM_INFO[] |
| modelValue | 当前选中项的id数组 | string | "" |
| showToggleMenu | 是否允许侧边菜单收起和打开(会在菜单顶部出现一个收缩按钮)<br>这里需要你的菜单项中提供icon图标,不然收起后左侧就取项目的第一个字符. | boolean | false |
| menuPosition | 菜单位置,left或者right<br>默认在左侧,不可以动态更改. | string | "left" |
| itemHeight | 左侧菜单项目的高,默认44,不能为百分比,auto这种<br>只能是如:'44','44px','88rpx' | string | "44" |
| itemSelectedStyle | 左侧菜单项目被选中时的style样式对象,可以覆盖默认的样式-<br>改成自己的设计稿样式. | UTSJSONObject | ():UTSJSONObject => {<br>    return {} as UTSJSONObject<br>} |
| layoutMode | 右侧布局模式,=scroll时,右侧为动态循环的scroll-view,item插槽<br>上方的插槽数据启用,你需要自己在循环内布局内容.如果为default默认就是之前的<br>模式右侧就是一个空view,内容需要自己写滚动.<br>default,scroll | string | "default" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 手动切换时触发 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认右边插槽内容 | **height** : string<br>**height** : string<br>**menuid** : string<br>**menuid** : string<br> |
| item | 左边动态菜单插槽项目 | **item** : Object<br> |
| toggle | 开启收缩菜单时,显示的顶部菜单指示项目插槽,可过这里可以自定义你自己的关闭和展开的菜单指示样式. | **opened** : Boolean<br> |
| menu | 左边动态菜单插槽项目 | **item** : Object<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/slider-menu

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
		<x-slider-menu :showToggleMenu="true" :list="list" layout-mode="scroll"  v-model="modelvalue" :item-selected-style="itemStyle">
			<!-- <template v-slot:menu="{item}">
				<view :style="{
					width:'100%',height:'100%',
					backgroundColor:modelvalue==(item.id)?'red':'white',
					borderLeft:modelvalue==(item.id)?'2px solid yellow':'none'
				}">
					<text :style="{color:modelvalue==(item.id)?'white':'#333333'}">{{item.title}}</text>
				</view>
			</template> -->
			<template v-slot:item="{item}">
				<view style="height: 220px;" >
					<view style="height: 20px;"></view>
					<x-sheet height="200" color="info">
						<x-text >{{item.title}}</x-text>
					</x-sheet>
				</view>
			</template>
		</x-slider-menu>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { SLIDER_TREE_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	import { xStore,xDate } from "@/uni_modules/tmx-ui/index.uts"
	export default {
		data() {
			return {
				modelvalue:'1-3-1',
				itemStyle:xStore.xConfig.dark=='dark'? ({backgroundColor:'#181a1b',border:'none'} as UTSJSONObject) : ({backgroundColor:'#ccd8e6',border:'none'} as UTSJSONObject),
				list: [
					{ title: '江西省', id: "1-2-1",icon:'cloud-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '安徽', id: "1-3-1",icon:'archive-2-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '福建', id: "1-4-9",icon:'verified-badge-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '北京', id: "1-5-2",icon:'attachment-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '山东', id: "1-5-3",icon:'bar-chart-2-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '广东', id: "1-5-4",icon:'mail-unread-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '深圳', id: "1-5-5",icon:'home-4-fill' } as SLIDER_TREE_ITEM_INFO,
					{ title: '广西', id: "1-5-6",icon:'global-fill' } as SLIDER_TREE_ITEM_INFO,
					
					{ title: '江西省', id: "2-2-1" } as SLIDER_TREE_ITEM_INFO,
					{ title: '安徽', id: "2-3-1" } as SLIDER_TREE_ITEM_INFO,
					{ title: '福建', id: "2-4-9" } as SLIDER_TREE_ITEM_INFO,
					{ title: '北京', id: "2-5-2" } as SLIDER_TREE_ITEM_INFO,
					{ title: '山东', id: "2-5-3" } as SLIDER_TREE_ITEM_INFO,
					{ title: '广东', id: "2-5-4" } as SLIDER_TREE_ITEM_INFO,
					{ title: '深圳', id: "2-5-5" } as SLIDER_TREE_ITEM_INFO,
					{ title: '广西', id: "2-5-6" } as SLIDER_TREE_ITEM_INFO,
					
					{ title: '江西省', id: "3-2-1" } as SLIDER_TREE_ITEM_INFO,
					{ title: '安徽', id: "3-3-1" } as SLIDER_TREE_ITEM_INFO,
					{ title: '福建', id: "3-4-9" } as SLIDER_TREE_ITEM_INFO,
					{ title: '北京', id: "3-5-2" } as SLIDER_TREE_ITEM_INFO,
					{ title: '山东', id: "3-5-3" } as SLIDER_TREE_ITEM_INFO,
					{ title: '广东', id: "3-5-4" } as SLIDER_TREE_ITEM_INFO,
					{ title: '深圳', id: "3-5-5" } as SLIDER_TREE_ITEM_INFO,
					{ title: '广西', id: "3-5-6" } as SLIDER_TREE_ITEM_INFO
				] as SLIDER_TREE_ITEM_INFO[]
			};
		}
	}
</script>

<style lang="scss">

</style>
		
