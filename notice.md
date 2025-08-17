
## 通知栏 xNotice

***

#### 介绍

速度可控，样式比较方便的调整。如果想要竖向的，请使用官方的轮播实现。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-notice/x-notice.uvue**

#### 使用

<x-notice></x-notice>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| speed | 速率 | number | 30 |
| color | 背景色 | string | "#ebf4ff" |
| darkColor | 暗黑时的背景色，如果不填写，取color暗黑浅背景。 | string | "" |
| fontColor | 文字和图标色 | string | "primary" |
| fontSize | 文字大小和图标大小 | string | "14" |
| icon | 图标，如果为空将不显示 。 | string | "megaphone-line" |
| iconColor | 不填写的话取fontColor | string | "" |
| iconSize | 不填写的话取fontSize | string | "" |
| label | 通知文本。 | string[] | () : string[] => [] |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | **index** : number | 项目被点击 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/notice

#### 示例源码


		
