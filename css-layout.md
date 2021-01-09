## CSS布局
- CSS知识体系的重中之重
- 早期以table为主(简单)
- 后来以技巧性布局为主(难)
- 现在flexbox/grid(偏简单)
- 响应式布局是必备

### 常用布局方法
- table表格布局
- float浮动+margin
- inline-block布局
- flexbox布局

### 盒子模型
![盒子模型](https://upload.cc/i1/2021/01/09/VPiq7t.jpg
)
宽高只对内容区域生效

### dispaly/position
- 确定元素的显示类型
  - block/inline/inline-block
- 确定元素的位置
  - static/relative/absolute/fixed 
  - relative的计算方式是按照原本它应该存在的位置来计算的
  - absolute使得控件脱离文档流,相当于独立的存在
    - absolute的定位不一定是针对于body的,他参考的是最近的absolute或者relative.但是要注意他是相对于外部层级来说的.比如body > p1-absolute p2-absolute,那么p2还是相对于body的,但是如果是body > p1 > p2,那么就是p2相对于p1.
  - fixed使得控件脱离文档流,其位置是相对于屏幕或者可视区域的
  - z-index:可以改变元素层叠的顺序,默认的情况是根据顺序来层叠,后来出现的就覆盖住前面出现的.

### flexbox
- 弹性盒子
- 盒子本来就是并列的
- 指定宽度即可  

### float布局
- 元素"浮动"
- 脱离文档流
- 但不脱离文本流
- 主要用于图文混排
- 对自身的影响:
  - 形成"块"(BFC) float作用于inline元素span使得span都有了宽和高 
  - 位置尽量靠上
  - 位置尽量靠左(右)
- 对兄弟的影响：
  - 上面贴非float元素
  - 旁边贴float元素
  - 不影响其他块级元素的位置
  - 影响其他块级元素内部文本
- 对父级元素的影响
  - 从布局上"消失"
  - 高度塌陷
#### 高度塌陷的解决方案
在例子中两个float块叠加起来最后高度塌陷了,其表现形式为好像整个容器的不在是矩形而是缺了一块,这使得下面的容器就要定格显示,从而造成了上下容器直接有重叠.
- 解决方案1就是在塌陷的容器添加`overflow: auto`.也就是说给容器添加高度的自动监测,从而让整个高度取最大值,从而撑开了容器.
- 解决方案2是用伪元素在容器的下方添加一个block从而将容器拓展开以和下面的元素拉开一定的距离.

### inline-block布局
- 像文本一样排block元素
- 没有清除浮动等问题
- 需要清除间隙

### 响应式布局和方法
- 在不同设备上正常使用
- 一般主要处理屏幕大小问题
- 主要方法
  - 隐藏+折行+自适应空间
  - rm/viewpoint/media query

### CSS 面试
1. 实现两栏(三栏)布局的方法
- 表格布局
- float+margin布局
- inline-block布局
- flexbox布局

2. position:absolute/fixed的区别
- 前者相对最近的absolute/relative
- 后者相对屏幕(viewport)

3. display:inline-block的间隙
- 原因: 字符间距
- 解决: 消灭字符或者消灭间距

4. 如何清除浮动
- 让盒子负责自己的布局
- overflow:hidden(auto)
- ::after{clear:both}

5. 如何适配移动端页面
- viewport
- rem/viewport/media query
- 设计上: 隐藏 折行 自适应