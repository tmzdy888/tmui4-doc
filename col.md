
## 布局子组件 xCol

***

#### 介绍

只能放置中x-row中布局

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-col/x-col.uvue**

#### 使用

<x-col></x-col>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| span | 列宽，它是根据row定义的总列宽计算具体的宽度值。 | number | 3 |
| offset | 可以输入%,数字或者带单位的偏移量 | string | '0' |
| _style | 自定义内部标签的style<br>请使用_style | string | "" |
| _class | 自定义内部标签的class,<br>请使用_class | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 单元格被点击的事件 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/col

#### 示例源码


		
