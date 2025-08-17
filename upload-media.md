
## 图片上传 xUploadMedia

***

#### 介绍

可以上传视频或者图片,注意不要混搭.要么上传视频,要么上传图片.当用户自行添加默认文件时可以给你的文件对象加status:0表示待上传,要确保你的上传文件路径是正确的
否则安卓会引发io错误,并且uni.upload是无法捕捉到fail事件中,会导致整个程序不可用

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-upload-media/x-upload-media.uvue**

#### 使用

<x-upload-media></x-upload-media>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| mode | 上传的类型,video,photo,默认是上传图片 | string | 'photo' |
| videoOps | 当mode=video时,选择视频上传的参数,<br>些参数为utsjson,所有字段为可选,具体字段为uni.chooseVideo(options)中的部分有效字段<br>pageOrientation,albumMode,compressed,compressed,maxDuration,camera | UTSJSONObject | ():UTSJSONObject =>{<br>    return {<br>        pageOrientation:'auto',<br>        albumMode:'system',<br>        sourceType:['album', 'camera'] as string[],<br>        compressed:true,<br>        maxDuration:60,<br>        camera:'back'<br>    } as UTSJSONObject<br>} |
| maxCount | 最大的可上传数量 | number | 9 |
| url | 上传地址 | string | "https://mockapi.eolink.com/LRViGGZ8e6c1e8b4a636cd82bca1eb15d2635ed8c74e774/admin/upload_pic/" |
| name | 上传到服务器的名称字段 | string | "file" |
| header | 上传到服务器的头文件 | UTSJSONObject | () : UTSJSONObject => {<br>    return {} as UTSJSONObject<br>} |
| formData | 额外的表单数据。 | UTSJSONObject \| null | () : UTSJSONObject => {<br>    return {} as UTSJSONObject<br>} |
| imgHeight | 图片高,此处不可使用%单位 | string | "80" |
| column | 一行显示几列 | number | 5 |
| okFileIsDelete | 上传成功的文件是否允许删除 | boolean | true |
| uploadingFileIsDelete | 上传中的文件是否允许删除 | boolean | true |
| modelValue | 等同v-model | XUPLOADFILE_FILE_VALUE[] | () : XUPLOADFILE_FILE_VALUE[] => [] as XUPLOADFILE_FILE_VALUE[] |
| beforeDel | 图片被删除时触发<br>如果返回Promise<false>删除失败否则成功<br>类型null\|(index:number,item:XUPLOADFILE_FILE_INFO)=>Promise<boolean> | funcalldel \| null | null |
| beforeComplete | 你需要原路返回参数提供的item<br>item可以自行修改响应内容，响应类型这样可以自己根据服务的内容判断<br>是成功还是失败或者没有权限。示例见demo使用。 | funbeforeCompelte\|null | null |
| beforeUpload | 上传前的最后一步执行,异步回调,函数返回一个item:XUPLOADFILE_FILE_INFO<br>返回时要原样类型返回Promise<XUPLOADFILE_FILE_INFO>,你可以在这里修改文件参数跳过上传或者<br>进行最后的头参数设置.demo有参考. | beforeUploadType\|null | null |
| autoStart | 是否自动上传 | boolean | true |
| sourceType | 图片来源同官方的sourceType：<br>'album','camera' | string[] | () : string[] => ['album', 'camera'] as string[] |
| compress | 是否压缩 | boolean | true |
| compressedHeight | 压缩后的缩放高，0表示不压缩高 | number | 0 |
| compressedWidth | 压缩后的缩放高，0表示不压缩宽 | number | 0 |
| quality | 压缩质量 | number | 80 |
| addPos | 添加图片的位置<br>'before'出现在前面<br>'after'出现在后面 | string | "after" |
| align | 子项对齐方式，left左对齐默认，right:右对齐 | string | "left" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| complete | **** : XUPLOADFILE_FILE_VALUE[] | 每次全部上传完时触发 |
| change | **** : XUPLOADFILE_FILE_VALUE[] | 变化时触发 |
| delete | **** : XUPLOADFILE_FILE_VALUE[] | 图片被删除时触发 |
| update:modelValue | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 上传图片按钮插槽。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| upload | - | - | 手动上传图片 |


#### 示例页面路径

