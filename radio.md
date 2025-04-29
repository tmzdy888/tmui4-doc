
## 单选框 xRadio

***

#### 介绍

使用时,x-radio能单独使用，如果要与x-radio-group配合，从1.1.2开始允许是非直接x-radio-group子节点布局,但考虑到性能建议是直接子节点.

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-radio/x-radio.uvue**

#### 使用

<x-radio></x-radio>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 当前主题色，空值时取全局 | string | "" |
| unCheckColor | 当前未选中时主题色，空值时取全局 | string | "" |
| darkUnCheckColor | 当前未选中时的暗黑主题色 | string | "" |
| modelValue | 由于uniappx 截止3.98<br>不支持联合类型，因此当前只支持string类型，后期如果官方支持<br>可扩展为string,number,boolean | string | "" |
| defaultChecked | 非受控下默认选中的状态 | boolean | false |
| value | 选中的值<br>由于uniappx 截止3.98<br>不支持联合类型，后期如果官方支持<br>可扩展为string,number,boolean | string | "1" |
| unCheckValue | 未选中的值<br>由于uniappx 截止3.98<br>不支持联合类型，后期如果官方支持<br>可扩展为string,number,boolean | string | "" |
| disabled | 是否禁用 | boolean | false |
| icon | 选中的图标名称。 | string | "checkbox-blank-circle-fill" |
| label | 右侧文字。 | string | "" |
| hiddenCheckbox | 是否隐藏选中框。然后利用默认插槽自定义选中所有样式和状态。 | boolean | false |
| size | 尺寸 | string | "24" |
| iconSize | 中间小图标大小 | string | "20" |
| labelFontSize | 文字大小 | string | "15px" |
| labelSpace | label和选中框间的间距 | string | '10' |
| onlyChecked | 是否允许取消选中.之前因为大家的需求不一样<br>有的人需要允许取消选中,有的人不需要取消选中<br>现在单独开这个属性各取所需,出现这个属性时,group或者单个使用时将不允许取消选中,至少保留一项选择.<br>这个属性我不能设置默认为true,因为要向下兼容,所有需要的人麻烦自己设置为true | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **check** : boolean**value** : number | 用户交互切换，选中变换时触发。 |
| click | - | 点击事件 |
| update:modelValue | - | 当前选中的值，等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| label | 默认文本插槽 | **checked** : boolean<br>**checked** : string<br>**value** : boolean<br>**value** : string<br> |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/daohang/radio

#### 示例源码


		
