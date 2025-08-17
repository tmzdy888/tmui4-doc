
## 浮动面板 FloatDrawer

***

#### 介绍

提供流畅的拖拉阻尼效果，回弹丝滑。右滑关闭逻辑已经实现,但在app体验不好,主要是scoll与事件冲突需要官方优化.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-float-drawer/x-float-drawer.uvue**

#### 使用

<x-float-drawer></x-float-drawer>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| show | 显示可v-model:show双向绑定<br>默认是打开还是放置在底部。 | boolean | false |
| onlyHeader | 是否仅允许通过标题栏拖动。 | boolean | false |
| duration | 动画时间 | number | 350 |
| round | 向上的圆角<br>空值时，取全局配置的圆角。 | string | "" |
| size | 百分比，数字字符或者带单位,<br>默认露出的内容高度 | string | "15%" |
| maxHeight | 弹层最大的高度值，默认为屏幕的可视高<br>提供值时不能为百分比，可以是px,rpx单位数字。如果你不带单位，默认转换为rpx单位。 | string | "80%" |
| triggerDy | 当拖动时，触发打开和关闭时的临界值，单位是px<br>如果没有达到此临界值时，将会回弹至原始位置。 | number | 180 |
| threshold | 当拖动时，如果已经达到了关闭和打开时的临界值时<br>可以继续拖拉时缓动阻尼值 | number | 0.045 |
| bgColor | 内容层的背景色 | string | "white" |
| darkBgColor | 暗黑的背景色,空时，取全局的sheetDarkColor | string | "" |
| actionColor | 拖动标题栏的横线背景色 | string | "#888888" |
| disabledScroll | 禁用内部的容器并采用view容器 | boolean | false |
| containerType | 没有禁用disabledScroll生效<br>容器内部使用的类型<br>scroll :scroll-view<br>list : list-view | string | 'scroll' |
| disabled | 是否禁用用户滚动等来触发关闭或者打开。 | boolean | false |
| zIndex | 层级 | number | 100 |
| contentMargin | 控制内容的边跑,有时需要自定布局时非常有用.<br>请直接使用style css规则写margin, | string | "0 16px 16px 16px" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| close | - | 关闭时执行 |
| open | - | 打开执行的事件 |
| beforeOpen | - | 打开前执行 |
| beforeClose | - | 关闭前执行 |
| heightChange | - | 高度位置变化时触发这个差值.返回参数evt是个百分比,0%是最低下,100%代表是在最顶部. |
| movestart | - | 开始拖动 |
| moveend | - | 结束拖动 |
| update:show | - | 等同v-model:show |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | **show** : Boolean<br>**show** : Number<br>**height** : Boolean<br>**height** : Number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/float-drawer

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view style="flex:1">
		<x-sheet color="primary" >
			<view ref="domview" class="heightani mb-16" :style="{height:spr+'px'}">
				<x-text  class="text-size-g text-weight-b ma-16" color="primary">我是丝滑般的差值效果{{spr}}</x-text>
			</view>
			<text class="text-size-g text-weight-b text-white">浮动面板 FloatDrawer</text>
			<text class="text-size-m text-grey mt-10 text-white line-8">可以自由设定露出最小值和最大值，支持rpx,px,%等单位，性能流畅回弹丝滑</text>
			<text class="text-size-m text-grey mt-10 text-white line-8 mb-16">也可以通过双向绑定手动控制打开和关闭</text>
			<text class="text-size-m text-grey mt-10 text-white line-8 mb-16">通过movestart,moveend,heightChange配合动画可以实现反向差值动画,类似头条的视频中的评论缩放效果.</text>
			<x-button :block="true" @click="showFloat=true">打开</x-button>
			
		</x-sheet>

		<x-float-drawer content-margin="0px" @beforeClose="onbeforeclose" @movestart='onmovestart' 
		@moveend="onmoveend" @heightChange="onheightChange" v-model:show="showFloat" size="120px" max-height="75%">
			<template v-slot:default="{show,height}">
				<x-sheet :margin="['0']">
					<x-text  class="text-size-g text-weight-b mb-16">请拖动我查看效果</x-text>
					<x-button color="success" :block="true" @click="showFloat=false">关闭</x-button>
				</x-sheet>
				<x-sheet height="100" v-for="item in 10" :key="item" color="primary" >
				</x-sheet>
			</template>
		</x-float-drawer>
		<view stle="height:1000px"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showFloat:false,
				spr:0,
				ismove:false
			}
		},
		methods: {
			onbeforeclose(){
				// console.log(11)
			},
			onmovestart(){
				let dom = this.$refs['domview']! as UniElement;
				dom.style.setProperty('transition-duration','0ms')
			},
			onmoveend(){
				let dom = this.$refs['domview']! as UniElement;
				dom.style.setProperty('transition-duration','300ms')
				
			},
			onheightChange(pre:number){
				let dom = this.$refs['domview']! as UniElement;
				this.spr = pre*1.5
				// console.log("接收HeightChange事件日志",this.spr)
				dom.style.setProperty('height',Math.ceil(this.spr)+'px')
				// console.log(pre+'%')
			}
		}
	}
</script>

<style scoped>
.heightani{
	/* transition-duration: 0ms; */
	transition-property: height;
	transition-timing-function: linear;
	background-color: #ffffff;
	overflow: hidden;
	border-radius: 8px;
}
</style>

		