/pages/biaodan/upload-media

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
			<x-text font-size="18" class=" text-weight-b mb-8">图片上传 xUploadMedia</x-text>
			<x-text color="#999999" class="text-size-b">
				允许长按图片进行拖动排序，上传中会禁止排序。
			</x-text>
		</x-sheet>

		<x-sheet>
			<x-upload-media :beforeUpload="beforeUpload" :header="headerestotken" :before-del="beforeRemove" v-model="list"
				:column="4"></x-upload-media>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">上传视频</x-text>
			<x-upload-media mode="video" ref="uploader" :auto-start="false" :column="4"></x-upload-media>
			<x-button class="mt-20" :block="true" @click="upload">ref触发上传</x-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">通过before-complete干预上传结果</x-text>
			<x-upload-media :before-complete="beforeComputed" :header="headerestotken" v-model="list3"
				:column="4"></x-upload-media>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b mb-8">演示循环数组绑定并改变顺序</x-text>
			<!-- 要注意,如果我循环变动key一定要唯一不能相同或者为Index数字vue3会有diff导致不刷新数据. -->
			<view v-for="(item,index) in (testlist as FORMLIST[])" :key="item.name">
				<view class="flex flex-row flex-row-center-between" style="height: 50px;">
					<x-text>{{(item as FORMLIST).name}}</x-text>
					<view class="flex flex-row">
						<x-button class="mr-12" size="mini" @click="moveto(index,'qian')">前移</x-button>
						<x-button size="mini" @click="moveto(index,'hou')">后移</x-button>
					</view>
				</view>
				<x-upload-media :column="4" :key="item.name" v-model="(item.value as XUPLOADFILE_FILE_VALUE[])"
					:auto-start="true"></x-upload-media>
			</view>
		</x-sheet>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	import { XUPLOADFILE_FILE_VALUE, XUPLOADFILE_FILE_INFO } from "@/uni_modules/tmx-ui/interface.uts"
	type FORMLIST = {
		name : string,
		value : XUPLOADFILE_FILE_VALUE[]
	}
	const formlist = [
		{
			name: "数据A",
			value: [
				{ url: "https://store.tmui.design/api_v2/public/random_picture?random=231266" },
			] as XUPLOADFILE_FILE_VALUE[]
		} as FORMLIST,
		{
			name: "靓仔B",
			value: [
				{ url: "https://store.tmui.design/api_v2/public/random_picture?random=212643246" },
			] as XUPLOADFILE_FILE_VALUE[]
		} as FORMLIST,
		{
			name: "小猫猫C",
			value: [
				{ url: "https://store.tmui.design/api_v2/public/random_picture?random=4234" },
			] as XUPLOADFILE_FILE_VALUE[]
		} as FORMLIST
	] as FORMLIST[]

	export default {
		data() {
			return {
				headerestotken: { accessToken: "99999" } as UTSJSONObject,
				testlist: formlist as FORMLIST[],
				list: [
					{ url: 'https://tmui.design/images/logoGreat.png' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=212' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=2' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
				] as XUPLOADFILE_FILE_VALUE[],
				list2: [
					{ url: 'https://tmui.design/images/logoGreat.png' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=212' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=2' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
					{ url: 'https://store.tmui.design/api_v2/public/random_picture?random=6' },
				] as XUPLOADFILE_FILE_VALUE[],
				list3: [] as XUPLOADFILE_FILE_VALUE[],
				
			};
		},
		onLoad() {
		},
		methods: {
			moveto(index : number, type : string) {
				let p = this.testlist.slice(0)
				let nowitem = this.testlist.slice(0)[index]
				let prevIndex = Math.max(index - 1, 0);
				let nextIndex = Math.min(index + 1, p.length - 1)
				if (index == 0 && type == 'qian') return
				if (index == p.length - 1 && type == 'hou') return

				let prevItem = p[prevIndex]
				let nextItem = p[nextIndex]

				if (type == 'qian') {
					p[prevIndex] = nowitem
					p[index] = prevItem
				} else {


					p[nextIndex] = nowitem
					p[index] = nextItem
				}
				this.testlist = p.slice(0)
			},
			qinkogn() {
				this.list = [] as XUPLOADFILE_FILE_VALUE[]
			},
			beforeUpload(item:XUPLOADFILE_FILE_INFO):Promise<XUPLOADFILE_FILE_INFO>{
				console.log(item)
				return Promise.resolve(item)
			},
			/** 删除前的回调函数。 */
			beforeRemove(index : number, item : XUPLOADFILE_FILE_INFO) : Promise<boolean> {
				console.log(index)
				return Promise.resolve(true)
			},
			//上传后，通过回调自行设置是成功还是失败
			beforeComputed(item : XUPLOADFILE_FILE_INFO) : XUPLOADFILE_FILE_INFO {

				let json = {} as UTSJSONObject;
				if (item.response != '') {
					try {
						json = JSON.parseObject(item.response)!
					} catch (e) {
						//TODO handle the exception
					}
				}

				let code = json['code']
				if (code != null) {
					let realCode = code as number;
					if (realCode != 200) {
						item.status = 5
						item.statusText = '没有权限'
					}
				}

				return item;
			},
			upload() {
				let up = this.$refs['uploader'] as XUploadMediaComponentPublicInstance
				up.upload();
			}
		}
	}
</script>

<style lang="scss">

</style>
		
