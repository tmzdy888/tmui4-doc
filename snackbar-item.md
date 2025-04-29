
## 消息条子节点 xSnackbarItem

***

#### 介绍

xSnackbar内部子组件，不可引用。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-snackbar-item/x-snackbar-item.uvue**

#### 使用

<x-snackbar-item></x-snackbar-item>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| content | 消息数据<br>注意，id一定要提供且是数字，可以随意，只要相对上一次变更下，就会触发<br>显示新的消息条。这种显示的方式就是避免你们引用ref方式来调用方法，相对更简单。 | SNACKBAR_ITEM | () : SNACKBAR_ITEM => {<br>    return {<br>        background: "black",<br>        color: "white",<br>        fontSize: "14px",<br>        content: "",<br>        id: -1,<br>        icon: ""<br>    } as SNACKBAR_ITEM<br>} |
| keyIndex |  | number | -1 |
| duration | 多少毫秒后销毁 | number | 2500 |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| close | - | - |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
