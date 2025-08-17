
## 侧边分类子节点 xSliderTreeChildren

***

#### 介绍

xSliderTree内部子组件，不可引用

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-slider-children/x-slider-children.uvue**

#### 使用

<x-slider-children></x-slider-children>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| itemTextColor | 选项项目未选中的文字颜色 | string | "#333333" |
| itemActiveColor | 选项项目选中的文字颜色，空值取全局主题 | string | "" |
| sliderContentBgColor | 右内容区域背景颜色 | string | "white" |
| list |  | SLIDER_TREE_ITEM[] | () : SLIDER_TREE_ITEM[] => [] as SLIDER_TREE_ITEM[] |
| modelValue | 当前选中项的id数组 | string[] | () : string[] => [] as string[] |
| multiple | 是否允许多选 | boolean | false |
| index | 当前的索引 | number | 0 |
| nowSelecteds | 父级选中的项。 | string[] | () : string[] => [] as string[] |
| height |  | string | '100%' |
| boxHeight |  | number | 0 |
| fontSize | 文字大小 | string | "16" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| back | - | - |
| itemClick | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 内部节点插槽，不对外 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
