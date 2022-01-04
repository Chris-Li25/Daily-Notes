### ES2020

#### Null判断运算符 ??

只有运算符左侧的值为`null`或`undefined`时，才会返回右侧的值

```js
false ?? 'test'		false
undefined ?? 'test' 'test'
null ?? 'test' 		'test'
```



### async/await的异常处理



async 声明的函数一定会返回Promise 会包一层

