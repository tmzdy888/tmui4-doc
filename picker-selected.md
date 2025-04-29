
## 搜索选择 xpickerSelected

***

#### 介绍

弹层式大数据列表筛选，搜索。可异步加载数据。可针对本地搜索及异步搜索加载数据，虚拟列表支持。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-picker-selected/x-picker-selected.uvue**

#### 使用

<x-picker-selected></x-picker-selected>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前选中的数据，any数组string[],number[]<br>否则报错，无法运行。 | any[] | () : any[] => [] as any[] |
| modelShow | 当前打开的状态。<br>等同v-model:model-show | boolean | false |
| modelStr | 回显当前选中的文本，只输出<br>等同v-model:model-str | string[] | () : string[] => [] as string[] |
| title | 顶部标题 | string | "请选择" |
| cancelText | 取消按钮的文本 | string | "取消" |
| confirmText | 确认按钮的文本 | string | "确认" |
| filterKey | 搜索的字段名称 | string | "text" |
| labelKey | 显示文本的字段 | string | "text" |
| idKey | 列表字段的唯一标识<br>注意它的数据是number或者string类型. | string | "id" |
| list | 数据列表。 | UTSJSONObject[] | () : UTSJSONObject[] => [] as UTSJSONObject[] |
| localSearch | 默认采用本地对list的结果集进行筛选搜索。<br>如果禁用用，你可以自行通过search事件来搜索<br>并赋值给list更新结果。 | boolean | true |
| multiple | 是否允许多选 | boolean | true |
| lazyContent | 是否懒加载内部内容。<br>当前你的列表内容非常多，且影响打开的动画性能时，请务必<br>设置此项为true，以获得流畅视觉效果。 | boolean | false |
| lazyDuration | lazyContent的延迟时间 单位 ms<br>如果你的 app效果不行，请加大此值 | number | 100 |
| itemHeight | 项目的高度.不要去动态改变高,内部是listview item虚拟列表动态改高<br>会出现问题的. | string | "50" |
| zIndex | 层级 | number | 1100 |
| showClose |  | boolean | false |
| refresh | 下拉刷新时v-model:refresh,触发时会设置为true，结束时需要自行设置为false<br>来结束状态 | boolean | false |
| bottomRefresh | 触底刷新时，v-model:bottomR-refresh,触发时会设置为true，结束时需要自行设置为false<br>来结束状态 | boolean | false |
| disabledPull | 是否禁用下拉刷新 | boolean | true |
| disabledBottom | 是否禁用触底刷新 | boolean | true |
| disabled | 是否禁用弹出 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| bottomRefresh | - | 触底刷新时触发，需要自行设置属性bottomRefresh为false结束状态 |
| refresh | - | 下拉刷新时触发，需要自行设置属性refresh为false结束状态 |
| search | - | 搜索时触发 |
| confirm | - | 确认选择时触发 |
| cancel | - | 取消搜索时触发 |
| open | - | 显示弹层时触发，<br>可以用来在此第一次加载list异步数据。 |
| update:modelShow | - | 变量控制打开状态<br>等同v-model:model-show |
| update:modelStr | - | 自动回显文本数组，此属性只对外输出。 |
| update:bottomRefresh | - | v-model:bottomR-refresh |
| update:refresh | - | v-model:refresh |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽,默认触发打开选择器。你的默认布局可以放置在这里。 | - |
| item | 动态循环列表的项目插槽 | **item** : xPickerSelectedListyType<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/picker-selected

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
			<x-text font-size="18" class=" text-weight-b mb-8">搜索选择 xPickerSelected</x-text>
			<x-text color="#999999" class="mb-20">通过弹出式的列表，异步加载数据来显示并选择数据</x-text>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">本地搜索</x-text>
			<x-text color="#999999" class="">此处使用了lazyContent属性展开内容超多，视觉效果也流畅</x-text>
			<x-sheet color="info" dark-color="#333" :margin="['0','16']">
				<x-text color="#999999">已选ids：{{model1.join(",")}}</x-text>
				<x-text color="#999999">回显文本：{{modelStr1.join(",")}}</x-text>
			</x-sheet>
			<x-picker-selected  label-key="name" :lazyContent="true" v-model:model-str="modelStr1" v-model="model1" :list="list">
				<x-button :block="true">打开本地数据集搜索</x-button>
				<!-- 演示如何使用动态插槽,自行改变项目排版样式结构. -->
				<template v-slot:item="{item}">
					<x-text>{{item.getAny('name')}}</x-text>
				</template>
			</x-picker-selected>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">下拉刷新触底加载</x-text>
			<x-picker-selected  
			v-model:refresh="refresTop" 
			v-model:bottom-refresh="refresBottom" 
			@refresh="refreshLoad"  
			@bottom-refresh="refresBottomhLoad"  
			:disabled-bottom="false"
			:disabled-pull="false"
			label-key="name" :lazyContent="true" v-model:model-str="modelStr1" v-model="model1" :list="list">
				<x-button :block="true">打开本地数据集搜索</x-button>
			</x-picker-selected>
		</x-sheet>

		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">异步搜索</x-text>
			<x-sheet color="info" dark-color="#333" :margin="['0','16']">
				<x-text color="#999999">已选ids：{{model2.join(",")}}</x-text>
				<x-text color="#999999">回显文本：{{modelStr2.join(",")}}</x-text>
			</x-sheet>
			<x-picker-selected :local-search="false" @search="onSearch" v-model:model-str="modelStr2" v-model="model2"
				:list="list2">
				<x-button :block="true">打开异步数据搜索</x-button>
			</x-picker-selected>
		</x-sheet>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	export default {
		data() {
			return {
				model1: [2, 8] as number[],
				modelStr1: [] as string[],
				model2: [] as number[],
				modelStr2: [] as string[],
				list: [
					{ id: 1, lid: '1001', name: '广州信瑞化妆品公司' } as UTSJSONObject,
					{ id: "2", lid: '1002', name: '深圳市创明展览设计有限公司' } as UTSJSONObject,
					{ id: 3, lid: '1003', name: '上海盟威实业发展有限公司' } as UTSJSONObject,
					{ id: 4, lid: '1004', name: '国都期货有限公司' } as UTSJSONObject,
					{ id: 5, lid: '1005', name: '山西宇达集团' } as UTSJSONObject,
					{ id: 6, lid: '1006', name: '博达网络有限公司' } as UTSJSONObject,
					{ id: 7, lid: '1007', name: '新贸易有限公司' } as UTSJSONObject,
					{ id: 8, lid: '1008', name: '东莞市东辉仪器有限公司' } as UTSJSONObject,
					{ id: 9, lid: '1009', name: '东省东莞市石碣镇东辉电子仪器有限公司' } as UTSJSONObject,
					{ id: 10, lid: '10010', name: '古兰电子科技有限责任公司' } as UTSJSONObject,
					{ id: 11, lid: '10011', name: '邦达礼品公司' } as UTSJSONObject,
					{ id: 12, lid: '10012', name: '广州市广花制冷配件公司' } as UTSJSONObject,
					{ id: 13, lid: '10013', name: '中国云南彩蝶谷服饰加盟连锁店' } as UTSJSONObject,
					{ id: 14, lid: '10014', name: '明珠盘艺有限公司' } as UTSJSONObject,
					{ id: 15, lid: '10015', name: '景滔塑胶五金有限公司' } as UTSJSONObject,
					{ id: 16, lid: '10016', name: '福建古拉特商贸公司' } as UTSJSONObject,
					{ id: 17, lid: '10017', name: '吐鲁番市英俊农产品有限责任公司' } as UTSJSONObject,
					{ id: 18, lid: '10018', name: '新疆亿艾斯国际贸易公司' } as UTSJSONObject,
					{ id: 19, lid: '10019', name: '淮安市万家家具用品有限公司' } as UTSJSONObject,
					{ id: 20, lid: '10020', name: '深圳市优派克电子有限公司销售部' } as UTSJSONObject,
					{ id: 21, lid: '10021', name: '深圳市精博艺印刷有限公司采购部' } as UTSJSONObject,
					{ id: 22, lid: '10022', name: '北京福茂源纸制品有限公司' } as UTSJSONObject,
					{ id: 23, lid: '10023', name: '淮安苏粤食品有限公司' } as UTSJSONObject,
					{ id: 24, lid: '10024', name: '巨龙燕泉饮品有限公司' } as UTSJSONObject,
					{ id: 25, lid: '10025', name: '浙江嘉力宝精机股份有限公司' } as UTSJSONObject,
					{ id: 26, lid: '10026', name: '嘉兴市南湖区欣鑫塑料厂' } as UTSJSONObject,
					{ id: 27, lid: '10027', name: '太原晓旭物流服务部' } as UTSJSONObject,
					{ id: 28, lid: '10028', name: '南昌三众实业有限公司' } as UTSJSONObject,
					{ id: 29, lid: '10029', name: '无锡托普电子有限公司' } as UTSJSONObject,
					{ id: 30, lid: '10030', name: '江阴市泰惠钢铁有限公司' } as UTSJSONObject,
					{ id: 31, lid: '10031', name: '东莞泓锐国际货运有限公司' } as UTSJSONObject,
					{ id: 32, lid: '10032', name: '苏必努商留有限公司业务部' } as UTSJSONObject,
					{ id: 33, lid: '10033', name: '东莞菲迩康自动化设备有限公司' } as UTSJSONObject,
					{ id: 34, lid: '10034', name: '恒盛贸易公司' } as UTSJSONObject,
					{ id: 35, lid: '10035', name: '杭州华声汉腾文化发展有限公司' } as UTSJSONObject,
					{ id: 36, lid: '10036', name: '固力锁业经营部' } as UTSJSONObject,
					{ id: 37, lid: '10037', name: '江苏德生纺织印染公司营销部' } as UTSJSONObject,
					{ id: 38, lid: '10038', name: '江都天都液压件有限公司' } as UTSJSONObject,
					{ id: 39, lid: '10039', name: '潮安县金石镇彩联五金制品厂' } as UTSJSONObject,
					{ id: 40, lid: '10040', name: '工西九江华卓工贸有限公司' } as UTSJSONObject,
					{ id: 41, lid: '10041', name: '深圳市分分印刷有限公司' } as UTSJSONObject,
					{ id: 42, lid: '10042', name: '上海乐金化学有限公司' } as UTSJSONObject
				] as UTSJSONObject[],
				list2: [] as UTSJSONObject[],
				refresTop:false,
				refresBottom:false,
			}
		},
		methods: {
			refreshLoad(){
				let t = this;
				setTimeout(function () {
					t.refresTop = false;
					uni.showToast({ 'title': "刷新成功", 'icon': "none" })
				}, 1500);
			},
			refresBottomhLoad(){
				let t = this;
				setTimeout(function () {
					t.refresBottom = false;
					uni.showToast({ 'title': "触底成功", 'icon': "none" })
				}, 1500);
			},
			onSearch(keyword : string) {
				uni.showLoading({ 'title': "..." })
				let t = this;
				setTimeout(function () {
					t.list2 =
						[
							{ "id": 1, "text": "北京" } as UTSJSONObject,
							{ "id": 2, "text": "上海" } as UTSJSONObject,
							{ "id": 3, "text": "广州" } as UTSJSONObject,
							{ "id": 4, "text": "深圳" } as UTSJSONObject,
							{ "id": 5, "text": "杭州" } as UTSJSONObject,
							{ "id": 6, "text": "成都" } as UTSJSONObject,
							{ "id": 7, "text": "重庆" } as UTSJSONObject,
							{ "id": 8, "text": "武汉" } as UTSJSONObject,
							{ "id": 9, "text": "南京" } as UTSJSONObject,
							{ "id": 10, "text": "西安" } as UTSJSONObject,
							{ "id": 11, "text": "长沙" } as UTSJSONObject,
							{ "id": 12, "text": "青岛" } as UTSJSONObject,
							{ "id": 13, "text": "大连" } as UTSJSONObject,
							{ "id": 14, "text": "厦门" } as UTSJSONObject,
							{ "id": 15, "text": "苏州" } as UTSJSONObject,
							{ "id": 16, "text": "天津" } as UTSJSONObject,
							{ "id": 17, "text": "沈阳" } as UTSJSONObject,
							{ "id": 18, "text": "哈尔滨" } as UTSJSONObject,
							{ "id": 19, "text": "福州" } as UTSJSONObject,
							{ "id": 20, "text": "济南" } as UTSJSONObject
						] as UTSJSONObject[]

					uni.hideLoading()
				}, 1500);
			}
		}
	}
</script>

<style>

</style>
		
