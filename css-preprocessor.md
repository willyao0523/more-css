## CSS 预处理器
- 基于CSS的另一种语言
- 通过工具编译成CSS
- 添加了很多CSS不具备的特性
- 能提升CSS文件的组织
- less
- sass

### 特性
- 嵌套 反映层级和约束
- 变量和计算 减少重复代码
- Extend和Mixin代码片段
- 循环 适用于复杂有规律的样式
- import CSS文件模块化

### less
`../node_modules/.bin/lessc nest.less`
`../node_modules/.bin/lessc nest.less>nest.css`

### sass
`../node_modules/.bin/node-sass nest.scss>nest-scss.css`
上面的写法是保持sass的嵌套，而下面的写法更像是css的格式
`../node_modules/.bin/node-sass --output-style expanded nest.scss>nest-scss.css`

### mixin
#### less
```less
@fontSize: 12px;
@bgColor: red;

body {
  padding: 0;
  margin: 0;
}

.block(@fontSize) {
  font-size: @fontSize;
  border: 1px solid #ccc;
  border-radius: 34px;
}

.wapper {
  // lighten表示颜色变浅 配合第二个参数表示颜色变浅40%
  background: lighten(@bgColor, 40%);
  .nav{
    .block(@fontSize);
  }
  .content{
    // 数值类型可以直接+-
    .block(@fontSize + 2px);
    &:hover{
      background: @bgColor;
    }
  }
}
```
#### sass
```scss
$fontSize: 12px;
$bgColor: red;

body {
  padding: 0;
  margin: 0;
}

@mixin block($fontSize) {
  font-size: $fontSize;
  border: 1px solid #ccc;
  border-radius: 34px;
}

.wapper {
  // lighten表示颜色变浅 配合第二个参数表示颜色变浅40%
  background: lighten($bgColor, 40%);
  .nav{
    @include block($fontSize);
  }
  .content{
    // 数值类型可以直接+-
    @include block($fontSize + 2px);
    &:hover{
      background: $bgColor;
    }
  }
}
```

### extend
#### less
```less
@fontSize: 12px;
@bgColor: red;

body {
  padding: 0;
  margin: 0;
}

.block {
  font-size: @fontSize;
  border: 1px solid #ccc;
  border-radius: 34px;
}

.wapper {
  background: lighten(@bgColor, 40%);
  .nav:extend(.block){    
  }
  .content:extend(.block){
    // &:extend(.block)
    &:hover{
      background: @bgColor;
    }
  }
}
```
#### sass
```scss
$fontSize: 12px;
$bgColor: red;

body {
  padding: 0;
  margin: 0;
}

.block {
  font-size: $fontSize;
  border: 1px solid #ccc;
  border-radius: 34px;
}

.wapper {
  background: lighten($bgColor, 40%);
  .nav{
    @extend .block;
    color: #333;   
  }
  .content{
    @extend .block;
    &:hover{
      background: $bgColor;
    }
  }
}
```

### loop
#### less
```less
.gen-col(@n) when (@n > 0) {
  .gen-col(@n - 1);
  .col-@{n} {
    width: 1000px/12*@n;
  }
}
.gen-col(12);
```
#### sass
```scss
@mixin gen-col($n) {
  @if $n > 0 {
    @include gen-col($n - 1);
    .col-#{$n} {
      width: 1000px/12*$n;
    }
  }
}

@include gen-col(12);
```
```scss
@for $i from 1 through 12 {
  .col-#{$1} {
    width: 1000px/12*$i;
  }
}
```

### import 模块化
#### less
```less
@import "logo";
@import "header";
@import "nav";
@import "article";
```
#### sass
```scss
@import "logo";
@import "header";
@import "nav";
@import "article";
```

### CSS预处理器框架
- SASS - Compass
- Less - Lesshat / EST
- 提供线程的mixin
- 类似JS类库 封装常用功能

### CSS 面试
1. 常见的CSS预处理器
- Less (node.js)
- Sass (Ruby/Node)

2. 预处理器的作用
- 帮助更好地组织css代码
- 提高代码复用率
- 提高可维护性

3. 预处理器的能力
- 嵌套 反映层级和约束
- 变量和计算 减少重复代码
- extend和mixin 代码片段
- 循环 适用于复杂有规律的样式
- import css文件模块化

4. 预处理器的优缺点
- 优点: 提高代码复用率和可维护性
- 缺点: 需要引入编译过程 有学习成本