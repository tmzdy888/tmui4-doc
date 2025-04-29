
## 步骤条 xSteps

***

#### 介绍

标签内仅可放置其直接子节点：x-steps-item

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-steps/x-steps.uvue**

#### 使用

<x-steps></x-steps>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue |  | number | 0 |
| icon | 默认图标，请在子级上动态修改 | string | "checkbox-blank-circle-fill" |
| activeIcon | 激活时的图标，请在子级上动态修改 | string | "checkbox-circle-fill" |
| iconSize | 图标大小,不可动态修改，请在子级上动态修改 | string | "14" |
| labelSize | 标题大小，请在子级上动态修改 | string | "14" |
| descSize | 下面的小文字介绍大小 | string | "11" |
| color | 未选中时的标题颜色，请在子级上动态修改 | string | "#333333" |
| activeColor | 激活时的颜色，默认空值取全局主题色。，请在子级上动态修改 | string | "" |
| vertical | 是否是竖向 | boolean | false |
| reverse | 是否反转,不是内容反转,是状态反向. | boolean | false |
| disabled | 是否禁用交互，即不可点击项目来切换进度。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **index** : number | 变换时触发 |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，仅可放置其直接子节点：x-steps-item | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/steps

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
			<x-text font-size="18" class=" text-weight-b mb-8">步骤条 Steps</x-text>
			<x-text color="#999999" >可统一通过父级定制样式，也可单独通过子组件StepsItem来设置，灵活度高。统一设置时，样式不可变，原因在于Uniapp
				x目前暂不能传递可变值</x-text>
		</x-sheet>

		<x-sheet :padding="['0','12']">
			<x-steps :model-value="2">
				<x-steps-item desc="昨天付的" label="已付钱"></x-steps-item>
				<x-steps-item desc="还不错" label="快递准备"></x-steps-item>
				<x-steps-item desc="出题表" label="已送货"></x-steps-item>
				<x-steps-item desc="2023年3月24" label="已签收"></x-steps-item>
				<x-steps-item desc="2023年1月10" label="已签收"></x-steps-item>
			</x-steps>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">可交互，点击项目触发切换</x-text>
		</x-sheet>
		<x-sheet :padding="['0','12']">
			<x-steps v-model="setp" icon="checkbox-blank-circle-line" active-color="error"
				active-icon="radio-button-fill" :disabled="false">
				<x-steps-item desc="一般般" label="已付钱"></x-steps-item>
				<x-steps-item desc="还不错" label="快递准备"></x-steps-item>
				<x-steps-item desc="出题表" label="已送货"></x-steps-item>
				<x-steps-item desc="2023年3月24" label="已签收"></x-steps-item>
			</x-steps>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">竖向</x-text>
		</x-sheet>
		<x-sheet :padding="['0','12']">
			<x-steps :model-value="1" :vertical="true">
				<x-steps-item desc="错哦 新专辑要开始制作了" label="我是Jay"></x-steps-item>
				<x-steps-item label="2023新专辑"></x-steps-item>
				<x-steps-item label="呃!" desc="tmui4.0就是好用"></x-steps-item>
				<x-steps-item label="2023新专辑要开始制作了哇"></x-steps-item>
			</x-steps>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">插槽定义</x-text>
		</x-sheet>
		<x-sheet :padding="['0','12']">
			<x-steps>
				<x-steps-item desc="哎呦~不错哦" label="我是Jay"></x-steps-item>
				<x-steps-item>
					<template v-slot:default="active">
						<x-sheet color="primary" :margin="['0']" :padding="['10']">
							<text class="text-size-m text-white">自定插槽</text>
						</x-sheet>
					</template>
				</x-steps-item>
				<x-steps-item label="2023新专辑要开始制作了哇"></x-steps-item>
			</x-steps>
		</x-sheet>

	<view style="height:80px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				setp:2
			};
		}
	}
</script>

<style lang="scss">

</style>
		
