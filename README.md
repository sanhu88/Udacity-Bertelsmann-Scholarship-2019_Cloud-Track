# Udacity-Bertelsmann-Scholarship-2019_Cloud-Track
Bertelsmann Tech Scholarship Challenge Course - Cloud Track on Udacity.com

> Total 24 lessons about 35 hours 1-12 git/ 12-17  cloud-fundamental /18-24  infrastructure-as-code 

Notice：

1.此篇笔记，代码在前，文字解释在代码区块下方。

[学习进度](https://progress-bar.dev/28/?title=Learned)

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

默认的是master 分支

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

切换回master

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

1. **无法删除当前工作的的分支** ，所以上方删除之前，需要切换到master分支
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

如果某个分支有些提交时master不包含的（多余master的提交），可以 fast forward merge 快进合并，把HEAD 指向最新的提交（因为master没有这些提交）。

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

会让HEAD都指向 footer 和master

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

> [@Md. Abdul Monim](https://bertelsmanncloud.slack.com/team/UQX0LCLMS) of Slack
>
> HEAD~n, number after ~ means 1->parent, 2->grandparent, 3->great grand parent.
> HEAD^n, number after ^ means 1->1st parent, 2-> 2nd parent when the current commit has multiple parents.

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

## Lesson 总结

1. git commit --amend 是改写或更新最近的提交
2. git revert是撤销特定的提交
3. git reset 是擦除或删除改变

## Git Hub

git skill 回顾：

1. git init 创建 git clone 下载
2. git status 查看状态
3. git log 看提交的日志 git diff 查看未保存的改变 git show 查看暂存区的改变
4. git add 添加提交
5. git commit 提交到仓库
6. git branch /git checkout <branchname> /git merge 分支操作
7. git commit --amend /git revert/git reset  取消操作

## 远程仓库

双人合作

1. 使用各自的电脑
2. 各自有各自的进度
3. 可以在大家都完成的时候进行合并

使用话题进行分支，保存各自不同的变更。

远程仓库，相对本地仓库而言。

Git是一个分布式版本控制系统，这意味着没有一个主要的信息仓库。Git is a *distributed* version control system which means there is not *one* main repository of information.

本地的分支可以合并成新的master 然后同步到远程仓库，也而可以所有分支分开同步到远程仓库。

## Git Remote

```bash
 git remote
```

如果没有配置远程仓库，此命令无输出

~~~bash
$ git remote
origin

~~~

origin是远程仓库的缩写，方便命令行使用。通常远程叫做origin

~~~bash
git remote -v
$ git remote -v
origin  git@github.com:sanhu88/Udacity-Bertelsmann-Scholarship-2019_Cloud-Track.git (fetch)
origin  git@github.com:sanhu88/Udacity-Bertelsmann-Scholarship-2019_Cloud-Track.git (push)

~~~

会打印完整路径，对比缩写

**演示仓库目录为my-travel-plans**

~~~bash
git remote add origin git@github.com:sanhu88/my-travel-plans.git
~~~

在本地创建好问津，在GitHub 创建不带READMD.mdD的仓库，然后连接

~~~bash
 git remote add repo-on-GitHub https://github.com/richardkalehoff/RichardsFantasticProject.git
~~~

可以把origin换成其他自定义的名字，只是一个缩写而已。

~~~bash
$ git remote -v
origin  git@github.com:sanhu88/my-travel-plans.git (fetch)
origin  git@github.com:sanhu88/my-travel-plans.git (push)

~~~

总结：

- `git remote add` is used to add a connection to a new remote repository. 用来创建和新远程仓库的连接
- `git remote -v` is used to see the details about a connection to a remote. 显示远程连接的细节

## Push 推送

~~~bash
git log --oneline --graph --decorate --all
~~~

查看日志

~~~bash
git push <remote-shortname> <branch>
~~~

push 的是本地的分支

如果push需要账号密码，因为：

* 使用的是HTTP 而不是SSH 版本remote add的
* 使用SSH 而且配置了key就不用输入账号密码



~~~bash
git push origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 1008 bytes | 252.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To github.com:sanhu88/my-travel-plans.git
 * [new branch]      master -> master


~~~

~~~bash
$ git log --oneline --graph --decorate --all
* 51664f6 (HEAD -> master, origin/master) revert index.html
* 661a6cd File complete local

~~~

(HEAD -> master, origin/master) 

## 从远程拉取改变到本地 Pull changes from a remote

如果远程origin 超过了本地master 的提交

~~~bash
git pull origin master
~~~

来拉取并合并到本地



~~~bash
$ git pull origin master
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
From github.com:sanhu88/my-travel-plans
 * branch            master     -> FETCH_HEAD
   51664f6..86a16b0  master     -> origin/master
Updating 51664f6..86a16b0
Fast-forward
 css/app.css | 6 +++++-
 1 file changed, 5 insertions(+), 1 deletion(-)

~~~

pull 到本地使用的是fast-forward merge 

如果不想自动合并，使用git fetch

If you don't want to automatically merge the local branch with the tracking branch then you wouldn't use `git pull` you would use a different command called `git fetch`.

总结：

git pull 运行时：

- the commit(s) on the remote branch are copied to the local repository
- the local tracking branch (`origin/master`) is moved to point to the most recent commit
- the local tracking branch (`origin/master`) is merged into the local branch (`master`)

## Pull 和 Fetch

当远程仓库具有本地仓库所不具有的提交时，使用

~~~bash
git fetch origin master
~~~

只是把 origin/master 分支更新到和远程一致，不会自动合并，但是master 分支没有任何改变。

如果想要把master 指向最新提交，需要使用merge命令来合并origin/master分支到master

~~~bash
git merge origin/master
~~~

fetch总结：

- the commit(s) on the remote branch are copied to the local repository 下载远程分支到本地
- the local tracking branch (e.g. `origin/master`) is moved to point to the most recent commit 本地对应的分支回指向最新提交（不是master）

You can think of `git fetch` as half of a `git pull` 可以理解成，fetch只做了pull的一半，pull多了merge。

主要用于远程和本地都有了对方没有的提交，使用fetch来拉取到origin/master 分支，然后手动再合并。最后整理到最新的去远程，远程也回记录不同的提交，然后合并到和本地一致。

One main point when you want to use `git fetch` rather than `git pull` is if your remote branch and your local branch both have changes that neither of the other ones has. In this case, you want to fetch the remote changes to get them in your local branch and then perform a merge manually. Then you can push that new merge commit back to the remote.

而且，本地具有远程没有的提交时，git pull不会工作

in [my-travel-plans](https://github.com/sanhu88/my-travel-plans)

~~~bash
git diff -w
~~~



~~~bash
$ git log --oneline --graph --all
* 2b41bde (HEAD -> master) add text on local for test fetch
* 86a16b0 (origin/master) change app.css
* 51664f6 revert index.html
* 661a6cd File complete local

~~~

![fetch_on_Github](.\images\fetch_on_Github.png)

on local repo we can see HEAD ->master SHA is 2b41bde but origin/master point to 86a16b0.

On the other hand,Github HEAD is e25d6a6 and 86a16b0 is HEAD^

~~~bash

$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From github.com:sanhu88/my-travel-plans
 * branch            master     -> FETCH_HEAD
   86a16b0..e25d6a6  master     -> origin/master
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.

~~~

~~~bash
$ git pull origin master
error: Pulling is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.


~~~

~~~bash
git fetch origin master
From github.com:sanhu88/my-travel-plans
 * branch            master     -> FETCH_HEAD

~~~



~~~bash
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

~~~

~~~bash
$ git log --oneline --graph --all
* 2b41bde (HEAD -> master) add text on local for test fetch
| * e25d6a6 (origin/master) add text on Github
|/
* 86a16b0 change app.css
* 51664f6 revert index.html
* 661a6cd File complete local

~~~

~~~bash

$ git merge origin/master
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.

~~~

~~~bash

git merge origin/master
Already up to date.

~~~

~~~bash
$ git log --oneline --graph --all
*   03f08b5 (HEAD -> master) fix merge conflict by pull
|\
| * e25d6a6 (origin/master) add text on Github
* | 2b41bde add text on local for test fetch
|/
* 86a16b0 change app.css
* 51664f6 revert index.html
* 661a6cd File complete local

~~~

~~~bash
git push -u origin master
~~~

update remote repo from local and keep both same

~~~bash
$ git log --oneline --graph --all
*   03f08b5 (HEAD -> master, origin/master) fix merge conflict by pull
|\
| * e25d6a6 add text on Github
* | 2b41bde add text on local for test fetch
|/
* 86a16b0 change app.css
* 51664f6 revert index.html
* 661a6cd File complete local

~~~

## Fork /Review /Permission

### fork

fork 名词时叉子，动词是（路）岔开了，Git中fork代表split 分成相同的两份，但是没有git fork命令，由宿主环境提供（Github）。复制一个仓库并成为拥有者

总结：

Forking is an action that's done on a hosting service, like GitHub. Forking a repository creates an identical copy of the original repository and moves this copy to your account. You have total control over this forked repository. Modifying your forked repository does not alter the original repository in any way.

### 查看已经存在的工作

~~~bash
git log
~~~

#### 按照贡献数量

~~~bash
$ git shortlog
Burt Zheng (5):
      translate from line 3490
      translate update to line 3500
      aupdate line 3501-3524
      aupdate line 3474-3489
      update line 3224-3290

Jimmy (1):
      Merge pull request #5 from sanhu88/master

MyoDaisy (1):
      Merge pull request #6 from sanhu88/master

SMP (2):
      update
      update

Sam (32):
      init
      init
      init
      init
      init
~~~

git shortlog 查看各提交者贡献多少提交 how many commits each contributor has added to the repository

~~~bash
git shortlog -s -n
    37  sam
    32  Sam
     5  Burt Zheng
     3  Sam Thomas
     2  SMP
     1  Jimmy
     1  MyoDaisy
     1  Simon Sippert

~~~

-s 代表只看提交总数，不查看提交备注信息to show just the number of commits (rather than each commit's message) 

-n 按照提交总数排序，而不是按照默认的名字首字母排序 sort them numerically (rather than alphabetically by author name).

#### 按作者查找

~~~bash
$ git log --author=Sam
commit 496b552658707f33bb61c7c27a20203197c94d89
Merge: 56acf3f 91a80af
Author: Sam Thomas <imsamthomas@users.noreply.github.com>
Date:   Thu May 23 10:46:59 2019 +0700

    Merge pull request #7 from sippsolutions/patch-1

    Remove fixed version from composer.json

commit 5b9e8b0fa7623526a43eafed174a07cb8c2581a2
Author: Sam <sam@mageplaza.com>
Date:   Wed Apr 10 17:40:15 2019 +0700

    Update Language Pack

~~~

--author 是过滤条件，会显示所有符合的作者详细提交信息



~~~bash
$ git log --author="Paul Lewis"
~~~

筛选特定的人名用上述方法

#### 按照特定的SHA来搜索

~~~bash
 git show 5966b66
~~~

会提供更多的提交信息，尤其是被注释的部分。it easier for others to review the changes to. Another thing is filtering commits by information in the current message or description area.

#### 按照关键字词来搜索

~~~bash
$ git log --grep=bug
$ git log --grep bug
~~~

按照关键词来搜索，留意，如果关键词包含空格，必须使用引号来包裹。

Grep is a pattern matching tool.

总结

- group commits by author

  ```bash
    $ git shortlog
  ```

- filter commits with the `--author` flag

  ```bash
    $ git log --author="Richard Kalehoff"
  ```

- filter commits using the `--grep` flag

  ```bash
    $ git log --grep="border radius issue in Safari"
  ```

### 按照约定去参与

#### Pull Request

如果发现原作者的repo有bug，可以fork后到自己的仓库修改，git pull修改然后，git psuh到GitHub

#### CONTRIBUTING.md File

this file lists out the information you should follow to contribute to the project. You should look for this file before you start doing development work of any kind.

In a CONTRIBUTING.md file it explains *how* your code should be formatted and the steps you should go about to contribute

我们参与前要仔细阅读相关要求 Do in Rome as Rome does

As you can see this contributor file has a ton of information in it. So you should definitely look for a CONTRIBUTING.md file when you want to contribute to a project.

#### GitHub Issues

比较大的变动，和开发者或者维护者沟通，也可以避免别人重复劳动（比如别人已经在做你准备要做的事情）

Now, "issues" doesn't mean that there's actually a bug, it can just be any change that needs to be made to the project. GitHub's issue tractor is quite sophisticated. Each issue can:

- have a label or multiple labels applied to it 可以有一个或者多个标签
- can be assigned to an individual 可以分配给个人
- can be assigned a milestone (for example the issue will be resolved by the next major release) 可以分配给一个里程碑

每一个issue，提供给参与者一个表单可以追踪一个话题

Another thing that's nice about issues is:

- they let you subscribe to an issue so you'll be notified of new comments and code changes-可以订阅这个话题，可以收到新的评论和代码变动
- you can communicate back and forth with a project maintainer on a specific change -以与项目维护者就特定的更改进行交流

发表新的话题前，应该提前搜索是否已经存在。

#### New Issue Page

如果repo包含CONTRIBUTING.md ，当提交新的话题时，会提醒你去查看指导方案。

话题页面支持MK语法，Udaciy有这门[课程](https://www.udacity.com/course/writing-readmes--ud777)

1. an issue with an informative title that explains briefly what you want to do 标题要简明说明
2. provide plenty of detail on what the change is, or why you think it's needed, or how this will make the project better 解释如何提升了项目
3. Once the project maintainer has given you the go-ahead it's time to start working on the changes you want to contribute back to the project. 等待项目维护者批准

#### 话题分支 Topic Branches

针对issue 创建一个话题分支，命名可以参考：

- `login`
- `login-bug`
- `signup-bug`
- `login-form-bug`
- etc.

So definitely check out the CONTRIBUTING.md file to see if they provide instructions on what you should name your topic branches.

命名分支前需要参考指导文档，`bugfix-` prefix.

#### 最佳实践 Best Practices

1. Write Descriptive Commit Messages 编写描述性提交消息

   ​	The more descriptive your branch name and commit messages are the more likely it is that the project's maintainer will not have to ask you questions about the purpose of your code or have dig into the code themselves.

2. Create Small, Focused Commits  更小的提交，更容易通过

   make sure your commits are in small enough chunks and that each commit is focused on altering just one thing. This way the maintainer can say I like commits A, B, C, D, and F but not commit E.

3. Update The README

   And lastly if any of the code changes that you're adding drastically changes the project you should update the README file to instruct others about this change.

   如果发生了重大改变，应该更新README文档中相关部分

#### 如何优雅的合作总结:

1. 开始之前，应该检查CONTRIBUTING.md 。Before you start doing any work, make sure to look for the project's CONTRIBUTING.md file.
2. 创建issue
   * ook at the existing issues to see if one is similar to the change you want to contribute 查看是否已经存在相近的话题
   * if necessary create a new issue 
   * communicate the changes you'd like to make to the project maintainer in the issue 和项目者在issue中沟通将要做的改变
3. 开始改进工作，在话题分支上进行
   * do not work on the master branch
   * make sure to give the topic branch clear, descriptive name 给出清晰的表述性的提交名称
4. general best practice for writing commits 书写提交的最佳实践
   * make frequent, smaller commits 小型化提交
   * use clear and descriptive commit messages 清楚描述性的提交信息
   * update the README file, if necessary

## Create a Pull Request

A **pull request** is a request to the *original* or *source repository's* maintainer to include changes in their project that you made in your fork of their project.

请求项目维护者包含自己在fork项目中做的改变。

自己创先的fix-bug-** 分支pull给项目维护者，接受后会在master 创建merge 然后point指向合并后的新提交

~~~bash
$ git push -u origin master
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'origin'.

Admin@DESKTOP-BEH3BD4 MINGW64 /d/Online/Udacity/course-collaboration-travel-plans (add-city-of-China)
$ git push -u origin add-city-of-China
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 615 bytes | 87.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote:
remote: Create a pull request for 'add-city-of-China' on GitHub by visiting:
remote:      https://github.com/sanhu88/course-collaboration-travel-plans/pull/new/add-city-of-China
remote:
To github.com:sanhu88/course-collaboration-travel-plans.git
 * [new branch]      add-city-of-China -> add-city-of-China
Branch 'add-city-of-China' set up to track remote branch 'add-city-of-China' from 'origin'.

~~~



As long as you following the steps we covered in the previous section on:

- reviewing the project's CONTRIBUTING.md file 查看CONTRIBUTING
- checking out the project's existing issues 查看issue里是否存在相同话题
- talking with the project maintainer 和项目维护者沟通

总结：

- you must *fork* the source repository 分发到自己的账号
- clone your fork down to your machine 克隆到本地
- make some commits (ideally on a topic branch!) 创建提交
- push the commits back to *your fork* 提交到自己fork的
- create a new pull request and choose the branch that has your new commits 创建pull