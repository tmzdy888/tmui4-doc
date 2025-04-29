
## 图片 xImage

***

#### 介绍

宽高可以设置，支持百分比，px,rpx

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-image/x-image.uvue**

#### 使用

<x-image></x-image>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| width | 宽度，默认100%<br>18rpx,18px,15%支持这三种单位，如果只写"18"就表示18rpx | string | "100%" |
| height | 高度,auto,%,rpx,px,string number<br>18rpx,18px,15%支持这三种单位，如果只写"18"就表示18rpx | string | "auto" |
| src | 图片源 | string | "" |
| previewSrc | 预览的图片源,如果为空则与src同步 | string | "" |
| model | 模式 | IMG_MODEL | "fill" |
| preview | 点击后是否预览图片 | boolean | true |
| ratio | 预览占位比例<br>宽/高，当数据没加载前，如果你设置了一项值比如宽，高会自动根据这个比例计算<br>当图片加载成功后，使用正确的原图片比例设置。<br>默认是5/4=1.25 | number | 1.25 |
| round | 圆角 | string | '0' |
| iconSize | 加载和失败时的图标大小。 | string | "16" |
| placeBgColor | 占位背景色 | string | "#F5F5F5" |
| placeDarkBgColor | 点位暗黑时的背景，如果不填写默认填充inputDarkBgcolor | string | "" |
| fadeShow | 是否在安卓上显示过渡动画 | boolean | false |
| lazy | 用于在scorllview根节点的页面进行懒加载,不可视范围内的不显示.请仅慎使用,不可在list-view中使用. | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 图片被点击 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| loading | 加载中的插槽,插槽内自行给你布局的view宽和高写100% | - |
| error | 加载失败时的插槽,插槽内自行给你布局的view宽和高写100% | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/image

#### 示例源码


		
