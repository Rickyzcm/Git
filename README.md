# Git

 + 中文释义：分布式版本控制系统
 + 可运行平台：Linux、Unix、Mac、Windows
 + 开发语言背景：C语言

## 一般与github联动步骤
+ 准备工作
  - 自己的github账号
  - 已经安装好Git软件的本地计算机
   
1. 登录github，创建一个新的repository，建立新项目后进入项目内，将url地址复制

1. 初始化一个 git 仓库：打开 Git Bash 窗口，先进入选定作为本地仓库的文件夹内，输入命令`git init`，将所在文件夹变成Git可以管理的仓库,文件路径就会存在一个隐藏的.git文件

1. 在本地仓库文件夹路径下输入命令`git clone `将github的仓库中项目结构分支克隆到本地仓库中

1. 将需要上传的项目文件夹拷贝至含有隐藏文件后缀名为`.git`文件的同一路径下

1. 输入命令`git add . ` 此语句就是讲当前目录下所有修改过的文件以及所有子目录下修改过的文件进行提交 

1. 输入命令`git commit -m "注释信息"`(提交到本地的版本控制库内，引号内是注释信息，选填)
   **控制台输出结果**  
   ```bash
    $ git commit -m "注释内容"
    [master 00db313] 注释内容
     1 file changed, 0 insertions(+), 0 deletions(-)
     rename filename.md => "MySQL******.md" (100%)

   ```

1. 输入`git push -u origin master`  
   **控制台输出结果**
   ```bash
    Counting objects: 3, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 3.78 KiB | 967.00 KiB/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To github.com:Rickyzcm/demos_SQL.git
        8c0d44a..c2bd4f2  master -> master
   ```
以上即可对远程库进行提交更新


## 可能出现的问题
#### 请确保git的工作路径不包含中文
    在使用windows工作环境下，含有中文字符的工作路径总是会存在各种莫名奇妙的问题，所以请确保在git工作路径不含有中文
#### 本地分支与与远程仓库断联 
##### 控制台显示
```
$ git push -u origin master
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.
```  

##### *解决方案*  
  1. 输入`git remote -v`查看本地分支的上游，若什么都没输出，则证实断连
  1. 输入`git remote add origin git@github:***github项目url***.git`   

##### *效果输出*
 ```
    $ git remote -v 
    origin  git@github:xxxx/******.git (fetch)
    origin  git@github:xxxx/******.git (push)
 ```

#### git push 之后在 github 上并未更新
##### 描述
   + `git push` 之后返回的结果是
     ```bash
      Everything up-to-date
     ```
     github上的仓库内文件并没有改变！
##### 原因
   + `git add .` 语句之后缺少 commit 步骤，暂存区内的文件更新还未提交给本地版本库。
##### 解决方案
   + 继续执行`git commit -m`语句更新本地库

## git 命令集合
```bash
+ git add 文件名 

+ git config user.name 查看用户名
+ git config user.email 查看用户邮箱地址
+ git config --global user.name "文本" 修改用户名
+ git config --global user.email "文本" 修改用户邮箱地址

+ git branch 查看本地分支
+ git branch -a 查看所有分支

+ git commit 
+ git commit -m "本次提交的说明" 待备注的提交版本库
+ git commit --amend 查看最近的log信息

+  git branch --unset-upstream

```