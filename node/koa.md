# KOA

#### koa-bodyparser 中间件
* 功能：获取post请求的参数
* 实现原理：（内部是一个Promise处理）
  1. 通过原生的 nodejs 请求对象 req
  2. 监听req的开始与结束中间的过程，累加接收到的请求数据
  3. req结束的时候将所有数据解析为json（query提取，解码）
  4. 将参数挂到ctx.request.body

#### app.on('error', fn)
* 监听app内的代码运行异常，出现异常会触发
* 注意：被try catch捕获的异常不会触发此事件，需要手动释放（触发）：`ctx.app.emit()`
* 处理异常建议：使用中间件统一处理

#### koa中返回异常
* statusCode：http层级的异常。下面两种方式都能实现这一效果
  1. `ctx.throw(500);`
  2. `ctx.response.status = 404; ctx.response.body = 'Page Not Found';`（express时下404很巧妙：res默认返回就是404）



