## Linux系统常用命令

[Linux 常用操作命令大全](https://blog.csdn.net/m0_46422300/article/details/104645072)



#### 更改用户密码

- 转为root用户

  ```bash
  sudo su
  ```

- ```bash
  sudo passwd user (user 是对应的用户名)
  ```



#### 查看进程



#### 编译C/C++代码

##### 编译过程

- 预处理/预编译（Preprocessing）：**.c==>.i**。处理源代码文件并执行一些预处理指令（以`#`开头，如`#include`用于包含头文件、`#define`用于宏定义等）
- 编译（Compilation）：**.i==>.s**。将预处理后文件翻译成汇编语言的过程。
- 汇编（Assembly）：**.s==>.o**。将汇编代码翻译成机器码的过程，通常是二进制形式的指令。，这一步由汇编器（assembler）执行。
- 链接（Linking）：**.o==>.exe**。链接是将程序中所有的模块（例如，源文件和库文件）组合在一起，生成最终的可执行文件的过程。

##### C/C++编译过程中产生的文件

.c（c源文件）==> .i（intermediate预处理后的中间文件） ==> .s（汇编文件） ==> .o（object目标文件，二进制码） ==> 可执行文件

```
在Linux和类Unix系统上，可执行文件通常没有特定的后缀名，这是因为Unix操作系统的文件类型由文件的权限位（权限模式）和文件内容来确定，而不是由文件的扩展名来决定。这种设计有几个原因：

1. **Unix哲学**：Unix哲学强调简单性和通用性。在Unix系统中，文件是按照其用途和内容来管理的，而不是依赖于文件名的扩展名。这使得文件类型更加灵活，允许用户根据需要更改文件的用途，而无需更改文件名。

2. **可移植性**：Unix系统的设计目标之一是可移植性，因此文件类型的标识符应该是不依赖于特定操作系统或文件系统的。使用扩展名来表示文件类型可能会导致可移植性问题，因为不同的操作系统和文件系统可能对扩展名有不同的处理方式。

3. **安全性**：在Unix系统上，文件的权限位（读、写、执行权限等）用于确定谁可以访问和执行文件，而不是依赖于文件名。这有助于系统管理员更好地控制文件的安全性，而不受文件名的影响。

4. **文件内容的多样性**：Unix系统支持各种不同类型的文件内容，包括文本文件、二进制文件、脚本文件等。为不同类型的文件指定扩展名可能会变得复杂，而不是简单而通用的。

虽然在Unix系统上没有强制要求可执行文件的后缀名，但是开发者和用户通常会约定一些命名规则，以便更容易识别文件的用途。例如，约定将可执行文件命名为没有扩展名或使用`.bin`、`.sh`、`.out`等后缀名来表示可执行文件。但是这些约定仍然是可选的，不会影响文件的执行或系统的正常运行。
```

##### 命令行编译

```bash
gcc -E hello.c -o hello.i  # 预处理阶段
gcc -S hello.i -o hello.s  # 编译阶段
gcc -c hello.s -o hello.o  # 汇编阶段
gcc hello.o -o hello       # 链接阶段
```

```bash
-o 选项：-o 选项用于指定编译输出文件的名称。
-E 选项：-E 选项用于执行预处理步骤而不进行编译
-S 选项：-S 选项用于生成汇编代码文件（.s 文件），而不进行汇编和链接。
-c 选项：-c 选项用于编译源代码文件，生成目标文件（.o 文件），但不进行链接操作。
```



##### 借助make编译

```bash
```

##### 借助cmake生成MakeFile



#### Vim

```bash
vim +行数 文件路径	//打开文件时，将光标移动到「指定行」
```

```bahs
:w		//保存文件
:W!		//若文件为只读模式，强制保存文件
:q		//离开vi/vim
:q!		//不保存强制离开vi
:wq		//保存并离开
:wq!	//强制保存后离开
```







1. ls: 在根目录下查看当前目录下的所有文件

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image002.png)

2. mkdir code：在根目录下创建一个名为code的目录

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image004.png)

3. rmdir code：删除根目录下的code子目录

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image006.png)

4. cd /etc：切换到根目录下的etc目录

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image008.png)

5. pwd：查看当前位置路径

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image010.png)

6. cp -r /code/pycode /code1：将/code/pycode目录下的所有文件复制到code1目录下

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image012.png)

7. mv code1 codeint：将目录code1改名为codeint

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image014.png)

8. rm test.txt：删除pycode目录下的test.txt文件

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image016.png)

9. chmod guo+w code1/py：将code1.py文件设置为所有人皆可写

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image018.png)

