Linux系统常见问题

##### 配置gedit编辑项

[ubuntu下gedit设置行号、tab宽度、显示样式等](https://blog.csdn.net/qq_34160841/article/details/106173106)

修改gedit的preference配置时报错：`failed to commit changes to dconf: Failed to execute child process “dbus-launch” (No such file or directory)`。

解决办法：安装`dbus-x11`

```bash
sudo apt-get update
sudo apt-get install dbus-x11
```

`gedit`是Linux系统中的一个文本编辑器

`D-Bus`是一个用于在Linux和Unix系统中进行进程间的通信（IPC）的**消息总线系统**。它允许不同应用程序或进程能够以结构化的方式相互通信。

`dbus-x11`是一个

`daemon`守护进程

`D-Bus`总线系统

每个总线都有一个唯一的地址，客户端可以通过该地址连接到总线并与其他客户端通信。

系统总线

会话总线

`D-Bus`的对象（原生对象、对象路径）和接口

- 当应用程序要使用D-Bus发送消息时，应用程序通过创建对象实例native object进行D-Bus的通信；
- 这些对象实例都有一个唯一的对象路径（例如/com/mycompany，因为D-Bus只处理object path），用于消息的路由；
- 每个对象路径下都可以包含多个接口，接口定义了一组方法和属性，可供客户端调用和访问。D-Bus对接口的命名方式，类似org.freedesktop.Introspectable。

`D-Bus`消息传递

D-Bus通信基于消息传递，客户端可以向总线发送消息，其他客户端可以订阅并接收这些消息。

`D-Bus`消息（消息通常包括目标对象路径、目标接口、方法名以及参数）：

- 方法调用消息（method calls）：调用对象的一个方法
- 方法返回消息（method returns）：触发的方法返回的结果
- 信号（signals）：可看作事件消息，用于通知其他应用程序或进程发生了某个事件或状态的变化，比如系统状态的变化、硬件设备的插拔、应用程序内部的事件等等。信号属于广播消息，不需要响应，当接收方通过注册列表（match rules）向daemon注册匹配的条件后，bus daemon会将signals发送给对它感兴趣的所有进程。信号的组成通常如下：
  - 信号源：指示发出信号的对象和接口
  - 信号类型
  - 参数：附加数据
- 错误（errors）：触发的方法返回一个异常

`D-Bus`发布/订阅机制

D-Bus使用发布/订阅模式，允许客户端订阅感兴趣的消息。这样，当某个消息与订阅的条件匹配时，订阅者将收到该消息。这使得多个客户端可以监听同一消息，而无需直接相互通信。

`D-Bus`权限和访问控制

D-Bus提供了权限管理机制，可以控制哪些进程可以连接到总线、哪些对象和接口可以访问以及哪些消息可以发送。这有助于确保安全性和隐私。

`D-Bus`地址

连接建立需要server和client，对于bus daemon，应用就是client，daemon就是server。

地址是指server用于监听，client用于连接的地方。

`D-Bus`语言绑定

D-Bus具有多种编程语言的绑定，使开发者可以在他们熟悉的编程语言中使用D-Bus。这包括C、C++、Python、Java等。



##### 配置vim编辑项

- 打开配置文件

  ```bash
  vim /etc/vim/vimrc
  ```

- 在打开的配置文件底部添加：

  ```bash
  syntax on //设置语法高亮
  
  set tabstop=4 //设置制表符宽度为4 或 set ts=4
  
  set expandtab //设置tab展开的（分开各个空格符）
  
  set softtabstop=4 //设置软制表符宽度为4
  
  set shiftwidth=4 //设置缩进的空格数为4
  
  set autoindent //设置自动缩进
  
  set cindent //设置使用 C/C++ 语言的自动缩进方式
  
  set nu //在左侧显示文本的行号
  ```



IPC进程间通信



WSL









