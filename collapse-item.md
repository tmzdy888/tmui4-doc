
## 折叠面板子组件 xCollapseItem

***

#### 介绍

可单，可多开,只可放置在x-collapse直接子节点组件,为了避免重复计算和性能x-collapse-item不能通过响应式修改内容。如果确实需要请通过刷新key解决

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-collapse-item/x-collapse-item.uvue**

#### 使用

<x-collapse-item></x-collapse-item>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| name | 唯一标识 | string | "" |
| showBottomLine | 是否显示底部边线 | boolean | true |
| disabled | 是否禁用 | boolean | false |
| titleFontSize | 标题大小 | string | '16px' |
| titleColor | 标题颜色 | string | '#333333' |
| darkTitleColor | 拒绝礼佛标题颜色，如果不填写取白 | string | '' |
| activeColor | 激活时的颜色，空值读取全局值。 | string | '' |
| color | 背景 | string | 'white' |
| darkColor | 暗黑时的背景，如果不填写默认取sheetDarkColor | string | '' |
| leftIcon | 左边图标 | string | '' |
| title | 标题 | string | '' |
| titleHeight | 标题高度 | string | '55' |
| titleLines | 标题最多显示几行出现省略号 | number | 1 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | **name** : string | 项目被点击时触发。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| left | 左边插槽 | **status** : boolean<br> |
| title | 标题插槽，如果你要完全自定标题样式请在此插槽内布局 | **status** : boolean<br> |
| right | 右边插槽 | **status** : boolean<br> |
| default | 默认内容插槽。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
