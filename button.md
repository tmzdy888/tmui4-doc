
## 按钮 xButton

***

#### 介绍

圆角，主题可通过配置统一设置或者动态全局设置，使设计风格统一并保持一致性。让你的风格独一无二。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-button/x-button.uvue**

#### 使用

<x-button></x-button>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| color | 主题名，名称或者合法的颜色值<br>默认为空，读取全局的主题色，可动态切换主题。 | string | '' |
| darkColor | 暗黑时的自定义背景色 | string | '' |
| bgColor | 自定义背景色，优先级高于color | string | '' |
| linearGradient | 渐变背景<br>数组格式如下<br>                 [方向:top,bottom,left,right,自定义值例:45deg,颜色1:,颜色2]<br>例:['left','black','white'] | string[] | () : string[] => [] |
| fontColor | 文字颜色 | string | '' |
| fontDarkColor | 文字颜色 | string | '' |
| fontSize | 文字大小 | string | "" |
| round | 圆角<br>空值时取全局的圆角值，大于-1时取本值。 | string | "" |
| border | 数字 | number | 0.5 |
| shadow | 投影 | number[] | () : number[] => {<br>    return [] as number[]<br>} |
| borderColor | 自定义边框颜色 ，优先于color自动生成 | string | "" |
| skin | 主题样式<br>default 默认空值不作处理<br>secondary 次要按钮，<br>text 文本 按钮,<br>outline 线性，<br>dashed 虚线边框<br>thin 浅色浅色按钮（自动把color按理论值设置为浅色模式） | string | "default" |
| icon | 暂时只支持内置图标，名称不要带ri- | string | "" |
| iconBtn | 是否为纯图标按钮 | boolean | false |
| iconSize | 图标大小,空值取文字大小。 | string | '' |
| size | 按钮尺寸 | string | "normal" |
| url | 提供url后，点击会导致该页面 | string | "" |
| navigateMode | url跳转模式,可以是官方指定的模式:navigateTo,redirectTo,switchTab,reLaunch,navigateBack | string | "navigateTo" |
| disabled | 禁用后无法点击 | boolean | false |
| loading | 是否加载中 | boolean | false |
| height | 自定义高度，可以是数字，单位或者百分比 | string | "" |
| width | 宽，单位合法即可数字，字符串带单位，百分比。 | string | "" |
| block | 是否块状态按钮 | boolean | false |
| formType | 表单属性，设置为form可以直接提交表单触发xform 的 submit<br>切记：如果你当作表单提交按钮时，一定是xform的直接子节点。<br>可填：form | 'form' | "" |
| lineHeight | 建议不要修改些值理论1时上下对齐<br>但由于uni sdk4.19-4.24之间会被裁剪，提供此属性<br>4.25之后建议改成1 | string | "1.4" |
| fontWeight | 字号权限,normal,bold | string | 'normal' |
| openType |  | string | "" |
| lang |  | string | "en" |
| sessionFrom |  | string | "" |
| sendMessageTitle |  | string | "" |
| sendMessagePath |  | string | "" |
| sendMessageImg |  | string | "" |
| appParameter |  | string | "" |
| showMessageCard |  | boolean | false |
| phoneNumberNoQuotaToast |  | boolean | true |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| click | - | 点击时触发 |
| getuserinfo | - | 点击 |
| contact | - | 点击 |
| getphonenumber | - | 点击 |
| getrealtimephonenumber | - | 点击 |
| error | - | 点击 |
| opensetting | - | 点击 |
| launchapp | - | 点击 |
| chooseavatar | - | 点击 |
| chooseaddress | - | 点击 |
| chooseinvoicetitle | - | 点击 |
| addgroupapp | - | 点击 |
| subscribe | - | 点击 |
| login | - | 点击 |
| agreeprivacyauthorization | - | 点击 |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |
| default | 默认插槽 | - |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径

/pages/fankui/button

#### 示例源码


		
