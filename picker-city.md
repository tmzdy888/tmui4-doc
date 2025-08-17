
## 城市选择器 xPickerCity

***

#### 介绍

是x-picker-view封装的弹出式，城市数据已经封装好。如果想更换更多级或者1级啥的可见数据站点：https://github.com/uiwjs/province-city-china

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker-city/x-picker-city.uvue**

#### 使用

<x-picker-city></x-picker-city>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 数据项同x-picker-view的X_PICKER_X_ITEM | X_PICKER_X_ITEM[] | () : X_PICKER_X_ITEM[] => [] as X_PICKER_X_ITEM[] |
| modelValue | 当前选中项的id值 | string[] | () : string[] => [] as string[] |
| modelStr | 当前选中项的回显文本等同v-model:model-str<br>请不要更改此值，此值只对外输出显示。 | string | "" |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| title | 顶部标题,默认：请选择 | string | "" |
| cancelText | 取消按钮的文本,默认：取消 | string | "" |
| confirmText | 确认按钮的文本,默认：确认 | string | "" |
| modelStrJoin | 自动同步modelstr拼接时的符号. | string | "," |
| zIndex | 层级 | number | 1100 |
| showClose |  | boolean | false |
| lazyContent | 是否懒加载内部内容。<br>当前你的列表内容非常多，且影响打开的动画性能时，请务必<br>设置此项为true，以获得流畅视觉效果。如果选择数据较少没有必要打开<br>注意:由于要兼容微信,此属性从1.1.9开始必须打开,除非不用微信小程序可以关闭. | boolean | true |
| disabled | 是否禁用弹出 | boolean | false |
| widthCoverCenter | 宽屏时是否让内容剧中显示<br>并限制其宽为屏幕宽，只展示中间内容以适应宽屏。 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| confirm | - | 确认触发 |
| change | **ids** : string[] | 滑动变换时触发 |
| update:modelShow | - | 变量控制打开状态<br>等同v-model:model-show |
| update:modelStr | - | 等同v-model:model-str<br>只对外输出当前回选区的选中项的文本，不要外部改变此值。 |
| update:modelValue | - | 点击确认时同步。等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽,默认触发打开选择器。你的默认布局可以放置在这里。 | **label** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/picker-city

#### 示例源码

<template>
	<!-- #ifdef APP -->
	<scroll-view style="flex:1">
	<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<page-meta :page-style="`background-color:${xThemeConfigBgColor}`">
			<navigation-bar :background-color="xThemeConfigNavBgColor"
				:front-color="xThemeConfigNavFontColor"></navigation-bar>
		</page-meta>
		<!-- #endif -->
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">城市选择器 xPickerCity</x-text>
			<x-text color="#999999"
				class="mb-20">是x-picker-view封装的弹出式，城市数据已经封装好。如果想更换更多级或者1级啥的可见数据站点：https://github.com/uiwjs/province-city-china</x-text>

			<x-picker-city :list="list" v-model:model-str="modelStr" v-model="modelValueIds">
				<x-button :block="true">选择城市</x-button>
			</x-picker-city>

			<x-sheet color="info" dark-color="#333" :margin="['0','16']">
				<x-text>
					选中项：{{modelValueIds.join('-')}}
				</x-text>
				<x-text>
					回显文本：{{modelStr}}
				</x-text>
			</x-sheet>
			<x-button :block="true" @click="fuzhi">赋值</x-button>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import cityscode from "./level.min.uts"
	import { X_PICKER_X_ITEM } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			return {
				modelValueIds: [] as string[],
				modelStr: "",
				list: JSON.parseArray<X_PICKER_X_ITEM>(cityscode)
			};
		},
		methods: {
			fuzhi() {
				this.modelValueIds = ['350000', '350600', '350626']
				// this.modelStr = '北京市-市辖区-东城区'
			}
		},
	}
</script>

<style lang="scss">

</style>
		
