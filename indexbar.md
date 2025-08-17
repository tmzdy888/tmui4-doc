
## 索引 xIndexbar

***

#### 介绍

特别提醒：本组件在1.0.9重构不向下兼容，并且删除了子组件：x-indexbar-item，不再需要子组件。请使用对应的动态插槽来渲染
数据，demo是526条数据的测试依赖右边索引滑动跟手流畅。
虚拟列表有个缺点会在滚动时分页读取数据并复用布局，因此如果你想做带图片的索引，
建议进入应用后启用后台缓存已有的头像或者图片数据类似微信那样缓存图片，这样虚拟加载的时候闪烁感就少了
重要：插槽内不要使用任何自定组件布局，也不要增加任何额外的节点，能少就少。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-indexbar/x-indexbar.uvue**

#### 使用

<x-indexbar></x-indexbar>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽 | string | "auto" |
| height | 高，%,rpx,px单位均可。 | string | "100%" |
| dotActiveColor | 侧边指示激活时的文字颜色<br>空值是取全局主题值 | string | "" |
| dotColor | 侧边指示未激活时的文字颜色 | string | "#c0c0c0" |
| dotBgColor | 侧边指示的背景颜色 | string | "white" |
| list |  | UTSJSONObject[] | () : UTSJSONObject[] => [] as UTSJSONObject[] |
| cellHeight | 项目的高<br>只能是数字，或者带rpx,px单位 | string | '50' |
| titleHeight | 项目的标题高<br>只能是数字，或者带rpx,px单位 | string | '32' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| header | 悬浮的菜单头 | - |
| default | 动态插槽 | **index** : UTSJSONObject<br>**index** : number<br>**index** : number<br>**currentIndex** : UTSJSONObject<br>**currentIndex** : number<br>**currentIndex** : number<br>**current** : UTSJSONObject<br>**current** : number<br>**current** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/indexbar

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
		<x-sheet style="flex:1" :padding="['24','0','0','0']">
			<x-indexbar :list="list" height="500" cellHeight="72">
				<template v-slot:default="{index,currentIndex,current}">
					<view class="flex flex-row flex-row-center-start" style="border-bottom: 1px solid rgba(100, 100, 100, 0.1);height:72px;">
						<image class="flex-shrink" :src="`https://store.tmui.design/api_v2/public/random_picture?row=${index}`" style="width:50px;height:50px;border-radius: 50px;"></image>
						<text :style="{color:isDark?'#ffffff':'#000000'}" class="ml-20">{{(current as UTSJSONObject).getAny("name")}}</text>
					</view>
				</template>
			</x-indexbar>
		</x-sheet>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->

</template>

<script>
	// 示例参数数据,请vip用户到demo中下载查询数据样例.
	import {dataslist} from "./indexdata.uts"
	import { xStore } from "@/uni_modules/tmx-ui/index.uts";
	
	export default {
		data() {
			return {
				list:dataslist as UTSJSONObject[]
			};
		},
		computed:{
			isDark:():boolean=>xStore.xConfig.dark=='dark'
		},
		onLoad() {
			
		},
		methods:{
			
		}
	}
</script>

<style lang="scss">

</style>
		
