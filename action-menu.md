
## 动作菜单面板 xActionMenu

***

#### 介绍

从底部弹出来的操作菜单。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-action-menu/x-action-menu.uvue**

#### 使用

<x-action-menu></x-action-menu>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| customStyle | 自定义遮罩样式 | string | "" |
| title | 标题 | string | "标题" |
| showTitle | 是否显示标题 | boolean | true |
| showClose | 是否显示关闭 | boolean | false |
| overlayClick | 遮罩是否允许点击被关闭 | boolean | true |
| cellClickClose | 选项点击时，是否允许关闭弹层。 | boolean | true |
| show | 显示可v-model:show双向绑定 | boolean | false |
| showCancel | 显示取消按钮 | boolean | true |
| duration | 动画时间 | number | 350 |
| round | 打开方向为上和下时的圆角<br>空值时，取全局配置的圆角。注意是取drawer的圆角，统一弹层的圆角 | string | "" |
| maxHeight | 弹层最大的高度值，默认为屏幕的可视高<br>提供值时不能为百分比，可以是px,rpx单位数字。如果你不带单位，默认转换为rpx单位。 | string | "" |
| list | 菜单条目 | XACTION_MENU_ITEM_INFO[] | () : XACTION_MENU_ITEM_INFO[] => [] as XACTION_MENU_ITEM_INFO[] |
| space | 弹层的层，两边是否留空白间隙，包括底部。 | boolean | true |
| watiDuration | 打开dom的延迟量，如果你打开 弹窗在ios正常。<br>请不要修改此值。如果遇到打不开，或者 打开 后没动画，关闭不了等可能是sdk bug导致 <br>此时需要加大值来避免。具体加多少以你弹窗内的节点复杂度有关，需要你自行压力测试。<br>此值仅在ios下生效。 | number | 120 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cancel | - | 取消时触发 |
| click | - | 点击遮罩事件 |
| close | - | 关闭时执行 |
| open | - | 打开执行的事件 |
| beforeOpen | - | 打开前执行 |
| beforeClose | - | 关闭前执行 |
| update:show | - | 等同v-model:show |
| item-click | **index** : number | 项目被点击。由于安卓端动画关闭前触发,会触发view渲染异常.导致动画失败.从而造成,下个页面返回时,上页无法执行结束. |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| trigger | 标签触发显示遮罩，免于使用变量控制 | **show** : Boolean<br> |
| title | 标题插槽 | **show** : Boolean<br> |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/action-menu

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">动作菜单 ActionMenu</x-text>
			<x-text color="#999999" >
				从底部弹出的菜单选项，自由度高。
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-action-menu @item-click="itemclick" :list="list2" title="测试菜单">
				<template #trigger>
					<x-button :block="true">默认</x-button>
				</template>
			</x-action-menu>
		</x-sheet>
		<x-sheet>
			<x-action-menu :list="list">
				<template #trigger>
					<x-button :block="true">可以定义颜色显示</x-button>
				</template>
			</x-action-menu>
		</x-sheet>
	</view>
</template>

<script>
	import { XACTION_MENU_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	import { xStore } from "@/uni_modules/tmx-ui/index.uts"
	export default {
		data() {
			return {
				list:[
					{
						icon:"notification-line",
						text:"通知栏",
						id:"1"
					} as XACTION_MENU_ITEM_INFO,
					{
						icon:"notification-line",
						text:"我被禁用",
						id:"2",
						disabled:true
					} as XACTION_MENU_ITEM_INFO,
					{
						icon:"notification-line",
						text:"我修改了颜色",
						id:"3",
						iconColor:'red',
						fontColor:'red'
					} as XACTION_MENU_ITEM_INFO,
					{
						text:"我没有图标",
						id:"4"
					} as XACTION_MENU_ITEM_INFO
				] as XACTION_MENU_ITEM_INFO[],
				list2:[
					{
						text:"我是菜单栏",
						id:"1"
					} as XACTION_MENU_ITEM_INFO,
					{
						text:"我是菜单栏",
						id:"2",
					} as XACTION_MENU_ITEM_INFO,
					{
						text:"我是菜单栏",
						id:"3",
					} as XACTION_MENU_ITEM_INFO
				] as XACTION_MENU_ITEM_INFO[]
			};
		},
		onLoad(){
		},
		methods:{
			itemclick(index:number){
				console.log(index)
			}
		}
	}
</script>

<style lang="scss">

</style>

		
