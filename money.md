
## 金额栅格 xMoney

***

#### 介绍

对金额进行栅格化

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-money/x-money.uvue**

#### 使用

<x-money></x-money>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| digit | 小数点后几位 | number | 2 |
| thousand | 开启千分位 | boolean | false |
| thousandUnit | 千分位的分隔符 | string | "," |
| thousandLen | 千分位的长度，<br>默认是3位一位，如果为4就是万分位依此类推 | number | 3 |
| symbolText | 货币符号 | string | '￥' |
| symbolPosition | 货币符号位置<br>left:左侧<br>right:右侧 | string | 'left' |
| color | 文字颜色 | string | 'primary' |
| darkColor | 暗黑时的文字颜色 | string | '' |
| fontSize | 文字大小 | string | '16' |
| preFontSize | 货币符号及小数字号大小 | string | '16' |
| showCn | 是否显示中文金额 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | **inter** : string<br>**inter** : string<br>**inter** : string<br>**inter** : string<br>**digit** : string<br>**digit** : string<br>**digit** : string<br>**digit** : string<br>**cn** : string<br>**cn** : string<br>**cn** : string<br>**cn** : string<br>**lineHeight** : string<br>**lineHeight** : string<br>**lineHeight** : string<br>**lineHeight** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/money

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
			<x-text font-size="18" class=" text-weight-b mb-8">金额栅格 xMoney</x-text>
			<x-text color="#999999" >考虑到这个比较常用，输入金额为数字即可，可以放心的使用保证精度，不采用toFiexd，保证金额精度无舍入。</x-text>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-between">
			<x-text>默认2位小数</x-text>
			<x-money :modelValue="1568"></x-money>
		</x-sheet>

		<x-sheet class="flex flex-row flex-row-center-between">
			<x-text>开启千分位,小数位为3</x-text>
			<x-money :thousand="true" :digit="3" fontSize="30" :modelValue="15568.398"></x-money>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-between">
			<x-text>千分位为4分割</x-text>
			<x-money :thousand="true" :thousandLen="4" :digit="3" :modelValue="15568.398"></x-money>
		</x-sheet>
		<x-sheet class="flex flex-row flex-row-center-between">
			<x-text>字号控制</x-text>
			<x-money :thousand="true" fontSize="24" :digit="3" :modelValue="15568.398"></x-money>
		</x-sheet>
		<x-sheet >
			<x-text>大写金额（仅到厘,不要超过后4位）</x-text>
			<x-money color="warn" darkColor="warn" :showCn="false" fontSize="16" :digit="4" :modelValue="money"></x-money>
			<x-money class="mb-20" :showCn="true" fontSize="16" :digit="4" :modelValue="money"></x-money>
			
			<x-button :block="true" @click="money = money==1568.3984?1548.36:1568.3984">试试修改金额</x-button>
		</x-sheet>
		<x-sheet >
			<x-text>去除小数，把小数置0即可，要注意我不会舍入，是直接丢掉小数</x-text>
			<x-money :showCn="false" fontSize="16" :digit="0" :modelValue="1568.398"></x-money>
			<x-text>可以直接写style修改样式</x-text>
			<x-money style="text-align: right;font-weight: bold;" :showCn="false" fontSize="24" preFontSize="14" :digit="1" :modelValue="1568.398"></x-money>
		</x-sheet>
		
		<x-sheet >
			<x-text>自定义货币符号</x-text>
			<x-money symbolText="$" fontSize="20" :modelValue="1568" preFontSize="12"></x-money>
			<x-money symbolText=" / 美元" fontSize="20" preFontSize="12"  symbolPosition='right' :modelValue="1568"></x-money>
			<x-money symbolText=" 元/个" fontSize="20" preFontSize="12"  symbolPosition='right' :modelValue="1568"></x-money>
			<x-money symbolText="人民币: " fontSize="20" preFontSize="12"  symbolPosition='left' :modelValue="1568"></x-money>
		</x-sheet>
	
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script setup>
		import {ref} from "vue"
		const money = ref(1568.3984)
</script>

<style>
		
</style>

		
