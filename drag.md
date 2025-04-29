
## 拖拽排序 xDrag

***

#### 介绍

自由布局拖拽排序组件,列或者宫格都支持。使用时,需要将需要拖拽排序的子元素设置为x-drag-item。
并且子元素和父元素不允许通过style来动态设置宽高,否则拖拽排序会失效。并且list及子元素中的order不允许动态设置,否则拖拽排序会失效。
想要动态修改数据可以通过vif切换重新渲染下。web支持响应式屏幕。本插件：引用了原生插件x-vibrate-s

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-drag/x-drag.uvue**

#### 使用

<x-drag></x-drag>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| itemHeight | 项目的高度,不要动态更改。 | string | "100" |
| col | 列数，默认1即列表布局,不要动态更改。<br>如果是1以上就是宫格布局了。 | number | 1 |
| list | 你的排序数据list，变动后，请通过change事件来取得<br>主要是用来骗编译器用的。 | UTSJSONObject[] | () : UTSJSONObject[] => [] as UTSJSONObject[] |
| scrollDiff | 当组件放置在scroll页面中,如果拖动时项目需要滚动时自动滚动的进步值<br>比如组件在屏幕被底部或者顶部遮挡一部分,当拖动靠近底部时,会向下滚动的值.<br>这个值是你外部自己通过设置滚动页面的scrollTop来达成的,具体见demo,已经为你写了示例. | number | 25 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 排序变动时触发 |
| move | - | 拖动的时候触发,可以根据参数进行对你超出页面屏幕高时进行一个滚动. |
| end | - | - |
| start | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 只可放置子组件x-drag-item | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/drag

#### 示例源码

<template>
	<!-- #ifdef APP -->
	<scroll-view style="flex:1" >
	<!-- #endif -->
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">拖拽排序 xDrag</x-text>
			<x-text color="#999999" >
				使用子组件窗口进行排序，组件内可以自由布局，最大的灵活度不影响你布局自己的外观。
				同时还支持设定col来定制为多列布局为宫格或者为列表模式。
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-drag @change="onchange" v-if="list.length>0" :list="list">
				<x-drag-item
				 style="display: flex;flex-direction: column;"
				 v-for="(item,index) in list" 
				 :order="index" 
				 :key="index">
					<view class="flex-1 mb-2 px-12 flex-row flex flex-row-center-start" :style="{backgroundColor: bgColor}">
						<x-text>长按{{item.getNumber('id')}}排序</x-text>
					</view>
				</x-drag-item>
			</x-drag>
			<x-empty v-if="list.length==0" ></x-empty>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b ">设置为2列形成宫格</x-text>
		</x-sheet>
		<x-sheet>
			<x-drag :col="2" :list="list2">
				<x-drag-item
				 style="display: flex;flex-direction: column;"
				 v-for="(item,index) in list2" 
				 :order="index" 
				 :key="index">
					<view @click="onclick(index)" class="flex-1 mb-2 mx-2 px-12 flex-row flex flex-row-center-start" :style="{backgroundColor: bgColor}">
						<x-text>长按{{item.getNumber('id')}}排序</x-text>
					</view>
				</x-drag-item>
			</x-drag>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b ">演示局部拖动,拖动时页面自动滚动</x-text>
		</x-sheet>
		<x-sheet>
			<x-drag :list="list4" @move="onmove" @start="ontouchstart" @end="ontouchend">
				<x-drag-item
				 style="display: flex;flex-direction: column;"
				 v-for="(item,index) in list4" 
				 :order="index" 
				 :key="index">
					<view class="flex-1 mb-2 px-12 flex-row flex flex-row-center-start" :style="{backgroundColor: bgColor}">
						<view 
						
						@longpress.stop="" 
						<!-- #ifdef WEB -->
						@mousedown.stop=""
						@mousemove.stop=""
						<!-- #endif -->
						@click.stop="onclick(index)"
						style="height:100%" 
						class="flex-1"
						>
							<x-text>{{index}}</x-text>
						</view>
						<view>
							<x-icon code="EF3E"></x-icon>
						</view>
					</view>
				</x-drag-item>
				
			</x-drag>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b ">设置更多的列</x-text>
		</x-sheet>
		<x-sheet>
			<x-drag :col="4" :list="list3">
				<x-drag-item
				 style="display: flex;flex-direction: column;"
				 v-for="(item,index) in list3" 
				 :order="index" 
				 :key="index">
					<view class="flex-1 mb-2 mx-2 px-12 flex-row flex flex-row-center-start" :style="{backgroundColor: bgColor}">
						<x-text>长按排序</x-text>
					</view>
				</x-drag-item>
			</x-drag>
		</x-sheet>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { xConfig } from "@/uni_modules/tmx-ui/config/xConfig.uts"
	export default {
		data() {
			return {
				list:[] as UTSJSONObject[],
				list2:[
					{id:1} as UTSJSONObject,
					{id:2} as UTSJSONObject,
					{id:3} as UTSJSONObject,
					{id:4} as UTSJSONObject,
					{id:5} as UTSJSONObject,
					{id:6} as UTSJSONObject
				] as UTSJSONObject[],
				list4:[
					{id:1} as UTSJSONObject,
					{id:2} as UTSJSONObject,
					{id:3} as UTSJSONObject,
					{id:4} as UTSJSONObject,
					{id:5} as UTSJSONObject,
					{id:6} as UTSJSONObject
				] as UTSJSONObject[],
				list3:[
					{id:1} as UTSJSONObject,
					{id:2} as UTSJSONObject,
					{id:3} as UTSJSONObject,
					{id:4} as UTSJSONObject,
					{id:5} as UTSJSONObject,
					{id:6} as UTSJSONObject,
					{id:7} as UTSJSONObject,
					{id:8} as UTSJSONObject,
					{id:9} as UTSJSONObject
				] as UTSJSONObject[],
				tid:10,
				nowPageScrollY:0,
				isMoveScroll:false,
				scrollDiff:25
			}
		},
		computed:{
			bgColor():string{
				return xConfig.dark=='dark'?'#333':'#e3e8f4'
			}
		},
		mounted() {
			let t = this;
			this.tid = setTimeout(function() {
				t.list = [
					{id:1} as UTSJSONObject,
					{id:2} as UTSJSONObject,
					{id:3} as UTSJSONObject,
					{id:4} as UTSJSONObject,
					{id:5} as UTSJSONObject,
					{id:6} as UTSJSONObject
				] as UTSJSONObject[]
			}, 500);
		},
		beforeUnmount() {
			clearTimeout(this.tid)
		},
		onPageScroll(opts) {
			if(this.isMoveScroll) return;
			this.nowPageScrollY = opts.scrollTop
			
		},
		methods: {
			ontouchstart(){
			
			},
			ontouchend(){
				this.isMoveScroll = false;
				
			},
			onmove(diff:number){
				let _this = this;
				this.isMoveScroll =true;
				_this.nowPageScrollY+=diff;
				uni.pageScrollTo({
					scrollTop:_this.nowPageScrollY
				})
			},
			onclick(index:number){
				uni.showToast({title:`点击了:${index}`,icon:'none'})
			},
			onchange(list:UTSJSONObject[]){
				console.warn("变动的数据：",list)
			}
		}
	}
</script>

<style>

</style>

		
