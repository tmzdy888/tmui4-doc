
## 加载中 xLoading

***

#### 介绍

加载中占位符，场景用到页面加载前。请在标签内写上你的文本, 如果不写，默认显示“加载中...”

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-loading/x-loading.uvue**

#### 使用

<x-loading></x-loading>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 图标颜色 | string | "#8b8b8b" |
| textColor | 文字颜色 | string | "#8b8b8b" |
| textSize | 文字大小 | string | "12" |
| iconSize | 图标大小 | string | "21" |
| vertical | 是否垂直，默认是水平 | boolean | true |
| icon | 图标 | string | "loader-line" |
| hideText | 隐藏加载文本插槽 | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 请在插槽内写上你的文本, 如果不写，默认显示“加载中...” | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/utsapi/loading

#### 示例源码


		
