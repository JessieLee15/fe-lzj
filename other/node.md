# node中后台方案

Node.js运行原理、高并发性能测试对比及生态圈汇总： https://segmentfault.com/a/1190000019425388?utm_source=tag-newest

思路参考：
关于nodejs作为系统中间件的理解: https://blog.csdn.net/qq_27965129/article/details/78766313
https://zhuanlan.zhihu.com/p/30384677


## 框架选择

node.js之十大Web框架： https://www.cnblogs.com/youcong/p/10503099.html

### sail.js ::: 基于express
免费 官方提供收费维护

不推荐：：：文档太少 只有官网（英文）

https://blog.csdn.net/wuqingdeqing/article/details/84678926

### sail.js


## 搭建流程

### express ：：：强大的 基础的 灵活的 web框架

http://www.360doc.com/content/18/0422/07/32517277_747703104.shtml
NodeJS+express如何新建一个自己需要的项目： https://blog.csdn.net/qq_38209578/article/details/82593591
nodejs+express搭建服务器：https://www.cnblogs.com/wgl0126/p/9290157.html
这里推荐一个热部署加载node工具–supervisor



## 部署
测试服 

服务器 性能监控、自动重启、负载均衡

端口 冲突？ ：：： 安装并配置 Nginx 的 upstream，端口的映射转发给后台的 Nodejs 服务，实现服务的识别和转发。

利用Pm2部署Node服务

Nodejs项目服务器部署： https://blog.csdn.net/u014465934/article/details/83663407
从原理上理解NodeJS的适用场景： https://www.cnblogs.com/kevin9103/p/5053517.html
node项目架构与优化： https://www.cnblogs.com/139199228-haicao/p/9193753.html


## express Routes

Nodejs express 框架之 路由与中间件: https://www.rokub.com/7066.html
Express路由和中间件: https://www.cnblogs.com/xuxiaozhi/p/7976107.html



html-webpack-plugin


https://tech.meituan.com/2018/09/06/fe-tiny-spa.html



# API设计

## 需求：
1. 响应格式的数据：适应不同屏幕 【聚合、裁剪、适配】


中台构想：
集成API
二次处理接口数据
接口可视化编辑