
## 表单 xForm

***

#### 介绍

从1.1.2开始允许xform可以嵌套view进行form-item布局了,但建议不要嵌套太深,影响性能.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-form/x-form.uvue**

#### 使用

<x-form></x-form>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| labelWidth | 标签宽（横向表单时有效）<br>不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改 | string | "100" |
| labelDirection | 不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改<br>vertical,horizontal | labelDirType | "horizontal" |
| labelFontColor | 标签的文本颜色,不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改 | string | "#333333" |
| errorAutoPage | 出错时，是否滚动到表单的位置<br>不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改 | boolean | true |
| modelValue | 等同v-model | any | () : UTSJSONObject => {<br>    return {} as UTSJSONObject<br>} |
| labelFontSize | 标签文本大小<br>不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改 | string | "16" |
| showLabel | 是否显示标题,不支持动态修改（uniappx 3.99不支持动态传递 inject）,可在子组件上动态修改 | boolean | true |
| errorAlign | 错误标签的对齐方式,left,center,right | string | 'left' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| submit | **result** : FORM_SUBMIT_RESULT | 按钮提交表单时触发。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 插槽内只能放置x-form-item子节点组件 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| valid | **keys** : string[] | 校验结果 | 手动执行触发校验函数，如果提供空数组，表示校验所有，如果提供了指定值，则表示只校验提供的字段。 |


#### 示例页面路径

