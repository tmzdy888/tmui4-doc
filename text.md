
## 文本 xText

***

#### 介绍

支持多文本高亮显示，目前uniapp x 4.0.1+正则。
可允许拓展：比如根据正则高亮电话号码，邮箱等，点击后打电话，发邮件。使用时一定要注意:尽量标签内容写文本,不要用label属性,label属性是用来高亮和正则的

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-text/x-text.uvue**

#### 使用

<x-text></x-text>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| _style | 自定文件标签的样式 | string | "" |
| _class | 自定文件标签的类,仅对标签插槽内的有效,如果使用label属性会变成richtext渲染,因为类将失效. | string | "" |
| label | 源文本，显示 的文本。 | string | "" |
| heightLight | 需要特别高亮的词 | string[] | () : string[] => [] as string[] |
| heightLightReg | 高亮的正则,<br>请尽量不要和heightLight字段结果集重叠,<br>也不要提供的正则数组出现重叠混乱。<br>默认是正则电话，邮箱 | string[] | () : string[] => [] as string[] |
| heightLightStyle | 高亮文本的自定义样式 | string | "" |
| lines | 最多显示几行，默认0不限制。<br>超过了此行会出现省略号。 | number | 0 |
| selectable | 是否允许复制。 | boolean | false |
| color | 文本颜色 | string | "#333333" |
| darkColor | 暗黑时的文本颜色，如果你不提供，将自动反转。<br>自动反转是根据亮度反转，色相不变。 | string | "" |
| heightLightColor | 高亮颜色 | string | "primary" |
| lineHeight | 行高 | string | "1.7" |
| fontSize | 文字大小。 | string | "" |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 整个组件被点击 |
| item-click | **str** : string | 文本被点击。比如高亮的文本被点击。 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认文本插槽，如果使用插槽，那么相关特性功能将会失效。 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/zhanshi/text

#### 示例源码


		
