# 前后端开发独立
## 前端不必本地运行后端代码
### 线上环境拦截静态资源进行开发
1. 下载SwitchOmega或类似URL代理拦截软件(charles)
2. 配置该URL正则表达式拦截静态资源
    ```    
    # 后端相关api请求不拦截
    ^http://www.xxx.com((?!api).)*$
    ```
3. 拦截资源指向本地node资源服务器(webpack)
4. [http-proxy-middleware增加配置](https://github.com/chimurai/http-proxy-middleware#examplei)
需要在router里添加一项，将线上域名替换为本机webpack地址

### 只针对接口负责，前端利用mock.js模拟接口情况

TODO:待补充

### 只针对接口负责，通过接口测试

TODO:待补充