/pages/biaodan/form

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
			<x-text font-size="18" class=" text-weight-b mb-8">表单 xForm</x-text>
			<x-text color="#999999">与官方不同的是，它只为数据进行验证，因此不仅仅局限表单组件。而是任意数据进行的验证收集，比官方更灵活，与web组件对齐的校验。</x-text>
			<x-text color="#999999">为了体验提供了属性：默认如果有字段校验不过，会把页面滚动到当前出错 的位置。</x-text>
		</x-sheet>

		<x-sheet>
			<x-form ref="form" @submit="(submitData as resultTtype)" v-model="(reqData as USER_TYPE)">
				<x-form-item :rule="validname" field="username" label="联系姓名" :required="true">
					<x-input cursor-color="red" color='transparent' v-model="(reqData.username as string)"
						align="right"></x-input>
				</x-form-item>
				<x-form-item v-if="reqData.testFiled!=null" field="testFiled" label="测试可空字段" :required="true">
					<x-input cursor-color="red" color='transparent' v-model="(reqData.testFiled as string|null)"
						align="right"></x-input>
				</x-form-item>
				<x-form-item :rule="vaildTitles" field="title" label="产品标题" :required="true">
					<x-input color='transparent' v-model="(reqData.title as string)" align="right"></x-input>
				</x-form-item>
				<x-form-item :rule="vaildPrices" field="price" label="产品价格" :required="true">
					<x-input color='transparent' type="number" v-model="(reqData.price as string)" right-text="万元"
						align="right"></x-input>
				</x-form-item>
				<x-form-item :show-bottom-boder="false" :rule="vaildNums" field="num" label="库存数量" :required="true">
					<view class="flex flex-row flex-row-center-end">
						<x-stepper width="120" v-model="(reqData.num as number)"></x-stepper>
					</view>
				</x-form-item>
				<x-form-item label="上传图片" field="upload" :required="true" :rule="vaildUpload">
					<x-upload-media v-model="(reqData.upload as XUPLOADFILE_FILE_VALUE[])" :column="3" style="width: 210px;" img-height="70px"></x-upload-media>
				</x-form-item>
		
				<x-form-item field="radio" label="选择性别" :required="true">
					<x-radio-group v-model="(reqData.radio as string)" class="flex flex-row flex-row-center-end">
						<x-radio class="mr-20" value="男" label="男"></x-radio>
						<x-radio value="女" label="女"></x-radio>
					</x-radio-group>
				</x-form-item>
				<x-form-item field="checkbox" label="选择水果" :required="true">
					<x-checkbox-group v-model="(reqData.checkbox as string[])"
						class="flex flex-row flex-row-center-end">
						<x-checkbox v-for="(item,index) in ['苹果','香蕉','梨子','地龙']" :key="index" class="ml-20"
							:value="item" :label="item"></x-checkbox>
					</x-checkbox-group>
				</x-form-item>


				<x-button form-type="form" class="mt-32" :block="true">保存资料</x-button>
				<x-text font-size="12" color="error"
					class="text-align-center pt-24">表单收集与组件不是绑定结构只与form-item绑定，因此不会像官方那样局限，可以作为一个数据验证器来理解。</x-text>
			</x-form>
		</x-sheet>
		<x-sheet >
			<x-text font-size="18" class=" text-weight-b mb-8">ref方法对上述表单验证</x-text>
			<view class="flex flex-row ">
				<x-button class="flex-1 mr-n6" @click="submitByClick">ref验证</x-button>
				<x-button class="flex-1" @click="submitref">只验证用户名</x-button>
			</view>
		</x-sheet>
		
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">风格可以自己随意变化</x-text>
		</x-sheet>
		<x-sheet>
			<x-form @submit="(submit as resultTtype)" v-model="(logindata as LOGIN_TYPE)" :label-direction="('vertical' as labelDirType)">
				<x-form-item :cell-padding="['0','0']" :showBottomBorder="false" :rule="validname" field="user"
					label="用户帐号" :required="true">
					<x-input darkBgColor="" left-icon="account-pin-circle-fill" placeholder="请输入你的帐号"
						v-model="(logindata.user as string)"></x-input>
				</x-form-item>
				<x-form-item :cell-padding="['0','0']" :showBottomBorder="false" :rule="vaildPasss" field="pass"
					label="登录密码" :required="true">
					<x-input darkBgColor="" :password="true" left-icon="lock-password-fill" placeholder="请输入8位密码"
						v-model="(logindata.pass as string)"></x-input>
				</x-form-item>
				<x-button form-type="form" class="mt-32" icon="lock-unlock-fill" :block="true">登入</x-button>
			</x-form>
		</x-sheet>

		<view style="height: 550px;"></view>

	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script lang="ts" setup>
	import { ref } from "vue"
	import { FORM_RULE } from "@/uni_modules/tmx-ui/interface.uts"
	import { FORM_SUBMIT_RESULT,XUPLOADFILE_FILE_VALUE } from "@/uni_modules/tmx-ui/interface.uts"
	// @ts-ignore
	const form = ref<XFormComponentPublicInstance|null>(null)
	type resultTtype = (evt:FORM_SUBMIT_RESULT)=>void ;
	type labelDirType = 'vertical' | 'horizontal'
	type USER_TYPE = {
		username : string;
		password : string;
		title : string;
		price : string;
		num : number;
		testFiled ?: string,
		radio : string,
		checkbox : string[],
		upload: XUPLOADFILE_FILE_VALUE[]
	};
	type LOGIN_TYPE = {
		user : string,
		pass : string
	}

	let vaildUsername = [
		{
			type: "string",
			errorMessage: "姓名填写不正确，不能空，且要小于4个字符",
			trigger:'blur',
			valid: (val : any | null) : boolean => {
				let pval = val as string;
				return pval.length > 0 && pval.length <= 4
			}
		} as FORM_RULE
	] as FORM_RULE[]

	let vaildTitle = [
		{
			type: "string",
			errorMessage: "产品标题不空，且大于5个字符小于12个字符",
			valid: (val : any | null) : boolean => {
				let pval = val as string;
				return pval.length > 5 && pval.length <= 12
			}
		} as FORM_RULE
	] as FORM_RULE[]

	let vaildPrice = [
		{
			type: "number",
			errorMessage: "价格不能小于30元",
			min:30
		} as FORM_RULE
	] as FORM_RULE[]
	let vaildNum = [
		{
			type: "number",
			errorMessage: "商品库存在2-200之间",
			min:2,
			max:100
		} as FORM_RULE
	] as FORM_RULE[]

	let vaildPass = [
		{
			type: "number",
			errorMessage: "请输入8位密码",
			valid: (val : any | null) : boolean => {
				let pval = val as string;
				return pval.length == 8
			}
		} as FORM_RULE
	] as FORM_RULE[]

	const validname = ref<FORM_RULE[]>(vaildUsername)
	const vaildTitles = ref<FORM_RULE[]>(vaildTitle)
	const vaildPrices = ref<FORM_RULE[]>(vaildPrice)
	const vaildNums = ref<FORM_RULE[]>(vaildNum)
	const vaildPasss = ref<FORM_RULE[]>(vaildPass)
	const vaildUpload = ref<FORM_RULE[]>([
		{
			type: "array",
			errorMessage: "请最少选择1张图片最多3张",
			min:1,
			max:3
		} as FORM_RULE
	] as FORM_RULE[])
	
	const reqData = ref<USER_TYPE>({
		username: "",
		password: "",
		title: "",
		price: "",
		num: 0,
		radio: "",
		checkbox: [] as string[],
		upload:[] as XUPLOADFILE_FILE_VALUE[]
	})
	const logindata = ref<LOGIN_TYPE>({
		user: "",
		pass: ""
	})

	
	const submitData = (evt : FORM_SUBMIT_RESULT) => {
		console.log(evt)
		if (!evt.valid) {
			uni.showToast({ title: evt.errorMessage, icon: 'none' })
			return;
		}
		
	}
	const submit  = (evt : FORM_SUBMIT_RESULT) => {
		if (!evt.valid) {
			uni.showToast({ title: evt.errorMessage, icon: 'none' })
			return;
		}
		console.log(evt)
	}
	// 只验证username
	const submitref = () => {
		form.value!.valid(['username'] as string[])
	}
	//验证全部
	const submitByClick = () => {
		let result = form.value!.valid([] as string[]) as FORM_SUBMIT_RESULT
		// console.log(result)
	}
</script>

<style lang="scss">

</style>
		
