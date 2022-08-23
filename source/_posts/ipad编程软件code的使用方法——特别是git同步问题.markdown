---
title: ipad编程软件code的使用方法——特别是git同步问题
date: '2022-08-04 00:02'
abbrlink: 34694
---
# iPad code app 使用
## 在 ipad 上进行编程可以使用 code APP
![IMG_0216.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb08bad3c8.png)    
![IMG_0217.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb3006912b.png)
    该软件支持 python、javascprits、html、c 等编程语言。
## code 使用过程的一些问题
### 1.新建文件是不可以在命名前文件类型，因为先点选文件类型的话会自动创建 1 个 default 名字的文件。
![IMG_0218.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb31c9520e.png)
### 2.不能使用蓝牙鼠标进行多选，有时可以。
### 3.从 GitHub 克隆文件仓库
    为了能够与 GitHub 进行同步，首先要在 GitHub 建立文件仓库 ，然后将文件仓库克隆到本地。
![IMG_0233.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb37872c77.png)
    将文件库克隆到本地后，为了能够成功的 commit 、push、fetch，所以要在设置中的版本控制中添加作者身份和凭据。
![IMG_0232.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb39c3378d.png)
    作者身份根据需要自己添加，凭据中添加 GitHub 账号和 GitHub 个人访问令牌。
![IMG_0231.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb3bc366b3.png)
### 4.code 提交 commit 的问题
![IMG_0234.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb3dc97699.png)
    code app 可以通过远吗管理功能将代码上传到 GitHub 进行版本控制。
![IMG_0221.png](http://ezblog.gnway.cc/i/2022/08/17/62fcba697489f.png)
    文件发生修改后，在源码管理页面的变更栏中会显示发生变化的文件，此时点击"+"，提交变更，会提示变更已经缓存。这时变更仅在本地缓存，随时可以撤销，要在上边的文本框中输入本次的更改注释，用来解释本次修改了哪些地方。
![IMG_0221.png](http://ezblog.gnway.cc/i/2022/08/17/62fcba697489f.png)
> 注意 code app 更改注释不可以为空，否层将不能提交缓存。右下角会提示 commit can not be empty.
> ![IMG_0222.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbe7d8e683.png)
    输入 commit 的注释后点击文本框下边的对号会提示 commit succeed，表示 commit 成功。
### 5.code 的 push 问题
    提交缓存之后点击文本文本框下边的三个点可以看到 push 和 fetch 按钮。
![IMG_0224.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbe9dbeea8.png)
> 注意如果设置中的凭据设置错误将会提示 too many redirects or authentication replays。
![IMG_0229.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbecebd738.png)
### 6.code app 的fetch 问题
    为了同步本地和 GitHub 仓库的文件，在更改本地文件前首先使用 fetch 将 GitHub 远端的文件拉到本地。成功后提示 fetch succeed。
![IMG_0224.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbe9dbeea8.png)
![IMG_0226.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbf14966fb.png)
    当成功将文件复制到本地后，长按界面左下角的 master，会弹出 checkout detached 界面。
![IMG_0234.png](http://ezblog.gnway.cc/i/2022/08/17/62fcb3dc97699.png)
    成功后再次点击 checkout detached 页面的 origin/master 分支就可以了。
![IMG_0228.png](http://ezblog.gnway.cc/i/2022/08/17/62fcbf7b8cd44.png)