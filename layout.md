
## 占位排版 xLayout

***

#### 介绍

这是一个占位排版布局组件,需要配合x-layout-item组件实现占位排版
具体表现为:当组件在可视区域外时或者你指定延迟渲染或者你指定不渲染时,会以一个空的view来占位,内容不渲染.以此来达到排版不塌陷,同时又提高渲染速度.
场景:非常适配个人中心/首页,或者需要占位,渲染较多的情况下使用

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| x | x️ | x | x | x️ | 4.14+ | 1.0.1 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-layout/x-layout.uvue**

#### 使用

<x-layout></x-layout>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| show | 默认是false自动判断要不要显示内容<br>如果你强制设置为true那内部不再判断,直接显示内容<br>并且不可动态更新,只有初始设置有效. | boolean | false |
| fade | 显示时,是否需要过渡. | boolean | true |
| customStyle |  | UTSJSONObject | ()=>{<br>    return {} as UTSJSONObject<br>} |
| color | 占位时的背景 | string | "transparent" |
| darkColor | 暗黑时的占位背景. | string | "transparent" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | - | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
