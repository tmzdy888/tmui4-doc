
## 表格 xTable

***

#### 介绍

格式与antd一样，我觉得那样的格式比较合理。可以单独设置样式和整体列设置样式。也可以单独设置列宽，项目列宽虽然 可以auto，但数据多的情况下不要用，还是定义具体的百分比或者数字比较快的渲染。
支持具名指定单元格插槽及行插槽，用于复杂的布局（使用插槽时，不可排序）
不管是头还是单元格它的style格式是一样的style:{key字段:{bgStyle,textStyle,align:'对齐方式:flex-start,center,flex-end'}}

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-table/x-table.uvue**

#### 使用

<x-table></x-table>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| list | 源数据 | UTSJSONObject[] | () : UTSJSONObject[] => [] as UTSJSONObject[] |
| columns | 列标题及字段定义 | xTableColumns[] | () : xTableColumns[] => [] as xTableColumns[] |
| height | 容器的高，如果不设定，不会有上下滚动<br>而直接从上往下布局。如果数据多建议设置。 | string | "auto" |
| width | 容器的宽,不可以填写auto。 | string | "100%" |
| maxHeight |  | string | "300" |
| cellHeight | 单元格的高，不能auto,%<br>请写固定的值，否则影响虚拟列表数据功能。 | string | "44" |
| cellWidth | 单元格的宽,不填写自动均分<br>它是允许任意值auto,%，固定值等<br>但我经过我测试auto，会影响原生渲染的速率（不是我影响的是自动布局的速率） | string | "" |
| fontSize | 单元格的文字大小<br>局部的设置会覆盖这里的 | string | "14" |
| fontColor | 单元格的文字颜色<br>局部的设置会覆盖这里的 | string | "#333333" |
| headerBgColor | 头的背景 | string | "#eeeeee" |
| darkHeaderBgColor | 暗黑时，如果未设置取inputDarkColor | string | "" |
| headerFontColor | 头的文字颜色,暗黑时取白 | string | "#333333" |
| ripple | 是否间隔波纹 | boolean | true |
| rippleColor | 波纹颜色, | string | "#fafafa" |
| rippleDarkColor | 波纹的暗黑颜色，不填写用的是sheetDark | string | "" |
| rowCellColor | 默认的行背景色，<br>通常你没有在数据中配置背景时，会读取这的颜色。 | string | "#ffffff" |
| rowCellDarkColor | 默认的行暗黑背景色，<br>通常你没有在数据中配置背景时，会读取这的颜色。 | string | "transparent" |
| safeTextWrap | 是否给文字高防止断行。<br>这是一个兼容性的试验参数，针对部分手机由于uni sdk原生安卓<br>上对文本的测量可能存在精度 问题，导致文本意外的断行。如果为true可以防止这种情况发生<br>可能会产生不能断行或者其它情况发生，请慎重使用。 | boolean | false |
| multiRowFloat | 是否启用多行固定功能<br>数据源中如果某行要滚动固定请添加一个字段float:true<br>默认关闭。 | boolean | false |
| selectable | 是否可选并复制文本 | boolean | false |
| refresh | 拉到底部时触发<br>如果返回Promise<any\|null> 底部刷新提示不会消失<br>类型null\|(type:string)=>Promise<any\|null><br>null值时不被执行 | RefreshFun \| null | null |
| showScrollbar | 是否显示滚动条 | boolean | false |
| hideHead | 是否隐藏头 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| cellClick | - | 单元格被点击 |
| refresh | - | 触底刷新时触发刷新事件. |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| item2.key | 行插槽插槽名称就是列的字段名称name:字段名,sucore:utsobject数据 | - |
| item2.key+'-'+item.getString('key') | - | - |
| refresh | 触底下拉刷新的插槽,你需要提供事件函数refresh才可开启 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/table

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
			<x-text font-size="18" class=" text-weight-b mb-8">表格 xTable</x-text>
			<x-text  color="#999999" >
				格式与antd一样，我觉得那样的格式比较合理。可以单独设置样式和整体列设置样式。也可以单独设置列宽，项目列宽虽然 可以auto，但数据多的情况下不要用，还是定义具体的百分比或者数字比较快的渲染。
				支持具名指定单元格插槽及行插槽，用于复杂的布局（使用插槽时，不可排序）
			</x-text>
		</x-sheet>
		<x-sheet :padding="['0']">
			<x-table  ripple-color="#f6f7ff" ripple-dark-color="#161821" max-height="900rpx" :list="list" :columns="columns3" ></x-table>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">超出左右上下滚动</x-text>
			<x-text color="#999999">
				多行滚动自动固定顶部ios,安卓会并排固定在顶部。在web端只有最后一个固定在顶部
				尽量不要使用多行固定的功能，以防未知问题，或者性能问题。如果数据不多应该问题不大。
			</x-text>
		</x-sheet>
		<x-sheet :padding="['0']">
			<x-table :refresh="refresfun" :multiRowFloat="true" cellWidth="42%" max-height="450rpx" :list="list" :columns="columns" >
				<!-- #ifdef APP || WEB -->
				<template v-slot:age="{sucore}">
					<x-text color="primary">{{(sucore as UTSJSONObject).getAny('age')}}</x-text>
				</template>
				<template v-slot:address="{sucore}">
					<x-button @click="editeActions(sucore)" size="small" >编辑</x-button>
				</template>
				<!-- #endif -->
			</x-table>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">定义样式</x-text>
		</x-sheet>
		<x-sheet :padding="['0']" >
			<x-table header-bg-color="primary" darkHeaderBgColor='primary' header-font-color="white" cellWidth="50%" max-height="450rpx" :list="list2" :columns="columns2" ></x-table>
		</x-sheet>
		<view style="height:50px"></view>
		
		<x-modal v-model:show="showEdite">
			<x-input v-model="editevalue" dark-bg-color=""></x-input>
			<x-text class="mt-12">
				确认后列表数据不会变动，我没有写业务逻辑，我这只是展示用法。
			</x-text>
		</x-modal>
		
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { xTableColumns } from "@/uni_modules/tmx-ui/interface.uts"
	export default {
		data() {
			const dataSource2 = [
				{
					key: '1',
					name: '胡彦斌1',
					age: "32",
					address: '西湖区',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '2',
					name: '胡彦祖2',
					age: "36",
					address: '湖底公园1号',
					style:{
						age:{
							bgStyle:"background:#7e6539",
							textStyle:"font-size:16px;color:#ffffff"
							
						} as UTSJSONObject
					} as UTSJSONObject,
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '3',
					name: '胡彦斌3',
					age: "40",
					address: '公园1号',
					test:"第4数据"
				} as UTSJSONObject
			] as UTSJSONObject[]
			const dataSource = [
				{
					key: '1',
					name: '胡彦斌1',
					age: "32",
					address: '西湖区湖底湖底公园',
					// 本行是否悬浮在顶部，滚动时
					float:true,
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '2',
					name: '胡彦祖2',
					age: "36",
					address: '西湖区湖底公园1号',
					float:true,
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '3',
					name: '胡彦斌3',
					age: '40',
					address: '西湖区湖底公园1号',
					test:"第4数据"
					
				} as UTSJSONObject,
				{
					key: '4',
					name: '胡彦祖4',
					age: "42",
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '5',
					name: '胡彦祖5',
					age: "37",
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '6',
					name: '胡彦斌6',
					age: "38",
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '7',
					name: '胡彦祖7',
					age: '39',
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '8',
					name: '胡彦祖8',
					age: '29',
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
				{
					key: '9',
					name: '胡彦祖9',
					age: '19',
					address: '西湖区湖底公园1号',
					test:"第4数据"
				} as UTSJSONObject,
			] as UTSJSONObject[];
			
			const columnsData = [
				{
					title: '姓名',
					key: 'name',
				} as xTableColumns,
				{
					title: '年龄',
					key: 'age'
					
				} as xTableColumns,
				{
					title: '住址',
					key: 'address',
				} as xTableColumns,
				{
					title: '第4列',
					key: 'test',
				} as xTableColumns
			] as xTableColumns[];
			const columnsData2 = [
				{
					title: '姓名',
					key: 'name',
				} as xTableColumns,
				{
					title: '年龄',
					key: 'age',
					width:"160rpx",
					style:{
						age:{
							bgStyle:"background:#69349e",
							textStyle:"font-size:16px;color:#ffffff",
						} as UTSJSONObject
					} as UTSJSONObject
				} as xTableColumns,
				{
					title: '住址',
					key: 'address',
				} as xTableColumns,
				{
					title: '第4列',
					key: 'test',
				} as xTableColumns
			] as xTableColumns[];
			const columnsData3 = [
				{
					title: '姓名',
					key: 'name',
					style:{
						name:{
							// 单元格对齐方式flex-start,center,flex-end(默认是center)
							align:"flex-start"
						} as UTSJSONObject
					} as UTSJSONObject
				} as xTableColumns,
				{
					title: '年龄',
					key: 'age',
					desc:true
				} as xTableColumns,
				{
					title: '住址',
					key: 'address',
				} as xTableColumns,
				{
					title: '第4列',
					key: 'test',
				} as xTableColumns
			] as xTableColumns[];
			return {
				showEdite:false,
				editevalue:'',
				list:dataSource,
				columns:columnsData,
				columns2:columnsData2,
				columns3:columnsData3,
				list2:dataSource2,
			};
		},
		methods:{
			editeActions(data:any|null){
				if(data==null) return;
				let value = (data! as UTSJSONObject).getAny('age')
				if(value!=null){
					let p = value! as string;
					this.editevalue = p;
					this.showEdite = true;
				}
			},
			refresfun(type:string):Promise<any|null>{
				return new Promise((res)=>{
					setTimeout(function() {
						res(true)
					}, 3500);
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
		
