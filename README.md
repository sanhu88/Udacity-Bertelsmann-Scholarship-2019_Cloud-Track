# Udacity-Bertelsmann-Scholarship-2019_Cloud-Track
Bertelsmann Tech Scholarship Challenge Course - Cloud Track on Udacity.com

> Total 24 lessons about 35 hours 1-12 git/ 12-17  cloud-fundamental /18-24  infrastructure-as-code 

Notice：

1.此篇笔记，代码在前，文字解释在代码区块下方。



## Shell Workshop

-  **operating system** 操作系统—like Windows, macOS, or Linux 
-  **shell** *is simply the outermost layer of an operating system. It's designed to provide a way for you to interact with the tools and services that your operating system provides.*  shell只是操作系统的最外层。它的目的是为您提供一种与操作系统提供的工具和服务进行交互的方式。 
-  **Graphical User Interface** or **GUI** (pronounced "gooey") ,  A user interface where you give instructions to the computer by interacting with things like windows, menus, icons, and buttons. 用户界面，通过与窗口、菜单、图标和按钮等交互向计算机提供指令。 
-  **Command-Line Interface** or **CLI**, A user interface where you give instructions to the computer by entering lines of text.  一种用户界面，你通过输入几行文字来给计算机指令。 
-  One of the most widely used shells is called **BASH** 

--为什么使用CLI 而不是GUI呢？

--It will make you a more powerful programmer. In other words, if you want to be a powerful developer (or even just a powerful user), it's essential to at least learn the basics of using a text shell and CLI. 

--It will open the door to other tools.

--learn Python



## echo

~~~BASH
echo Hi KK!
~~~

结果是Hi KK!

~~~bash
echo Hi KK!!
~~~

得出结果并不是 Hi KK！！

 When we entered the `!!`, it replaced it with our last command .再次运行上次命令

如果想要只出，则需要加单引号

~~~bash
echo 'Hi KK!!'
~~~



exercise  2

鼠标无法在终端里移动光标。

 Unfortunately, most default terminals don't allow you to use the mouse to move the cursor position. 

## 变量Variables

等号赋值

~~~bash
x=100
x = 100
~~~

第二行会报错  -bash: x: command not found 

**在BASH 中空格有严格意义 **



~~~bash
x=100
echo $x
100
~~~

打印时，需要加美元符

~~~bash
x=42
echo 'The answer is' $x'.'
~~~

打印变量和字符串，直接拼接，连句点都没有

~~~bahs
echo $COLUMNS x $LINES
80 x 24

~~~

## Navigating directories

~~~bash
ls
~~~

### ls 

list的缩写，还有ll

~~~bash
cd
~~~

### cd 

 Change Directory 更改目录，默认是当前目录互动

- 不在cd 后加/ 代表是当前目录下的文件夹名字 Download/
- 在cd 后加 / 代表是 绝对路径
- cd .. 上一句目录
- **； 分号可以一行写两个命令**

  BASH is a **case sensitive** language ，大小写敏感的语言

### pwd 

pwd = print working directory

当前目录路径

..代表上一级

. 代表当前 ls . 等同于 ls

### ~

主目录 home directory，

### Absolute vs. relative path

~~~bash
cd /home/workspace
~~~

上方就是绝对路径跳转，不关乎当前在哪里。 This will work no matter where you are currently located. 

~~~bash
cd ~ #是一个绝对路径
~~~



相对目录，不以/打头，只能往下(内部)，除了 cd ..

## 选项Options

~~~bash
ls -l
~~~

l 代表long 长目录，打印更多细节：最后修改日期；文件体积

 the `-l` option will give you the date that each file was last modified, as well as the size of the file (in bytes) 



