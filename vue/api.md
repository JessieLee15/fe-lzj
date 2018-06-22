# Vue.API  -资源来自[官方API](https://vuejs.org/v2/guide)及[Vue源码](https://github.com/vuejs/vue "git仓库")

### Plugins
给Vue添加的全局性的功能/方法/模块（methods、properties、directives/filters/transitions、component options - mixin、 Vue instance methods、library）

虽然官方没说 a plugin is an obj，但是感觉此处理解应该是obj

* a plugin应该满足的条件：必须对外暴露一个install方法
    * install方法入参：1.Vue constructor; 2.自定义参数
* 调用plugin：`Vue.use(plugin)`，据说会自动识别多次调用，保证每个plugin只会注册一次


---

## Global API

### Vue.use
官方解释：用于安装一个plugin

此处的plugin有两种模式：
* Object：必须包含一个对外暴露的install方法
* function：会被直接当成install方法

### Vue.directive
官方解释：注册或重写一个全局指令（Vue的）

入参：1.(string) id 2.(function | object) definition

### Vue.mixin
