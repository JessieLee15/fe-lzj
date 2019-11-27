# 基础



* 目录 ～, /, /home的差异
  * /： 最高级 根目录 （所有用户共享）
  * ～： 当前用户的home目录 【/root或/root/home/[username]】
  * /home：所有普通用户的父目录


## 常用指令
* `netstat -tlnp` 查看端口占用情况 
* `scp -r 本地文件夹路径 root@服务器ip:/服务器文件夹` 上传文件
* `ln -s 源目录 目标目录` 软连接


  ### aliyun server
  #### nginx指令：（软连接已创建，任何地方可直接使用 `nginx`）
  `ln -s /usr/local/nginx/sbin/nginx /usr/local/bin/nginx`
  * 启动： `/usr/local/nginx/sbin/nginx`
  * 重启： `/usr/local/nginx/sbin/nginx -s reload`
  * 停止： `/usr/local/nginx/sbin/nginx -s stop`
  * 测试配置文件是否正常： `/usr/local/nginx/sbin/nginx -t`
  * 强制关闭： `pkill nginx`

  * 配置文件： `/usr/local/nginx/conf/nginx.conf`

  #### node
  * /root/node-v6.9.5-linux-x64 下装了一个系统版本
  * nvm已就绪 后续直接用nvm管理

  #### pm2
  * `pm2 ls` 查看服务
  * 启动服务`pm2 start <script_file|config_file> [options]`
    * `pm2 start app.js --name app`       启动app.js应用， 设置name
    * `pm2 start app.sh --watch`      脚本启动，监听模式启动，当文件发生变化，自动重启
    * `pm2 start app.js -i max`      启用群集模式（自动负载均衡）max 表示PM2将自动检测可用CPU的数量并运行尽可能多的进程，max可以自定义
    * `2pm2-dev start ...`      开发模式启动，即不启用后台运行
  * `pm2 show <appName> [options]` 显示指定应用详情
  * `pm2 stop <appName> [options]` 停止指定应用
    * `pm2 stop all`        停止所有应用
  * `pm2 reload|restart <appName> [options]` 重启指定应用
    * `pm2 gracefulReload all`  //以群集模式重新加载所有应用程序
  * `pm2 delete <appName> [options]` 删除指定应用 (_如果修改了应用配置行为，需要先删除应用，重新启动后方才会生效_)
  * `pm2 kill` 杀掉pm2管理的所有进程
  * `pm2 logs <appName>` 查看指定应用的日志，即标准输出和标准错误
  * `pm2 monit` 监控各个应用进程cpu和memory使用情况


  #### docker【后期学习了解后使用】
  * docker docker-compose 均已安装 docker-compose软连接已设置
  * /usr/local/bin/docker-compose


  #### 端口使用
  * 80：不晓得被啥占用 
  * 8090：ss代理
  * 3000: nginx demo 
  * 6000: node demo

  