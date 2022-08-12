---
title: ipad编程软件code的使用方法——特别是git同步问题
date: 2022-08-04 00:02
---
# iPad code app 使用
## 在 ipad 上进行编程可以使用 code APP
![](./_image/2022-08-04/dcfaf148508807e9f910938fad5df399.jpg)    ![](./_image/2022-08-04/a5f7df78156d21d15431953d56fea310.jpg)
    该软件支持 python、javascprits、html、c 等编程语言。
## code 使用过程的一些问题
### 1.新建文件是不可以在命名前文件类型，因为先点选文件类型的话会自动创建 1 个 default 名字的文件。
![](./_image/2022-08-04/df79d555475dda213497811eb8566013.jpg)
### 2.不能使用蓝牙鼠标进行多选，有时可以。
### 3.从 GitHub 克隆文件仓库
    为了能够与 GitHub 进行同步，首先要在 GitHub 建立文件仓库 ，然后将文件仓库克隆到本地。
![](./_image/2022-08-04/a80ec265d879453ed5f1cb593ee00d19.jpg)
    将文件库克隆到本地后，为了能够成功的 commit 、push、fetch，所以要在设置中的版本控制中添加作者身份和凭据。
![](./_image/2022-08-04/18b9385ee85103568e7a09500c30b877.jpg)
    作者身份根据需要自己添加，凭据中添加 GitHub 账号和 GitHub 个人访问令牌。
![](./_image/2022-08-04/02e4de616939cf2e1a902031fb2f560d.jpg)
### 4.code 提交 commit 的问题
![](./_image/2022-08-04/6bbe338fd4db79805d297aaec13c233a.jpg)
    code app 可以通过远吗管理功能将代码上传到 GitHub 进行版本控制。
![](./_image/2022-08-04/949462026ca2bcde596413de1ffcd555.jpg)
    文件发生修改后，在源码管理页面的变更栏中会显示发生变化的文件，此时点击"+"，提交变更，会提示变更已经缓存。这时变更仅在本地缓存，随时可以撤销，要在上边的文本框中输入本次的更改注释，用来解释本次修改了哪些地方。
![](./_image/2022-08-04/cc54940e048b0b170786c8c135d05ca2.jpg)
> 注意 code app 更改注释不可以为空，否层将不能提交缓存。右下角会提示 commit can not be empty.
> ![](./_image/2022-08-04/11fa1489034c4c7d080def0d2212ad18.jpg)
    输入 commit 的注释后点击文本框下边的对号会提示 commit succeed，表示 commit 成功。
### 5.code 的 push 问题
    提交缓存之后点击文本文本框下边的三个点可以看到 push 和 fetch 按钮。
![](./_image/2022-08-04/36751dd242364f9ad4b5fb8bf2473951.jpg)
> 注意如果设置中的凭据设置错误将会提示 too many redirects or authentication replays。
> ![](./_image/2022-08-04/ac147ea526bc2e9f6c24d920589a96cb.jpg)
### 6.code app 的fetch 问题
    为了同步本地和 GitHub 仓库的文件，在更改本地文件前首先使用 fetch 将 GitHub 远端的文件拉到本地。成功后提示 fetch succeed。
![](./_image/2022-08-04/36751dd242364f9ad4b5fb8bf2473951.jpg)
![](./_image/2022-08-04/8584f979a5c0b776e6b416b871c6a395.jpg)
    当成功将文件复制到本地后，长按界面左下角的 master，会弹出 checkout detached 界面。
![](./_image/2022-08-04/273554babb413f682121a5bd471cc033.jpg)
    成功后再次点击 checkout detached 页面的 origin/master 分支就可以了。
![](./_image/2022-08-04/55f4aa38b84029a3626f999f48900986.jpg)