10. find . -name “*.py”：将当前目录及其子目录下所有文件后缀名为.py的文件列出来

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image020.png)

11. tar -zcvf abc.tgz abc：将abc文件夹中的所有文件压缩成一个文件abc.tgz，保存在根目录下。

tar -zxvf abc.tgz：将压缩文件解压到当前目录

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image022.png)

12. gzip a.txt：将a.txt文件压缩为a.txt.gz，并删除源文件

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image024.png)

13. cat a.txt：查看a.txt和b.txt文件的内容

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image026.png)

14. more test.cpp：一页一页地显示test.cpp中的内容

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image028.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image030.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image032.png)

15. less -e test.cpp：显示test.cpp的内容，按空格可以逐行显示，-e表明文件显示结束后会自动离开。

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image034.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image036.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image038.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image040.png)

16. echo ‘beautiful “world” it is.’：要打印双引号，需将其放入单引号或用反斜杠字符进行转义。

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image042.png)

17. date +”%Y-%m-%d”：以年-月-日的格式显示当前日期

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image044.png)

18. write root：tt用户通过write命令向root用户发送“hello, I’m tt”的信息。

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image046.png)

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image048.png)

19. mesg：查看当前终端的写权限，即是否让其他用户向本终端发信息，y-有，n-无。

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image050.png)

20. ps -A：一次性给出当前系统中进程状态

![img](https://raw.githubusercontent.com/fograinwater/PicGo-img/master/clip_image052.png)   

21. top  -d2：每隔2秒动态地持续监听进程的运行状态



#### 同时运行多个命令

##### 连续运行命令

前一命令运行完毕后后一命令就开始运行，不论前一命令运行是否成功。

command1运行完毕后运行command2，command2运行完毕后运行command2。

```bash
$ command1 ; command2 ; command3
```

##### 使用逻辑运算符

根据前一个命令运行成功或失败的状态来决定是否运行。

`&&`：在前一个命令运行成功后执行下一条命令

`||`：在前一个命令运行失败后执行下一条命令

```bash
$ command1 && command2 	# command1运行成功后运行command2
$ command1 || command2	# command1运行失败后运行command2
```

##### 并行执行命令

使命令在后台并行执行，而不会阻塞当前终端。

如果用&连接多个命令则会使多个命令同时在后台执行。

如果运行在后台的命令有输出的话还是会输出到终端，因此在这种情况下最好将输出重定向到一个文件中。

```bash
$ command &					# 后台执行单个命令
$ command1 & command2	&	# command1和command2同时执行
```

##### 持续后台运行

命令在后台运行且不会随着终端的关闭而停止

```bash
$ nohup command &			
```

##### 分组命令

如果要按照特定顺序执行一组命令，可以使用括号+逻辑运算符+并行运算符的组合。

```bash
$ (command1 ; command2) && command3	# command1和command2都运行后再运行command3
```

##### 使用命令行管道

将一个命令的输出传递给另一个命令作为输入。

```bash
$ command1 | command2		# 将command1的输出作为command2的输入
```

##### 编写bash脚本自动化重复任务

如果需要经常执行一组特定的命令，可以通过编写一个简单的bash脚本来实现。

- 在文本编辑器中编写bash命令，并将其保存为`.sh`拓展名
- 运行 `chmod +x myscript.sh` 使脚本可执行
- 使用 `./myscript.sh` 执行该脚本

`myscript.sh`：

```bash
#!/bin/bash
command1 & command2 
```



#### 杀死进程

##### kill 根据PID杀死进程

- 查找命令对应的PID

  ```bash
  $ ps aux | grep command_name
  或
  $ pgrep -x command_name
  ```

- 使用kill命令终止进程

  ```bash
  $ kill PID		# 杀死对应PID的进程
  $ kill -9 PID	# 强制杀死进程
  ```

##### pkill 根据命令名杀死进程

终止名为 `command_name` 的所有相关进程

```bash
$ pkill -x command_name
```



#### 输入输出重定向

##### 标准输入重定向 `<`

```bash
$ command < input.txt
```

##### 标准输出重定向 `>`

```bash
$ command > output.txt	# 将输出保存到文件中，并覆盖现有文件的内容
```

##### 标准输出追加重定向 `>>`

```bash
$ command >> output.txt	# 将输出附加到文件末尾，而不覆盖现有文件的内容
```

##### 标准错误输出重定向 `2>`

```bash
$ command 2> error.txt
```

##### 标准错误输出追加重定向 `2>>`

```bash
$ command 2>> error.txt
```

##### 管道

```bash
$ command1 | command2
```





