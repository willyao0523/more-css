## CSS 动画
### 动画的原理：
- 视觉暂留的作用
- 画面逐渐变化

### 动画的作用
- 愉悦感
- 引起注意
- 反馈
- 掩饰

### CSS中的动画类型
- transition补间动画
  - 位置-平移 (left.right.margin.transform)
  - 方位 - 旋转(transform)
  - 大小 - 缩放(transform)
  - 透明度(opacity)
  - 其他 - 线性变换(transform)
  - transition: delay延迟时间值 property变化的属性或者all time动画时间
  - transition-timing-function 指定动画进度和时间的关系 linear/ease-in-out
- keyframe关键帧动画
相当于多个补间动画
与元素状态的变化无关
定义更加灵活
```css
animation: run 1s timing-function;
animation-direction: reverse;
animation-fill-mode: forwards;
animation-iteration-count: infinite;
animation-paly-style: paused;
@keyframes run {
  /* from{} */
  0%{ 
    width: 100px;
  }
  /* to{} */
  100%{
    width: 800px;
  }
}
```
- 逐帧动画
每一个帧都是关键帧
适用于无法补间计算的动画
资源比较大
使用steps `animation-timing-function: steps(1);` 中间状态静止 steps里面表示在关键帧变化的时候画面有有几个画面

### CSS 面试
1. CSS动画的实现方式？
- transition
- ketframes(animation)

2. 过渡动画和关键帧动画的区别
- 过渡动画需要有状态变化
- 关键帧动画不需要有状态变化
- 关键帧动画能控制更精细

3. 如何实现逐帧动画
- 使用关键帧动画
- 去掉补间steps

4. CSS动画的性能
- 性能不坏
- 部分情况下优于JS
- 但JS可以做的更好
- 部分高危属性 box-shadow等
