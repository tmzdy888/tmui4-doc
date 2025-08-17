
## 单选框组 xRadioGroup

***

#### 介绍

使用时,从1.1.2开始允许是非直接xRadio子节点布局,但考虑到性能建议是直接子节点.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-radio-group/x-radio-group.uvue**

#### 使用

<x-radio-group></x-radio-group>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前选中的值。null表示未选中。 | string | "" |
| direction | 对齐方式 | string | "row" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **val** : string | 选项变化时触发。 |
| update:modelValue | - | 等同v-model="" |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 从1.1.2开始允许是非直接xRadioGroup子节点布局,但考虑到性能建议是直接子节点. | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
