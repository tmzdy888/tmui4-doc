
## 嵌入式日期选择器 xDateView

***

#### 介绍

内嵌日期选择，可以控制显示精确到秒。默认的开始时间为当前时间的上一年，结束时间为默认当前时间
使用时，建议不要显示过多年份以防卡太多数据。

***

#### 平台兼容

| H5 | andriod | IOS | 小程序 | UTS | UNIAPP-X SDK | version |
| --- | --- | --- | --- | --- | --- | --- |
| ☑ | ☑️ | ☑️ | ☑️ | ☑️ | 4.44+ | 1.1.9 |

***

#### 文件路径

**@/uni_modules/tmx-ui/components/x-date-view/x-date-view.uvue**

#### 使用

<x-date-view></x-date-view>

#### Props 属性

| 名称 | 说明 | 类型 | 默认值 |
| ------ | ---- | ---- | ---- |
| modelValue | 当前时间,与modelStr不同，此提供的值必须是正常的时间格式<br>否则报错，无法运行。可以提供以下合法格式：<br>YYYY,YYYY-MM,YYYY-MM-DD,YYYY-MM-DD HH,YYYY-MM-DD HH:mm,YYYY-MM-DD HH:mm:ss | string | "" |
| modelStr | 当前时间经过format格式化后输出的值。<br>此值不会处理输入，只输出显示。 | string | "" |
| title | 顶部标题 | string | "请选择时间" |
| start | 开始时间，请提供正确的时间格式 | string | "" |
| end | 结束时间，请提供正确的时间格式 | string | "" |
| type | 精确到的级别<br>year:年<br>month:年月<br>day:年月日<br>hour:年月日小时<br>minute:年月日小时分钟<br>second:年月日小时分钟秒 | ModelType | "day" |
| format | 输出时间格式，只对v-model:modelStr有效<br>如果桢同步对vmodel:modelValue有效需要设置formatSyncValue为true<br>有效格式：<br>YYYY年<br>MM月<br>DD日<br>hh小时<br>mm分钟<br>ss秒 | string | "YYYY-MM-DD" |
| formatSyncValue | 是否将format格式化的v-model:modelStr同步到v-model:modelValue<br>默认false,注意：如果开启了同步，你要确保format的值是正常的时间值<br>正常兼容以下时间格式：<br>YYYY,YYYY-MM,YYYY-MM-DD,YYYY-MM-DD HH,YYYY-MM-DD HH:mm,YYYY-MM-DD HH:mm:ss | boolean | false |
| cellUnits | 上方的单位名称 | string[] | () : string[] => ['年', '月', '日', '时', '分', '秒'] as string[] |



#### Events 事件

| 名称 | 参数 | 说明 |
| ------ | ---- | ---- |
| change | **date** : string | 滑动变换时触发 |
| update:modelStr | - | 经格式化后的值。等同v-model:model-str |
| update:modelValue | - | 点击确认时同步。等同v-model |


#### Slots 插槽

| 名称 | 说明 | 数据 |
| ------ | ---- | ---- |


#### Ref 方法

| 名称 | 参数 | 返回值 | 说明 |
| ------ | ---- | ---- | ---- |


#### 示例页面路径



#### 示例源码


		
