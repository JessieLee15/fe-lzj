# iframe

X-Frame-Options是一个相应头，主要是描述服务器的网页资源的iframe权限。目前的支持度是IE8+(已经很好了啊喂)有3个选项:
  * DENY：当前页面不能被嵌套iframe里，即便是在相同域名的页面中嵌套也不允许,也不允许网页中有嵌套iframe
  * SAMEORIGIN：iframe页面的地址只能为同源域名下的页面
  * ALLOW-FROM：可以在指定的origin url的iframe中加载

  ```js
    if (top.location.hostname != window.location.hostname) { 
    　　　　top.location.href = window.location.href;
    }

  ```

对于第二种方式的跨域（主域相同而子域不同）,可以使用iframe进行解决。
在两个不同子域下(某一方使用iframe嵌套在另一方)，
即:
http: //www.foo.com/a.html和http: //script.foo.com/b.html
两个文件中分别加上document.domain = ‘foo.com’,指定相同的主域，然后,两个文档就可以进行交互。
```js
document.domain = 'foo.com';
```

如果你设置的iframe的域名和你top window的域名完全不同。 则可以使用CDM(cross document messaging)进行跨域消息的传递。该API的兼容性较好 ie8+都支持.
发送消息: 使用postmessage方法
接受消息: 监听message事件