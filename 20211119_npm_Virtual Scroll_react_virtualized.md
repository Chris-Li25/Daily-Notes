### npm

#### 开发中遇到的小问题记录：

​		当项目在使用打包软件启动运行时，安装一些的库会失败。尽量先停止运行项目后再进行安装。



### 虚拟滚动（Virtual Scroll）

​		在遇到输出log或其他展示信息的场景时，需要输出大量信息。此时完整渲染长列表是不可取的，不仅会消耗巨大的性能且页面可能卡顿

#### 原理

​		虚拟列表是一种根据滚动容器元素的可视区域来渲染长列表数据中某一个部分数据的技术

#### 可视区域渲染

##### 滚动容器元素

​		一般情况下，滚动容器元素是 `window` 对象。然而，我们可以通过布局的方式，在某个页面中任意指定一个或者多个滚动容器元素。只要某个元素能在内部产生横向或者纵向的滚动，那这个元素就是滚动容器元素考虑每个列表项只是渲染一些纯文本。在本文中，只讨论元素的纵向滚动。

##### 可滚动区域：

​		滚动容器元素的内部内容区域。假设有 100 条数据，每个列表项的高度是 50，那么可滚动的区域的高度就是 100 * 50。可滚动区域当前的具体高度值一般可以通过(滚动容器)元素的 `scrollHeight` 属性获取。用户可以通过滚动来改变列表在可视区域的显示部分。

##### 可视区域：

​		滚动容器元素的视觉可见区域。如果容器元素是 `window` 对象，可视区域就是浏览器的视口大小(即[视觉视口](https://user-images.githubusercontent.com/7871813/43363609-26e0d164-933b-11e8-85e5-1ec21d5ba398.png))；如果容器元素是某个 `div` 元素，其高度是 300，右侧有纵向滚动条可以滚动，那么视觉可见的区域就是可视区域。

#### 实现

实现虚拟列表就是在处理用户滚动时，要改变列表在可视区域的渲染部分

具体步骤如下：

- 计算当前可见区域起始数据的 startIndex
- 计算当前可见区域结束数据的 endIndex
- 计算当前可见区域的数据，并渲染到页面中
- 计算 startIndex 对应的数据在整个列表中的偏移位置 startOffset，并设置到列表上
- 计算 endIndex 对应的数据相对于可滚动区域最底部的偏移位置 endOffset，并设置到列表上



### React-virtualized

React components for efficiently rendering large lists and tabular data.



### React-window

`react-window` is a complete rewrite of `react-virtualized`.

focused on making the package **smaller**1 and **faster**.

If `react-window` provides the functionality your project needs, I would strongly recommend using it instead of `react-virtualized`. However if you need features that only `react-virtualized` provides, you have two options:

1. Use `react-virtualized`. (It's still widely used by a lot of successful projects!)
2. Create a component that decorates one of the `react-window` primitives and adds the functionality you need. You may even want to release this component to NPM (as its own, standalone package)! 🙂



### 参考资料

##### [bvaughn/react-virtualized](https://github.com/bvaughn/react-virtualized)

##### [bvaughn/react-window](https://github.com/bvaughn/react-window#how-is-react-window-different-from-react-virtualized)

##### [浅说虚拟列表的实现原理](https://blog.csdn.net/asdf8968/article/details/83183470)

##### [在React项目中，如何优雅的优化长列表 ](https://juejin.cn/post/6844903729460674567#heading-13)

