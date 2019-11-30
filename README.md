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