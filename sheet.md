
## 容器 xSheet

***

#### 介绍

可方便快速的更改属性以塑造符合你的设计风格。背景，圆角，间隙等统一风格可全局配置。
主要是用来统一页面风格，间距等可统一设置，提高设计的一致性。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-sheet/x-sheet.uvue**

#### 使用

<x-sheet></x-sheet>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 主题名，名称或者合法的颜色值<br>默认为white,填写transparent为透明值。 | string | 'white' |
| darkColor | 如果你不填写会读取全局的暗黑背景。<br>但如果你的color颜色是彩色的则是反转color而非采用全局的黑白 | string | '' |
| followTheme | 是否跟随全局主题设置为背景色,<br>注意：开启后。本组件color将失效，始终以全局color主题为唯一值。 | boolean | false |
| hoverColor | 自定义按下去的背景色，<br>默认为空，自动配色不需要你考虑。 | string | '' |
| url | 跳转链接，提供将当作跳转使用。 | string | '' |
| linearGradient | 渐变背景<br>数组格式如下<br>                 [方向:top,bottom,left,right,自定义值例:45deg,颜色1:,颜色2]<br>例:['left','black','white']<br>如提供，暗黑及主题失效。 | string[] | () : string[] => [] |
| round | 圆角<br>数组数字时<br>[全部]<br>[顶左，顶右，底右，底左]<br>[顶左，底右]<br>[顶左，顶右，底右]<br>空数组时取全局值 | string[] | () : string[] => [] |
| border | 边线<br>数组数字时<br>数组数字时<br>[全部]<br>[左，上，右，下]<br>[左右，上下]<br>[左，上，右]<br>空数组时取全局值 | string[] | () : string[] => [] |
| shadow | 投影<br>提供格式为[y,blur,color]<br>空数组时取全局值 | string[] | () : string[] => [] as string[] |
| borderColor | 边框颜色<br>格式同border边线。<br>空数组时取全局值 | string[] | () : string[] => [] |
| darkBorderColor | 如果不填写，默认取xConfig里面的默认边线颜色值 | string[] | () : string[] => [] |
| borderStyle | 边线类型，默认solid,可以为none | string | 'solid' |
| margin | 间隙[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值 | string[] | () : string[] => [] as string[] |
| padding | 内间隙[x]全部,[x,x]左右，上下,[x,x,x]左上右,[x,x,x,x]左上右下<br>空数组时取全局值 | string[] | () : string[] => [] as string[] |
| isLink | 是否开启点按效果 | boolean | false |
| loading | 是否加载中 | boolean | false |
| height | 自定义高度，可以是数字，单位或者百分比,auto | string | "auto" |
| width | 宽，单位合法即可数字，字符串带单位，百分比,auto | string | "auto" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击事件 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/chongyong/sheet

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
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">容器 Sheet</x-text>
			<x-text color="#999999" class="line-8">属性比较多，可快速的用来布局，减轻你的布局压力，让效率提升。实验证明：一个普通的小程序20个页面。使用容器+我的组件布局。2天内完成布局，2天对接完成后端。</x-text>
			<x-text color="error" class="line-8">并且背景，圆角，间隙允许全局动态/统一配置，布局后的页面可根据后期设计要求，一键修改所有设计风格。绝对布局利器。</x-text>
		</x-sheet>
		<x-sheet :round="['12','2']" color="primary">
			<x-text color="white">更改圆角</x-text>
		</x-sheet>
		<x-sheet :round="['12','2']" :border="['2','2']" :border-color="['red','primary']">
			<x-text font-size="18" class=" text-weight-b">边线</x-text>
		</x-sheet>
		
		<x-sheet :round="['12','2']" :linearGradient="['left','#ff667f','#fdb247']">
			<x-text color="white">渐变</x-text>
		</x-sheet>

		<x-sheet :loading="true">
			<x-text font-size="18" class=" text-weight-b mb-24">还允许让内容处于加载中</x-text>
			<x-sheet :margin="['0']" :linearGradient="['left','#ff667f','#fdb247']">
				<x-text color="white" >渐变</x-text>
			</x-sheet>
			<x-sheet :margin="['0','12','0','0']" color="primary">
				<x-text color="white" class=" text-weight-b ">更改圆角</x-text>
			</x-sheet>
		</x-sheet>
		
		
		
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

		
