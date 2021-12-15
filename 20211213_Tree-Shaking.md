### Tree-Shaking

![img](./img/2021121301.awebp)

上图形象的解释了Tree-shaking 的本意

本文所说的前端中的tree-shaking可以理解为通过工具"摇"我们的JS文件

将其中用不到的代码"摇"掉，是一个性能优化的范畴。

具体来说，在 webpack 项目中，有一个入口文件，相当于一棵树的主干，入口文件有很多依赖的模块，相当于树枝。实际情况中，虽然依赖了某个模块，但其实只使用其中的某些功能。

通过 tree-shaking，将没有使用的模块摇掉，这样来达到删除无用代码的目的。



### 原理

Tree-shaking的本质是消除无用的js代码。

无用代码消除在广泛存在于传统的编程语言编译器中，编译器可以判断出某些代码根本不影响输出，然后消除这些代码，这个称之为DCE（dead code elimination）。



##### DCE（dead code elimination）

Dead Code 一般具有以下几个特征

- 代码不会被执行，不可到达
- 代码执行的结果不会被用到
- 代码只会影响死变量（只写不读）



传统编译型的语言中，都是由编译器将Dead Code从AST（抽象语法树）中删除。

javascript中是由代码压缩优化工具uglify完成javascript的DCE



## 参考资料

[Tree-Shaking性能优化实践 - 原理篇 ](https://juejin.cn/post/6844903544756109319)