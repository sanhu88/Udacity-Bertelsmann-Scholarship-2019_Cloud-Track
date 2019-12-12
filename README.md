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



