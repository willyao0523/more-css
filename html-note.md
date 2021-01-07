## HTML知识点

### HTML常见元素和理解
#### head区
- meta
- title
- style
- script
- base
#### body区
- div/section/article/aside/header/footer 容器、块元素
- p 段落
- span/em/strong 行内元素
- table/thead/tbody/tr/td 表格元素
- ul/ol/li/dl/dt/dd 列表元素
- a 链接元素
- form/input/select/textarea/button 表单元素

```html
<!-- 字符集 -->
<meta charset="utf8">
<!-- viewport视窗 屏幕的尺寸 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<!-- 基础路径 -->
<base href="/>
```

#### HTML重要属性
- a[href, target]
  - target:控制在当前页面或者新页面或者框架中打开
- img[src, alt]
- table td[colspan, rowspan]
- form[target, method, enctype]
- input[type, value]
- button[type]
- select>option[value]
- labe[for]

### HTML版本
- HTML4/4.01 基于SGML
- XHTML 基于XML
- HTML5

|HTML4|XHTML|HTML5|
|---|---|---|
|标签允许不结束|标签必须结束|标签允许不结束|
|属性不用带引号|属性必须带引号|属性不用带引号|
|标签属性可大写|标签属性必须小写|标签属性可大写|
|Boolean属性可省略值|Boolean属性必须写值|Boolean属性可省略值|

#### HTML5新内容
- 新区块标签
  - section
  - article
  - nav
  - aside
- 表单增强
  - 日期、时间、搜索
  - 表单验证
  - placeholder 自动聚焦
- HTML5新增语义
  - header/footer 头尾
  - section/article 区域
  - nav 导航
  - aside  侧边栏
  - em/strong 强调
  - i icon

### HTML元素分类
- 按默认样式分类
  - 块级 block 方型 独占一行 div/p
  - 行内 inline 可以挤在在一行
  - inline-block 有方型 但是可以挤在在一行
- 按内容分
![内容划分HTML元素](https://upload.cc/i1/2021/01/07/D2OI5k.jpg)

### HTML元素嵌套关系
- 块级元素可以包含行内元素
- 块级元素不一定能包含块级元素
- 行内元素一般不能包含块级元素(a可以包含块级元素)
- a>div是否合法是取决于a外部是什么。a是不纳入计算的。如果a外部是div那么计算上就是div>div这就是合法的.如果外部是p/span那么就是不合法的.

### HTML元素默认样式和定制化
- 默认样式的意义
- 默认样式的问题
- CSS Reset
去掉默认的样式
1. CSS reset
[css reset resource](https://meyerweb.com/eric/tools/css/reset/)
2. *改写
```css
/* 可能会带来CSS性能的问题 */
* {
  margin: 0;
  padding: 0;
}
```
3. [Normalize.css](https://necolas.github.io/normalize.css/)
将浏览器的默认设置变得更统一和谐而不是全局的reset
### HTML面试相关
1. doctype的意义是什么
- 让浏览器以标准模式渲染
- 让浏览器知道元素的合法性
2. HTML XHTML HTML5的关系
- HTML属于SGML
- XHTML属于XML,是HTML进行XML严格化的结果
- HTML5不属于SGML或XML,比XHTML更宽松
3. HTML5的变化
- 新的语义化元素
- 表单增强
- 新的API(离线、音视频、图形、实时通信、本地存储、设备能力)
- 分类和嵌套变更
4. em和i有什么区别
- em是语义化的标签,表示强调
- i是纯样式的标签,表斜体
- HTML5中i用作图标的表示
5. 语义化的意义
- 开发者容易理解
- 机器容易理解结构(搜索、读屏软件)
- 有助于SEO
- sematic microdata
6. 哪些元素可以自闭合
元素内不可以带入其他元素
- 表单元素 input
- 图片 img 
- br hr
- meta link
7. HTML和DOM的关系
- HTML是"死"的
- DOM由HTML解析而来的,是"活"的
- JS可以维护DOM
8. property和attribute的区别
- attribute是"死"的
- property是"活"的,更多是对DOM而言的
9. form的作用有哪些
- 直接提交表单
- 使用submit/reset按钮
- 便于浏览器保存表单
- 第三方库可以整体提取值
- 第三方库可以进行表单验证
