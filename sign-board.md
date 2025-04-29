
## 签名板 xSignBoard

***

#### 介绍

手写签名板，适合需要签字的场景

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-sign-board/x-sign-board.uvue**

#### 使用

<x-sign-board></x-sign-board>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽度，可任意单位 | string | '100%' |
| height | 高度，可任意单位 | string | '150' |
| backgroundColor | 背景颜色 | string | 'transparent' |
| strokeColor | 画笔颜色 | string | 'primary' |
| strokeWidth | 画笔粗细 | number | 8 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| getLineCount | - | - | 获取当前的笔画数量<br>这是个大概值，并非完全准确，但至少可以验证<br>出用户写了多少笔，是否真的签名了。 |
| clear | - | - | 清空画布 |
| getImage | - | {src:图片路径,width:图片宽,height:图片高,error:错误信息} | 获取图片数据 |


#### 示例页面路径

/pages/qita/sign-board

#### 示例源码

<template>
	<!-- #ifdef MP-WEIXIN -->
	<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
		<navigation-bar :background-color="xThemeConfigNavBgColor" :front-color="xThemeConfigNavFontColor"></navigation-bar>
	</page-meta>
	<!-- #endif -->
	<view >
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">签名板 SignBoard</x-text>
			<x-text color="#999999" >
				提供高性能流畅性的原生绘制
			</x-text>
		</x-sheet>
		<x-sheet dark-color="#333">
			<x-sign-board height="200" ref="boardRef" :stroke-color="color" ></x-sign-board>
		</x-sheet>
		
		
		<x-sheet class="flex flex-row">
			<x-button width="31%"  @click="saveImg">保存图片</x-button>
			<x-button width="31%"  class="mx-10"  @click="checkCount">是否签名</x-button>
			<x-button width="31%" color="error" @click="clear">清除</x-button>
		</x-sheet>
		
		<x-sheet dark-color="#333">
			<x-text font-size="18" class=" text-weight-b mb-8">演示在弹层内</x-text>
			<x-modal @open="opended" @close="show=false" height="350">
				<template v-slot:trigger>
					<x-button :block="true" >打开</x-button>
				</template>
				<x-text v-if="!show">加载中</x-text>
				<x-sign-board v-if="show" height="200" ref="boardRef" :stroke-width="3" :stroke-color="color" ></x-sign-board>
			</x-modal>
		</x-sheet>

		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">点击上方保存图片预览</x-text>
			<image :style="{width:width+'px',height:height+'px'}" :src="img"></image>
		</x-sheet>
	</view>
</template>

<script lang="uts" setup >
	const img = ref("")
	const width = ref(0)
	const height = ref(0)
	const color = ref("primary")
	const boardRef = ref<XSignBoardComponentPublicInstance|null>(null)
	const clear = ()=>{
		boardRef.value!.clear()
	}
	const saveImg = ()=>{
		boardRef.value!.getImage().then((res:UTSJSONObject)=>{
			img.value = res.getString('src') as string;
			width.value  = res.getNumber('width') as number;
			height.value  = res.getNumber('height') as number;
		})
	}
	const checkCount = ()=>{
		let count = boardRef.value!.getLineCount();
		if(count<5){
			uni.showToast({
				title:"连笔过多或者未签名",
				icon:"error"
			})
			return;
		}
		uni.showToast({
			title:"已签名",
			icon:"success"
		})
	}

	const show = ref(false)
	const opended = ()=>{
		setTimeout(function() {
			show.value = true;
		}, 300);
	}
	
</script>

<style lang="scss">

</style>

		
