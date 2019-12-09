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

## repo

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

This command:

- lists one commit per line
- shows the first 7 characters of the commit's SHA
- shows the commit's message



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

This command:

- displays the file(s) that have been modified
- displays the number of lines that have been added/removed
- displays a summary line with the total number of modified files and lines that have been added/removed