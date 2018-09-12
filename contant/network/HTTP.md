# HTTP

* 超文本传输协议 Hypertext Transfer Protocol 

* 无状态（ stateless ）的协议

* 资源：动态&静态 URL（统一资源定位地址） 静态：css、js、html 动态：实际指向一段代码入口，经服务器运算，返回资源

* GET与POST:是否携带负载数据（payload） get携带数据（解码：encodeURIComponent()）

* 请求头
Referer(发出请求的页面URL，实为Referrer)

* 响应：响应头 响应主体

### 会话
* 这里的会话一般指客户端和服务器保持关联的这段时间，这个关联依靠服务器端的session（通过sessionID认证）

* 会话劫持 （攻击者拿到sessionID,拥有词用户的权限）

* https （加密请求与响应）

### 安全
* XSS (Cross-site scripting)
* CSRF (Cross-site request forgery)

### HTTP2