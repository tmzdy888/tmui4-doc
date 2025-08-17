
## 虚拟列表 xVirtualList

***

#### 介绍

这是一个超高虚拟列表，无论几万数据都能轻松应对是你列表处理数据的不二之选，集成下拉刷新，触底更新，指定索引位置等。
未来将应于表格，picker等系列组件，作为其它组件的底层存在，极大提高性能。使用时请注意demo示例使用方法。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.14 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-virtual-list/x-virtual-list.uvue**

#### 使用

<x-virtual-list></x-virtual-list>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| itemHeight | 项目高度，不可用auto,只能是数字（默认为px),带单位的rpx,px | string | "50" |
| viewCount | 渲染显示多少个,它不是最终的渲染数量，是最少数量，因为内部还有个缓存数量 | number | 5 |
| list | 数据列表 | Array | () => [] as any[] |
| bufferSize | 缓冲区大小，在可视区域前后额外渲染的项目数量 | number | 2 |
| enableVirtual | 是否启用虚拟滚动 | boolean | true |
| refresherEnabled | 启用下拉刷新 | boolean | false |
| pullState | 需要自行管理下拉状态，默认为false,通过事件pull触发设置为true,结束设置为False | boolean | false |
| refresherBottomEnabled | 启用触底刷新 | boolean | false |
| bottomState | 需要自行管理下拉状态，默认为false,通过事件bottom触发设置为true,结束设置为False | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| scroll | - | 滚动事件 |
| pull | - | 滚动到顶时触发 |
| bottom | - | 触底时触发 |
| rangeChange | - | 渲染范围变化时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 内容插槽你在这里渲染内容 | **data** : any[]<br>**data** : number<br>**data** : number<br>**startIndex** : any[]<br>**startIndex** : number<br>**startIndex** : number<br>**endIndex** : any[]<br>**endIndex** : number<br>**endIndex** : number<br> |
| bottom | 底部插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| scrollToIndex | - | - | 滚动到指定索引 |
| refreshSize | - | - | 刷新容器尺寸 |
| resetScroll | - | - | 重置滚动位置 |
| getRenderRange | - | - | 获取当前渲染范围 |
| getContainerBounds | - | - | 获取容器尺寸 |


#### 示例页面路径

/pages/zhanshi/virtual-list

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
			<x-text font-size="18" class=" text-weight-b mb-8">虚拟列表 xVirtualList</x-text>
			<x-text color="#999999">通过插槽渲染数据，但不要让项目高超过指定的项目高。本页面演示数量为：1万条，打开时间为60ms左右，不存在卡页面情况。</x-text>
			<view class="flex flex-row flex-row-center-between mb-10">
				<x-button class="flex-1" @click="scrollTo" >指定</x-button>
				<x-button class="ml-5 flex-1" @click="reloadData" >追加</x-button>
				<x-button class="mx-5 flex-1" @click="changeData" >20条</x-button>
				<x-button class="flex-1" @click="clearAll" >清空</x-button>
			</view>
		</x-sheet>
		<x-virtual-list 
		v-if="list.length>0"
		ref="virtual" 
		:pullState="pullState"
		:bottomState="bottomState"
		@pull="onpull"
		@bottom="bottomLoad"
		:refresherEnabled="true"
		:refresherBottomEnabled="true"
		style="flex: 1;margin: 0 16px;" itemHeight="80" :list="list">
			<template v-slot:default="{data,startIndex,endIndex}">
				<view class="item" v-for="(item,index) in (data as UTSJSONObject[])" :key="index" :style="{height:'80px'}">
					<view class="itemWrap flex flex-row flex-row-center-start">
						<!-- 为什么要给图片加key，是因为浏览器它同样的key变动时在vue中是重复的图片加载有个视觉停留，会
						 给人感觉图片虚的变动时好像是旧数据，而app不需要加，因为app图片是缓存读取直接显示更换，没有延迟，给人感觉就是加载动态的数据。
						 -->
						<image 
						class="round-6"
						<!-- #ifdef MP||WEB||APP-HARMONY -->
						:key="item.getAny('id')" 
						<!-- #endif -->
						style="width: 50px;height:50px;" :src="`https://store.tmui.design/api_v2/public/random_picture?random=${item.getAny('id')}`"></image>
						<text class="ml-10" style="font-size:18px">{{item.getAny('text')}}</text>
					</view>
				</view>
			</template>
		</x-virtual-list>
		<x-empty @click="load" btn-label="加载1万条" v-if="list.length==0" :loading="false" :empty="true"></x-empty>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>

	// @ts-ignore
	const virtual = ref<XVirtualListComponentPublicInstance|null>(null)
	const list = ref<UTSJSONObject[]>([])
	const pullState = ref(false)
	const bottomState = ref(false)
	function load(){
		let tmeplist = [] as UTSJSONObject[]
		for(let i=0;i<10000;i++){
			tmeplist.push({
				id:i,
				text:`数据项目-${i+1}`
			} as UTSJSONObject)
		}
		list.value = tmeplist
	}
	function reloadData(){
		let tmeplist = [] as UTSJSONObject[]
		for(let i=0;i<20;i++){
			tmeplist.push({
				id:i,
				text:`数据项目-a${i+1}`
			} as UTSJSONObject)
		}
		list.value = [...list.value,...tmeplist] 
	}
	
	function clearAll(){
		pullState.value = false
		bottomState.value = false
		list.value = [] as UTSJSONObject[]
	}
	function changeData(){
		list.value = list.value.slice(0,20)
	}
	
	function onpull(){
		pullState.value = true
		setTimeout(()=>{
			pullState.value = false
		},6020)
	}
	function bottomLoad(){
		bottomState.value = true
		
		setTimeout(()=>{
			bottomState.value = false
			// 加载更多数据
			reloadData()
		},1200)
	}
	
	function scrollTo(){
		virtual.value?.scrollToIndex?.(2)
	}
	onReady(()=>{
		load()
	})
</script>

<style scoped lang="scss">
	.item{
		display: flex;
		flex-direction: column;
		padding-bottom: 5px;
	}
	.itemWrap{
		background-color: white;
		padding: 16px;
		flex: 1;
	}
</style>

		
