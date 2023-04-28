### 组件介绍
#### 1. type-writer
名称：打字机组件
效果：实现文本打字定数输出效果

参数：
props
参数名|参数属性|参数类型|默认值|是否必传
文本列表|contentList|Array|[]|true
延迟时间|delaytime|Number|100|false
文本标识|uid|String|''|


Events
事件名|说明|回调参数
finish|打字效果完毕|---
pause|打字效果暂停|text:暂停住的所有文本


Methods
名称|说明|参数
pause|暂停打字|---
continues|继续打字|---
reset|重置|---