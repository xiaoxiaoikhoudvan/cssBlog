# 浏览器渲染原理以及transition和animation

## 一、浏览器渲染原理
### 第一步：构建DOM树
---

处理 HTML 标记并构造 DOM 树。HTML 解析涉及到 tokenization 和树的构造。HTML 标记包括开始和结束标记，以及属性名和值。 如果文档格式良好，则解析它会简单而快速。解析器将标记化的输入解析到文档中，构建文档树。

DOM 树描述了文档的内容。<html> 元素是第一个标签也是文档树的根节点。树反映了不同标记之间的关系和层次结构。嵌套在其他标记中的标记是子节点。DOM 节点的数量越多，构建 DOM 树所需的时间就越长。


### 第二步：构建CSSOM树
---
第二步是处理 CSS 并构建 CSSOM 树。CSS 对象模型和 DOM 是相似的。DOM 和 CSSOM 是两棵树. 它们是独立的数据结构。浏览器将 CSS 规则转换为可以理解和使用的样式映射。浏览器遍历 CSS 中的每个规则集，根据 CSS 选择器创建具有父、子和兄弟关系的节点树。

### 第三步：Style
---
将 DOM 和 CSSOM 组合成一个 Render 树，计算样式树或渲染树从 DOM 树的根开始构建，遍历每个可见节点

### 第四步：Layout
---
在渲染树上运行布局以计算每个节点的几何体。布局是确定呈现树中所有节点的宽度、高度和位置，以及确定页面上每个对象的大小和位置的过程。回流是对页面的任何部分或整个文档的任何后续大小和位置的确定。

构建渲染树后，开始布局。渲染树标识显示哪些节点（即使不可见）及其计算样式，但不标识每个节点的尺寸或位置。为了确定每个对象的确切大小和位置，浏览器从渲染树的根开始遍历它。

### 第五步：绘制
---
将各个节点绘制到屏幕上。在绘制或光栅化阶段，浏览器将在布局阶段计算的每个框转换为屏幕上的实际像素。绘画包括将元素的每个可视部分绘制到屏幕上，包括文本、颜色、边框、阴影和替换的元素（如按钮和图像）。


## 二、transition 和 animation

* transition的属性：
---

1. transition-property：动画展示哪些属性，可以使用all关键字；

2. transition-duration：动画过程有多久；

3. transition-timing-function: linear,ease,ease-in,ease-out,ease-in-out，贝塞尔曲线等：控制动画速度变化；

4. transition-delay：动画是否延迟执行

* animation-属性：
---
  
1. animation-name：keyframes中定义的动画名称；

2. animation-duration：动画执行一次持续的时长；

3. animation-timing-function：动画速率变化函数；

4. animation-delay：动画延迟执行的时间；

5. animation-iteration-count：动画执行的次数，可以是数字，或者关键字（infinate）;

6. animation-direction：alternate(奇数次超前运行，偶数次后退运行)。

7. animation-fill-mode：告诉浏览器将元素的格式保持为动画结束时候的样子。

* 两者区别
---
transition是过渡属性，强调过渡，他的实现需要触发一个事件（比如鼠标移动上去，焦点，点击等）才执行动画，过渡只有一组（两个：开始-结束）关键帧。

animation是动画属性，他的实现不需要触发事件，设定好时间之后可以自己执行，且可以循环一个动画（设置多个关键帧）





