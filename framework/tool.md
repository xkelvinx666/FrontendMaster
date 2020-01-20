# 前端本地构建工具(webpack)

> 仅讨论webpack方案

## 一个入口
使用webpack，要记住一个entry对应一个输出的js，[HTML](https://webpack.docschina.org/plugins/html-webpack-plugin)和[CSS](https://webpack.docschina.org/plugins/mini-css-extract-plugin/)都是根据插件(plugins)配置对js里的信息进行提取使用。

认准入口文件，开始读代码，才能知道代码的执行流程
## 不建议深入学习webpack
webpack只是一个开发构建工具。工欲善其事，必先利其器。学做菜，不必要连，菜刀的制作过程都深入理解。webpack官放自己的文档都写的不清不楚，而且例子都是小案例，在大型web项目中不一定直接照搬。网上有很多已有的打包解决方案，直接使用即可。
## 建议把webpack打成npm包，比初始化模版boilerplate更容易进行维护
1. [nuxt](https://zh.nuxtjs.org)
2. [next](https://nextjs.org)
