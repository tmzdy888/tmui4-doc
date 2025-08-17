
## 单滑块 xSlider

***

#### 介绍

此为单向滑块,双向滑块见:x-slider-double

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | x | ☑️ | 4.14+ | 1.0.0 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-slider/x-slider.uvue**

#### 使用

<x-slider></x-slider>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 等同v-model当前的值 | number | 0 |
| max | 最大值 | number | 100 |
| min | 最小值 | number | 0 |
| disabled | 是否禁用 | boolean | false |
| step | 步进值 | number | 0 |
| stepCount | 步进值刻度值<br>比如max-min为100总值,刻度为20,那么setpCount就是4, | number | 0 |
| color | 激活时的颜色，空值取全局值 | string | "" |
| bgColor | 默认的背景色 | string | "info" |
| size | 滑条的大小 | string | "3" |
| btnSize | 滑块的尺寸 | string | "24" |
| round | 滑条的圆角。<br>为空值时，取全局的进度条值 | string | "" |
| showLabel | 是否显示进度条上的label文本 | boolean | false |
| labelColor | 文本颜色 | string | "black" |
| labelFontSize | 文本文字大小 | string | "12" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **value** : number | 拖动变换时触发 |
| update:modelValue | **value** : number | 松开拖动按钮时触发同步值，等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| right | 右插槽 | **value** : number<br>**value** : number<br>**percentage** : number<br>**percentage** : number<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/slider

#### 示例源码


		
