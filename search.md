
## 搜索栏 xSearch

***

#### 介绍

可定制化强

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-search/x-search.uvue**

#### 使用

<x-search></x-search>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| round | 输入框圆角 | string | "8" |
| showClear | 是否显示清除图标 | boolean | true |
| rightText | 右侧文本 | string | "搜索" |
| modelValue | 双向绑定的输入值 | string | "" |
| placeholder | 输入框提示语 | string | "请输入" |
| iconColor | 搜索图标和清除图标的颜色 | string | "#bfbfbf" |
| color | 搜索条背景 | string | "#ffffff" |
| cancelFontColor | 取消的文本色 | string | "#000000" |
| darkColor | 暗黑模式下的搜索条背景，空值取：sheetDarkColor | string | "" |
| inputBgColor | 输入框的背景 | string | "#f5f5f5" |
| fontColor | 输入框的字体颜色 | string | "#333333" |
| border | 边框style请输入规范的css<br>格式:1px,solid,red<br>默认空值，表示不设置边 | string[] | () : string[] => [] as string[] |
| darkBorderColor | 边框style请输入规范的css<br>如:red,暗黑变换时，如果你设定了border，但没有设定本值，将会自动取全局的边线颜色。<br>默认空值，表示不设置边 | string | "" |
| placeholderStyle | 输入框的提示样式 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cancel | - | 取消时触发 |
| clear | - | 清空时触发 |
| rightClick | **** : string | 点击右侧文本时触发,如果你使用了插槽替换了，此事件不会触发 |
| confirm | **** : string | 输入法点了确认搜索按钮时触发 |
| input | **** : string | 输入时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| left | 左插槽 | - |
| inputLeft | - | - |
| inputRight | - | - |
| cacel | - | - |
| right | - | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/index/search

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor"
			:front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view style="flex:1;display: flex;flex-direction: column;">

		<x-input class="mx-14 mb-14" @input="searchWordList" v-model="word" color="white" left-icon="search-2-line" placeholder="输入关联组件名或者英文名"></x-input>
		
		<!-- #ifdef MP -->
		<view style="flex:1;display: flex;flex-direction: column;position: relative;margin:0 16px;">
		<!-- #endif -->
		<list-view class="flex-1"
		<!-- #ifdef MP -->
		style="position: absolute;height: 100%;width:100%"
		<!-- #endif -->
		<!-- #ifndef MP -->
		style="margin:0 16px;"
		<!-- #endif -->
		>
			<list-item v-for="(item,index) in list" :key="index">
				<navigator :url="item.url" class="lsitCell flex flex-row flex-row-center-between" :style="{backgroundColor: listBgcColor}">
					<text :style="{color:textcColor}">{{item.title}}</text>
				</navigator>
			</list-item>
			
			<list-item>
				<x-empty title="没组件,换个词" :showBtn="false" :empty="true" :loading="false" :error="false" v-if="list.length==0"></x-empty>
			</list-item>
		</list-view>
		<!-- #ifdef MP -->
		</view>
		<!-- #endif -->

	</view>

</template>

<script setup lang="uts">
	import { listdata, type INDEXITEMINFO_AR,INDEXITEMINFO } from "./index.uts"
	import { xStore, xDate } from "@/uni_modules/tmx-ui/index.uts"
	const word = ref('')
	const list = ref<INDEXITEMINFO[]>([])
	let tid = 2232
	const listBgcColor = computed(():string=>{
		return xStore.xConfig.dark == 'dark'?xStore.xConfig.sheetDarkColor:'#ffffff'
	})
	const textcColor = computed(():string=>{
		return xStore.xConfig.dark == 'dark'?'#fff':'#333'
	})
	
	const searchWordList = (value:string)=>{
		if(value.trim()==''){
			list.value = [] as INDEXITEMINFO[]
			return
		}
		clearTimeout(tid)
		let temvalue = value.toLowerCase()
		tid = setTimeout(function() {
			let listtem = [] as INDEXITEMINFO[];
			for(let i=0;i<listdata.length;i++){
				let children = listdata[i].children;
				for(let j=0;j<children.length;j++){
					let item = children[j];
					let title = item.title.toLowerCase();
					let pagename = item.url.split('/').pop()!.toLowerCase()
					if(title.indexOf(temvalue)>-1||pagename.indexOf(temvalue)>-1){
						listtem.push(item)
					}
				}
			}
			list.value = [...listtem]
		}, 350);
	}
	onLoad((obj:OnLoadOptions)=>{
		let tempWord = obj['word'] ?? ""
		searchWordList(tempWord)
		word.value = tempWord
	})
	onBeforeUnmount(()=>{
		clearTimeout(tid)
	})
</script>

<style >
	/* #ifdef MP */
	page,body{
		height:100vh;
		display: flex;
		flex-direction: column;
	}
	/* #endif */
	.lsitCell{
		height: 50px;
		padding: 0 16px;
		margin-bottom: 1px;
		/* #ifndef APP */
		box-szing:border-box;
		/* #endif */
	}
</style>
		
