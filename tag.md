
## 标签 xTag

***

#### 介绍

标签组件，可用于属性的提醒，显示，强调用。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-tag/x-tag.uvue**

#### 使用

<x-tag></x-tag>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| _class |  | string | '' |
| _style |  | string | '' |
| color | 主题名，名称或者合法的颜色值<br>默认为空时取全局的主题。 | string | '' |
| bgColor | 自定义背景色，优先级高于color和全局 | string | '' |
| darkBgColor | 暗黑时的自定义背景色 | string | '' |
| linearGradient | 渐变背景<br>数组格式如下<br>[<br>                 方向:top,bottom,left,right,<br>                 颜色1:<br>                 颜色2<br>             ]<br>例:['left','black','white'] | string[] | () : string[] => [] |
| fontColor | 自定义字体颜色优先级高于color自动生成 | string | '' |
| fontSize | 字号大小 | string | "" |
| round | 圆角数字 | number | -1 |
| border | 数字 | number | 1 |
| borderColor | 自定义边框颜色 ，优先于color自动生成 | string | "" |
| darkBorderColor | 如果不填写，默认取xConfig里面的默认边线颜色值 | string | "" |
| skin | default 默认空值不作处理,<br>secondary 次要按钮，<br>text文本 按钮,<br>outline 线性，<br>dashed 虚线边框<br>thint 浅色浅色按钮（自动把color按理论值设置为浅色模式） | string | "default" |
| icon |  | string | "" |
| size | 尺寸<br>normal 标准<br>mini 超小<br>mdeium 中等<br>large 大 | string | "normal" |
| url |  | string | "" |
| disabled | 禁用后无法点击 | boolean | false |
| loading | 是否加载中 | boolean | false |
| height | 自定义高度，可以是数字，单位或者百分比 | string | "" |



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

/pages/biaodan/tag

#### 示例源码


		
