## CSS 效果
### 效果属性
- box-shadow
  - 营造层次感(立体感)
  - 充当没有宽度的边框
  - 特殊效果
- text-shadow
  - 立体感
  - 印刷品质感  
- border-radius
  - 圆角矩形
  - 圆形
  - 半圆/扇形
  - 一些奇怪的角
- background
  - 纹理、图案
  - 渐变
  - 雪碧图动画
  - 背景图尺寸适应
    - background-position: center center; 将图片放在中间
    - background-repeat: no-repeat/repeat-x/repeat-y;
    - background-size: cover/contain;
- clip-path
  - 对容器进行裁剪
    - `clip-path:circle(50px at 100px 200px);`
    - 支持动画而且不需要改变容器的大小
  - 常见几何图形
  - 自定义路径

- 3D变换
  - 变换transform
    - translate
      - `translateX(100px) translateY(100px) ratate(25deg)`
      - `translateZ(10px)`
    - scale
    - skew
    - rotate   
   
### CSS 面试
1. 如何用一个div画xxx
- box-shadow无限投影
- ::before
- ::after

2. 如何产生不占空间的边框
- box-shadow
- outline

3. 如何实现圆形元素(头像)
- border-radius

4. 如何实现ios图标
- clip-path(svg)

5. 如何显示半圆、扇形等图形
- border-redium组合
- 有无边框
- 边框粗细
- 圆角半径

6. 如何显示背景图居中、不重复、改变大小
- background-position
- background-repeat
- background-size(cover/contain)

7. 如何平移、放大一个元素
- transform: translateX(100px)
- transform: scale(2)

8. 如何实现3d效果
- perspective: 500px
- transform-style: perserve-3d
- transform: translate rotate ...