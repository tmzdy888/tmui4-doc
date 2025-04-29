
## 宫格子组件 xGridItem

***

#### 介绍

不可单独使用，请把放它在x-grid标签内。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-grid-item/x-grid-item.uvue**

#### 使用

<x-grid-item></x-grid-item>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| bgColor | 背景，默认为空值，读取父xGrid组件统一设置的背景<br>如果这里提供了，以子组件为准。 | string | 'transparent' |
| icon | 图标 | string | '' |
| text | 文字 | string | '' |
| iconColor | 图标颜色，空值取父xGrid的值 | string | '' |
| textColor | 图标颜色，空值取父xGrid的值 | string | '' |
| fontSize | 文字大小，空值取父xGrid的值 | string | '' |
| iconSize | 图标大小，空值取父xGrid的值 | string | '' |
| isLink | 是否开启链接hover效果 | boolean | true |
| url | url链接地址，如果填写，点击会跳转 | string | '' |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 项目点击时触发。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽内容 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
