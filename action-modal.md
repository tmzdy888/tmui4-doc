
## 底部对话框 xActionModal

***

#### 介绍

样式与darawer不一样，风格更为圆润精致，适于提醒框，阅读对话框等场景。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-action-modal/x-action-modal.uvue**

#### 使用

<x-action-modal></x-action-modal>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| customStyle | 自定义遮罩样式 | string | "" |
| title | 标题 | string | "标题" |
| showTitle | 是否显示底部关闭按钮 | boolean | true |
| showClose | 是否显示关闭 | boolean | false |
| overlayClick | 遮罩是否允许点击被关闭 | boolean | true |
| show | 显示可v-model:show双向绑定 | boolean | false |
| showConfirm | 显示取消按钮 | boolean | true |
| duration | 动画时间 | number | 350 |
| round | 打开方向为上和下时的圆角<br>空值时，取全局配置的圆角。注意是取drawer的圆角，统一弹层的圆角 | string | "" |
| maxHeight | 弹层最大的高度值，默认为屏幕的可视高<br>提供值时不能为百分比，可以是px,rpx单位数字。如果你不带单位，默认转换为rpx单位。 | string | "" |
| bgColor | 弹层的背景 | string | "white" |
| darkBgColor | 弹层的暗黑背景，如果为空取sheetDarkColor | string | "" |
| btnColor | 空值取全局主题值。 | string | "" |
| btnText | 确认按钮的文本 | string | "确认" |
| btnFontColor | 空值最自动计算文本色。 | string | "" |
| watiDuration | 打开dom的延迟量，如果你打开 弹窗在ios正常。<br>请不要修改此值。如果遇到打不开，或者 打开 后没动画，关闭不了等可能是sdk bug导致 <br>此时需要加大值来避免。具体加多少以你弹窗内的节点复杂度有关，需要你自行压力测试。<br>此值仅在ios下生效。 | number | 120 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| confirm | - | 底部按钮被点击时触发 |
| click | - | 点击遮罩事件 |
| close | - | 关闭时执行 |
| open | - | 打开执行的事件 |
| beforeOpen | - | 打开前执行 |
| beforeClose | - | 关闭前执行 |
| update:show | - | 等同v-model:show |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| trigger | 标签触发显示遮罩，免于使用变量控制 | **show** : Boolean<br> |
| title | 标题插槽 | **show** : Boolean<br> |
| default | 默认插槽 | - |
| footer | 页脚按钮插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/action-modal

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
			<x-text font-size="18" class=" text-weight-b mb-8">底部对话框 ActionModal</x-text>
			<x-text color="#999999" >
				样式与darawer不一样，风格更为圆润精致，适于提醒框，阅读对话框等场景。
			</x-text>
		</x-sheet>
		<x-sheet>
			<x-action-modal :show="showModal" title="技巧提醒" btn-text="我知道了哇">
				<template #trigger>
					<x-button :block="true">显示技巧提醒</x-button>
				</template>
			
				<x-sheet class="flex flex-col flex-col-center-center">
					<x-icon font-size="96" color="primary" name="pantone-fill"></x-icon>
					<x-text font-size="18" class="text-weight-b">你学会了吗？</x-text>
					<x-text class="text-align-center text-grey">风格与drawer样式不同的是两边和底部有间隙？风格是否喜欢呢？</x-text>
				</x-sheet>
			</x-action-modal>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				showModal: false
			};
		},
		onReady() {
			this.showModal = true;
		}
	}
</script>

<style lang="scss">

</style>
		
