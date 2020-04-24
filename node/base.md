# 基础


## CommonJS
* 每个js文件都是一个模块
* 模块对外暴露变量：```module.exports = variable;```
* 引用其他模块的变量：```var ref = require('module_name');```

### CommonJS原理
* 模块的隔离：Javascript是函数式编程语言，支持closure。把模块代码扔到一个自执行函数里面，实现封闭作用域/命名空间
* module.exports：Node事先准备一个对象-module（有load方法，返回module.exports）。在加载函数中（load方法）module作为参数传入（在模块内可以使用module，其实是一个函参）。。。。


### module.exports vs exports

* 区别：不能直接对exports赋值
* 原因：


## 原生模块

### 一、网络
#### net
用于TCM服务：
* 传输控制协议，传输层，三次握手（两个套接字形成连接，传输数据）
* a. 发送端：对小数据包有优化策略——Nagle算法（数据可能呗被延迟发送） => socket.setNoDelay(true) 
* b. 接收端：有合并小数据包的策略，因此data的触发与client端的send可能并不是1V1
* Demo:
  * [服务端: try/test01](git@github.com:JessieLee15/FeSaasService.git)
  * [客户端: try/test01](git@github.com:JessieLee15/FeSaasService.git)

#### dgram
用于UDP服务：
* 用户数据包协议，传输层
* 服务端和客户端使用相同（可以理解为对比TCP，TCP是面向链接的，链接一旦建立，在通讯双方中的任何一方主动断开链接之前TCP都会一直保持下去，客户端与另一个TCP服务通信，则需要新建套接字；体现：server.close()方法实际作用是使server停止接受新的套接字连接，但保持当前存在的连接，等待所有连接都断开后，才触发server的close事件）；一个套接字可与多个UDP服务通信
* 不可靠、丢包，无需连接、资源消耗少、快速灵活
* Demo:
  * [服务端: try/test02](git@github.com:JessieLee15/FeSaasService.git)
  * [客户端: try/test02](git@github.com:JessieLee15/FeSaasService.git)

#### http/https
用于HTTP/HTTPS服务：
* 超文本传输协议，构建在TCP之上，属于应用层协议
* node中继承自net模块
* 事件驱动，并不为每个连接创建一个线程
* 使用：
  * res.setHeader()/res.writeHeader():  只有调用writeHeader，报文头才会写入连接
  * res.write()/res.end(): end方法会先调用write发送数据，然后发送信号告知server此次相应结束（此连接将用于下一个请求或关闭）
    * 响应结束时务必关闭连接 - 调用end
    * 延迟调用end: 实现长连接
  * 事件：
* HTTP客户端：http.request() => return http.ClientRequest
* HTTP代理（连接池）：ClientRequest基于TCP，在keep-alive情况下，一个底层会话连接可以用于多次请求；http模块包含一个默认客户端代理对象http.globalAgent用于重用TCP连接，管理每个服务器端（host+port）连接。默认对同一服务器请求连接最多可创建5个

#### WebSocket
* node没有内置的WebSocket库，查看相关社区
* 客户端首先发起HTTP请求（握手，upgrade协议，服务器切换协议，响应客户端）
* 之后数据传输使用WebSocket的数据帧协议