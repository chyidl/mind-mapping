GNU/Linux OS
============

Basic Linux Command Line
------------------------
```
$ passwd - change user password
$ useradd - create a new user or update default new user infomation
$ cat - concatenate files and print on the standard output
  ➜ cat /etc/passwd
  chyi:x:1000:1000:chyi,,,:/home/chyi:/usr/bin/zsh

  ➜ cat /etc/group
  chyi:x:1000:

$ ls - list directory contents
  ➜ ls -l
  drwxr-xr-x  3 chyi chyi 4096 Dec 16 23:37 Desktop
              |--- hard link number
```

Linux程序设计
------------

Linux内核机制
-------------

Linux内核源码
------------

定制化Linux组件
--------------


Appendix A:
-----------
* <鸟哥的Linux私房菜> 
* <UNIX and Linux System Administration Handbook, 5th Edition>
* <Advanced Programming in the UNIX Environment, 3rd Edition>
* <Understanding The Linux Kernel>

Appendix B:
-----------

* 1.在Linux上安装一个软件的常用方式?
```
A. make install 
B. 通过rpm 和 deb文件 
C. 通过yum 和 apt-get 
D. 下载压缩包解压缩后设置PATH
```

* 2.下列过程在实模式下运行的有
```
A. BIOS加载启动扇区
B. 启动扇区加载Grub 的 kernel.img
C. Grub 加载 Linux内核
D. Linux 内核加载驱动
```

* 3.在Linux内核初始化阶段创建进程
```
A. 0号进程是所有用户态进程的祖先
B. 1号进程是所有用户态进程的祖先
C. 1号进行是所有内核态进程的祖先 
D. 2号进程是所有内核态进程的祖先
```

* 4.属于系统调用指令的有
```
A. int $0x80 
B. sysenter 
C. syscall 
D. systemcall 
```

* 5. 对于内核中进程管理的描述
```
A. 将所有进程放在一个链表中，所有线程放在另一个链表中
B. 处于TASK_RUNNING 状态的进程一定在占用CPU 
C. 父进程和子进程之间可以通过指针相互访问 
D. 从用户态到内核态要切换到内核栈
```

* 6.进程调度
```
A. 优先级低的进程可以采取FIFO策略
B. 优先级低的进程可以采取轮流调度策略 
C. 对于普通进程可以采取CFS调度策略 
D. 对于实时进程可以采取CFS调度策略
```

* 7.对于进程的内存管理
```
A. 进程的代码非常关键，要放在内核态
B. 进程的代码非常关键，不能修改 
C. 进程的栈被划分为两部分，用户栈和内核栈
D. 不同进程的内核态映射到相同的地方
```

* 8.物理内存的管理
```
A. 无力内存先被划分为大小相同的段，然后在分为大小相同的页
B. 物理内存的页需要被标记这个页是属于内核的还是用户的
C. 很可能CPU访问不同页的页速度不同
D. 会有多个链表保存空闲的页面
```

* 9.对于文件
```
A. 文件描述符仅在一个进程内有效
B. 每个进程维护一个file链表，维护它打开的文件
C. 操作系统统一维护一个file链表，维护所有打开的文件 
D. 每个文件都要有一个inode
```

* 10.对于虚拟文件系统
```
A. 文件系统需要注册才能使用 
B. dentry结构维护了文件名和inode之间的关系
C. 每种文件系统对于读、写、打开、关闭操作都可以有自己的实现
D. 虚拟文件系统可以对接NFS之类的网络文件系统
```

* 11.对于输入输出设备
```
A. 对于设备的操作可以完全使用文件的方式
B. 块设备可以使用缓存，也可以不使用缓存进行读写
C. 字符设备可以使用缓存，也可以不使用缓存进行读写 
D. 设备也会关联inode
```

* 12. 对于网络通信
```
A. 七层协议全部都有在内核里面实现
B. 套接字也是一个文件，因而也有inode 
C. 相同机器的两个进程Socket通信智能通过Loopback 
D. 相同机器的两个进程Socket通信可以通过文件
```