~~~bash
ls -l Documents/*.pdf
~~~

列出所有Document 文件夹下的pdf文件

习题：

~~~bash
ls *poem*
~~~

## 创建和移动文件

### mkdir

mkdir  = make directory 创建目录

~~~bash
mkdir Document/Books
~~~



### mv

mv = move

mv 需要移动的文件 目标文件夹

如果目标文件夹后面跟了具体的文件名和文件格式，转移过去的，会被重命名和格式

~~~bash
mv Document/*epub Document/Books
~~~

## 下载 curl

Curl =  see URL

如果是是网页地址，看到的是网页源代码

~~~BASH
curl -L 'https://baidu.com'
~~~

-L 代表遵循重定向

~~~bash
curl -o qq.html -L 'https://news.qq.com'
~~~

-o 保存到文件，后面加文件名

留意，url中包含特殊字符，比如&%,是BASH有特殊含义的。

练习：

~~~bash
$ curl 'baiud.com'
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   184  100   184    0     0    326      0 --:--:-- --:--:-- --:--:--   326<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx/1.4.2</center>
</body>
</html>

~~~

 不加-L，不跳转，错误的域名就会有6行

This should only output a relatively short block of HTML (about six lines). 

## 查看文件 cat， less

cat = catenate / concatenate 连接多个事物

less 查看文件的一部分内容，只会显示占满一屏幕的内容，

* 空格键或箭头键下滚。
* B用来返回
* / 用来搜索
* Q用来退出

## 移动文件 rm ， rmdir

rm = remove

rm 添加提示选项 -i (interactive 交互)

rmdir 只会删除非空文件夹  when using the `rmdir` command, it will only delete a directory that is *empty* 

两者都是permanently delete 永久删除

删除多个可以直接以空格隔开

~~~bash
rmdir example1 example2 example3
~~~

如果文件夹包含空格，给文件夹加上引号

~~~bash
rmdir 'example 1'  'example 2'  'example 3'
~~~

删除也可以使用通配符 *

## What is Version Control 

(此部分是Udacity的free课程里有)

游戏进度保存来引入版本管理的概念。

目前流行的版本管理：Git / Subversion / Mercurial

## 术语

官方给的学习材料 [ud123-git-keyterms.pdf](./ud123-git-keyterms.pdf)

### version control system / Source Code Manager

版本控制系统，源代码管理器

version control system (abbreviated as **VCS**）source code manager (abbreviated as **SCM**) 

Git is an SCM (and therefore a VCS)

### Commit

提交

save the state of your project in Git

a commit is *the* fundamental unit in Git/基本单元

### Repository / repo

仓库

A **repository** is a directory which contains your project work

A repository is made up of commits

### Working Directory

工作目录

The **Working Directory** is the files that you see in your computer's file system

### Checkout

签出/切换出

A **checkout** is when content in the repository has been copied to the Working Directory.

### Staging Area / Staging Index / Index

暂存区域/指针/索引

the **staging area** as a prep table where Git will take the next commit

### SHA

编码id

A **SHA** is basically an ID number for each commit. Here's what a commit's SHA might look like: `e2adf8ae3e2e4ed40add75cc44cf9d0a869afeb6`.

It is a 40-character string

### Branch

分支

A **branch** is when a new line of development is created that diverges from the main line of development

Git 跟踪的是变化为核心

## IDE与Git的设置

### Atom 

~~~
git config --global core.editor "atom --wait" 
~~~

### Sublime Text

~~~
git config --global core.editor "'C:/Program Files/Sublime Text 2/sublime_text.exe' -n -w"
~~~

### VSCode 

~~~
git config --global core.editor "code --wait"
~~~

## Git Init

The `init` subcommand is short for "initialize" , which is helpful because it's the command that will do all of the initial setup of a repository.

初始化仓库

创建实验课目录

~~~bash
mkdir -p udacity-git-course/new-git-project && cd $_
~~~

.git文件夹探索

* config file 比如邮件/姓名等全局设置
* description file ：only used by the GitWeb program, so we can ignore it，与我们无关，可以忽略
* hooks directory 这是我们可以放置客户端或服务器端脚本的地方，我们可以使用它们来连接到Git的不同生命周期事件
* info directory ：contains the global excludes file包含全局排除文件
* objects directory 存储所有的提交
* refs directory  存储指针，比如分支和标签

## repo ： git log

git log 和 git show

git log 是提交的细节，

k键向上，u是半页向上，b是全页向上，Page Up键

j键向下滚动，d是半页向下，f是全页向下，空格键或Page Down键

冒号变成（end）是文末，q退出

git show 是修改内容 ，可以提供具体的ID来查看q退出



### --oneline

```bash
git log --oneline
```

拼写很重要，online不会现实

git log --oneline 总结：

This command:

- lists one commit per line 每行一条
- shows the first 7 characters of the commit's SHA  7位数ID
- shows the commit's message  提交信息



### --stat

会包含修改文件。

```bash
$ git log --stat
```

~~~
Author: Richard Kalehoff <richardkalehoff@gmail.com>
Date:   Mon Dec 5 16:34:15 2016 -0500

    Center content on page

 css/app.css | 5 +++++
 1 file changed, 5 insertions(+)

~~~

git log --stat 总结：

This command:

- displays the file(s) that have been modified 哪些文件
- displays the number of lines that have been added/removed 哪些行数
- displays a summary line with the total number of modified files and lines that have been added/removed 合计变动数量

### --patch  /-p

用来查看文件修改

~~~bash
diff --git a/css/app.css b/css/app.css
index 78cef20..07c36fa 100644
--- a/css/app.css
+++ b/css/app.css

~~~

diff也就是path的意思，a代表之前的，b代表修改后的

index 之后是修改前的Hash和修改之后Hash

下面的减减加加和第一行一样的意思

~~~bash
@@ -38,6 +38,11 @@ p {
     line-height: 1.5;
 }

+.container {
+    margin: auto;
+    max-width: 1300px;
+}
+

 /*** Header Styling ***/
 .page-header {

~~~

@@后面代表，之前版本是从第38行，显示有6行代码，现在变成从38行起，变成了11行，多了五行，也就是++显示的部分。

删除的提交时减号开头红色部分显示，增加的时绿色，加号开头

git 跟踪代码是，以行为基本单位的，如下图所示

![The Terminal application showing the output of the `git log -p` command.](https://video.udacity-data.com/topher/2017/February/58a37f65_ud123-l3-git-log-p-lines-removed-annotated/ud123-l3-git-log-p-lines-removed-annotated.png)

- 🔵 - the file that is being displayed
- 🔶 - the hash of the first version of the file and the hash of the second version of the file
  - not usually important, so it's safe to ignore
- ❤️ - the old version and current version of the file
- 🔍 - the lines where the file is added and how many lines there are
  - `-15,83` indicates that the old version (represented by the `-`) started at line 15 and that the file had 83 lines
  - `+15,85` indicates that the current version (represented by the `+`) starts at line 15 and that there are now 85 lines...these 85 lines are shown in the patch below
- ✏️ - the actual changes made in the commit
  - lines that are red and start with a minus (`-`) were in the original version of the file but have been removed by the commit
  - lines that are green and start with a plus (`+`) are new lines that have been added in the commit

~~~bash
git log --stat -p
~~~

show the stats info above the patch info，先显示stats也就是具体那些文件修改了，然后再显示path也就是具体修改的内容

~~~bash
git log -p -w
~~~

-w，全程是**--ignore-all-space**参数会忽略空格键带来的代码改变



git log -p 总结：

This command adds the following to the default output:

- displays the files that have been modified 哪些文件
- displays the location of the lines that have been added/removed 哪些行数
- displays the actual changes that have been made 实际上的改动

### 定位

~~~bash
git log -p fdf5493
~~~

可以加ID会从此ID开始展示

~~~bash
git show fdf5493
~~~

git show只会展示指定的，无法前后查看

两者都包含

- the commit  提交的ID
- the author 作者
- the date 日期
- the commit message 提交的信息
- the patch information 具体修改的信息

当然也可以后带参数

* --stat 多少文件被修改和行数的变动，不显示具体内容
* -p / --path 具体的修改内容
* -w 忽略缩进和空格的的变化

练习题

当只给出提交信息时，查找修改了多少文件：

Fantastic job! I first used `git log --oneline` to find the SHA of the commit, then I used `git log --stat` with the SHA to find the right info.

## git add/commit

回顾：

* git init 创建
* git clone 下载
* git log 日志
* git status 状态

会学到

1. git add 	把文件从工作区添加到暂存区
2. git commit  把文件从暂存区保存到仓库
3. git diff  比较两个版本的差异，和git log -p的结果一致



当文件夹内有新的仓库时，add .会报错如下

~~~bash
$ git add .
warning: adding embedded git repository: course-git-blog-project/course-git-blog-project
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint:   git submodule add <url> course-git-blog-project/course-git-blog-project
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint:   git rm --cached course-git-blog-project/course-git-blog-project
hint:
hint: See "git help submodule" for more information.

~~~

~~~
As a side note, git rm --cached is not like the shell's rm command. git rm --cached will not destroy any of your work; it just removes it from the Staging Index.
~~~

git rm --cached 不是真的删除文件，而是不会放在暂存区里。





~~~bash
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

~~~

Period 句号点 .

~~~bash
git add .
~~~

添加所有文件和文件夹（好像空文件夹不行）



~~~bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   css/app.css
        new file:   index.html
        new file:   js/app.js

~~~

### git commit

~~~bash
git commit -m "Initial commit"
~~~

需要先add 再commit

**The goal is that each commit has a single focus.**

每一个commit 只跟踪一件事（一个单元的改变）。比如

- add a new image to the project files
- alter the HTML
- add/modify CSS to incorporate the new image

一个commit应该是相关部分的。

The best way that I've found to think about what should be in a commit is to think, "What if all changes introduced in this commit were erased?". If a commit were erased, it should only remove one thing.

如果删除此次提交，应该只包含一件事情

### Commit Messages

如何是一个优秀的commit 信息？

* 保持简洁do keep the message short (less than 60-ish characters)
* 解释本次提交改动了什么 do explain *what* the commit does (not *how* or *why*!)

不需要的再信息里的：

1. 解释为什么会有代码改变
2. 解释怎样改变了代码
3. 不要使用“和”，如果使用了and代表你有太多的改变，应该分次提交

练习题：

~~~

"Add a

tag to the body"


The commit message should not contain specifics on how the change was made. This information can be found by running git log -p.

提交消息不应该包含关于如何进行更改的细节。可以通过运行git log -p找到这些信息。

~~~



~~~
"Add changes to app.js"

Saying that changes have been added is not helpful. A commit can only include changes of some kind (new content, content being removed, content being altered. Saying that changes were made to "app.js"

说已经添加了更改是没有帮助的。提交只能包含某些类型的更改(新内容、要删除的内容、要更改的内容)。只需说更改了“app.js”
~~~



### Udacity's Commit Style Requirements

[https://udacity.github.io/git-styleguide/](https://udacity.github.io/git-styleguide/)

## git diff

用来查看还没有提交的改变

~~~bash
$ git diff
diff --git a/index.html b/index.html
index 8996430..e16c565 100644
--- a/index.html
+++ b/index.html
@@ -1,7 +1,7 @@
 <!doctype html>
 <html lang="en">
 <header>
-    <h1>Expedition</h1>
+    <h1>Adventure</h1>^M
 </header>
 <head>
     <meta charset="utf-8">

~~~

git diff是git log -p 的另外一种形式，git log包含已经有的提交

git diff总结：

- the files that have been modified	改变的文件
- the location of the lines that have been added/removed 改变的定位行数
- the actual changes that have been made 实际的改变内容

## Git Ignore Files

~~~bash
.gitignore
~~~

~~~bash
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .gitignore

nothing added to commit but untracked files present (use "git add" to track)

~~~

通配符Globbing 

* 空白行可用于间距
* #代表注释部分，不会起作用
* 星号\*  代表0个或多个字符
* ？ 代表一个字符
* [abc] 代表 匹配 a, b或者c
* 两个星号\** 代表匹配多重目录，a/**/z 代表
  * a/z
  * a/b/z
  * a/b/c/z

~~~bash
samples/*.jpg
~~~

代表sample文件夹下的所有jpg图片

练习题：

1. 通配的部分不区分大小写 

   That's right! Adding `*.png` will cause Git to ignore *all* PNG images.

2. 要和.git目录保持再同一目录



## git tag

关于末次提交的永久指针

~~~bash
git tag -a v1.0
~~~

*the* `-a` *flag is used. This flag tells Git to create an* *annotated* *flag.*  -a代表是有注释的提交

### 验证

~~~bash
$ git tag
v1.0

~~~

git log的新参数 --decorate，git 2.13以后版本 已经自带此参数

~~~bash
git log --decorate
commit e428e290241c3dd2aa75b97e8ce08fbd9c6ec66c (HEAD -> master, tag: v1.0)
Author: Burt Zheng <504779282@qq.com>
Date:   Thu Dec 12 22:26:58 2019 +0800

    git diff

commit ce5c5cd347f6c8cc49eb5895cb74deb1233f1da1
Author: Burt Zheng <504779282@qq.com>
Date:   Wed Dec 11 20:40:23 2019 +0800

    Add header to blog

commit e4f0aba0cab0592e62982815e26b3369f84098ea
Author: Burt Zheng <504779282@qq.com>
Date:   Wed Dec 11 20:37:05 2019 +0800

    Initial commit

~~~

### 删除tag

with the `-d` flag (for *delete*!) 

~~~bash
git tag -d v1.0
~~~

和

~~~bash
git tag --delete v1.0
~~~

### 为之前的提交添加标签

在语句后添加SHA就可以

~~~bash
git tag -a v1.0 a87984
~~~

## git branch

默认的是Master 分支

~~~bash
git branch sidebar
~~~

创建分支

HEAD 指针，指向当前活跃的分支

~~~bash
git checkout sidebar
~~~

切换HEAD指针到sidebar，也可以

~~~bash
git checkout master
~~~

切换回Master

往前溯源

~~~bash
git branch header-fix a
~~~

a是sidebar之前的提交SHA，也就是创建了一个新的交header-fix的分支，a最为分支开始点

~~~bash
git branch
~~~

可以用来

* 显示仓库所有分支的名字
* 创建一个分支
* 删除分支

~~~bash
$ git branch
* master


~~~

练习:

即便创建了分支，没有切换过去前，还是在当前分分支。

~~~bash
git checkout sidebar
~~~

checkout的操作有两部：

1. 删除当前工作目录中git跟踪的文件（仓库中仍然存在，没有丢失）
2. 从仓库中拉取，分支所指向的文件和文件夹

### 在log中查看branch

~~~bash
$ git log --oneline --decorate
e428e29 (HEAD -> sidebar, tag: v1.0, master) git diff
ce5c5cd Add header to blog
e4f0aba Initial commit

~~~

可以看到HEAD指向的是sidebar

### 查看活动的branch

~~~bash
$ git branch
  master
* sidebar

~~~

活动的分支前面有星号（An asterisk will appear next to the name of the active branch.），而且是绿色的

### 删除分支

分支常用来修复项目中不会项目的问题。修复完后回合并到master里

~~~bash
git branch -d sidebar
~~~

两种情况不允许删除：

1. **无法删除当前工作的的分支** ，所以上方删除之前，需要切换到Master分支
2. **如果要删除的分支，提交了其他分支没有的内容，也不允许删除**

~~~bash
$ git branch -d footer
error: The branch 'footer' is not fully merged.
If you are sure you want to delete it, run 'git branch -D footer'.

~~~



强制删除用-D flag：

~~~bash
git branch -D sidebar
~~~

### Branch 有效性

如果内容存储在一个分支上，但是提交在另外一个分支，这些另外的提交时不可见的，除非切换到另外的分支上。

git diff 查看还没提交的修改

创建并切换到新分支的快捷命令：

~~~bash
git checkout -b richards-branch-for-awesome-changes
~~~

git log 新flag

~~~bash
git log --oneline --decorate --graph --all
~~~

* --graph 将项目符号和行添加到输出的最左边部分（adds the bullets and lines to the leftmost part of the output）
* --all 将显示仓库中所有的分支

### Merging 合并

合并sidebar到master ，不会影响到sidebar，可以继续对sidebar 进行修改提交

如果某个分支有些提交时Master不包含的（多余Master的提交），可以 fast forward merge 快进合并，把HEAD 指向最新的提交（因为Master没有这些提交）。

撤销一次合并：

~~~bash
git reset --hard HEAD^
~~~

最好带上-m 注释部分

~~~bash
git merge <name-of-branch-to-merge-in>
~~~

当合并发生时，git会：

* 检查要合并的分支
* 回溯提交历史，找到两者都有的一个提交
* 将不同分支的代码合并在一起
* 为合并进行一次提交

当合并时：

1. 不会合并到两个分支到一个全新的分支
2. 不会合并当前分支到另外的分支（是我们git merge中提到的，合并到当前）

### Fast-forward Merge

A Fast-forward merge will just move the currently checked out branch *forward* until it points to the same commit that the other branch (in this case, `footer`) is pointing to.

~~~bash
$ git merge footer
Updating fd4dcb8..9743d0f
Fast-forward
 index.html | 14 ++++++++++++++
 1 file changed, 14 insertions(+)

~~~

会让HEAD都指向 footer 和Master

~~~bash
9743d0f (HEAD -> master, footer) add footer social account links

没合并前是：
* 9743d0f (HEAD -> footer) add footer social account links
~~~

### 常规合并

~~~bash
$ git merge sidebar
Auto-merging index.html
Merge made by the 'recursive' strategy. #recursive[数] 递归的
 index.html | 7 +++++++
 1 file changed, 7 insertions(+)

~~~

### 合并失败处理

When a merge is performed and fails, that is called a **merge conflict**，下面会学到

总结：

常见两种合并类型：

1. Fast-forward merge,要求合并的分支必须在当前分支的前面，当前分支的HEAD指针会移动到合并分分支相同的提交
2. the regular type of merge常规提交。两个不同的分支会合并；合并提交会被创建。

### 合并冲突

自动合并失败，叫做合并冲突 **merge conflict**

git使用(e.g. `>>>` and <<<) 需要手动修复

#### 什么会造成合并冲突？

git跟踪的是行改变，多个分支改变在同一行，就会带来合并冲突

~~~bash
$ git merge heading-update
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

~~~

提示有合并冲突

~~~bash
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")

~~~

git给出的冲突的文件，处理办法

~~~bash
    <header>
<<<<<<< HEAD
        <h1>Quest</h1>
=======
        <h1>Crusade</h1>
>>>>>>> heading-update
    </header>
~~~

1. <<<<<<< HEAD ，代表是当前分支的代码，至下一个提示符号前
2. ||||||| merged common ancestors，代表是共有的祖先代码是什么样子，至下一个提示符号前
3. ======= ，代表原始代码的结束。接下来至下一个提示符，是正在合并的分支的代码
4. \>>>>>>> heading-update，正要合并分支的代码 ，告诉了分支名称

### 解决合并冲突

1. choose which line(s) to keep 选择保留的代码行
2. remove all lines with indicators 删除所有提示符的代码行

git不会因为有合并冲突的提示符就停止提交，所以处理完合并冲突后，建议用git diff 检查，提交后使用git show -w

## 撤销修改提交

### --amend 改变最后一次提交

~~~bash
git commit --amend
~~~

--amend vt. 修改；改善，改进 vi. 改正，改善；改过自新

比如笔误，或者是字体颜色，或者有些文件没有提交

步骤：

- edit the file(s) 编辑修改文件
- save the file(s) 保存文件
- stage the file(s) 暂存文件
- and run `git commit --amend` 运行

~~~bash
$ git commit --amend
[master ae37d47] fix a typo of header with git commit --amend
 Date: Tue Dec 17 21:13:47 2019 +0800

~~~

git log --oneline --graph --all 查看

~~~bash
之前
 6a2b973 (HEAD -> master) fix merge conflict set header to adventurous Quest
之后
 ae37d47 (HEAD -> master) fix a typo of header with git commit --amend

~~~

### Revert  恢复复原提交

恢复提交，将会和恢复到的提交A操作后，相反操作，比如A添加了代码，revert就删掉这部分；如果A删除了，vice verse

使用方法：

~~~bash
git revert <SHA-of-commit-to-revert>
~~~

我本地运行

~~~bash
 git revert ae37d47
error: commit ae37d47d94152864f4f83c08f2a887e713e5be19 is a merge but no -m option was given.
fatal: revert failed

~~~

revert vt. 使恢复原状

总结：

This command:

- will undo the changes that were made by the provided commit 撤销指定的提交的改变
- creates a new commit to record the change 常见一个新的提交

### Rest 重置提交

Reverting creates a new commit that reverts or undos a previous commit. Resetting, on the other hand, *erases* commits!

revert是恢复之前的然后创建一个提交，reset是擦除一个提交。

reset后内容也会丢失，使用reflog可以看到SHA

#### 相对提交引用 Relative Commit References

Ancestry References 祖先引用

* ^ 代表的是父提交
* ~ 代表第一个父提交

当前提交的父提交

1. HEAD^
2. HEAD~
3. HEAD~1

祖父级提交：

1. HEAD^^
2. HEAD~2

曾祖父提交：

1. HEAD^^^
2. HEAD~3

当一个提交时merge而来的时候，会有两个父提交：

^ 代表的是第一父提交，也就是git merge的是所在的分支

^2 代表的是第二父提交，也就是被合并进的分支。(因为^表示第一父提交不加数字)

练习

在git log 里 看到第一个是当前提交

The `git reset` command is used to reset (erase) commits:

~~~bash
git reset <reference-to-commit>
~~~

一般用于：

- move the HEAD and current branch pointer to the referenced commit 移动HEAD和分支指针到指定提交
- erase commits 擦除提交
- move committed changes to the staging index 移动提交的改变到暂存区
- unstage committed changes 在暂存区移除已提交的改变

#### git reset flag

--mixed 是默认的，reset到父提交时，当前提交会放在工作目录，再提交时，SHA不会时当前的SHA

--soft reset到父提交时，将当前提交所作的更改移动到暂存区,再提交时，SHA不会时当前的SHA

--hard reset到父提交时，将当前提交所作的更改移动到 Trash 垃圾箱

为了以防万一，会在reset之前，会未当前分支创建一个backup 

```bash
git branch backup
```

##### --mixed

```bash

$ git reset --mixed HEAD^
Unstaged changes after reset:
M       index.html

```

~~~bash
/ 放弃单个文件修改,注意不要忘记中间的"--",不写就成了检出分支了!
git checkout -- filepathname
// 放弃所有的文件修改
git checkout .  
~~~

在有backup分支后

可以删除工作目录中的未提交的的改变

然后把backup合并到master

##### --soft

Running `git reset --soft HEAD^` will take the changes made in commit `9ec05ca` and move them directly to the Staging Index.

##### --hard

Running `git reset --hard HEAD^` will take the changes made in commit `9ec05ca` and erases them.