
## 表单子组件 xFormItem

***

#### 介绍

从1.1.2开始允许非xform直接子节点了,也就是在xform可以嵌套view进行form-item布局了,但建议不要嵌套太深,影响性能.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-form-item/x-form-item.uvue**

#### 使用

<x-form-item></x-form-item>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| label | 表单名称 | string | "" |
| showLabel | 是否显示标题 | boolean \| null | null |
| field | 校验的字段名称<br>字段名称一定要存在于form表单数据中。否则报错。 | string | "" |
| required | 是否是必填项.<br>设置了此值，才会执行校验。 | boolean | false |
| showRequired | 是否显示校验必填项前面的红*符号 | boolean | true |
| rule | 校验规则对象,uniappx暂不支持对象中嵌套泛型函数<br>从1.1.10开始rule对象中增加了trigger:change,blur校验时机,blur主要是用在input组件上的<br>如果你内部没有input而使用blur,会造成不校验的问题,请认真阅读文档. | FORM_RULE[] | () : FORM_RULE[] => [] as FORM_RULE[] |
| labelWidth | 标签宽（横向表单时有效）<br>默认空值取父form统一的设置。 | string | "" |
| labelDirection | 默认空值取父form统一的设置。<br>vertical\|horizontal | string | "" |
| labelFontColor | 默认空值取父form统一的设置。<br>标签的文本颜色 | string | "" |
| labelFontSize | 默认空值取父form统一的设置。<br>标签的文本颜色 | string | "" |
| labelAlign | 标签标题对齐方式<br>left,right,center | string | "left" |
| showBottomBorder | 是否显示底部边框 | boolean | true |
| cellPadding | 排版布局上和下的间隙。<br>数组必须是2长度<br>第一个是上间隙，第二个是下间隙，<br>如果showBottomBorder为false时下间隙第二个参数会被取消。<br>如果label为horizontal横向时，第一个参数的上间隙生效，如果是上下排列不生效。 | string[] | () : string[] => ['10', '10'] as string[] |
| labelPadding | 排版布局上和下的间隙。<br>数组必须是2长度<br>第一个是上间隙，第二个是下间隙，<br>如果label为horizontal横向时，些参数失效，只有竖向时才生效。 | string[] | () : string[] => ['12', '12'] as string[] |
| showError | 校验时，是否显示下边的出错信息 | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| label | 标题 | - |
| default | 默认内容区域 | - |
| error | 出错提示的插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
