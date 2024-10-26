# Mach

* `Mach`
  * 是什么：操作系统的内核
  * 类型：`Microkernel`=`微内核`
  * 发展历史
    * 最早：卡耐基梅隆大学开发
      * 目标：取代`BSD`的`UNIX`核心
    * 后来：Apple采用，作为`Darwin`的核心的`XNU`的其中一部分
  * 历史版本
    * 早期
      * `Mach v2.5`
        * 来自：`Carnegie Mellon University`=`卡耐基梅隆大学`
      * `Mach v3.0`
        * 来自：`Carnegie Mellon University`=`卡耐基梅隆大学`
      * `Mach v4`
        * 来自：`University of Utah`=`犹他大学`
    * 后来
      * `OSFMK` 7.3
        * `OSFMK`=`Open Software Foundation Mach Kernel`
          * 来自：`OSF`=`The Open Software Foundation`
  * （这个微内核）包含=组成
    * 仅能处理最基本的操作系统职责
      * 虚拟内存的管理=`memory protection`=`Virtual Memory`=`Protected Memory`
        * virtual memory support
          * support for large virtual address spaces, shared memory regions, and memory objects backed by persistent store
        * support for pagers
      * 任务管理
        * 进程和线程的抽象
          * `Parallel Execution`
            * `Preemptive Multitasking`=preemptively scheduled threads
            * 支持`SMP`
        * 任务调度
        * `IPC`=进程间通信=进程间通信和消息传递机制
          * messaging
            * 概述：a messaging-centered infrastructure
            * `Message Passing`=`消息传递`
          * `RPC`
          * synchronization
          * notification
  * 特点
    * 优点
      * 服务进程容易扩展
        * 得益于这种扩展性，使得
          * `Mach-O`能支持多架构文件
            * 详见
              * [可执行文件格式：Mach-O](https://book.crifan.org/books/exec_file_format_macho/website/)
          * [macOS](../../ios_internal_logic/apple_os_part/darwin/macos.md)能顺利的从`PowerPC`过渡到`Intel`再到`M1`
      * 服务进程出问题不会危及到`kernel`
    * 缺点
      * 微内核的功能本来就少，其他 OS 功能是作为基础服务建设在用户模式下的。因为这个特性其内部任务的调用会有更频繁的内核态/用户态上下文切换，这会额外消耗时间。同时内核与服务进程之间的消息传递也会降低运行效率，所以这种设计通常会降低性能
  * 资料
    * [Mach Overview](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Mach/Mach.html)

## Mach Message=Mach消息（传递）

* Mach Message
  * （Mach的IPC的）核心点
    * Mach最基础的概念就是两个端点`Port`中交换的`message`
  * message
    * 是什么：一个message就是msgh_size大小的blob, 带着一些flags，从一个端口发送到另一个端口
  * 核心函数
    * `mach_msg()`
    * `mach_msg_send()`
    * `mach_msg_receive()`
    * `mach_msg_trap()`
    * `mach_msg_overwrite_trap()`
  * 架构
    * ![mach_msg_arch](../../assets/img/mach_msg_arch.webp)
  * Mach Message细节
    * ![mach_message_layout](../../assets/img/mach_message_layout.png)

### 相关定义

* `<mach/message.h>`

```c
typedef struct {
    mach_msg_header_t header;
    mach_msg_body_t   body;
} mach_msg_base_t;

// 消息头是必须的，它定义了一个消息所需要的数据
typedef struct {
    mach_msg_bites_t   msgh_bits;
    mach_msg_size_t    msgh_size;
    mach_port_t        msgh_remote_port;
    mach_port_t        msgh_local_port;
    mach_msg_size_t    msgh_reserved;
    mach_msg_id_t      msgh_id;
} mach_msg_header_t;

mach_msg_return_t mach_msg(mach_msg_header_t            msg,f
                           mach_msg_option_t            option,
                           mach_msg_size_t              send_size,
                           mach_msg_size_t              reveive_limit,
                           mach_port_t                  reveive_name,
                           mach_msg_timeout_t           timeout,
                           mach_port_t                  notify,
                           );
```