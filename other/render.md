# BS Render - BS 架构中的渲染/加载/解析那些事儿

> 模版引擎 （Node:Nunjucks VS Browser:MVVM）    渲染时间、地点及效率

> 三大MVVM框架的渲染/加载/解析， 传说中的react的服务器渲染

> 顺带说说js怎么跑起来的(尼玛Java还需要JVM呢)： 为什么在服务器也能跑？ 端这边就不说了，肯定是有中间层的（Browser, wechat, webview/uiwebview,wkwebview）

> 再顺带说说请求这个事儿：静态资源,动态资源； GET,POST; HTTP请求结构(请求的解析) https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432011939547478fd5482deb47b08716557cc99764e0000

> 再顺带说说BS和CS开发中使用请求（HTTP为例）有啥区别？为啥会有这些差异？

* 在生产环境下，静态资源是由部署在最前面的代理服务器（如Nginx）处理的，Node程序不需要处理静态文件。而在开发环境
  1. 可由koa处理（需要手动写处理程序）
  2. 手动配置一个反向代理服务器（项目复杂了）