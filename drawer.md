
## 抽屉 xDrawer

***

#### 介绍

提供四个方向的弹出。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-drawer/x-drawer.uvue**

#### 使用

<x-drawer></x-drawer>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| customStyle | 自定义遮罩样式 | string | "" |
| title | 标题 | string | "标题" |
| showFooter | 显示底部操作栏 | boolean | false |
| showTitle | 是否显示标题 | boolean | true |
| showClose | 是否显示底部关闭按钮 | boolean | false |
| overlayClick | 遮罩是否允许点击被关闭 | boolean | true |
| show | 显示可v-model:show双向绑定 | boolean | false |
| showCancel | 显示取消按钮 | boolean | true |
| cancelText | 取消按钮的文本 | string | "取消" |
| confirmText | 确认按钮的文本 | string | "确认" |
| duration | 动画时间 | number | 300 |
| watiDuration | 打开dom的延迟量，如果你打开 弹窗在ios正常。<br>请不要修改此值。如果遇到打不开，或者 打开 后没动画，关闭不了等可能是sdk bug导致 <br>此时需要加大值来避免。具体加多少以你弹窗内的节点复杂度有关，需要你自行压力测试。<br>此值仅在ios下生效。 | number | 120 |
| position | 打开方向。 | string | "bottom" |
| round | 打开方向为上和下时的圆角<br>空值时，取全局配置的圆角。 | string | "" |
| size | 左右时为内容宽，<br>上下时为内容高<br>百分比，数字字符或者带单位,或者为auto(根据内容自动高度或者宽高) | string | "50%" |
| maxHeight | 弹层最大的高度值，默认为屏幕的可视高<br>提供值时不能为百分比，可以是px,rpx单位数字。如果你不带单位，默认转换为rpx单位。 | string | "" |
| bgColor | 背景颜色 | string | 'white' |
| darkBgColor | 暗黑背景颜色，如果不提供默认读取全局的sheet配置 | string | '' |
| overflayBgColor | 遮罩的背景色 | string | 'rgba(0, 0, 0, 0.4)' |
| disabledScroll | 是否禁用内部的scroll标签<br>禁用后内容不会滚动，如果设定了指定高，内容超出指定高，会被裁切<br>但如果没有指定高，内容自动的话，高是自动的。 | boolean | false |
| contentMargin | 内容区域左右和下的边距。 | string | '16' |
| widthCoverCenter | 宽屏时是否让内容剧中显示<br>并限制其它宽为屏幕宽，只展示中间内容以适应宽屏。<br>注意只有top,bottom才会生效。 | boolean | false |
| swiperLenClose | 滑动左右或者上下关闭弹出层<br>注意如果设置为0就表示关闭该功能。<br>默认drawer嵌套了scroll-view，再你滚动到顶或者底时，如果继续滑动的距离大于此值关闭层。<br>但如果你是禁用了内部scroll-view，而是采用自己的scorll-view，此时该功能会与你的滚动手势冲突，请自行考虑。<br>建议要打开时设置为80-100比较合理 | number | 0 |
| offsetTop | 距离顶部的偏移量,如果你布局顶会遮罩弹层可以考虑使用此值 | string | '0' |
| offsetBottom | 距离底部的偏移量,如果你布局底会遮罩弹层可以考虑使用此值 | string | '0' |
| zIndex | 弹层的层级 | number | 1100 |
| lazy | 懒加载<br>为了解决业务布局节点超多时,你可能需要内容延迟加载以免阻塞动画流畅度.<br>如果你启用了lazy,每次打开时,动画执行后才会显示内容.这样动画就流畅,不会因为节点过多造成的卡.<br>开启了此属性后ios端前面的watiDuration属性可以不用再设置了. | boolean | false |
| disabledConfirm | 是否禁用确认按钮 | boolean | false |
| btnColor | 底部按钮操作的主题色，空取全局 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击遮罩事件 |
| close | - | 关闭时执行 |
| open | - | 打开执行的事件 |
| beforeOpen | - | 打开前执行 |
| beforeClose | - | 关闭前执行 |
| update:show | - | 等同v-model:show |
| cancel | - | 取消时触发 |
| confirm | - | 确认时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| trigger | 标签触发显示遮罩，免于使用变量控制 | **show** : Boolean<br> |
| title | 标题插槽 | **show** : Boolean<br> |
| default | 默认插槽 | - |
| footer | 底部操作栏 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/drawer

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
			<x-text font-size="18" class=" text-weight-b mb-8">抽屉 Drawer</x-text>
			<x-text color="#999999" >
				提供四个方向的弹出，如果要居中显示，请使用overlay组件。可以设置高为auto,百分比,最大值
				可以是插槽触发或者变量控制触发
			</x-text>
		</x-sheet>
		
		<x-sheet class="flex flex-row flex-row-center-between">
			<x-drawer @open="openDrawer" style="width:24%" size="80%" position="left" :show-footer="true">
				<template #trigger><x-button :block="true" >左弹出</x-button></template>
				<x-checkbox label="标签"></x-checkbox>
				<x-switch-slider height="88" >
					<x-cell min-height="88" :showBottomBorder="false" :card="false" icon="discuss-line"
					title="可以左滑菜单演示" desc="可以双向绑定,手动管理状态"></x-cell>
					<template #menu>
						<view class="flex flex-row flex-row-center-center" style="width:110px;background:black;height: 100%;">
							<text class="text-white">分享</text>
						</view>
						<view class="flex flex-row flex-row-center-center"  style="width:110px;background:red;height: 100%;">
							<text class="text-white">删除</text>
						</view>
					</template>
				</x-switch-slider>
				<x-picker :list="list">
					<x-button :block="true">打开选项</x-button>
				</x-picker>
			</x-drawer>
			<x-drawer style="width:24%" position="right">
				<template #trigger><x-button :block="true" >右弹出</x-button></template>
			</x-drawer>
			<x-drawer  style="width:24%" :show-title="false" :show-close="true"  position="top">
				<x-text>此弹层有内容开启了事件协商和手势关闭,向上滑一定的距离能关闭弹层。</x-text>
				<template #trigger><x-button :block="true" >顶弹出</x-button></template>
			</x-drawer>
			<x-drawer style="width:24%" :show-close="true" position="bottom">
				<template #trigger>
					<x-button :block="true" >底弹出</x-button>
					</template>
			</x-drawer>
		</x-sheet>
	
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b">嵌套</x-text>
		</x-sheet>
		
		<x-sheet >
			<x-button @click="show2 = true" :block="true">显示底部操作栏+嵌套</x-button>
		</x-sheet>
		
		<x-drawer :lazy="true" v-model:show="show2"  position="bottom" :show-footer="true" size="64%">
			<x-form :show-label="false">
				<x-form-item :show-bottom-border="false">
					<x-input placeholder="请输入帐号" dark-bg-color=""></x-input>
				</x-form-item>
				<x-form-item :show-bottom-border="false">
					<x-input placeholder="请输入密码" dark-bg-color=""></x-input>
				</x-form-item>
				<x-button form-type="form" icon="lock-unlock-fill" :block="true">登入</x-button>
			</x-form>
			<x-drawer :show-close="true" position="bottom">
				<template #trigger><x-button class="mt-32"  :block="true" >嵌套2</x-button></template>
				
				<x-drawer :show-close="true" position="bottom" size="34%">
					<template #trigger><x-button :block="true" >嵌套3</x-button></template>
				</x-drawer>
			</x-drawer>
			<text class="text-size-m text-grey mt-10 line-8">塞拉利昂共和国总统 比奥：中国在不长的时间内取得了巨大的发展成就，发展不仅需要领导人提出规划，还需要人民的共同努力。习近平主席非常专注，习主席知道应为中国人民带来什么，他不受外界噪音的干扰，明确了发展愿景，赢得了中国人民的拥护，取得了卓越成效。</text>

		</x-drawer>
		
		<x-sheet >
			<x-button @click="show = true" :block="true">定义底部插槽</x-button>
		</x-sheet>
		
		<x-drawer v-model:show="show"  position="bottom" :show-footer="true">
			<text class="text-size-m text-grey mt-10 line-8">此弹层有内容开启了事件协商和手势关闭。可以向上滚动内容，或者向下拉会关闭弹层</text>
			<text class="text-size-m text-grey mt-10 line-8">国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发塞拉利昂共和国总统 比奥：中国在不长的时间内取得了巨大的发展成就，发展不仅需要领导人提出规划，还需要人民的共同努力。习近平主席非常专注，习主席知道应为中国人民带来什么，他不受外界噪音的干扰，明确了发展愿景，赢得了中国人民的拥护，取得了卓越成效。</text>
			<text class="text-size-m text-grey mt-10 line-8">国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发塞拉利昂共和国总统 比奥：中国在不长的时间内取得了巨大的发展成就，发展不仅需要领导人提出规划，还需要人民的共同努力。习近平主席非常专注，习主席知道应为中国人民带来什么，他不受外界噪音的干扰，明确了发展愿景，赢得了中国人民的拥护，取得了卓越成效。</text>
			<text class="text-size-m text-grey mt-10 line-8">国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发塞拉利昂共和国总统 比奥：中国在不长的时间内取得了巨大的发展成就，发展不仅需要领导人提出规划，还需要人民的共同努力。习近平主席非常专注，习主席知道应为中国人民带来什么，他不受外界噪音的干扰，明确了发展愿景，赢得了中国人民的拥护，取得了卓越成效。</text>
			<text class="text-size-m text-grey mt-10 line-8">国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发国在不长的时间内取得了巨大的发展成就，发塞拉利昂共和国总统 比奥：中国在不长的时间内取得了巨大的发展成就，发展不仅需要领导人提出规划，还需要人民的共同努力。习近平主席非常专注，习主席知道应为中国人民带来什么，他不受外界噪音的干扰，明确了发展愿景，赢得了中国人民的拥护，取得了卓越成效。</text>
			<template #footer>
				<x-button @click="show=false" :block="true">定义底部插槽</x-button>
			</template>
		</x-drawer>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { PICKER_ITEM_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	const items = [
		{
			title: '江西',
			id: "9-1",
			children: [
				{
					title: '南昌',
					id: "132",
					children: [
						{ title: '青山湖区', id: "1-2" } as PICKER_ITEM_INFO,
						{ title: '高新区', id: "1-3", disabled: true } as PICKER_ITEM_INFO,
						{ title: '红谷滩区', id: "1-4" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
				{

					title: '九江', id: "222",
					children: [
						{ title: '2青山湖区', id: "1-32" } as PICKER_ITEM_INFO,
						{ title: '2高新区', id: "1-33" } as PICKER_ITEM_INFO,
						{ title: '3红谷滩区', id: "1-34" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],
				} as PICKER_ITEM_INFO,
			] as PICKER_ITEM_INFO[],
		} as PICKER_ITEM_INFO,
		{
			title: '安徽',
			id: "10-13",
			children: [
				{
					title: '5南昌',
					id: "3",
					children: [
						{ title: '5青山湖区', id: "1-52" } as PICKER_ITEM_INFO,
						{ title: '5高新区', id: "1-53" } as PICKER_ITEM_INFO,
						{ title: '5红谷滩区', id: "1-54" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
				{
					title: '5南昌',
					id: "36",
					children: [
						{ title: '6青山湖区', id: "61-52" } as PICKER_ITEM_INFO,
						{ title: '6高新区', id: "61-53" } as PICKER_ITEM_INFO,
						{ title: '6红谷滩区', id: "61-54" } as PICKER_ITEM_INFO,
					] as PICKER_ITEM_INFO[],

				} as PICKER_ITEM_INFO,
			] as PICKER_ITEM_INFO[],
		} as PICKER_ITEM_INFO,

	] as PICKER_ITEM_INFO[];
	export default {
		data() {
			return {
				list: items,
				show:false,
				show2:false,
			};
		},
		onLoad() {
			let _this = this;
			
		},
		methods:{
			openDrawer(){
				console.log(12)
			}
		}
	}
</script>

<style lang="scss">

</style>

		
