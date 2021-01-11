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
              |  |    |---------------------------------- user group name
              |  |--------------------------------------- user name 
              |------------------------------------------ hard link number

$ chown - change file owner and group 
$ chgrp - change group ownership
$ dpkg - package manager for Debian
  dpkg -l|--list List packages concisely
  dpkg -r|--remove <package>
$ rpm - RPM Package Manager
  rpm -qa 

$ grep, egrep, fgrep, rgrep - print lines that match patterns
$ more - file perusal filter for crt viewing 
  > more是分页只能往后翻页，翻到最后一页自动结束返回命令行
$ less - opposite of more
  > less是往前往后都能翻页，需要输入q|quit返回命令行
$ apt-get - APT package handling utility -- command-line interface
$ apt-cache - query the APT cache
$ wget - The non-interactive network downloader
$ tar - an archiving utility
$ nohup - run a command immune to hangups, with output to a non-tty (no hang up)
    ➜ nohup date > date.out 2>&1 &
    [1] 3623008
    [1]  + 3623008 done       nohup date > date.out 2>&1
  
  # 1: 标准输出; 2: 标准错误输出; 
  # 2>&1: 表示标准输出和错误输出合并
  
    ➜ cat date.out
    nohup: ignoring input
    Sun Jan 10 15:14:34 CST 2021
$ ps - report a snapshot of the current processes
$ awk - pattern scanning and processing language
$ xargs - build and execute command lines from standard input
$ systemctl - Control the systemd system and service manager
  start - Start (activate) one or more units
  stop - Stop (deactivate) one or more units
  enable - Enable on or more unit files
$ shutdown - Halt, power-off or reboot the machine
```

* System Call
```
fork - create a child process
  > Linux中，创建一个新进程需要父进程(Parent Process)调用fork实现，新产生的子进程(Child Process)

  > 对于fork系统调用的返回值，如果当前进程是子进程，就返回0, 如果当前进程是父进程，就返回子进程的进程号

execve - execute program

wait, waitpid, waitid - wait for process to change state

Code Segment: 代码段 -- 存放程序代码
Data Segment: 数据段 -- 进程运行中产生数据的部分
Heap: 堆 -- 动态分配 较长时间保存，指明才销毁

brk, sbrk - change data segment size
mmap, munmap - map or unmap files or devices into memory


# 文件管理
open, openat, creat - open and possibly create a file
close - close a file descriptor
lseek - reposition read/write file offset
read - read from a file descriptor
write - write to a file descriptor

File Descriptor: 文件描述符

# 项目异常处理与信号处理
kill - send a signal to a process
sigaction, rt_sigaction - examine and change a signal action

# 进程间通信
Message Queue: 消息队列
msgget - get a System V message queue identifier
msgrcv, msgsnd - System V message queue operations

Share Memory
shmget - allocates a System V shared memory segment
shmat, shmdt - System V shared memory operations

Semaphore: 信号量
sem_wait, sem_timedwait, sem_trywait - lock a semaphore
sem_post - unlock a semaphore

Socket: 套接字

glibc - The GNU C Library project provides the core libraries for the GNU system and GNU?Linux systems, as well as many other systems that use Linux as the kernel.
strace - trace system calls and signals
```

* X86 Arch
```
# 计算机的工作模式
CPU: Central Processing Unit 中央处理器
  - 运算单元 - 加、减、位移操作
  - 数据单元 - 包括CPU内部的缓存和寄存器组
    - 通用寄存器: 8086处理器内部有8个16位的通用寄存器
      - AX [AH AL] H: High, L: Low
      - BX [BH BL]
      - CX [CH CL]
      - DX [DH DL]
      - SP 
      - BP 
      - SI 
      - DI
  - 控制单元 - 获得下一条指令
    - IP: Instruction Pointer Register 指令指针寄存器:存放下一条指令在内存中的地址
    - 段寄存器:为了指向不同进程的地址空间,四个16位的段寄存器
      - CS - Code Segment Register 代码段寄存器
      - DS - Data Segment Register 数据段寄存器
      - SS - Stack Register 栈寄存器 [Push: 入栈 Pop: 出栈]
      - ES - 
    - 8086CPU 最多只能访问1M的内存空间，段最多64K。
BUS: 总线
  - Address Bus: 地址总线
  - Data Bus: 数据总线
Memory: 内存
Real Pattern: 实模式
Protected Pattern: 保护模式

Process Switch: 进程切换

汇编语言指令集:
  MOV: 传送字或字节
  CALL: 过程调用
  JMP: 无条件转移指令
  INT: 中断指令
  RET: 过程返回
  ADD: 加法
  OR: 或运算符
  XOR: 异或运算
  SHL: 逻辑左移
  SHR: 逻辑右移
  PUSH: 把字压入堆栈
  POP: 把字弹出堆栈
  INC: 加1
  DEC: 减1
  SUB: 减法
  CMP: 比较(两个操作数作减法，仅修改标志位，不回送结果)
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

Appendix C
-----------
* The Linux Kernel Archives [5.10.6]
