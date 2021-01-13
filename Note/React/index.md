# React 笔记索引
## JSX
> JSX可以在Javascript中写HTML，而不是用HTML包含Javascript。它能帮助快速开发，不需担心字符串和换行等。
>> JSX每一个组件都有一个 render 方法，这个方法产生一个”ViewModel(视图模型)” 
>> 在返回HTML到组件之前，可以将这个模型(ViewModel)的信息放入视图中，意味着你的HTML会根据这个模型动态改变(i.e. a dynamic array)。

## State (状态）
1. 每一个组件都有其自己的"状态"。当要使用状态时，首先需要定义初始状态，然后才可以使用 this.setState 来更新状态。
2. 当使用 this.setState 来更新状态时，组件都会再一次调用 render 函数，拿新的值去替换或者改变之前渲染的值。
3. 可以使用 this.state 来访问状态.

## Props (属性）
1. state 和 props 主要的区别在于 props 是不可变的，而 state 可以根据与用户交互来改变。
2. 组件类的 defaultProps 属性可以为 props 设置默认值。
3. 可以在父组件中设置 state， 并通过在子组件上使用 props 将其传递到子组件上。
