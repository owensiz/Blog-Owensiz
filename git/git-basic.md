# 1 git基础

>参考 https://time.geekbang.org/course/intro/145

## 1-1 git 官网和安装

- git官网: https://git-scm.com/

- git文档，可选语言，简体中文：https://git-scm.com/book/zh/v2

- git安装，官网下载，使用以下命令在终端来检查安装是否成功。
```
git --version
``` 

## 1-2 准备：使用git的最小配置
### 配置user信息： name & email
```
git config --global user.name 'owensiz'
git config --global user.email 'owensiz@qq.com'
```
每次code变更会带上user信息，做code review也更清晰。

### git config的三个作用域
```
git config --global // 全局生效；常用
git config --local // 对某一仓库生效；缺省时，默认为local
git config --system // 对系统所有登录用户生效；基本不用
```

### 查看git config
> git config --list (--global/--local/--system)




## 1-3 创建git仓库

### 两种建库场景
- 已有项目纳入git管理

```
cd myProj
git init
```

- 新建项目并用git管理
```
cd myFolder
git init myProj
cd myProj
```


## 1-4 git commit & 工作区和暂存区
```
👀git add/rm myFile // add与rm
git commit -u 
// u表示update，对已经纳入git管理且被update的文件进行commit

```


## 1-5 git与重命名

- 普通方式是直接在工作区重命名，正常提交。git status仍能识别为renamed。
- 👀重命名命令：git mv myFile.js myNewFile.js
- git reset --hard （无后缀）用于恢复当前工作区和暂存区，当前所有的变更都会被清理。


## 1-6 git log

```
git log
git log --oneline     // 获取简略信息
git log -n+数字        // 如-n4，表示最近几次的log
git log -n3 --oneline // 组合使用
git log --all         // 所有分支版本历史，默认是当前分支
git log myBranch      // 后加分支名，指定分支历史
git help --web log    // 用浏览器打开help log
```


```
git branch -v
git branch -a
git branch -av
git commit -am 'xx' 
// = git add .+ git commit 工作区内容直接加入版本库
```
 


## 1-7 git 图形化工具

shell中输入 gitk


## 1-8 .git目录

使用git init可以创建一个仓库，创建完毕后会在当前路径下生成一个.git文件夹。
```
ls -al 
cat .git
```


### HEAD
HEAD是一个文本文件，表示当前所在分支。切换分支之后会改变。  
```
cat HEAD
  ref: refs/heads/owensiz
```


### config
```
cat config
  [core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
  [user]
    name = chuzihang
    email = 11xxxx@qq.com
```





pwd 当前工作路径
ls
ls -al 当前目录下文件
cp ../文件的相对路径？  拷贝某文件到当前文件夹
cp -r 递归拷贝？
cat xxx
vi xxx
mkdir myFolder 创建新文件夹
untracked files 没有被跟踪的文件