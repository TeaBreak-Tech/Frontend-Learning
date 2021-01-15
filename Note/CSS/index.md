# CSS笔记索引
## 背景

|属性  					|	描述									|
------------------------|----------------------------------------
|background 			| 简写属性，作用是将背景属性设置在一个声明中。	|
|background-attachment  |  背景图像是否固定或者随着页面的其余部分滚动	|
|background-color  		|  设置元素的背景颜色。					|
|background-image  		|  把图像设置为背景。						|
|background-position  	|  设置背景图像的起始位置。					|
|background-repeat  	|  设置背景图像是否及如何重复。				|

## 文本
|属性			|描述				|
--------		|------
|color			|设置文本颜色			|
|direction		|设置文本方向。		|
|line-height	|设置行高。			|
|letter-spacing	|	设置字符间距。	|
|text-align		|对齐元素中的文本。	|
|text-decoration|	向文本添加修饰。	|
|text-indent	|缩进元素中文本的首行。|
|text-shadow	|设置文本阴影			|
|text-transform	|控制元素中的字母 		|
|unicode-bidi	|设置文本方向。		|	
|white-space	|设置元素中空白的处理方式。|
|word-spacing	|设置字符间距。|	


## Fonts(字体）
1. font-style：指定斜体文字的字体样式属性
2. font-size：设置文本的大小(...px)
3. font-weight: 指定字体的粗细
...
### white-space

|值		  |空白符	| 换行符	|自动换行|
|---------|---------|-------|-------|
|pre-line |合并  	|	保留	|	允许	|
|normal	  |合并  	|	忽略	|	允许	|
|nowrap	  |合并		|   忽略	|不允许	|
|pre	  |保留  	|	保留	|不允许	|
|pre-wrap |保留		|   保留	|允许	|

## Table(表格）
1. border: 指定CSS表格边框
2. border-collapse: 设置表格的边框是否被折叠成一个单一的边框或隔开：
3. width/height

## Border(边框）
1. border-style：定义边框的样式
2. border-width：定义边框指定宽度。
3. border-top-style: 不同侧面的边框

## Dimension(尺寸）
1. height: 设置元素的高度。
2. line-height: 设置行高。
3. max-height: 设置元素的最大高度。
4. max-width: 设置元素的最大宽度。
5. min-height: 设置元素的最小高度。
6. min-width: 设置元素的最小宽度。
7. width: 设置元素的宽度。

## Position(定位)
> position: 指定了元素的定位类型
1. static: HTML 元素的默认值，即没有定位，遵循正常的文档流对象。
2. fixed: 元素的位置相对于浏览器窗口是固定位置, 即使窗口是滚动的它也不会移动.
3. relative: 相对定位元素的定位是相对其正常位置。
4. absolute: 绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>.
5. sticky: 基于用户的滚动位置来定位。

## Animation(动画)
> 要创建 CSS3 动画，需要了解 @keyframes 规则。@keyframes 规则是创建动画。@keyframes 规则内指定一个 CSS 样式和动画将逐步从目前的样式更改为新的样式。

## Transition(过渡）
> CSS3 过渡是元素从一种样式逐渐改变为另一种的效果。
>> 指定要添加效果的CSS属性.  指定效果的持续时间。
1. transition-property: 规定应用过渡的 CSS 属性的名称。	
2. transition-duration: 定义过渡效果花费的时间。默认是 0。	
3. transition-timing-function: 规定过渡效果的时间曲线。默认是 "ease"。	
4. transition-delay: 规定过渡效果何时开始。默认是 0。



