
## 提及 xMention

***

#### 介绍

它是依照微信的输入体验来的,请自行体验效果,样式是可以直接在标签上写style来定义你想的外观.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-mention/x-mention.uvue**

#### 使用

<x-mention></x-mention>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| bgColor | 输入框背景及标签背景 | string | "#f5f5f5" |
| darkBgColor | 输入框的暗黑背景色<br>空值读取全局的Input暗黑背景色 | string | "" |
| btnColor | 右边按钮主题色，空取全局主题色 | string | "" |
| fontSize | 文本大小 | string | "16" |
| fontColor | 文本颜色，暗黑时取白 | string | "#333333" |
| width | 宽 | string | "auto" |
| height | 高 | string | "40" |
| round | 圆角 | string | "" |
| placeholder | 输入提示词,请输入内容，@选择朋友,按确认完成 | string | "" |
| modelValue | 双向绑定 | string | "" |
| mentionChar | 提及符号 | string | "@" |
| autFoucs |  | boolean | false |
| adjustPosition |  | boolean | false |
| holdKeyboard |  | boolean | false |
| beforeRemove |  | MENTION_BEFOREREMOVE_TYPE | (tag : string) : boolean => {<br>    return true<br>} |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : string[] | 标签变化时触发 |
| mention | - | 输入提及符时触发 |
| removemention | - | 用记在删除字符时,如果触发删除标签时触发 |
| confirm | **value** : string | 标签变化时触发 |
| input | **value** : string | 输入时触发. |
| blur | - | 失去焦点 |
| foucs | - | 获得焦点 |
| keyboardheightchange | - | 键盘高度变化时 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| setFoucus | **val** : boolean | - | 设置当前焦点 |


#### 示例页面路径

/pages/qita/mention

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
			<x-text font-size="18" class=" text-weight-b mb-8">提及 xMention</x-text>
			<x-text color="#999999">此组件的输入体验与微信基本相符,体验比较完善它不与选择视图绑定,通过事件控制将会完美的支持自定界面.</x-text>
		</x-sheet>
	
		<x-sheet v-for="(item,index) in chat" :key="index" >
			<x-text :label="item" :height-light="pengyouListNames" height-light-color="red" ></x-text>
		</x-sheet>
		<x-sheet>
			
			<x-mention dark-bg-color="#333" 
			style="border-radius: 6px;"
			@confirm="onconfirm" ref="mention" @mention="onmention" :beforeRemove="beforeRemove" @removemention="removemention"
				v-model="(keyword as string)"></x-mention>
				
				<x-text class="mt-n8 opacity-5" font-size="12" color="#999999">可以像微信一样选择朋友并在编辑朋友删除字符让之前选择的失效.然后继续选择,会在删除前和删除后通过事件通知.</x-text>
		</x-sheet>

		<x-drawer :showClose="true" :show-footer="false" title="请选择朋友" v-model:show="(show as boolean)" size="500px">
			<view>
				<x-cell @click="cellClick(item.name)" v-for="(item,index) in pengyouList" :card="false" :key="index"
					:title="item.name" :bottom-border-insert="false"></x-cell>
			</view>
		</x-drawer>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup lang="uts">
	import { ref } from "vue"
	type PENGYOU_TYPE = {
		name : string,
		id : string
	}
	const show = ref<boolean>(false)
	const keyword = ref("")
	const mention = ref<XMentionComponentPublicInstance | null>(null)
	const pengyouList = ref<PENGYOU_TYPE[]>([])
	const pengyouListNames = computed(():string[] => pengyouList.value.map((el:PENGYOU_TYPE):string=> ('@'+el.name)))
	const chat = ref<string[]>([])
	const tags = ref<string[]>([])

	// 添加虚拟数据
	for (let i = 0; i < 10; i++) {
		pengyouList.value.push({
			name: "朋友" + i,
			id: i.toString()
		} as PENGYOU_TYPE)
	}

	const onmention = () => {

		show.value = true;
	}
	const cellClick = (str : string) => {
		if(mention.value==null) return;
		keyword.value += str + ' '
		show.value = false;
		mention.value!.setFoucus(true)
		tags.value.push(str)
	}
	//删除前需要校验当前删除的标签是不是朋友标签,因为如果用户把光标移动有名称内删除,打乱了标签,其实已经不构成是标签了,就不需要删除了.
	const beforeRemove = (tag : string) : boolean => {
		let index = pengyouList.value.findIndex((el : PENGYOU_TYPE) : boolean => el.name == tag)
		console.log("即将删除标签:", tag, index > 1 ? '是' : '否')
		return index > -1
	}
	const removemention = (tag : string) => {
		console.log("被删除标签:", tag)
	}
	const onconfirm = (nowval:string)=>{
		chat.value.push(nowval)
		keyword.value = ''
	}
</script>

<style lang="scss">

</style>

		
