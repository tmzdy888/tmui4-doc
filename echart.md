
## 图表 xEchart

***

#### 介绍

是百度图表5.4.1,全量版本
传递正常的百度对象数据且需要将数据JSON.stringify化
图表文档：https://echarts.apache.org/zh/index.html
编译微信版本：https://echarts.apache.org/zh/builder.html
注意的是：如果你的配置中函数函数，需要自己转换为字符串【如果是微信端建议直接传对象，不要转为字符串这样兼容性更好。】
比如：函数对象请参考我demo页面的示例规则分平台写否则无法实现函数对象。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-echart/x-echart.uvue**

#### 使用

<x-echart></x-echart>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 窗口宽 | string | 'auto' |
| height | 窗口高 | string | '250px' |
| opts | 图表数据，你需要把对象数据转换为string<br>数据变动会触发更新。 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| init | - | 图表加载初始化完成后触发此事件。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |
| setEcharts | **e** : any | - | 将百度对象绑定到组件内,微信小程序必需要实现. |
| setOptions | **opts** : string | - | 设置图表数据 |
| getImg | - | 目前仅支持web平台，输入base64图片数据 | 获取图片数据 |
| cahrtActions | **fun** : Function**opts** : string**evt** : union | 目前仅支持web平台，输入base64图片数据 | echart对象执行的函数,比如:cahrtCall('clear','')执行清空动作，web的json string后的参数需要自己加‘’号app不用。 |


#### 示例页面路径

/pages/qita/echart

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
			<x-text font-size="18" class=" text-weight-b mb-8">图表 Echart</x-text>
			<x-text color="#999999" >
				是百度图表5.4.1,全量版本
			</x-text>
		</x-sheet>
		<x-sheet dark-color="#dcdcdc">
			<x-echart ref="echart" @init="oninit" :opts="opts"></x-echart>
			<x-button :block="true" @click="changeData">改变数据</x-button>
			<x-button class="mt-20" :block="true" @click="addEchartsclick">注册click事件(不要重复注册)</x-button>
		</x-sheet>
		<x-sheet>
			<x-text font-size="18" class=" text-weight-b ">测试饼图</x-text>
		</x-sheet>
		<x-sheet dark-color="#dcdcdc">
			<x-echart ref="echart2" height="300px" @init="initPie" :opts="opts2"></x-echart>
		</x-sheet>
		<view style="height:50px"></view>
	<!-- #ifdef APP -->
	</scroll-view>
	<!-- #endif -->
</template>

<script>
	// #ifdef MP-WEIXIN
	const echarts = require("./echarts.min.js")
	// #endif
	export default {
		data() {
			
			return {
				opts: "",
				opts2:""
			};
		},
		onReady() {
			// #ifdef MP
			let ele = this.$refs["echart"] as XEchartComponentPublicInstance
			let ele2 = this.$refs["echart2"] as XEchartComponentPublicInstance
			ele.setEcharts(echarts)
			ele2.setEcharts(echarts)
			// #endif
		},
		methods: {
			addEchartsclick(){
				let ele = this.$refs["echart"] as XEchartComponentPublicInstance
				ele.cahrtActions("click","",(data:any)=>{
					console.log(data)
					// 打印点击图表中的click事件。data是属性，一般是UTSJONObject
					if(data instanceof UTSJSONObject){
						uni.showModal({
							title:"提醒",
							content:JSON.stringify(data! as UTSJSONObject),
							showCancel:false
						})
					}
				})
			},
			oninit() {
				let opts = {
					title: {
						text: 'ECharts示例'
					},
					tooltip: {
						backgroundColor:'transparent',
						borderWidth:0,
						extraCssText:'box-shadow:none;',
						// #ifdef MP||WEB
						formatter:function (params) {const list = params.reduce(function(str, item){str+='<div style="display:flex;align-items:center;margin-top:10px"><div style="background-color:'+ item.color+';width:5px;height:5px;border-radius: 100%;"></div><div style="margin-left: 5px;color: #ffffff;">'+item.seriesName+'</div><div style="margin-left:10px;color:#ffffff;font-weight: 900;">'+((item.data?.value || item.data?.value === 0)?item.data?.value:'--'+item.data?.unit||'')+'</div></div>';return str;}, '');return '<div style="display: flex;flex-direction:column;font-size:12px"><div style="color: #ffffff;line-height: 1;">'+params[0].axisValue + '</div>'+list+'</div>';},
						// #endif
						// #ifdef WEB
						formatter:`function (params) {return '<div style="background-color:#0579FF;width:100%;line-height:30px;padding:0px 8px;height:30px;color:white;">'+params.name+":"+params.value+"</div>";}`,
						// #endif
						// #ifdef APP
						formatter:`function (params) {return \`<div style=\\"background-color:#0579FF;width:100%;line-height:30px;padding:0px 8px;height:30px;color:white;\\">\`+params.name+\\":\\"+params.value+\\"</div>\\";}`,
						// #endif
					},
					legend: {
						data: ['销量']
					},
					xAxis: {
						data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
					},
					// #ifdef MP
					formatter:function(val){ if(typeof val == "string") return val; var str = val.data + "件";return str;},
					// #endif
					// #ifdef H5
					formatter:`function(val){ if(typeof val == "string") return val; var str = val.data + "件";return str;}`,
					// #endif
					// #ifdef APP
					formatter:`function(val){ if(typeof val == \\"string\\") return val; var str = val.data + \\"件\\";return str;}`,
					// #endif
					yAxis: {},
					series: [
						{
							name: '销量',
							type: 'bar',
							data: [5, 20, 36, 10, 10, 20]
						}
					],
					
				} as UTSJSONObject
				// #ifdef MP
				this.opts = opts
				// #endif
				// #ifndef MP
				this.opts = JSON.stringify(opts)
				// #endif
			},
			changeData() {
				let opts = {
					title: {
						text: 'xui'
					},
					tooltip: {},
					legend: {
						data: ['xui']
					},
					xAxis: {
						data: ['衬衫', '羊毛衫', '裤子', '高跟鞋', '袜子', '1高跟鞋']
					},
					yAxis: {},
					series: [
						{
							name: 'xui',
							type: 'bar',
							data: [100, 50, 20, 70, 40,600]
						}
					]
				} as UTSJSONObject
				// #ifdef MP
				this.opts = opts
				// #endif
				// #ifndef MP
				this.opts = JSON.stringify(opts)
				// #endif
				
				let ele = this.$refs["echart"] as XEchartComponentPublicInstance
				ele.cahrtActions('resize','',null)
			},
			initPie(){
				let option = {
				  title: {
				    text: 'Referer of a Website',
				    subtext: 'Fake Data',
				    left: 'center'
				  },
				  tooltip: {
				    trigger: 'item'
				  },
				  legend: {
				    orient: 'vertical',
				    left: 'left'
				  },
				  series: [
				    {
				      name: 'Access From',
				      type: 'pie',
				      radius: '50%',
				      data: [
				        { value: 1048, name: 'Search Engine' },
				        { value: 735, name: 'Direct' },
				        { value: 580, name: 'Email' },
				        { value: 484, name: 'Union Ads' },
				        { value: 300, name: 'Video Ads' }
				      ],
				      emphasis: {
				        itemStyle: {
				          shadowBlur: 10,
				          shadowOffsetX: 0,
				          shadowColor: 'rgba(0, 0, 0, 0.5)'
				        }
				      }
				    }
				  ]
				} as UTSJSONObject;
				
				this.opts2 = JSON.stringify(option)
			}
		},

	}
</script>

<style lang="scss">

</style>
		
