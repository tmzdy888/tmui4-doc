
## 开关 xSwitch

***

#### 介绍

开关，用于直观的展示选项表单的选择。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-switch/x-switch.uvue**

#### 使用

<x-switch></x-switch>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 激活时的背景色,空值时取全局的值。 | string | "" |
| bgColor | 未激活时的背景 | string | "info" |
| darkBgColor | 未激活时的暗黑背景<br>空取inputDarkColor | string | "" |
| btnColor | 按钮的背景色 | string | "white" |
| size | 尺寸 | string | "normal" |
| space | 间隙，px单位 | number | 2 |
| modelValue | 当前打开的状态，默认为false<br>等同v-model="" | boolean | false |
| disabled | 是否禁用 | boolean | false |
| loading | 是否加载中 | boolean | false |
| label | 开关文字数组第一个为开，后一个为关 | string[] | () : string[] => [] |
| round | 圆角。空值时取全局值。 | string | "" |
| activeIcon | 激活时的按钮图标，不提供不显示 | string | "" |
| icon | 未激活时的图标，不提供不显示 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **status** : boolean | 状态变换时触发。 |
| click | **status** : boolean | 组件被点击时触发。 |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/switch

#### 示例源码


		
