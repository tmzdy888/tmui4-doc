
## 动态全屏 xViewTofull

***

#### 介绍

动态全屏，点击某一区域时，让该内容自动全屏展开，关闭时，回落到原位置，场景比如：视频播放，详情等不想开新页面的时候非常有用。
如果想完全全屏，可以自定义导航栏和自定义关闭按钮实现。web端使用时注意：不能套在父组件设置了css transform属性里面，否则错乱。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-view-tofull/x-view-tofull.uvue**

#### 使用

<x-view-tofull></x-view-tofull>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| bgColor | 全屏弹出来时的背景色。 | string | '#ffffff' |
| darkBgColor | 全屏弹出来时的暗黑背景色。<br>默认为空，取全局的暗黑背景 | string | '' |
| duration | 展开时的动画时长，单位ms | number | 300 |
| showClose | 是否显示关闭按钮<br>你可以关闭，通过ref来关闭。<br>如果要全屏可以自定义导航栏。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| close | 关闭按钮插槽 | **opened** : boolean<br> |
| default | 默认内容插槽 | **opened** : boolean<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| open | - | - | 手动打开弹层 |
| close | - | - | 手动ref调用关闭弹层。 |


#### 示例页面路径

/pages/fankui/view-tofull

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
			<x-text font-size="18" class="text-weight-b mb-8">动态全屏 xViewTofull</x-text>
			<x-text >点击某一区域时，让该内容自动全屏展开，关闭时，回落到原位置，场景比如：视频播放，详情等不想开新页面的时候非常有用。</x-text>
		</x-sheet>
		
		<view class="mx-16 flex flex-row flex-wrap">
			<x-view-tofull style="height:120px;overflow: hidden;background-color: #0579FF;width: 50%;" bg-color="#0579FF" dark-bg-color="#333">
				<template v-slot:default="{opened}">
					<view style="min-height:120px; padding: 16px; height: 100%;">
						<x-text color="white" font-size="20" dark-color="white" :lines="1">如果美国继续针对中国，中国将</x-text>
						<view v-if="(opened as boolean)" >
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
							<x-image :preview="false" src="https://store.tmui.design/api_v2/public/random_picture?random=183"></x-image>
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
						</view>
					</view>
				</template>
			</x-view-tofull>
			
			<view style="width: 50%;">
				<x-view-tofull style="height:120px;overflow: hidden;">
					<template v-slot:default="{opened}">
						<view style="min-height:120px; background-color: #f8b563;padding: 16px; height: 100%;">
							<x-text color="white" font-size="20" dark-color="white">话题标题演示</x-text>
							<x-text class="mb-16" color="white" dark-color="white">点击该区域展示效果哦点击该区域展示效果哦</x-text>
							
							<x-sheet v-if="(opened as boolean)" :padding="['0']" :margin="['0']">
								<x-cell style="border-radius: 6px 6px 0px 0px;"  :card="false" url="/pages/index/button" icon="apps-line" desc="UTS版本tmui组件库,高质量库"
									title="常见组件库"></x-cell>
								<x-cell :card="false" url="/pages/index/icon" icon="price-tag-3-line" label="+￥32" label-color="red"
									icon-color="red"></x-cell>
								<x-cell :card="false" icon="chat-smile-2-line" url="/pages/index/tag" label="tmx测试"
									icon-color="orange"></x-cell>
								<x-cell  style="border-radius:0px 0px  6px 6px ;" :card="false" :show-bottom-border="false" icon="chat-smile-2-line" url="/pages/index/tag"
									label="tmx测试" icon-color="orange"></x-cell>
							</x-sheet>
						</view>
					</template>
				</x-view-tofull>
			</view>
			<view style="background-color: #00aa7f;width: 50%;">
				<x-view-tofull style="height:120px;overflow: hidden;" bg-color="success" dark-bg-color="#333">
					<template v-slot:default="{opened}">
						<view style="min-height:120px; padding: 16px; height: 100%;">
							<x-text color="white" font-size="20" dark-color="white" :lines="1">社评：嫦娥六号彰显了“国际范儿”</x-text>
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
							<x-image :preview="false" src="https://store.tmui.design/api_v2/public/random_picture?random=183"></x-image>
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
						</view>
					</template>
				</x-view-tofull>
			</view>
			<view style="background-color: #7b33e6;width: 50%;">
				<x-view-tofull style="height:120px;overflow: hidden;" bg-color="success" dark-bg-color="#333">
					<template v-slot:default="{opened}">
						<view style="min-height:120px; padding: 16px; height: 100%;">
							<x-text color="white" font-size="20" dark-color="white" :lines="1">张海鹏、冯琳：试图动摇2758号决议，是美国的梦呓</x-text>
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
							<x-image :preview="false" src="https://store.tmui.design/api_v2/public/random_picture?random=183"></x-image>
							<x-text color="white" dark-color="white">2020年10月，习近平总书记来到潮州市考察，沿牌坊街了解潮州市修复保护历史文化街区等情况。总书记指出，潮州有很多宝，潮绣、木雕、潮剧、工夫茶、潮州菜等，都很有特色，弥足珍贵，实属难得。我们爱这个城市，就要呵护好她、建设好她。</x-text>
						</view>
					</template>
				</x-view-tofull>
			</view>
		</view>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">

</style>

		
