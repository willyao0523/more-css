## CSS基础
Cascading Style Sheet - 层叠样式表
### 基本规则
```
选择器 {
  属性:值;
  属性:值
}
```
### 选择器
- 用于匹配HTML元素
  - 有不同的匹配规则 tag/class/id
  - 多个选择器可以叠加
- 分类和权重
- 解析方式和性能
```css
.body div .hello {
  color: red;
}
/* 在浏览器的匹配过程中属性的匹配是从右到左,也就意味着先是找到.hello,然后查看上级是否是div并以此类推 */
/* 这么做的原因是因为父级的范围更广,更难确定匹配元素 */
```
#### 选择器的分类
- 元素选择器 a{}
- 伪元素选择器 ::before{} 
  - 真实存在的元素有样式
- 类选择器 .link{}
- 属性选择器 [type=radio]{}
- 伪类选择器 :hover{}  
  - 是一个元素的状态,不同于伪元素
- ID选择器 #id{}
- 组合选择器 [type=checkbox]+label{} 
- 否定选择器 :not(.link){}
- 通用选择器 *{}
#### 选择器的权重
- ID选择器 #id{}  +100
- 类 属性 伪类 +10
- 元素 伪元素 +1
- 其他选择器 +0
- !important 优先级最高
- 元素属性 优先级高
- 相同权重 后写的生效
**CSS选择器权重计算是不进位的**
```css
/* 计算1 */
/* #id .link a[href] */
/* #id + 100 .link + 10 a +1 [href] + 0 === 111 */
/* 计算二 */
/* #id .link.active */
/* #id +100 .link +10 .active +10 === 120 (权重更高，覆盖其他选择器) */
```
### 非布局样式
- 字体、字重、颜色、大小、行高
- 背景、边框
- 滚动、换行
- 粗体、斜体、下划线
- 其他

- 字体族 (font-family)
  - serif(衬线字体 字体周围会有装饰) 
  - sans-serif(非衬线字体 没有弯钩装饰) 
  - monospace(等宽字体 每个字母大小一致) 
  - cursive(手写体) 
  - fantasy(花体 华丽的字体)
- 多字体fallback
  - 找不到以后会向后自动查找
- 网络字体、自定义字体
- iconfont  

#### 自定义字体
```css
@font-face {
  font-familt: "IF";
  src: url("./字体名称.ttf");
  /* url中可以指定远程字体但需要注意跨域  */
}
/* 将自顶字体用于特定的部分 */
.custom-font {
  font-family: IF
}
```
#### 关于行和行高
- 行高的构成
  - line-height可以撑起来盒子的高度但是不会改变内容的高度(定高)
- 行高相关的现象和方案
  - 字体居中 line-height
  - `vertical-align: middle` 按照盒子对齐不是按照字体
- 行高的调整
  - 当文字和图片inline排布的时候,图片下部可能距离下部有一定的距离,此时我们可以使用`vertical-align: bottom`来使得图片按照底部对齐,这样就可以去掉这个间隔
#### 背景
- 背景颜色
  - white
  - #FFF (16进制格式)
  - hsl(色相,饱和度,亮度,透明度)
  - rgba(R色度,G色度,B色度)
  - 背景图: background: url("./test.png")
- 渐变色背景
  - 旧写法 `background: -webkit-linear-gradient(left, red, green);` 从左到右 从红色到绿色的线性渐变
  - 新写法 `background: linear-gradient(to right, red, green);`
  - `background: linear-gradient(0deg, red, green);`其中第一个值是角度值比如0deg表示从下到上45deg表示从左下到右上
- 多背景叠加
  - `background: linear-gradient(135deg, transparent 0, transparent 49.5, green 49.5, green 50.5, transparent 50.5, transparent 100);`相当于在中间划了一条绿色线条
  - 渐变色可以配合background-size使用 `background-size:30px 30px`
  - `background: linear-gradient(45deg, transparent 0, transparent 49.5, red 49.5, red 50.5, transparent 50.5, transparent 100);` 可与上面叠加表现出交叉状态
- 背景图片和属性(雪碧图)
  - `background: red url(./xxx.png);`
  - `background-repeat: no-repeat` 不要图片平铺，只出现一个
  - `background-repeat: repeat-x` x方向平铺
  - `background-repeat: repeat-y` y方向平铺
  - `background-position: center center` 背景图在中间出现
  - `background-position: 20px 30px` 举例坐上的像素值位置
  - `background-size: 100px 50px;` 设置背景图的尺寸
  -  雪碧图 其实就是把需要的图片元素在一个图片上,限制显示的宽高然后定宽定高的区域就只能显示图片的某个部分,在通过图片对于左上角位置的偏移使得特定的图片显示出来
- base64和性能优化
  - 减少HTTP连接数
  - 增大了存储的要求 
- 多分辨率适配

#### 边框
- 边框的属性: 线型 大小 颜色
- 边框背景图
```css
*{
  border: 30px solid transparent;
  border-image: url('./border.png') 30 round;
  /* border-image: url('./border.png') 30 repeat; */
}
```
- 边框衔接

#### 滚动
- 滚动行为和滚动条
```css
overflow: visiable;
overflow: scroll;
overflow: hidden;
overflow: auto;
```

#### 文字折行
- overflow-warp(word-warp) 通用换行控制
  - 是否保留单词
- word-break 针对多字节文字
  - 中文句子也是单词
- white-space 空白处是否断行    

#### 装饰性属性即其他
- 字重(粗体) font-weight
```css
font-weight: normal;
font-weight: bold;
font-weight: bolder;
font-weight: lighter;
font-weight: 100;
/* 100-900 取整百 */
```
- 斜体 font-style:itatic
- 下划线 text-decoration
- 指针 cursor

#### CSS Hack
- Selctor Hacks
- Property/Value Hacks
- Media Query Hacks

#### 面试题
1. CSS样式(选择器)的优先级
- 计算权重确定
- !important
- 内联样式
- 后写的优先级高
2. 雪碧图的作用
- 减少HTTP请求数 提高加载性能
- 有一些情况下可以减少图片大小 
3. 自定义字体的使用场景
- 宣传、品牌、banner等固定文案
- 字体图标
4. base64的使用
- 减少HTTP请求
- 适用于小图片
- base64的体积约为原图4/3
5. 伪类和伪元素的区别
- 伪类表状态
- 伪元素是真的有元素
- 前者单冒号,后者双冒号
6. 如何美化checkbox
- label[for]和id
- 隐藏原生input
- :checked + label