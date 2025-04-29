
## 标签导航 xTabs

***

#### 介绍

标签导航，常用于页面顶部导航时使用，角标，数字角标功能。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-tabs/x-tabs.uvue**

#### 使用

<x-tabs></x-tabs>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| round | 圆角 | string | "0" |
| width | 宽 | string | "auto" |
| height | 高是必填，不可为auto。 | string | "44" |
| color | 背景 | string | "white" |
| darkColor | 暗黑时的背景,如果不填写读取sheetDark | string | "" |
| activeTitleColor | 文本激活时的颜色 ，空值默认取全局主题色 | string | "" |
| titleColor | 文本默认颜色 | string | "#888888" |
| darkTitleColor | 文本默认的暗黑颜色，如果不填写取白色。 | string | "#cacaca" |
| lineColor | 底部线条激活时的颜色，空值默认取全局主题色 | string | "" |
| lineGradient | 渐变背景<br>数组格式如下<br>                 [方向:top,bottom,left,right,自定义值例:45deg,颜色1:,颜色2]<br>例:['left','black','white']<br>如提供，暗黑及主题失效。 | string[] | () : string[] => [] |
| lineHeight |  | string | "2px" |
| lineFull | 底部的线条是与项目等宽还是固定默认的小宽度。 | boolean | false |
| showLine | 是否显示底部的线条 | boolean | true |
| list |  | TABS_ITEM_INFO[] | () : TABS_ITEM_INFO[] => [] as TABS_ITEM_INFO[] |
| modelValue | id值，如果数据没有提供id属性，这里的id就是索引（但要转换为字符串）<br>等同v-model | string | "0" |
| fontSize | 标题字号 | string | "16" |
| activeFontSize | 激活时的标题字号 | string | "16" |
| itemWidth | 项目宽度，默认是auto，即自动根据标题内容自动撑开宽度。<br>如果你想均分（适合不超过一行），比如你有5个标签，那么你就可以设置为"20%" | string | "auto" |
| titlePadding | 标题的padding是左右的间隙。 | string | "12px" |
| isItemCenter | 是否让内容居中显示,<br>默认为false,如果你开启了项目超过了宽出现滚动时,会自动向左对齐以便<br>让内容能滚动,但如果内容少于可滚动,内容会自动居中. | boolean | false |
| itemActiveStyle | 激活时的项目自定样式 | string | "" |
| itemStyle | 未激活时的项目自定样式 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **item** : TABS_ITEM**index** : number | 切换时触发 |
| update:modelValue | - | 当前选中的id值等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | tabs循环节点插槽,插件名称是tabs_+item.id,使用时请务必通过 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/tabs

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
			<x-text font-size="18" class=" text-weight-b mb-8">标签导航 Tabs</x-text>
			<x-text color="#999999" >样式定义灵活，有效应对各种场景。</x-text>
		</x-sheet>
	
		<x-sheet>
			<x-tabs item-width="33.3%" :list="list"></x-tabs>
		</x-sheet>
		<x-sticky>
			<template v-slot:default="{status}">
				<x-tabs  :is-item-center="true" v-model="activeId" width="100%" :list="list3"></x-tabs>
			</template>
		</x-sticky>
		<view style="height:20px"></view>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">动态插槽定制</x-text>
			<x-tabs item-width="33.3%" :list="list" :showLine="false"
			item-active-style="background-color:rgb(5, 121, 255)"
			item-style="background-color:transparent"
			>
				<template v-slot:default="{item,active}">
					<x-text :color="active?'white':'rgb(5, 121, 255)'" :style="active?'font-weight:bold;':''">{{item.title}}</x-text>
				</template>
			</x-tabs>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">定义样式</x-text>
		</x-sheet>
		<x-sheet >
			<x-tabs round="32" color="black" dark-color="black" title-color="rgba(255,255,255,0.6)" active-title-color="yellow"
				item-width="33.3%" :list="list"></x-tabs>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">定义线条，角标等</x-text>
		</x-sheet>
		<x-sheet :padding="['0']" :loading="loadingData">
			<x-tabs :line-gradient="['right','#0579ff','#7a00c6']" height="44" v-model="activeId2"  :lineFull="true" itemWidth="33.3%" :list="list2"></x-tabs>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">过多标签，自动排列，并位移项目</x-text>
		</x-sheet>
		<x-sheet>
			<x-tabs v-model="activeId" :list="list3"></x-tabs>
			<view style="height: 600px;" class="mt-24">
				<x-button :block="true" @click="activeId='3'">变量控制切换{{activeId}}</x-button>
			</view>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { TABS_ITEM_INFO,TABS_ITEM } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			return {
				list: [
					{ title: "全部" } as TABS_ITEM_INFO,
					{ title: "已完成" } as TABS_ITEM_INFO,
					{ title: "已删除" } as TABS_ITEM_INFO,
				],
				list2: [] as TABS_ITEM_INFO[],
				list3: [
					{ title: "全部" } as TABS_ITEM_INFO,
					{ title: "被禁用", disabled: true } as TABS_ITEM_INFO,
					{ title: "已删除" } as TABS_ITEM_INFO,
					{ title: "审核中" } as TABS_ITEM_INFO,
					{ title: "审核失败" } as TABS_ITEM_INFO,
					{ title: "售后中" } as TABS_ITEM_INFO,
					{ title: "已处理已处理" } as TABS_ITEM_INFO,
					{ title: "已处理2" } as TABS_ITEM_INFO,
					{ title: "已已处理处理3" } as TABS_ITEM_INFO,
					{ title: "已已处理处理4" } as TABS_ITEM_INFO,
					{ title: "已处理5" } as TABS_ITEM_INFO,
					{ title: "已处理8" } as TABS_ITEM_INFO,
				] as TABS_ITEM_INFO[],
				activeId:"2",
				activeId2:"-1",
				loadingData:true,
			};
		},
		onLoad() {
			/** 下面是模拟数据异步加载。 */
			let t = this;
			t.activeId2 = "1"
			setTimeout(function() {
				t.list2=[
					{ title: "全部" } as TABS_ITEM_INFO,
					{ title: "已完成", dotType: 'dot' } as TABS_ITEM_INFO,
					{ title: "已删除", dotType: 'label', dotText: '36' } as TABS_ITEM_INFO,
				] as TABS_ITEM_INFO[]
				t.loadingData = false
			}, 1500);
		},

		methods:{
			
		}
	}
</script>

<style lang="scss">

</style>
		
