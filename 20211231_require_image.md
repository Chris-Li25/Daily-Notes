## JS引用

需要一次引入多个模块或图片时可以用 require.context

### require.context

#### 三个参数

1. `directory {String}` -读取文件的路径
2. `useSubdirectories {Boolean}` -是否遍历文件的子目录
3. `regExp {RegExp}` -匹配文件的正则

#### 语法: 

```
require.context(directory, useSubdirectories = false, regExp = /^.//);
```

### require.context函数执行后返回的是**一个函数**

#### **这个函数有3个属性**

1. `resolve {Function}` -接受一个参数request,request为test文件夹下面匹配文件的相对路径,返回这个匹配文件相对于整个工程的相对路径
2. `keys {Function}` -返回匹配成功模块的名字组成的数组
3. `id {String}` -执行环境的id,返回的是一个字符串,主要用在module.hot.accept,应该是热加载?

require.context返回的函数接受参数 **文件的相对路径**（也就是keys返回的内容） 时返回对应的模块对象



```javascript
const requireContext = require.context("./images", true, /^\.\/.*\.png$/);
const images = requireContext.keys().map(requireContext);
```

上述代码可以读取对应文件夹中所有图片



## 参考资料

[使用require.context实现前端工程自动化](https://www.jianshu.com/p/c894ea00dfec)

[react中引入大量图片](https://blog.csdn.net/qq_39081974/article/details/93044916)

