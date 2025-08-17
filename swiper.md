
## 轮播 xSwiper

***

#### 介绍

注意：本组件非官方的swiper轮播的封装，而是作者设计并开发的轮播，因此有些使用上的区别，请仔细看文档。
之所以要重新设计轮播，是为了后期的功能扩展。当前的一些功能已经比官方的还更好。
比如支持阻尼动效的设计，动效函数的设置。临界位置回弹的设置。指示点位置的偏移设置（这点非常有用，然官方不支持，而我的由于是自行开发的可以随意设置）
如果你有更多需求，你只需要阅读源码后自行扩展更多的功能。
内部只能放置子组件x-swiper-item

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-swiper/x-swiper.uvue**

#### 使用

<x-swiper></x-swiper>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前播放的索引值，可v-model动态更改。 | number | 0 |
| width | 宽 | string | "auto" |
| height | 高是必填，不可为auto。 | string | "150" |
| threshold | 当滑动时小于此值，会回弹到原位。 | number | 30 |
| damping | 当拖动时，如果已经达到了左右临界值时<br>可以继续拖拉时的缓动阻尼值<br>越小，拖的越费劲,1是不限制可以流畅的拖动 | number | 0.1 |
| animationDuration | 当打开或者松开时的动画时间 | number | 350 |
| spaceOffset | 露边出来的距离，px单位 | number | 0 |
| space | 露边出来的间隙，px单位 | number | 0 |
| model | space 两边露出，只对横向有效<br>spaceIn 两边露出，但它是被叠在了视图中的下方，只对横向有效<br>spaceOnly 单边向左露出<br>card 左右滑动切换，使用了这个就不要去设置space,spaceOffset<br>空值正常普通轮播 | string | '' |
| animationFun | 缓动动画函数。<br>见：https://easings.net/zh-cn | string | "cubic-bezier(0, 0.55, 0.45, 1)" |
| duration | 轮播时的间隔 | number | 5000 |
| vertical | 是否竖向 | boolean | false |
| round | 圆角 | string | "10" |
| dotColor | 指示点的颜色 | string | "rgba(255,255,255,0.5)" |
| dotActiveColor | 指示点的激活色 | string | "rgba(255,255,255,1)" |
| dotOffset | 指示点距离边界的位置 | string | "15" |
| dotSize | 指示点大小。 | string | "6" |
| showDot | 是否显示指示 | boolean | true |
| autoPlay | 是否开启自动播放。 | boolean | true |
| loop | 当你拖拉时，拉到最右侧/底部时<br>是否需要返回到第一个视频继续可以拖拉。 | boolean | true |
| showLastView | 当拉到最右侧时继续左拉时，是否显示<br>右侧自定的内容。具体见demo,<br>要使用此尽可能的关闭loop，并且配合事件dragLastEnd来达到业务需求。 | boolean | false |
| showScalAni | 是否开启缩放动画，<br>即前后显示时，有一个缩放的动画过程，如果不开启就是平缓的切换。<br>如果后期支持3d样式，也可后期定义更多动画。目前如果你有需要<br>你可以在子节点中改变源码中的动画效果过程，不局限于缩放效果。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | - | 切换变化时触发 |
| click | - | 点击事件 |
| dragLastEnd | - | 触发最后一个事件。 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽内只允许放其子节点x-swiper-item | - |
| lastView | - | - |
| dotV | 竖向指示插槽,可完全自定义指示样式 | **current** : number<br>**current** : number<br>**len** : number<br>**len** : number<br> |
| dot | 横向指示插槽,可完全自定义指示样式 | **current** : number<br>**current** : number<br>**len** : number<br>**len** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/swiper

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
			<x-text font-size="18" class=" text-weight-b mb-8">轮播 Swiper</x-text>
			<x-text  color="#999999" >注意：本组件非官方的swiper轮播封装，而是作者设计并开发的轮播,后续拓展更为自由</x-text>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">横向</x-text>
			<x-text  class="mb-16" color="#999999" >拉到最后一个继续向左拉会有惊喜！！！</x-text>
			<x-swiper v-model="activeIndex" @change="change" :loop="false" :showLastView="true"  height="150" :autoPlay="true" >
				<x-swiper-item  v-for="(item,index) in list" :order="index" :key="index">
					<x-image @click="clicktest(index)" :preview="false" height="150" :src="item.image"></x-image>
				</x-swiper-item>
			</x-swiper>
			<x-text font-size="18" class=" text-weight-b my-16">纵向</x-text>
			<x-swiper v-model="activeIndex" :vertical="true" height="150" :autoPlay="true" >
				<x-swiper-item  v-for="(item,index) in list" :order="index" :key="index">
					<x-image @click="clicktest(index)" :preview="false" height="150" :src="item.image"></x-image>
				</x-swiper-item>
			</x-swiper>
			
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">单边向左边露出</x-text>
		</x-sheet>
		<x-sheet>
			<x-swiper height="150" :space="5" model="spaceOnly" :spaceOffset="20" :autoPlay="true" >
				<x-swiper-item v-for="(item,index) in 4" :order="index" :key="index">
					<x-image :preview="false"   height="150" :src="`https://store.tmui.design/api_v2/public/random_picture?random=12${index}73`"></x-image>
				</x-swiper-item>
				
			</x-swiper>
		
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">两边露出</x-text>
		</x-sheet>
		<x-sheet>
			<x-swiper  :modelValue="1" height="150" :space="10" width="325" model="space" :spaceOffset="25" :autoPlay="false" >
				<x-swiper-item v-for="(item,index) in 5" :order="index" :key="index">
					<x-image :preview="false"  width="325"  height="150" :src="`https://store.tmui.design/api_v2/public/random_picture?random=12${index}3`"></x-image>
				</x-swiper-item>
				
			</x-swiper>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">向里堆叠</x-text>
		</x-sheet>
		<x-sheet>
			<x-swiper :modelValue="1" height="150" :space="10" model="spaceIn" :spaceOffset="25" :autoPlay="false" >
				<x-swiper-item v-for="(item,index) in 5" :order="index" :key="index">
					<x-image :preview="false"   height="150" :src="`https://store.tmui.design/api_v2/public/random_picture?random=12${index}3`"></x-image>
				</x-swiper-item>
				
			</x-swiper>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">自定义插槽指示</x-text>
			<x-text  color="#999999" >如果你想了解如何自定义,请参考示例修改，插槽中已经返回了你所需参数。可以随意制作你想要样式</x-text>
		</x-sheet>
		<x-sheet>
			<x-swiper  height="150":autoPlay="true" >
				
				<x-swiper-item v-for="(item,index) in 5" :order="index" :key="index">
					<x-image :preview="false"   height="150" :src="`https://store.tmui.design/api_v2/public/random_picture?random=12${index}3`"></x-image>
				</x-swiper-item>
				
				<template #dot="{current,len}">
					<view class="flex flex-row flex-center">
						<view v-for="(item,index) in (len as number)" :key="index"
						class="dotTest mx-5 round-16 flex flex-row flex-center" 
						:style="{backgroundColor:current==index?'rgb(0, 115, 255)':'rgba(255,255,255,0.5)'}">
							<text :style="{color:current==index?'white':'rgba(255,255,255,1)',fontSize:'9px'}">{{index+1}}</text>
						</view>
					</view>
				</template>
			</x-swiper>
		</x-sheet>
		
	
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	type itemType = {
		image:string,
		title:string
	}
	export default {
		data() {
			return {
				testCount:5,
				activeIndex:0,
				list:[] as itemType[]
			};
		},
		onLoad(){
			let t=  this
			setTimeout(function() {
				t.list = [
					{image:'https://store.tmui.design/api_v2/public/random_picture?random=12',title:"1"} as itemType,
					{image:'https://store.tmui.design/api_v2/public/random_picture?random=162',title:"1"} as itemType,
					{image:'https://store.tmui.design/api_v2/public/random_picture?random=962',title:"1"} as itemType,
					{image:'https://store.tmui.design/api_v2/public/random_picture?random=962',title:"1"} as itemType,
					{image:'https://store.tmui.design/api_v2/public/random_picture?random=962',title:"1"} as itemType,
				] as itemType[]
			
			}, 1000);
		},
		methods:{
			change(page:number){
				console.log('change',page,'***')
			},
			clicktest(page:number){
				let t = this;
				console.log('click',page,'+++')
				// uni.previewImage({
				// 	current:t.list[page].image,
				// 	urls:t.list.map((el:itemType):string=>el.image)
				// })
				
			}
		}
	}
</script>

<style lang="scss">
.dotTest{
	width:16px;
	height:16px;
}
</style>
		
