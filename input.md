
## 输入框 xInput

***

#### 介绍

表单输入框，样式可定制化强

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-input/x-input.uvue**

#### 使用

<x-input></x-input>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| _style | 自定义style<br>标签请写_style,不是-style，插件文档转换问题 | string | "" |
| focusBorder | 输入框统一的聚集样式<br>第3表示默认的边颜色(如果为空表示默认边颜色不生效.),第4表示聚焦时的颜色(空表示取全局color,transparent为不生效就是没有聚集样式)<br>['2px','solid','','']<br>全局的配置名称是:inputFocusBorder,可以全局设置. | string[] | ():string[] => [] as string[] |
| placeholderStyle | 占位的样式 | string | "" |
| _class | 自定class<br>标签请写_class,不是-class，插件文档转换问题 | string | "" |
| round | 输入框圆角 | string | "" |
| showClear | 是否显示清除图标 | boolean | false |
| rightText | 右侧文本 | string | "" |
| leftText | 左侧文本 | string | "" |
| modelValue | 双向绑定的输入值 | string | "" |
| placeholder | 输入框提示语 | string | "请输入" |
| iconColor | 左图标的颜色<br>默认空值取全局的主题色。 | string | "" |
| clearColor | 清除图标的颜色 | string | "#bfbfbf" |
| color | 输入框背景 | string | "" |
| darkBgColor | 输入框暗黑背景，空值取全局的配置<br>提供会覆盖全局的配色。默认是透明 | string | "transparent" |
| fontColor | 输入框的字体颜色 | string | "#333333" |
| darkFontColor | 如果你提供，就会覆盖自动的反转配色。<br>默认是fontColor的反转颜色。 | string | "" |
| fontSize | 文字大小 | string | "16" |
| leftIcon | 左图标 | string | "" |
| name | 见官方文档：https://doc.dcloud.net.cn/uni-app-x/component/input.html | string | "" |
| disabled | 见官方文档：https://doc.dcloud.net.cn/uni-app-x/component/input.html | boolean | false |
| type | 类型<br>"text"\|"number"\|"digit"\|"tel"<br>见官方文档：https://doc.dcloud.net.cn/uni-app-x/component/input.html<br>不管你是number,还是digit或者tel是可以让用户按规范填写的只能是数字<br>但你定义modelValue类型时，只能是string，请特别注意。 | string | "text" |
| password | 是否是密码类型 | boolean | false |
| maxlength | 最大字符数量，如果要显示统计字符，请设置showChartCount为ture | number | -1 |
| cursorSpacing |  | number | 0 |
| cursorColor |  | string | "" |
| autoFocus |  | boolean | false |
| focus |  | boolean | false |
| confirmType |  | string | "next" |
| confirmHold |  | boolean | false |
| cursor |  | number | 0 |
| selectionStart |  | number | -1 |
| selectionEnd |  | number | -1 |
| adjustPosition |  | boolean | true |
| width | 宽 | string | "auto" |
| height | 高 | string | "44" |
| trim | 自动删除首尾空格?<br>只会在失去焦点时删除.<br>这里需要个解释:由于用户输入过快或者允许用户自由的输入,组件本身不会去干涉用户输入<br>因为一旦干涉就在会在低端机上会出现字符闪烁的情况(特别是微信小程序上的安桌机),看似简单的功能后面隐藏着非常大的风险<br>因此你在事件中收到的字符绝对是经过处理的字符串,但用户的输入框可能还是有空格. | boolean | true |
| align | 文本对齐方式 | string | "left" |
| autoHeight | type=textarea时生效 | boolean | false |
| fixed | 如果 textarea 是在一个 position:fixed 的区域，需要显示指定属性 fixed 为 true | boolean | false |
| showFooter | 显示底部的注释说明及出错信息。 | boolean | false |
| showChartCount | 是否显示字符统计。 | boolean | false |
| inputPadding | 格式就是正常的css格式<br>比如：8rpx 8rpx 0rpx 0rpx | string | "8px 12px" |
| inputmode |  | string | 'text' |
| holdKeyboard |  | boolean | false |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击整个输入框触发 |
| clear | - | 清空时触发 |
| rightClick | **value** : string | 点击右侧文本时触发,如果你使用了插槽替换了，此事件不会触发 |
| confirm | **value** : string | 输入法点了确认搜索按钮时触发 |
| input | **value** : string | 输入时触发 |
| focus | **evt** : UniInputFocusEvent | 获取焦点时 |
| blur | **evt** : InputBlurEvent | 失去焦点时 |
| linechange | **evt** : UniTextareaLineChangeEvent | 键盘高度变化时触发 |
| keyboardheightchange | **evt** : UniInputKeyboardHeightChangeEvent | 键盘高度变化时触发 |
| update:modelValue | - | 等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| left | 左插槽 | - |
| inputLeft | 输入框内的左插槽 | - |
| inputRight | 输入框内右插槽 | - |
| right | 右插槽 | - |
| footer | 底部提示插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/qita/input

#### 示例源码


		
