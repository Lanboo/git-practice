# Git操作——入门级操作

[Git的起源](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137402760310626208b4f695940a49e5348b689d095fc000)




#####git 各个操作流转图
![](https://img-blog.csdn.net/20170423160307093)

[git入门](https://blog.csdn.net/zy00000000001/article/details/70505150)


## 1、练习
### 1.1、准备工作
1、在Server上创建仓库，比如这里的git-practice
2、在本地某目录下创建git-practice文件夹
3、在git-practice文件夹，右键-Git Bash Here

![右键-Git Bash Here](https://github.com/Lanboo/git-practice/blob/master/resource/res1.png)
### 1.2、`git init`命令
> 将当前目录创建成新的本地仓库



敲入`git init`

### 1.3、`git remote add origin`命令
> 将当前的本地仓库与Server端的仓库创建连接
```
git remote add origin git@github.com:Lanboo/git-practice.git
// 其中git@github.com:Lanboo/git-practice.git是Server端某个仓库的SSH
```
### 1.4、创建`gitTemp.txt`文件
方式一：鼠标创建（编辑一下，随便写点东西）
方式二：利用linux命令创建
```
touch gitTemp.txt
vi gitTemp.txt
```
[touch命令](https://blog.csdn.net/tanga842428/article/details/52856864)

[vi命令](http://man.linuxde.net/vi)
### 1.5、`git add`
>会将文件放到暂存区
``` git
git add gitTemp.txt
```
[git add 命令](https://www.cnblogs.com/skura23/p/5859243.html)
##### Git Version 1.x
![](http://i.stack.imgur.com/YfLUZ.jpg)
##### Git Version 2.x
![](http://i.stack.imgur.com/KwOLu.jpg)

`add`后的文件，状态`git status`将会进入`unstage`
`commit`后会进入本地仓库
`push`后会同步到Server端

### 1.6、`git commit`
> `commit`会将`add`的文件放到本地仓库
```
git commit -m 'message'   // message是注释内容、log日志
```

### 1.7、`git push`
> 提交至Server端
```
git push origin master
```


## 2、其他命令
### `git config --list`
> 查看本地仓库的配置

另外`git config`查看config的相关命令

### `git status`
> 查看本地仓库的状态

没事就`git status`

### `git clone`
> 将Server端的某仓库克隆到本地

[git clone命令详解](https://blog.csdn.net/zmzwll1314/article/details/53161958)
```
// 将项目克隆到当前文件夹
git clone xxx.git
// 克隆到指定目录
git clone xxx.git "指定目录"
// clone时创建新的分支替代默认Origin HEAD（master）
git clone -b [new_branch_name]  xxx.git
```
### `git branch`
> 一般用于分支的操作，比如创建分支，查看分支等等
> 一般和`git checkout`一起使用
> [git branch 和 git checkout](https://www.cnblogs.com/qianqiannian/p/6011404.html)
```
git branch  //不带参数：列出本地已经存在的分支，并且在当前分支的前面用"*"标记
git branch -r  //查看远程版本库分支列表
git branch -a  //查看所有分支列表，包括本地和远程
git branch dev  //创建名为dev的分支，创建分支时需要是最新的环境，创建分支但依然停留在当前分支
git branch -d dev  //删除dev分支，如果在分支中有一些未merge的提交，那么会删除分支失败
git branch -D dev  //强制删除dev分支
git branch -vv   //可以查看本地分支对应的远程分支
git branch -m oldName newName //给分支重命名
```



### `git checkout`
> a、操作文件  b、操作分支
> 一般和`git branch`一起使用
> [git branch 和 git checkout](https://www.cnblogs.com/qianqiannian/p/6011404.html)
```
//操作文件
git checkout filename  //放弃单个文件的修改
git checkout .  //放弃当前目录下的修改

//操作分支
git checkout master  //将分支切换到master
git checkout -b master  //如果分支存在则只切换分支，若不存在则创建并切换到master分支
                        //repo start是对git checkout -b这个命令的封装，将所有仓库的分支都切换到master，master是分支名

//查看帮助
git checkout --help
git checkout -h
```


## 异常

### `Warning: Permanently added the RSA host key for IP address '13.250.177.223' to the list of known hosts.git@github.com: Permission denied (publickey).fatal: Could not read from remote repository.`

解决：https://www.cnblogs.com/qcwblog/p/5709720.html