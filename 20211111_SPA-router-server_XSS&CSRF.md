### SPA

#### 疑惑：

1. webpack打包生成后的index.html不能跳转路由
2. SPA需要服务器才能正常浏览吗
3. 只需一个静态资源服务器即可浏览，这个服务器的作用是什么
3. 服务器类型、作用、区别



#### 理解：

##### SPA应用路由实现有两种方法：

1. ##### hash模式
   
   - 使用location.hash和hashchange事件实现路由
2. ##### history模式
   
   - 使用html5的history api实现，主要就是popState事件等



hash模式进行路由可以直接使用file://的方式打开页面



如果直接使用file://的方式打开页面，就会出现下面的情况

```javascript
Uncaught SecurityError: A history state object with URL 'file:///C:/xxx/xxx/xxx/xxx.html' cannot be created in a document with origin 'null'.
```

因为pushState的url和当前的Url必须是同源的，而file://的形式是不存在同源的说法的，所以我们必须用http://localhost的方式，可使用本地服务器进行测试



#### 参考资料

##### [SPA路由核心原理](https://zhuanlan.zhihu.com/p/296769602)

##### [单页面应用路由的两种实现方式 ](https://www.cnblogs.com/zhuzhenwei918/p/7421430.html)

##### [单页应用程序相关问题](https://www.5axxw.com/questions/content/3cw9ad)

> 单页应用程序需要一个服务器来服务它所需的`.css`、`index.html`和`.js`文件。SPA完全不需要通过任何方式与应用服务器通信。
>
> 你的内容可以是静态的，也可以是应用程序自己生成的。如果您需要与后端服务器通信，您可以通过http、https、websockets或服务器端事件等协议上的某种api使用它。
>
> 总结一下。SPA可以是完全独立的，也可以访问api来提供功能。一个独立的应用程序只需要一个服务器来提供应用程序本身的组件文件(.css、.js、.html）。





### XSS & CSRF

##### XSS

- XSS，即 Cross Site Script，中译是跨站脚本攻击；其原本缩写是 CSS，但为了和层叠样式表(Cascading Style Sheet)有所区分，因而在安全领域叫做 XSS。
- XSS攻击可以分为3类：
  - 反射型（非持久型）
  - 存储型（持久型）
  - 基于DOM。
- XSS攻击的防范
  - HttpOnly 防止劫取 Cookie
  - 输入检查
  - 输出检查

##### CSRF

- CSRF，即 Cross Site Request Forgery，中译是跨站请求伪造，是一种劫持受信任用户向服务器发送非预期请求的攻击方式。
- 通常情况下，CSRF 攻击是攻击者借助受害者的 Cookie 骗取服务器的信任，可以在受害者毫不知情的情况下以受害者名义伪造请求发送给受攻击服务器，从而在并未授权的情况下执行在权限保护之下的操作。
- CSRF 攻击的防范
  - 验证码
  - Referer Check
    - 根据 HTTP 协议，在 HTTP 头中有一个字段叫 Referer，它记录了该 HTTP 请求的来源地址。通过 Referer Check，可以检查请求是否来自合法的”源”
  - 添加 token 验证(token==令牌)

