
## 富文本编辑器 xEditor

***

#### 介绍

传递正常markdown或者html内容即可,传递markdown时会自动转换为html,如果直接传递html不会转换直接赋值.
值得注意的是:在微信小程序端它是没有样式高亮显示的.其它平台有样式指示,这是因为受限于微信官方本身就不支持.
另外我测试发现HBX4.53 sdk ios端的输入框焦点有问题，导致无法设置样式，待官方修复。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑ | ☑️ | 4.53+ | 1.1.10 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-editor/x-editor.uvue**

#### 使用

<x-editor></x-editor>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 窗口宽 | string | 'auto' |
| height | 窗口高,可以传递所支持的任意单位高. | string | '350' |
| value | 需要渲染的markdow或者html内容。 | string | "" |
| isHtml | 是否启用纯html渲染。如果你的内容含有特殊字符比如:%,^&%这种不要出现在里面<br>此时你启用isHtml会经过数据处理直接跳过插件,直接赋值内容到html.就不要启用Markdown了. | boolean | false |
| nodeStyle | 富文本的style样式,不可以动态更改.<br>为了对齐所有端,默认已经把所有平台的样式删除.因此你可以自己设置默认样式来对齐所有平台. | string | "line-height:1.6;color:#000" |
| nodeDarkStyle | 同上，暗黑时的样式. | string | "line-height:1.6;color:#fff" |
| color | 默认的按钮背景色 | string | "#f5f5f5" |
| activeColor | 激活时的选中背景色<br>空值取全局 | string | "" |
| customColos | 自定义默认的文字/背景颜色 | string[] | () : string[] => ['#ff0000', '#ff00ff', '#00ff00', '#00ffff', '#ffff00', '#ffffff', '#000000'] as string[] |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| tagClick | **** : undefined | 特定的a,img标签被点击触发,小程序不支持,其它平台支持. |
| init | - | 图表加载初始化完成后触发此事件。 |
| getValue | - | 需要通过ref函数调用getHtml才会触发此函数 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| getHtml | - | - | 获取html内容。注意本函数不会返回内容，你要通过事件getValue得到html内容. |


#### 示例页面路径

/pages/biaodan/editor

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
		<x-editor @getValue="myVale" ref="edite" @tagClick="ontagclick" :value="str" height="450px" ></x-editor>
		<x-button class="mt-20" @click="appendText" :block="true">追加内容</x-button>
		<x-button class="mt-20" @click="getHtml" :block="true">获取Html内容</x-button>
		
		
	</x-sheet>
	<x-sheet>
		<x-text font-size="18" class=" text-weight-b mb-8">富文本编辑器 xEdite</x-text>
		<x-text  color="#999999">
			它允许传入markdown内容和html内容，然后进行编辑，再导出html内容，不支持导出markdown格式。
			另外由于需要全端兼容，请以微信的编辑器所支持的html标签为准。markdown时，也同样只支持基本的格式，不支持复杂的代码，公式等。
		</x-text>
	</x-sheet>
	
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>


	export default {
		data() {
			return {
				ids:0,
				str:'# 全局配置\n## 介绍\n *本配置参数会影响整个app风格，请慎重配置，或者根据你的UI/UX设计师指示配置*\n',
			}
		},
		onLoad() {
			
		},
		onUnload(){
			
		},
		methods: {
			ontagclick(detail:UTSJSONObject){
				let text = detail.getString('attr')
				text = text == null?'':(text!)
				uni.showToast({
					title:text,
					icon:'none'
				})
			},
	
			getHtml(){
				let el = this.$refs["edite"] as XEditorComponentPublicInstance
				el.getHtml()
			},
			myVale(str:string){
				uni.showModal({
					title:"内容",
					content:str,
					showCancel:false
				})
			},
			appendText(){
				this.str += '\n辣椒炒肉的热量和营养成分会因配料的比例和烹饪方式有所不同。以下是一个大致的估算，以100克辣椒炒肉为例： \n - **热量**: 约 150-250 千卡 \n - **碳水化合物**: 约 5-10 克 \n - **脂肪**: 约 10-15 克 \n - **蛋白质**: 约 8-12 克 \n 具体数值会根据所使用的肉类（如猪肉、牛肉等）的脂肪含量、辣椒的量、油的使用量以及是否添加其他调料（如酱油、糖）等因素而有所不同。如果你有具体的食材比例，可以更精确地计算这些数值。'
				
			}
		}
	}
</script>

<style>

</style>

		
