# Udacity-Bertelsmann-Scholarship-2019_Cloud-Track
Bertelsmann Tech Scholarship Challenge Course - Cloud Track on Udacity.com

> Total 24 lessons about 35 hours 1-1 Git/ 12-24 Cloud

## 1. Shell Workshop

-  **operating system** 操作系统—like Windows, macOS, or Linux 
-  **shell** *is simply the outermost layer of an operating system. It's designed to provide a way for you to interact with the tools and services that your operating system provides.*  shell只是操作系统的最外层。它的目的是为您提供一种与操作系统提供的工具和服务进行交互的方式。 
-  **Graphical User Interface** or **GUI** (pronounced "gooey") ,  A user interface where you give instructions to the computer by interacting with things like windows, menus, icons, and buttons. 用户界面，通过与窗口、菜单、图标和按钮等交互向计算机提供指令。 
-  **Command-Line Interface** or **CLI**, A user interface where you give instructions to the computer by entering lines of text.  一种用户界面，你通过输入几行文字来给计算机指令。 
-  One of the most widely used shells is called **BASH** 

--为什么使用CLI 而不是GUI呢？

--It will make you a more powerful programmer. In other words, if you want to be a powerful developer (or even just a powerful user), it's essential to at least learn the basics of using a text shell and CLI. 

--It will open the door to other tools.

--learn Python



## 2. echo

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

## 3. Variables

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

## 4. Navigating directories

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
- ； 分号可以一行写两个命令

  BASH is a **case sensitive** language ，大小写敏感的语言

### pwd 

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