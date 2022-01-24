## electron localstorage问题

`electron` 应用之间是通过 `package.json` 中的 `name` 进行区分的，因此如果是复制粘贴的程序而没有修改 `name` 则会使用存储在同一地址中的 `localstorage` ，造成数据变动的问题。

