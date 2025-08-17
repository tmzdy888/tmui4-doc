
## 折叠面板 xCollapse

***

#### 介绍

可单，可多开,内部只可放置x-collapse-item直接子节点组件，为了避免重复计算和性能x-collapse-item不能通过响应式修改内容。如果确实需要请通过刷新key解决

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-collapse/x-collapse.uvue**

#### 使用

<x-collapse></x-collapse>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前打开的组。可v-model | string[] | () : string[] => [] as string[] |
| multiple | 是否允许打开多个。 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : string[] | 变换时触发 |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽，仅可放置x-collapse-item子节点 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/collapse

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
			<x-text font-size="18" class=" text-weight-b mb-8">折叠面板 Collapse</x-text>
			<x-text color="#999999" >允许单开，和多开。</x-text>
		</x-sheet>
		<x-sheet :padding="['0']">
			<x-collapse>
				<x-collapse-item left-icon="settings-line" name="1" title="系统设置">
					<x-text class="line-10">
						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。
					</x-text>
					<view class="flex-1">
						<x-image width="100%"
							src="https://store.tmui.design/api_v2/public/random_picture?random=993"></x-image>
					</view>
				</x-collapse-item>
				<x-collapse-item :showBottomLine="false" left-icon="question-line" name="2" title="交易帮助信息提示交易帮助信息提示交易交易帮助信息提示帮助信息提示交易帮助信息提示">
					<x-text class="line-10">
						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。
					</x-text>
				</x-collapse-item>
			</x-collapse>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">只能展开一个</x-text>
		</x-sheet>
		
		<x-sheet :padding="['0']">
			<x-collapse :multiple="false" >
				<x-collapse-item @click="onClick" left-icon="ancient-gate-fill" name="3" title="如何提高低成本的效率">
					<x-text class="line-10">
						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。
					</x-text>
				</x-collapse-item>
				<x-collapse-item left-icon="mail-unread-fill" name="1" title="如何使用本UI组件库,会很难吗？">
					<x-text class="line-10">
						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。

					</x-text>
					<view class="flex-1">
						<x-image width="100%"
							src="https://store.tmui.design/api_v2/public/random_picture?random=993"></x-image>
					</view>
				</x-collapse-item>
				<x-collapse-item :disabled="true" left-icon="calendar-schedule-fill" name="6" title="如何使用本UI组件库,会很难吗？">
					<x-text class="line-10">
						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。
					</x-text>
				
				</x-collapse-item>
				<x-collapse-item :showBottomLine="false" left-icon="discuss-fill" name="2" title="如何提高低成本的效率">
					<x-text class="line-10">

						在贴牌代工这一业务方面，据阿宽食品官网显示，其公司旗下拥有全资及绝对控股的五大生产基地，分别是：成都龙泉驿工厂、北京顺义工厂、杭州富阳工厂、四川宜宾工厂、四川德阳工厂。
						根据光大证券研究所数据，2018年-2021年，阿宽销售额复合增长率在行业前十厂商中排名第1，2021年的方便面销售额已位居内资品牌前3。
					</x-text>
				</x-collapse-item>
			</x-collapse>
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
		},
		onLoad() {
			
		},
		methods:{
			onClick(id:string,opened:boolean){
				console.log(id,opened)
			}
		}
	}
</script>

<style lang="scss">

</style>
		
