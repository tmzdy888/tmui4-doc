
## 富文本 xMarkdown

***

#### 介绍

这是一个预览markdown的组件。当前支持markdown:表格，及数学公式的展示。
【小程序端请注意】从1.1.14开始支持LaTex数学公式，但要注意数学公式暂时不要混合在表格内，会造成表格断列，样式异常。
【组件目录内】有一个fonts.zip字体压缩包，请上传到你自己的服务器，并打开katex.min.css，把里面的字体链接换成你的字体连接，如果不换可能我服务器一关你就用不了了。
传递正常markdown或者html内容即可,已经支持了暗黑适配，请自行配置样式。
预览md:支持流式解析,支持动态解析内容.方便大家对话用.同时也支持了动态高,自动适配.
同时也放开了内容复制(但会导致安卓(截止sdk4.53)页面滚动不了,需要你们自己解决:给这个组件盖个view屏蔽webview的事件,这是sdk底层问题,我修复不了.)
1.1.10废弃了函数:getMarkdown
所有平台的样式已经重置为none,你需要通过属性nodeStyle来设置默认样式.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑ | ☑️ | 4.53+ | 1.1.10 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-markdown/x-markdown.uvue**

#### 使用

<x-markdown></x-markdown>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 窗口宽 | string | 'auto' |
| height | 窗口高,auto时会自动适配高. | string | 'auto' |
| value | 需要渲染的markdow或者html内容。 | string | "" |
| isHtml | 是否启用纯html渲染。如果你的内容含有特殊字符比如:%,^&%这种不要出现在里面<br>此时你启用isHtml会经过数据处理直接跳过插件,直接赋值内容到html.就不要启用Markdown了. | boolean | false |
| nodeStyle | 富文本的style样式,不可以动态更改.<br>为了对齐所有端,默认已经把所有平台的样式删除.因此你可以自己设置默认样式来对齐所有平台. | string | "line-height:1.6;color:#000" |
| nodeDarkStyle | 同上，暗黑时的样式. | string | "line-height:1.6;color:#fff" |



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

/pages/zhanshi/markdown

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
		<x-text font-size="18" class=" text-weight-b mb-8">富文本 markdown</x-text>
		<x-text  color="#999999">
			它支持传入html,markdown格式等内容进行预览，同时也支持动态的相关格式内容解析（常见SSE流式内容更新赋值解析，可能标签被拆分再解析）
			不管你传的是什么格式，建议遵循微信小程序的富文本所支持的标签。这样可以和另一个组件x-edite相互转换编辑和预览。
		</x-text>
	</x-sheet>
	<x-sheet>
		<x-markdown @tagClick="ontagclick" @init="sse" :value="str" ></x-markdown>
		<x-button class="mt-20" @click="appendText" :block="true">追加内容</x-button>
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
				str:
`# 全局配置
## 介绍

本配置参数会影响整个app风格，请慎重配置，或者根据你的UI/UX设计师指示配置

**可以在任意位置导入并设置，立即生效，全局响应**\n**堙**

| This header    | spans two | Header A |
|-------------|------------|----------|
| Cell A      | Cell B     | Cell C   |
| Cell A      | Cell B     | Cell C   |
| TMUI4.0   | Cell B     | 好棒  |

## 数学公式
$4x=x^2$ $C^a_b+\\sqrt{c}$ 
$c = \\pm\\sqrt{a^2 + b^2}$
$x=x^2$ $4x=x^2$
<img style="width:100px;height:88px" src="https://xui.tmui.design/assets/logo-a483vlZl.png">

$$
C^a_b+\\sqrt{c}
$$

## CSS代码
\`\`\`css
<uni-view data-v-361a5606="" class="xSheet" 
style="background-color: rgb(255, 255, 255); 
width: auto; height: auto; border-radius: 14px; border-width: 0px; 
border-color: transparent; margin: 0px 14px 14px; padding: 14px; box-shadow: none; border-style: solid;">
<--!>输入内容<!-->
</uni-view>

\`\`\`

\`\`\`css
const highlight = "code";
\`\`\`


`
			}
		},
		onLoad() {
			
		},
		onUnload(){
			
			clearInterval(this.ids)
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
			sse(){
				// 下面是演示流式解析markdown
				let list = [
					"**你好",
					"**好吧\n",
					"## 好的哦\n",
					"****\n",
					"<a href='https://tmui.design'>点我事件被拦截</a> \n被",
					"<span style='color:red'>十的</span>",
					`
\`\`\`javascript
const highlight = "code";
\`\`\`

					`
					
				]
				let i=0;
				let ids = 0;
				let _this = this
				clearInterval(_this.ids)
				this.ids = setInterval(()=>{
					if(i>=list.length){
						clearInterval(_this.ids)
						return;
					}
					_this.str += list[i]
					i++;
				},150)
			},
			getHtml(){
				let el = this.$refs["mk"] as XMarkdownComponentPublicInstance
				el.getHtml()
			},
			myVale(str:string){
				uni.showModal({
					title:"内容",
					content:decodeURIComponent(str),
					showCancel:false
				})
			},
			appendText(){
this.str = this.str + `
辣椒炒肉的热量和营养成分会因配料的比例和烹饪方式有所不同。以下是一个大致的估算，以100克辣椒炒肉为例： \n - **热量**: 约 150-250 千卡 \n - **碳水化合物**: 约 5-10 克 \n - **脂肪**: 约 10-15 克 \n - **蛋白质**: 约 8-12 克 \n 具体数值会根据所使用的肉类（如猪肉、牛肉等）的脂肪含量、辣椒的量、油的使用量以及是否添加其他调料（如酱油、糖）等因素而有所不同。如果你有具体的食材比例，可以更精确地计算这些数值。
`
				
			}
		}
	}
</script>

<style>

</style>

		
