# 一、Git简介

**1 Git简介**

Git是一个开源的**分布式版本控制系统**，用于敏捷高效地处理任何项目。
 它采用了分布式版本库的方式，不用服务器端软件支持。

**2 Git的下载**

Git 目前支持 Linux/Unix、Solaris、Mac和 Windows 平台上运行。

下载好，按默认安装即可（推荐安转在D盘中）。安装完成后，在开始菜单里找到“Git”->“Git Bash”

双击出命令行窗口

![在这里插入图片描述](https://img-blog.csdnimg.cn/9f8ec7b63834460ca01c0bf17dd44e96.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUyNTk2MjU4,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/c6d9c434a08a4d3e9d00577652603fdd.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUyNTk2MjU4,size_16,color_FFFFFF,t_70)

**3 Git的配置**

  在命令行输入：

`$ git config --global user.name "Your Name"`
`$ git config --global user.email "email@example.com"`

完成初始配置

配置查询

要检查已有的配置信息，可以使用 `git config --list` 命令

也可以单独查看某项配置：

```java
$ git config user.name
$ git config user.email
```

**4 Git的使用流程**

- 克隆Git资源作为工作目录；
- 在克隆的资源上添加或修改文件；
- 如果其他人更改，你可以更新资源；
- 在提交前查看修改状态；
- 提交修改；
- 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。
- ![在这里插入图片描述](https://img-blog.csdnimg.cn/8d313bcbf321458a857e85eb16000cbf.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUyNTk2MjU4,size_16,color_FFFFFF,t_70)



**5 Git的工作区、暂存区和版本库**

- **工作区：** 就是你电脑里能看到目录；

- **暂存区：** stage或index，一般放在`.git(可隐藏文件)`目录下的`index`文件（.git/index）中，所以我们把暂存区有时候也叫做索引（index）；

- **版本库：** 工作区有一个隐藏目录，`.git`，这个实际上是Git的本地版本仓库

  **工作区、版本库中的暂存区和版本库之间的关系：**![在这里插入图片描述](https://img-blog.csdnimg.cn/e8c53b6a130a43d8bbcc98bad2acae5c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUyNTk2MjU4,size_16,color_FFFFFF,t_70)

**左侧为工作区，右侧为版本库**。

**在版本库中标记为“index”的区域是暂存区（stage/index），**

**标记为“master”的是master主分支代表的目录数。**

**HEAD实际上是指向master主分支的一个“游标”**
图中的objects标识的区域为Git的对象库，实际位于“.git/objects”目录下，里面包含了创建的各种对象及内容。
当工作区进行修改（或新增）的文件执行git add命令时，暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库（此时的对象库可以认为是暂存区中的对象库）中的一个新的对象中，而该对象的ID被记录在暂存区中的文件索引中。
当执行提交操作git commit时，暂存区的目录树就被提交到版本库中的对象库（objects）中，master主分支会做相应的更新。即master指向的在暂存区提交过来的目录树。
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。
可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

# 二、Git基本命令操作



**1 创建版本库**

`git init`命令把目录变成Git可以管理的仓库：

**2 创建一个文件**

#在当前目录创建一个文件

```
$ touch myfirst_try.txt 

$ vim readme.txt    #编辑该文件
```

然后`esc`退出编辑，输入`:wq`回车，保存并退出

```
$ cat readme.txt   *#查看当前文件的内容*
```

**3  将文件提交到本地git版本仓库中（两步走战略）**

```
$ git status      *#查看当前git状态(新建了一个文件)*
```

第一步`add`到暂存区：

```再查看状态：
$ git add readme.txt      #添加到暂存区
```

再查看状态：

```sql
$ git status        #查看当前git状态(readme.txt被添加到暂存区)
```

第二步`commit`到本地版本仓库

```sql
$ git commit -m "wrote a readme file"
```

然后再再次查看状态（没有可提交的文件）：

简单解释下git commit -m "记录提交内容"命令，-m 后面写的是本次提交的记录内容，

最好是有意义的，这样就能从历史记录中清楚的知道每次的改动的内容和操作。

如果你在团队开发中做了提交不写记录内容，别人就没办法知道你做了哪些修改操作，所以说可读性非常重要,记录内容是必要的！！！

为什么Git提交文件需要两步呢？因为commit可以一次提交很多文件.

**4 Git回退版本和重返**

- **想回退历史：** `git log`命令查看以便回到哪个版本；
- **想重返未来版本：** `git reflog`命令查看每个版本的`commit id`，直接`git reset --hard commit_id`即可。

  如果关闭了窗口咋办，

命令`git reflog`，可以展示你每次的命令

**5 Git撤销操作**

**`git restore file`命令撤回操作**

**命令`git restore file`**

作用就是将readme.txt文件在工作区做的修改全部撤回，其实此处有两种情况：

第一种：readme.txt修改后还没放到暂存区，现在，可以直接撤回到与版本库中的readme.txt一样的状态；
第二种：readme.txt做了两次修改，第一次修改添加到暂存区了，第二次修改没有添加，现在，撤回的是第二次在工作区的修改，回到的状态是第一次修改添加到暂存区后的状态，也就是说这个撤回命令不能够撤回已经添加到暂存区的内容。
总之，**就是让这个文件撤回到最近一次的git add或git commit后的状态。**





撤回工作区修改命令：

> ```
> git restore file（推荐）
> ```

撤回暂存区修改命令：

> ```
> git restore --staged file（推荐）
> ```

- ```
  注意：从暂存区撤回后，工作区的也要接着撤回
  ```

  > `git restore file`

**6  Git删除操作**

```
rm file
```

**工作区test.txt文件被删除了**

**只是在工作区中删除了`test.txt`文件，**

**版本库中仍然存在，使用命令`git restore test.txt`，可以撤回删除的`test.txt`文件；**

**命令`git rm test.txt`**

**版本库中也被删除**

# 三、Git基本操作总结

## Git常用的6个命令：

- **git clone**

- **git push**

- **git add**

- **git commit**

- **git checkout**

- **git pull**

  ![在这里插入图片描述](https://img-blog.csdnimg.cn/f0729d5bc6504c2283ecff9fdb3e484a.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUyNTk2MjU4,size_16,color_FFFFFF,t_70)

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

```
git add	添加文件到暂存区
git status	查看仓库当前的状态，显示有变更的文件
git diff	比较暂存区和版本库中文件的差异
git commit	提交暂存区到本地仓库
git reset	回退版本
git rm	删除工作区和版本库中的文件
git mv	移动或重命名工作区文件

git log  (–pretty=oneline)	查看历史提交记录 (后者代表每个记录在一行显示)
git blame file	以列表形式查看指定文件的历史修改记录
	

git remote	远程仓库操作
git fetch	从远程获取代码库
git pull	拉取下载远程代码并合并
git push	将本地代码上传至远程仓库并合并
```

