*摘自：https://mp.weixin.qq.com/s/Bf7uVhGiu47uOELjmC5uXQ*

**分布式版本控制 	Git**

每个人都拥有全部的代码！安全隐患！

所有版本信息仓库全部同步到本地的每个用户，这样就可以在本地查看所有版本历史，可以离线在本地提交，只需在连网时push到相应的服务器或其他用户那里。由于每个用户那里保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，但这增加了本地存储空间的占用。
![image-20210812170404639](/home/song/.config/Typora/typora-user-images/image-20210812170404639.png)
不会因为服务器损坏或者网络问题，造成不能工作的情况！

Git是免费、开源的，最初Git是为辅助 Linux 内核开发的，来替代 BitKeeper！**是目前世界上最先进的分布式版本控制系统。**



![image-20210812170404639](/home/song/.config/Typora/typora-user-images/image-20210812170404639.png)

- Workspace：工作区，就是你平时存放项目代码的地方

- Index / Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表的信息

- Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本

- Remote Directory：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

  ![image-20210812170404639](/home/song/.config/Typora/typora-user-images/image-20210812170404639.png)

本地的三个区域确切的说应该是git仓库中HEAD指向的版本：

![图片](https://github.com/Songwxu/Git/blob/main/68747470733a2f2f6d6d62697a2e717069632e636e2f6d6d62697a5f706e672f754a4441554b724743374b737538556c4954774d6c6258336b4d47745a39703069637a365832616962496755577a4878747758386b696350434b70.webp)

- Directory：使用Git管理的一个目录，也就是一个仓库，包含我们的工作空间和Git的管理空间。
- WorkSpace：需要通过Git进行版本控制的目录和文件，这些目录和文件组成了工作空间。
- .git：存放Git管理信息的目录，初始化仓库的时候自动创建。
- Index/Stage：暂存区，或者叫待提交更新区，在提交进入repo之前，我们可以把所有的更新放在暂存区。
- Local Repo：本地仓库，一个存放在本地的版本库；HEAD会只是当前的开发分支（branch）。
- Stash：隐藏，是一个工作状态保存栈，用于保存/恢复WorkSpace中的临时状态。



**操作步骤**

**1 创建/克隆本地仓库**

```
# option(a)在当前目录新建一个Git代码库
$ git init
# 在GitHub/Gitee上创建远程仓库
# git add .   加所有文件到暂存区
$ git commit -m "消息内容"    # 提交暂存区中的内容到本地仓库 -m 提交信息
# 绑定远程仓库
$ git push origin master(或其它分支)
```

```
# option(b)克隆一个项目和它的整个代码历史(版本信息)
$ git clone [url]  # https://gitee.com/kuangstudy/openclass.git
```

**2 看文件状态**

```
#查看指定文件状态
$ git status [filename]
#查看所有文件状态
$ git status
```

**3 忽略文件**

```
#为注释
*.txt        #忽略所有 .txt结尾的文件,这样的话上传就不会被选中！
!lib.txt     #但lib.txt除外
/temp        #仅忽略项目根目录下的TODO文件,不包括其它目录
build/       #忽略build/目录下的所有文件
doc/*.txt    #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

**4 本机绑定SSH公钥，实现免密码登录**

```
# 进入 C:\Users\Administrator\.ssh 目录
# 生成公钥 ssh-keygen
```

**5 Git分支中常用指令：**

```
# 列出所有本地分支
$ git branch
# 列出所有远程分支
$ git branch -r
# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
# 切换分支
$ git checkout [branch-name]
# 新建一个分支，并切换到该分支
$ git checkout -b [branch-name]
# 将分支推到远程仓库
$ git push origin [branch-name]
# 合并指定分支到当前分支
$ git merge [branch-name]
# 删除分支
$ git branch -d [branch-name]
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [delete remote branch]
```



**公钥与私钥：**

**公钥（Public Key）**与**私钥（Private Key）**是通过加密算法得到的一个密钥对（即一个公钥和一个私钥，也就是非对称加密方式）。公钥可对会话进行加密、验证数字签名，只有使用对应的私钥才能解密会话数据，从而保证数据传输的安全性。公钥是密钥对外公开的部分，私钥则是非公开的部分，由用户自行保管。

通过加密算法得到的密钥对可以保证在世界范围内是唯一的。使用密钥对的时候，如果用其中一个密钥加密一段数据，只能使用密钥对中的另一个密钥才能解密数据。例如：用公钥加密的数据必须用对应的私钥才能解密；如果用私钥进行加密也必须使用对应的公钥才能解密，否则将无法成功解密。


一、概述

        Github上边的repositories翻译为代码仓库，可以保存多个代码工程和项目的代码，资源，文本、图片......等;
    
        而projects可以翻译为项目板，是project-boards的简写。简单说，可以理解为工作计划表之类的书签，制定一下工作计划，Bug，流程什么的。
    
        这么看，这很反直觉哇，我还以为projects也是项目什么的，没想到和我印象中的差得很远。。。

二、官方说明

        repositories：仓库就像项目的文件夹。 项目的仓库包含项目的所有文件，并存储每个文件的修订记录。 您也可以在仓库中讨论并管理项目的工作。您可以个人拥有仓库，也可以与组织中的其他人共享仓库的所有权。
    
        projects：GitHub 上的项目板帮助您组织工作和排列工作的优先级。 您可以为特定功能工作、全面的路线图甚至发布检查列表创建项目板。 通过项目板可以灵活地创建适合需求的自定义工作流程。项目板包括议题、拉取请求和注释，在选择的列中分类为卡片。 您可以拖放或使用键盘快捷键对列中的卡片重新排序，在不同列之间移动卡片，以及更改列的顺序。 


​	                                                                                                                      **To be continued ...**
