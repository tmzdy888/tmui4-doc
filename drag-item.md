
## 拖拽排序子组件 xDragItem

***

#### 介绍

仅可放置在父容器x-drag中，如果在组件上写style时，不可写left,top,width,height等属性来影响组件的高和宽。
也不可直接写padding,margin来影响组件的位置。你可以在组件中自己写view后，再自由的布局写间隙等。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-drag-item/x-drag-item.uvue**

#### 使用

<x-drag-item></x-drag-item>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| order | 索引，vfor时提供index,必填<br>而且一定是正确的索引列表顺序，不可随便填写。 | number | 0 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击时触发 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
