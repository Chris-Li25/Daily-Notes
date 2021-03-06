# Module Format

### CJS

CommonJS，只能在 NodeJS 上运行，使用 `require("module")` 读取并加载模块。

缺点：不支持浏览器，执行后才能拿到依赖信息，由于用户可以动态 require（例如 [react 根据开发和生产环境导出不同代码](https://link.zhihu.com/?target=https%3A//cdn.jsdelivr.net/npm/react%4017.0.1/index.js) 的写法），无法做到提前分析依赖以及 [Tree-Shaking](https://link.zhihu.com/?target=https%3A//rollupjs.org/guide/zh/%23tree-shaking) 。

### AMD

Asynchronous Module Definition，可以看作 CJS 的异步版本，制定了一套规则使模块可以被异步 require 进来并在回调函数里继续使用，然后 require.js 等前端库也可以利用这个规则加载代码了，目前已经是时代的眼泪了。

### UMD

Universal Module Definition，同时兼容 CJS 和 AMD，并且支持直接在前端用 `<script src="lib.umd.js"></script>` 的方式加载。现在还在广泛使用，不过可以想象 ESM 和 IIFE 逐渐代替它。

### IIFE

[Immediately Invoked Function Expression](https://link.zhihu.com/?target=https%3A//developer.mozilla.org/en-US/docs/Glossary/IIFE)，只是一种写法，可以隐藏一些局部变量，前端人要是不懂这个可能学的是假前端。可以用来代替 UMD 作为纯粹给前端使用的写法。

### ESM

ECMAScript Module，现在使用的模块方案，使用 `import` `export` 来管理依赖。由于它们只能写在所有表达式外面，所以打包器可以轻易做到分析依赖以及 Tree-Shaking。当然他也支持动态加载（`import()`）。

浏览器直接通过 `<script type="module">` 即可使用该写法。NodeJS 可以通过使用 mjs 后缀或者在 package.json 添加 `"type": "module"` 来使用，注意他还有一些 [实验性的功能](https://link.zhihu.com/?target=https%3A//nodejs.org/api/esm.html%23esm_experimental_json_modules) 没有正式开启。考虑到大量 cjs 库没有支持，如果要发布 esm 版的库还是通过 rollup 打包一下比较好（同时相关依赖可以放到 devDependencies 里）。



# DDoS

**Distributed denial of service attack  分布式拒绝服务攻击**

分布式拒绝服务攻击可以使很多的计算机在同一时间遭受到攻击，使攻击的目标无法正常使用，分布式拒绝服务攻击已经出现了很多次，导致很多的大型网站都出现了无法进行操作的情况，这样不仅仅会影响用户的正常使用，同时造成的经济损失也是非常巨大的



# 参考资料

[cjs, umd, esm or iife?](https://zhuanlan.zhihu.com/p/304552279)