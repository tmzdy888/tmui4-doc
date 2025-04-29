
## 多选框 xCheckbox

***

#### 介绍

使用时,x-checkbox能单独使用，如果要与x-checkbox-group配合，只能是它的的直接子节点

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-checkbox/x-checkbox.uvue**

#### 使用

<x-checkbox></x-checkbox>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 当前主题色，空值时取全局 | string | "" |
| unCheckColor | 当前未选中时主题色，空值时取全局 | string | "" |
| darkUnCheckColor | 当前未选中时的暗黑主题色 | string | "" |
| modelValue | 由于uniappx 截止3.98<br>不支持联合类型，后期如果官方支持<br>可扩展为string,number,boolean | string | '' |
| defaultChecked | 非受控下默认选中的状态 | boolean | false |
| value | 选中的值，<br>由于uniappx 截止3.98<br>不支持联合类型，后期如果官方支持<br>可扩展为string,number,boolean | string | '1' |
| unCheckValue | 未选中的值<br>由于uniappx 截止3.98<br>不支持联合类型，后期如果官方支持<br>可扩展为string,number,boolean | string | '' |
| disabled | 是否禁用 | boolean | false |
| icon | 选中的图标名称。 | string | "check-line" |
| label | 右侧文字。 | string | "" |
| hiddenCheckbox | 是否隐藏选中框。然后利用默认插槽自定义选中所有样式和状态。 | boolean | false |
| indeterminate | 半选中 | boolean | false |
| size | 尺寸 | string | "24" |
| iconSize | 中间小图标大小 | string | "20" |
| labelFontSize | 文字大小 | string | "15px" |
| labelSpace | label和选中框间的间距 | string | '10' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **check** : boolean**value** : number | 用户交互切换，选中变换时触发。 |
| click | - | 点击事件 |
| update:modelValue | - | 当前选中的值，等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| label | 默认文本插槽 | **checked** : boolean<br>**checked** : number<br>**value** : boolean<br>**value** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/biaodan/checkbox

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
			<x-text font-size="18" class=" text-weight-b mb-8">多选框 checkbox</x-text>
			<x-text  color="#999999">
				由于uniappx3.98不支持联合类型推断，因此选中和未选中值只能是number，待后续官方兼容类型推断
			</x-text>
		</x-sheet>
		<x-loading v-if="loading"></x-loading>
		<view v-if="!loading">
			<x-sheet class="flex flex-row">
				
				<x-checkbox @change="onlyChange" label="苹果"></x-checkbox>
				<x-checkbox color="error"  unCheckColor="error" class="ml-12" label="香蕉"></x-checkbox>
				<x-checkbox color="warn"  unCheckColor="warn" class="ml-12" label="豆腐"></x-checkbox>
				<x-checkbox :model-value="'1'" color="success"  unCheckColor="success" class="ml-12" label="李子"></x-checkbox>
			</x-sheet>
			<x-sheet>
				<x-checkbox   unCheckColor="primary" >
					<template v-slot:label><x-text>由于uniappx3.98不支持联合类型推断，因此选中和未选中值只能是number，待后续官方兼容类型推断</x-text></template>
				</x-checkbox>
				<x-checkbox color="error"   unCheckColor="error"  class="mt-12">
					<template v-slot:label><x-text>由于uniappx3.98不支持联合类型推断，因此选中和未选中值只能是number，待后续官方兼容类型推断</x-text></template>
				</x-checkbox>
				<x-checkbox-group direction='column'>
					<x-checkbox  color="error"   unCheckColor="error"  class="mt-12">
						<template v-slot:label>
							<x-text>由于uniappx3.98不支持联合类型推断，因此选中和未选中值只能是number，待后续官方兼容类型推断</x-text>
						</template>
					</x-checkbox>
				</x-checkbox-group>
			</x-sheet>
			<x-sheet>
				<x-text font-size="18" class=" text-weight-b mb-8">通过插槽完全自定样式</x-text>
				<x-text  color="#999999" class="text-size-b">
					不需要再引入其它变量，可通过插槽变量控制样式
				</x-text>
			</x-sheet>
			<x-sheet>
				<x-checkbox :hidden-checkbox="true">
					<template v-slot:label="{checked,value}">
						<x-sheet :margin="['0']" :color="checked?'primary':'info'"
							class="flex flex-row flex-row-center-start">
							<x-checkbox :model-value="value" color="warn"></x-checkbox>
							<x-text :class="[checked?'text-white':'text-black']" class="flex-1">{{checked}}点击我来切换选中</x-text>
						</x-sheet>
					</template>
				</x-checkbox>

				<x-checkbox :hidden-checkbox="true">
					<template v-slot:label="{checked,value}">
						<x-sheet :margin="['0','16','0','0']" :color="checked?'success':'info'"
							class="flex flex-row flex-row-center-start">
							<x-checkbox :model-value="value" :color="checked?'warn':'error'"></x-checkbox>
							<x-text :class="[checked?'text-white':'text-black']" class="flex-1">{{checked}}点击我来切换选中</x-text>
						</x-sheet>
					</template>
				</x-checkbox>

			</x-sheet>
			<x-sheet>
				<x-text font-size="18" class=" text-weight-b">修改选中的图标</x-text>
			</x-sheet>
			<x-sheet class="flex flex-row">
				<x-checkbox :model-value="'1'" icon="check-double-line" label="苹果"></x-checkbox>
				<x-checkbox :model-value="'1'" icon="thunderstorms-fill" color="error" class="ml-12"
					label="香蕉"></x-checkbox>
				<x-checkbox :model-value="'1'" icon="flutter-fill" color="success" class="ml-12" label="香蕉"></x-checkbox>
			</x-sheet>

			<x-sheet>
				<x-text font-size="18" class=" text-weight-b mb-8">多选框组 x-checkbox-group</x-text>
				<x-text  color="#999999" class="text-size-b">
					使用时,x-checkbox可以不是x-checkbox-group的直接子节点
				</x-text>
				<x-text  color="#999999" class="text-size-b">
					{{checkbox.toString()}},选项组时value是唯一值，不可重复。
				</x-text>

			</x-sheet>
			<x-sheet>
				<x-checkbox-group v-model="checkbox">
					<x-checkbox  v-for="(item,index) in list" :key="index" class="pr-12 mb-12" :label="item.label"
						:value="item.id"></x-checkbox>
				</x-checkbox-group>
				<x-button :block="true" @click="checkbox = ['4','5']">赋值['4','5']</x-button>
			</x-sheet>
			<x-sheet>
				<x-checkbox-group v-model="checkbox" direction="column">
					<view hover-class="opacity-5" :hover-stay-time="100" @click="groupPhus(item.id)" v-for="(item,index) in list" :key="index" class="flex flex-row flex-row-center-between">
						<x-text>{{item.label}}</x-text>
						<x-checkbox  style="pointer-events: none;" class="py-12" :value="item.id" labelSpace="0"></x-checkbox>
					</view>
				</x-checkbox-group>
			</x-sheet>
			

			<x-sheet>
				<x-text font-size="18" class=" text-weight-b ">半选中状态{{checkbox2.toString()}}</x-text>
			</x-sheet>
			<x-sheet>
				<x-checkbox class="mb-12" @change="allChange" v-model="checked" :indeterminate="indeterminate"
					label="全部"></x-checkbox>
				<x-checkbox-group @change="onChange" v-model="checkbox2">
					<x-checkbox v-for="(item,index) in list" :key="index" class="pr-12 mb-12" :label="item.label"
						:value="item.id"></x-checkbox>
				</x-checkbox-group>
			</x-sheet>
		</view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	type listtype = {
		label : string,
		id : string
	}
	export default {
		data() {
			return {
				
				loading:true,
				checkbox: ['2', '3'],
				checkbox2: [] as string[],
				indeterminate: false,
				checked: '',
				list: [
					{ label: "香蕉", id: "1" } as listtype,
					{ label: "豆腐", id: "2" } as listtype,
					{ label: "苹果", id: "3" } as listtype,
					{ label: "大豆", id: "4" } as listtype,
					{ label: "李子", id: "5" } as listtype,
				] as listtype[]
			};
		},
		onLoad() {
			setTimeout(()=>{
				this.loading = false;
			},1000)
		},
		methods: {
			onlyChange(isChecked:boolean){
				console.log(isChecked)
			},
			groupPhus(id:string){
				let obxids = this.checkbox.slice(0)
				let index = this.checkbox.findIndex((eid:string):boolean => eid == id)
				if(index>-1){
					obxids.splice(index,1)
				}else{
					obxids.push(id)
				}
				this.checkbox = obxids
			},
			onChange(value : string[]) {
				if (value.length == this.list.length) {
					this.indeterminate = false;
					this.checked = "1";
				} else if (value.length < this.list.length && value.length > 0) {
					this.indeterminate = true;
					this.checked = "";
				} else {
					this.indeterminate = false;
					this.checked = "";
				}
			},
			allChange(ischecked : boolean) {
				if (ischecked && !this.indeterminate) {
					this.indeterminate = false;
					this.checkbox2 = ["1","2","3","4","5"]
				}
				if (!ischecked && !this.indeterminate) {
					this.indeterminate = false;
					this.checkbox2 = []
				}
				if (this.indeterminate) {
					this.indeterminate = false;
					this.checkbox2 = ["1","2","3","4","5"]
					this.checked = '1'

				}

			}
		}
	}
</script>

<style lang="scss">

</style>
		
