# 使用 vspicgo 插件在vscode中快速插图

首先明确一个概念，`Picgo`是一个独立的app，提供快速上传图片到图床的功能。而`vspicgo`是`Picgo`的
在vscode的插件。所以，暂时来说，`vspicgo`只是相当于在vscode里调用`Picgo`的小脚本。所以需要下载`Picgo`。
这个问题其实在`vspicgo`的简介里有提到
> which are supported by PicGo-Core.

## 安装
### 安装 PicGo-Gore
`Picgo`是一个app，而`PicGo-Core`是这个app的底层核心。由于比较喜好简介版本，所以不想下载整个app。
于是，我兴高采烈的下载了[PicGo-Core](https://github.com/PicGo/PicGo-Core)。在电脑安装有`npm`的情况下
#### Global install
```shell
npm install picgo -g

# or

yarn global add picgo
```

#### Local install
```shell
npm install picgo -D

# or

yarn add picgo -D
```

安装结束后，现在仅仅得到的是`Picgo`功能部分的核心。(是不是特别 ~~傻~~ 干净)

运行一下看看
```shell
picgo -v #看版本
picgo -h #看帮助手册
```
---
#### 题外话
`Picgo`的默认图床是`smms`，到此为止，正常来说，使用普通的上传图床功能应该是没有问题的，于是我快乐的截了图(推荐`snipaste`)，并复制到的剪切板。然后命令行上传！(干净！)
```shell 
picgo upload
[PicGo INFO]: Before transform
[PicGo INFO]: Transforming...
[PicGo INFO]: Before upload
[PicGo INFO]: Uploading...
[PicGo WARN]: failed
[PicGo ERROR]: Error: API v1 is deprecated, please refer to https://doc.sm.ms/ for v2 API documentation.
```
你会发现这么一个问题。大概是说，`smms`的API v1不能用了。（题外：我的第一反应是，可能要配置一些调用API的设置，于是点进去给的链接唰唰唰的看，去`PicGo-Core`的文档看怎么配置设置。看得我头昏脑胀没有收获。这是弯路，只是想吐槽！）  
最终最终！我依旧不知道需要怎么解决的时候。已经打算妥协去下载app版本了，打开了`Picgo`的主页看见：![20200226175931.png](https://i.loli.net/2020/02/26/Y3Hc95XxL6ZUrhD.png) 

我的表情：  
@import "https://i.loli.net/2020/02/26/JwHIRmpexoXdfPF.png" {width="200px" height="180px" title="我"}  

好吧！那我打开了`smms-user`插件的[主页](https://github.com/xlzy520/picgo-plugin-smms-user)，只要设置一个`Authorization`参数，就能正常使用啦。作者真厉害！点赞！还告诉我去`SM.MS`[官网](https://sm.ms)注册一个账号，然后点击[这里](https://sm.ms/home/apitoken)，进入自己账号的管理界面。生成一个`Secret Token`，然后把这串神秘代码设置成`Authorization`参数就可以啦。![20200226181501.png](https://i.loli.net/2020/02/26/IhsKAaGp7T4YlOq.png)

那我们愉快的安装把！
![20200226181930.png](https://i.loli.net/2020/02/26/mV4K79CrYOFPueS.png)  
当我选择Core版本的时候，这注定不是一帆风顺的路。如果你留意到输入`picgo -h`之后返回的结果，就有可能发现Core也能用搜索功能安装插件。  

---

### 安装 smms-user
命令行走你
```shell 
picgo install smms-user
```
:ok:

## 配置 PicGo-Core

我们安装完`smms-user`就是需要配置它，配置那个厉害的`Authorization`属性。在`PigGo-Core`的[文档](https://picgo.github.io/PicGo-Core-Doc/zh/guide/)里面说了配置文件存放在什么地方：![20200226182820.png](https://i.loli.net/2020/02/26/akosHw4UI3NDYQn.png)
打开配置文件应该看到大概是这样的配置：
```json
{
  "picBed": {
    "current": "smms"
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true
  }
}
```
建议你看着的同时打开`PigGo-Core`的文档看一看，能发现`picBed`是一个指定`uploader`的选项。`uploader`的概念就是一个上传器。按理解可知我们要用`smms-user`这个上传器。顺便把`current`改成`uploader`舒服些
```json
{
  "picBed": {
    "uploader": "smms-user"
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true
  }
}
```

好的选中了这个之后，直接上传是不行的（我试了），还记得需要配置`Authorization`吗？
找找文档，可以看到官方文档介绍如何给插件设置配置![20200226183559.png](https://i.loli.net/2020/02/26/Hd4x8v7uGM3NZLS.png)

你品品，你细细的品，这段话是什么意思？

---
#### 题外
我品出来的设置是这样的
```json
{
  "picBed": {
    "uploader": "smms-user"
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true
  },
  "picgo-plugin-xxx":{
      "config": ""
  }
}
```

于是我写了
```json
{
  "picBed": {
    "uploader": "smms-user"
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true
  },
  "picgo-plugin-smms-user":{
      "Authorization": "神秘代码"
  }
}
```

这样的结果是告诉我
```shell 
[PicGo ERROR]: Error: Can't find uploader config
```

呵呵哒，最终你猜怎么着？  
我在`smms-user`的源代码里面翻，找到这么一段：  
![20200226195530.png](https://i.loli.net/2020/02/26/x4w8PcbB9lRUVdS.png)


---

直觉告诉我，配置文件应该这样加入神秘代码的配置
```json
{
  "picBed": {
    "uploader": "smms-user",
    "smms-user":{
        "Authorization": "神秘代码"
    }
  },
  "picgoPlugins": {
    "picgo-plugin-smms-user": true
  }
}
```

终于，正确了。现在能使用`PicGo-Core`上传图片了！
```shell
picgo upload
```

最终还差一步，就是弄好`vspicgo`。

去`vscode`扩展搜`vspicgo`安装好之后进入设置，找到`Config Path`，把`PigGo-Core`的配置文件路径填好就行啦～
![20200226201627.png](https://i.loli.net/2020/02/26/2XPUmxnA7Iw9gvt.png)

又看文档又装插件又翻源码可终于把它弄完了。

现在就能享受用vs码字的时候按`option+cmd+u`就可以直接把剪切板的图片上传`SM.MS`并且在光标处生成链接。:smile: