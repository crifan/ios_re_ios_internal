# Apple苹果相关开发资料

TODO：

* 【已解决】iOS中st_size的off_t是什么类型
* 【已解决】iOS或Linux或C中pid_t的定义

---

此处整理，Apple苹果的，和iOS逆向相关的，尤其是涉及到iOS底层机制方面的，开发资料。

* `Apple`=`苹果`
  * 相关开发资料
    * 源码 源代码
    * 官网文档

## Apple苹果官网

### 源码+文档

概述=总入口：

[Open Source - Apple Developer](https://developer.apple.com/opensource/)

详解：

* 开源代码Open Source Projects
  * Apple Open Source
    * https://opensource.apple.com
      * 文档
        * Kernel
          * https://developer.apple.com/library/mac/#documentation/Darwin/Conceptual/KernelProgramming/build/build.html
        * Frameworks
          * https://developer.apple.com/library/mac/#documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html
        * Security
          * https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Introduction/Introduction.html
      * 源码
        * 离线下载 源码 总入口
          * https://opensource.apple.com/tarballs/
          * 子模块
            * ObjC Runtime
              * https://opensource.apple.com/tarballs/objc4/
            * xnu
              * https://opensource.apple.com/tarballs/xnu/
            * dyld
              * https://opensource.apple.com/tarballs/dyld/
            * cctools
              * https://opensource.apple.com/tarballs/cctools/
        * 在线浏览 源码 总入口
          * https://opensource.apple.com/source/
          * 子模块
            * xnu
              * https://opensource.apple.com/source/xnu/
              * kern
                * sysctl
                  * https://opensource.apple.com/source/xnu/xnu-792/bsd/kern/kern_sysctl.c.auto.html
            * dlyd
              * https://opensource.apple.com/source/dyld/
            * system_cmds
              * https://opensource.apple.com/source/system_cmds/
              * sysctl
                * system_cmds-880.60.2
                  * https://opensource.apple.com/source/system_cmds/system_cmds-880.60.2/sysctl.tproj/
                    * sysctl的源码
                      * https://opensource.apple.com/source/system_cmds/system_cmds-880.60.2/sysctl.tproj/sysctl.c.auto.html
            * Libc
              * posix_spawn
                * https://opensource.apple.com/source/Libc/Libc-825.25/sys/posix_spawn.c.auto.html
            * objc4 = Objc
              * https://opensource.apple.com/source/objc4/
              * 不同版本
                * https://opensource.apple.com/source/objc4/objc4-818.2/
                * https://opensource.apple.com/source/objc4/objc4-532
                * https://opensource.apple.com/source/objc4/objc4-646
              * 子模块
                * runtime
                  * objc_release
                    * https://opensource.apple.com/source/objc4/objc4-532/runtime/NSObject.mm.auto.html
                  * objc_alloc
                    * https://opensource.apple.com/source/objc4/objc4-646/runtime/objc-internal.h
                  * objc_msgSendSuper2
                    * https://opensource.apple.com/source/objc4/objc4-532/runtime/objc-abi.h.auto.html
                  * objc_retainBlock
                    * https://opensource.apple.com/source/objc4/objc4-493.9/runtime/objc-arr.mm.auto.html
            * libpthread
              * pthread_get_stackaddr_np
                * https://opensource.apple.com/source/libpthread/libpthread-105.10.1/src/pthread.c.auto.html
  * MacOS Forge
    * [www.macosforge.org](http://www.macosforge.org/)

### 函数和命令的文档

注：`man` = `manual` = `手册`

* Apple文档总入口：[Documentation Archive (apple.com)](https://developer.apple.com/library/archive/navigation/index.html)
  * 函数 man手册 总入口：[API Reference: iOS Manual Pages (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/index.html)
    * 分很多大类
      * Section 2: system calls and error numbers
        * Section 2 of the manual contains documentation on UNIX system calls, error codes, and C library routines that wrap system calls. Most of these functions are described in headers that reside in /usr/include/sys.
        * For a detailed introduction, see intro(2)
          * [Mac OS X Manual Page For intro(2) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man2/intro.2.html#//apple_ref/doc/man/2/intro)
      * Section 3: C libraries
        * Section 3 of the manual contains documentation on C library routines. This section excludes library routines that merely wrap UNIX system calls. Most of these functions are described in headers that reside in /usr/include or subdirectories therein.
        * For a detailed introduction, see intro(3)
          * [Mac OS X Manual Page For intro(3) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/intro.3.html#//apple_ref/doc/man/3/intro)
      * Section 3cc: 加密 解密 算法 相关
        * [API Reference: iOS Manual Pages (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/index.html#group_Section_3cc)
      * Section 3ssl
        * Section 3ssl of the manual contains documentation on OpenSSL library routines. These functions are described in headers that reside in /usr/include/openssl, and are split between the libssl and libcrypto libraries
        * For a detailed introduction, see crypto(3) and ssl(3)
          * [Mac OS X Manual Page For crypto(3ssl) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/crypto.3ssl.html#//apple_ref/doc/man/3/crypto)
            * crypto - OpenSSL cryptographic library
          * [Mac OS X Manual Page For ssl(3ssl) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/ssl.3ssl.html#//apple_ref/doc/man/3/ssl)
            * SSL - OpenSSL SSL/TLS library
      * Section 3x
        * Section 3x of the manual contains documentation on curses-related library routines used for general formatting on text terminals. These functions are described in headers that reside in /usr/include, and are located in the libncurses library.
        * For a detailed introduction, see ncurses(3)
          * [Mac OS X Manual Page For ncurses(3x) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/ncurses.3x.html#//apple_ref/doc/man/3/ncurses)
            * ncurses - CRT screen handling and optimization package
      * Section 5
        * Section 5 of the manual contains documentation on file formats and conventions. It includes documentation about file-system data structures, information about configuration files for various daemons, and information about data structures used in various binary and text file formats used by various parts of the operating system.
        * For a detailed introduction, see intro(5).
          * [Mac OS X Manual Page For manpages(5) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man5/manpages.5.html)
            * manpages -- An introduction to manual pages

#### log日志的字符串格式化参数语法

[String Format Specifiers (apple.com)](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFStrings/formatSpecifiers.html#//apple_ref/doc/uid/TP40004265)

## The iPhone Wiki

### syscall

[Kernel Syscalls - The iPhone Wiki](https://www.theiphonewiki.com/wiki/Kernel_Syscalls)

### hw.machine 机型 映射

* [Models - The iPhone Wiki](https://www.theiphonewiki.com/wiki/Models)

## 其他来源

### 内核原理和机制

[OS Internals: (newosxbook.com)](http://newosxbook.com/index.php?page=Appendix)

->

* [MAC OS X Internals: A Systems Approach: Singh, Amit: 9780321278548: Books: Amazon.com](https://www.amazon.com/gp/product/0321278542/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321278542&linkCode=as2&tag=newosxbookcom-20)
* [J's Entitlement DataBase (newosxbook.com)](http://newosxbook.com/ent.jl)
  * OS X/iOS Entitlement Database - v0.8
  * As compiled by Jonathan Levin, @Morpheus______
  * Now with entitlements from iOS 9.0.2 through 15.2, MacOS 11.4 through 15.3

## iOS逆向英文教程

据说是第一本英文书的专门详细介绍iOS逆向的书：

[iosre/iOSAppReverseEngineering: The world’s 1st book of very detailed iOS App reverse engineering skills :) (github.com)](https://github.com/iosre/iOSAppReverseEngineering)

->

https://github.com/iosre/iOSAppReverseEngineering/blob/master/iOSAppReverseEngineering.pdf

有需要可以学习和参考。
