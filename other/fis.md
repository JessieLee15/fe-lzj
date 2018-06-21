
## FIS
### server：
    fis server start
    fis server stop
    fis server open

### fis release

默认目录：~/.fis-tmp

#### 参数：
    --optimize / -o

资源压缩，仅仅是压缩！！！去空格及换行符啥的


    --md5 / -m

为静态资源加版本号，类似于时间戳啦～（以前手动在引入文件后面手动加过?time=20170619这种时间戳的🙋）

    --pack / -p

资源合并（依赖fis-postpackager-simple插件打包）安装插件、fis_conf中配置打包规则并开启插件
也可开启自动合并

    --omp

---

## FIS3
> 项目根目录：FIS3 配置文件（默认fis-conf.js）所在的目录为项目根目录。

### 特点
1.资源定位：就是构建的时候会替换资源URL为绝对URL；这样开发就不需要关心外部路径，构建后的程序可移植性强

2.

### server：
    fis3 server start
    fis3 server stop
    fis3 server open

### fis3 release
默认目录：~/.fis3-tmp

#### 参数：

### fis-conf
1.

    fis.match(selector, props); //后面覆盖前面，属性追加

    useHash: true   //添加 md5 戳
    optimizer:  //压缩

2.

    fis.media() //多种状态功能，比如有些配置是仅供开发环境下使用，有些则是仅供生产环境使用的。

3.

    fis3 inspect <media>    // 查看特定 media 的分配情况


### 发布远端
FIS3 默认支持使用 HTTP 上传代码，首先需要在测试机部署上传接收脚本（或者服务）



---

## FISP


[^N2018-06-19]: 宠辱不惊，闲看庭前花开花落；去留无意，漫随天外云卷云舒。