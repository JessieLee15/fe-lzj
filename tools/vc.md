# VC

## preview功能
1.这个功能叫preview。。。（对于不熟悉的人来讲真的是画蛇添足的事儿。。。）

我不说你一定不会发现：preview的文件tab上显示的文件名是斜体！！！真正open的文件不是！！！

2.解决：

  a.”workbench.editor.enablePreview": false, 

  b.要把当前的preview文件变成open：双击tab上的文件名或者edit->save
  
## VC插件Local History使用说明：
一直怀念IntelliJ的系列IDE的强大及良好体验～

发现其中特别实用的Local History功能在VC中也有插件～开心

但是发现用起来有点坑：

1.默认本地缓存路径在各项目目录下，.history文件夹下，当然也可以更改这个设置：

```json
// Specify a location for .history folder (null: use workspaceFolder)
"local-history.path": “${workspaceFolder}”
```

2.我还是建议放在默认位置，单个项目，便于自己手动管理缓存，因此要修改两个地方：

  a. gitignore必然的

  b.VC的全局搜索，这个不设置一搜索就要炸了。。。

 ```json
  // 配置 glob 模式以在搜索中排除文件和文件夹。例如，文件资源管理器根据此设置决定文件或文件夹的显示和隐藏。
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/dist": true,
    "**/.git": true,
    "**/.history": true
  },
  ```