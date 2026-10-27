---
category: coding
date: 2012-11-15
title: 《UNIX环境高级编程》学习笔记
---

# 《UNIX 环境高级编程》学习笔记

Thread synchronization, deadlock avoidance( same locking order)

Register, volatile, automatic variables( storage location). an automatic variable can never be referenced after the function that declares it returns.

赋值传递，引用传递

指针变量本身不一定存储在堆中。

## A basic understanding of the characteristics of atomic operation

Atomicity does not prevent an operation from failure( e.g. power lose), it only ensures that when it fails, it fails completely.

Basically a system treats an atomic operation as failed by default from the beginning, and only accept it as successful until the last instruction is completed. If anything causes the operation failure( e.g. Power lose), the system will simply treat it as failed and will not attempt to recover it afterwards.

So data lose caused by failure is inevitable, atomicity only means if it fails, if fails completely.

Any state before the final state is treated as failure in an atomic operation.

## The difference between Noblocking IO and Asyncronous IO

Noblocking IO is a machenism to allow the caller read or write a file which can return immediately.

Asyncronous IO is to let the system notify the caller when the file is available.

## Unix system calls

Unix system calls( write, create, etc) are wrappers of CPU instructions( MOV, ADD, CALL, etc).

微机原理学的是 CPU 指令，与操作系统无关的。操作系统调用是对 CPU 指令的封装。而 C 库函数又是对系统调用的封装。

## IPC

Chapter 5 Interprocess Communication
In this chapter, we discuss five types of interprocess communication:

- Shared memory permits processes to communicate by simply reading and writing to a specified memory location.
- Mapped memory is similar to shared memory, except that it is associated with a file in the filesystem.
- Pipes permit sequential communication from one process to a related process.
- FIFOs are similar to pipes, except that unrelated processes can communicate because the pipe is given a name in the filesystem.
- Sockets support communication between unrelated processes even on different computers.

These types of IPC differ by the following criteria:

- Whether they restrict communication to related processes (processes with a common ancestor), to unrelated processes sharing the same filesystem, or to any computer connected to a network
- Whether a communicating process is limited to only write data or only read data
- The number of processes permitted to communicate
- Whether the communicating processes are synchronized by the IPC — for example, a reading process halts until data is available to read

### 5.1 Shared Memory

One of the simplest interprocess communication methods is using shared memory.

Shared memory allows two or more processes to access the same memory as if they all called malloc and were returned pointers to the same actual memory. When one process changes the memory, all the other processes see the modification.

### 5.1.1 Fast Local Communication

**Shared memory is the fastest form of interprocess communication because all**

**processes share the same piece of memory.** Access to this shared memory is as fast as accessing a process’s nonshared memory, and it does not require a system call or entry to the kernel. It also avoids copying data unnecessarily.

### 5.3 Mapped Memory

**Mapped memory permits different processes to communicate via a shared file.**

Although you can think of mapped memory as using a shared memory segment with a name, you should be aware that there are technical differences. Mapped memory can be used for interprocess communication or as an easy way to access the contents of a file.

### 5.4 Pipes

A pipe is a communication device that permits unidirectional communication. Data written to the “write end” of the pipe is read back from the “read end.” Pipes are serial devices; the data is always read from the pipe in the same order it was written.

**Typically, a pipe is used to communicate between two threads in a single process or between parent and child processes.**

In a shell, the symbol | creates a pipe. For example, this shell command causes the shell to produce two child processes, one for ls and one for less:

% ls | less

The shell also creates a pipe connecting the standard output of the ls subprocess with the standard input of the less process.The filenames listed by ls are sent to less in exactly the same order as if they were sent directly to the terminal.

A pipe’s data capacity is limited. If the writer process writes faster than the reader process consumes the data, and if the pipe cannot store more data, the writer process blocks until more capacity becomes available. If the reader tries to read but no data is available, it blocks until data becomes available.Thus, the pipe automatically synchronizes the two processes.

### 5.4.5 FIFOs

**A first-in, first-out (FIFO) file is a pipe that has a name in the filesystem**. Any process can open or close the FIFO; the processes on either end of the pipe need not be related to each other. FIFOs are also called named pipes.

### 5.5 Sockets

A socket is a bidirectional communication device that can be used to communicate with another process on the same machine or with a process running on other machines.

**Sockets are the only interprocess communication we’ll discuss in this chapter that**

**permit communication between processes on different computers.** Internet programs such as Telnet, rlogin, FTP, talk, and the World Wide Web use sockets.

## System memory layout

**Physical and virtual memory maps**

![]({{site.baseurl}}/assets/images/XqsBMgx.png)

The physical map of a system is usually available with the technical literature accompanying your hardware. In the case of the iPAQ, the StrongARM manual, the SA-1110 Developer's manual, is available from Intel's web site.

The physical map is important, because it provides you with information on how to configure the kernel and how to develop custom drivers. During the kernel's configuration, for instance, you may need to specify the location of the flash devices in your system. During development, you may also need to write a driver for a memory-mapped peripheral. You will also need to provide your bootloader with information regarding the components it has to load. For these reasons, it is good practice to take the time to establish your system's physical memory map before starting software development.
