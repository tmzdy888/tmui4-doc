
## 倒计时 xCountdown

***

#### 介绍

倒计时，可以精确到秒，毫秒,记住

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-countdown/x-countdown.uvue**

#### 使用

<x-countdown></x-countdown>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| time |  | number | 0 |
| actions | 指令，通过变动此值来达到暂停，开始，结束的功能。<br>以代替ref方法的使用，会更多方便。<br>请使用v-model:actions="xx"来控制方法 | string | "" |
| format | 显示格式<br>DD天，HH时，MM分，SS秒，MS毫秒 | string | "DD天HH时MM分SS秒" |
| autoStart |  | boolean | false |
| unit | 以秒还是毫秒为单位到计时。<br>ss\|ms | string | "ss" |
| fontSize | 文本大小 | string | "16" |
| color | 文本颜色 | string | "#333333" |
| captcha | 是否使用验证码模式<br>启用后,整个应用不管你用了多少个此组件,倒计时都是共用的<br>直到结束某一个结束,其它的才可以启用,这样可以保证,任何时候切换页面验证发送<br>都能保证在60秒内的间隔,防止刷验证码. | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **time** : number | 时间变化时触发 |
| pause | - | 暂停时触发 |
| start | - | 开始时触发 |
| complete | - | 结束时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽 | **status** : string<br>**status** : number<br>**status** : number<br>**status** : number<br>**status** : number<br>**status** : number<br>**status** : number<br>**status** : number<br>**time** : string<br>**time** : number<br>**time** : number<br>**time** : number<br>**time** : number<br>**time** : number<br>**time** : number<br>**time** : number<br>**label** : string<br>**label** : number<br>**label** : number<br>**label** : number<br>**label** : number<br>**label** : number<br>**label** : number<br>**label** : number<br>**ms** : string<br>**ms** : number<br>**ms** : number<br>**ms** : number<br>**ms** : number<br>**ms** : number<br>**ms** : number<br>**ms** : number<br>**ss** : string<br>**ss** : number<br>**ss** : number<br>**ss** : number<br>**ss** : number<br>**ss** : number<br>**ss** : number<br>**ss** : number<br>**mm** : string<br>**mm** : number<br>**mm** : number<br>**mm** : number<br>**mm** : number<br>**mm** : number<br>**mm** : number<br>**mm** : number<br>**hh** : string<br>**hh** : number<br>**hh** : number<br>**hh** : number<br>**hh** : number<br>**hh** : number<br>**hh** : number<br>**hh** : number<br>**dd** : string<br>**dd** : number<br>**dd** : number<br>**dd** : number<br>**dd** : number<br>**dd** : number<br>**dd** : number<br>**dd** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| start | - | - | 开始 |
| pause | - | - | 暂停 |
| reset | - | - | 重置 |
| getStatus | - | - | 获取当前运行状态 |


#### 示例页面路径

/pages/zhanshi/countdown

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
			<x-text font-size="18" class=" text-weight-b mb-8">倒计时 xCountdown</x-text>
			<x-text  color="#999999" >倒计时，可以精确到秒，毫秒，尽量通过插槽来布局样式。</x-text>
		</x-sheet>
		<x-sheet >
			<view class="flex flex-row flex-row-center-center" >
				<x-countdown font-size="20" color="primary" :time="1000*59" v-model:actions="actions"></x-countdown>
			</view>
			<view class="flex flex-row flex-row-center-center mt-32">
				<x-button width="26%" @click="actions = 'play'">开始</x-button>
				<x-button width="26%" @click="actions = 'pause'" class="mx-20">暂停</x-button>
				<x-button width="26%" @click="actions = 'reset'">重置</x-button>
			</view>
		</x-sheet>
		
		<x-sheet >
			<view class="flex flex-row flex-row-center-center" >
				<x-countdown  font-size="20" color="error" unit="ms" format="SS:MS" :time="1000*5" v-model:actions="actions2"></x-countdown>
			</view>
			<view class="flex flex-row flex-row-center-center mt-32">
				<x-button width="26%" @click="actions2 = 'play'">开始</x-button>
				<x-button width="26%" @click="actions2 = 'pause'" class="mx-20">暂停</x-button>
				<x-button width="26%" @click="actions2 = 'reset'">重置</x-button>
			</view>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				actions:"",
				actions2:"",
			};
		}
	}
</script>

<style lang="scss">

</style>
		
