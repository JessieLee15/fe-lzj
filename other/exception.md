# Exception

如何处理前端异常

### 异常
* JS语法错误、代码异常
* AJAX请求异常
* 静态资源加载异常
* Promise异常
* Iframe异常
* 跨域Script error
* 崩溃和卡顿

### 异常处理

#### 一、Try-Catch
捕获 __同步 运行时__ 错误 （语法和异步捕获不到）

#### 一、window.onerror
当js _运行时_ 错误发生时，window会触发一个ErrorEvent接口的error时间，并执行 `window.onerror()`