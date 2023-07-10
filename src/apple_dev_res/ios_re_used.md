# iOS逆向常涉及内容

在iOS逆向期间，常涉及到很多Apple苹果相关的开发资料，整理如下供参考。

## ObjC的类

### UIDevice

[UIDevice | Apple Developer Documentation](https://developer.apple.com/documentation/uikit/uidevice?language=objc)

## xnu

由于`xnu`很重要，iOS逆向期间经常涉及到，所以单独介绍相关内容：

* xnu
  * 离线下载
    * https://opensource.apple.com/tarballs/xnu/
  * 在线浏览
    * https://opensource.apple.com/source/xnu/

### 查看自己的xnu版本

对于自己的越狱手机，此处的iPhone7，去查看对应的xnu的版本：

```bash
➜  ~ ssh root@192.168.0.33
iPhone7:~ root# uname -a
Darwin iPhone7 19.6.0 Darwin Kernel Version 19.6.0: Sat Jun 27 04:35:37 PDT 2020; root:xnu-6153.142.1~4/RELEASE_ARM64_T8010 iPhone9,1 arm64 D10AP Darwin
```

此处被测的已越狱的iPhone的xnu是：

`xnu-6153.142.1`

去官网找对应版本的代码：

[xnu Source Browser (apple.com)](https://opensource.apple.com/tarballs/xnu/)

没看到这个版本

-》只能找到，最接近的版本：

* xnu-6153.141.1.tar.gz
  * https://opensource.apple.com/tarballs/xnu/xnu-6153.141.1.tar.gz

可下载下来，供后续参考研究。

### iOS中的基本类型的定义

关于iOS中的很多相关的底层的类型：

* __darwin_mode_t
* __darwin_off_t
* __darwin_pid_t

的定义是：

```c
typedef __uint16_t   __darwin_mode_t;        /* [???] Some file attributes */
typedef __int64_t       __darwin_off_t;         /* [???] Used for file sizes */
typedef __int32_t       __darwin_pid_t;         /* [???] process and group IDs */
```

来源：

* Apple的opensource
  * https://opensource.apple.com/source/xnu/xnu-792/bsd/sys/_types.h
* 其他
  * [apple/darwin-xnu: The Darwin Kernel (mirror)](https://github.com/apple/darwin-xnu)
    * https://github.com/apple/darwin-xnu/blob/main/bsd/sys/_types.h

### 头文件 errno.h

* 旧版本：`xnu-201`
  * https://opensource.apple.com/source/xnu/xnu-201/bsd/sys/errno.h

```c
#define ENOTSUP      45              /* Operation not supported */
#ifndef _POSIX_SOURCE
#define EOPNOTSUPP       ENOTSUP                /* Operation not supported */
```

* 新版本：`xnu-792`
  * https://opensource.apple.com/source/xnu/xnu-792/bsd/sys/errno.h.auto.html

```c
#define ENOTSUP                45              /* Operation not supported */
```

结论：

* `ENOTSUP` = `45`

### 在线浏览`xnu`代码

[XXR - XNU cross reference - Alpha (newosxbook.com)](http://newosxbook.com/xxr/index.jl)

![xnu_code_online_view](../assets/img/xnu_code_online_view.jpg)

## man手册文档

前面介绍的

Apple 函数 man手册 总入口：[API Reference: iOS Manual Pages (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/index.html)

中有很多，iOS逆向期间，常常会涉及到的一些`API`或`命令`，整理如下：

* [Section 2: system calls and error numbers](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man2/intro.2.html#//apple_ref/doc/man/2/intro)
  * ENOMEM 错误码定义
    * 12 = ENOMEM Cannot allocate memory
      * The new process image required more memory than was allowed by the hardware or by system-imposed mem-ory memory ory management constraints.  A lack of swap space is normally temporary; however, a lack of core is not.  Soft limits may be increased to their corresponding hard limits.
  * stat64
    * [Mac OS X Manual Page For stat64(2)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man2/stat64.2.html)
* [Section 3: C libraries](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/intro.3.html#//apple_ref/doc/man/3/intro)
  * system
    * [Mac OS X Manual Page For system(3)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/system.3.html)
  * sysctl
    * [Mac OS X Manual Page For sysctl(3)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/sysctl.3.html)
  * strlen
    * [Mac OS X Manual Page For strlen(3)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/strlen.3.html)

## iPhone iOS SDK 源码

* iPhoneOS13.0.sdk
  * [iOS-SDKs/iPhoneOS13.0.sdk at master · xybp888/iOS-SDKs (github.com)](https://github.com/xybp888/iOS-SDKs/tree/master/iPhoneOS13.0.sdk)
    * stat.h
      * [iOS-SDKs/stat.h at master · xybp888/iOS-SDKs (github.com)](https://github.com/xybp888/iOS-SDKs/blob/master/iPhoneOS13.0.sdk/usr/include/sys/stat.h)
    * syscall.h
      * [iOS-SDKs/syscall.h at master · xybp888/iOS-SDKs (github.com)](https://github.com/xybp888/iOS-SDKs/blob/master/iPhoneOS13.0.sdk/usr/include/sys/syscall.h)
    * sysctl.h
      * [iOS-SDKs/sysctl.h at master · xybp888/iOS-SDKs (github.com)](https://github.com/xybp888/iOS-SDKs/blob/master/iPhoneOS13.0.sdk/usr/include/sys/sysctl.h)
    * types.h
      * [iOS-SDKs/types.h at master · xybp888/iOS-SDKs (github.com)](https://github.com/xybp888/iOS-SDKs/blob/master/iPhoneOS13.0.sdk/usr/include/sys/types.h)

## 改机相关

### sysctl相关

* 苹果官网文档
  * sysctlbyname
    * [sysctlbyname | Apple Developer Documentation](https://developer.apple.com/documentation/kernel/1387446-sysctlbyname)
  * sysctl
    * [sysctl | Apple Developer Documentation](https://developer.apple.com/documentation/installer_js/system/1812308-sysctl)
* man手册
  * SYSCTL
    * [Mac OS X Manual Page For sysctlbyname(3) (apple.com)](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/sysctlbyname.3.html)
* 源码
  * [sysctl.c (apple.com)](https://opensource.apple.com/source/system_cmds/system_cmds-880.60.2/sysctl.tproj/sysctl.c.auto.html)
* 其他
  * [sysctlbyname (freebsd.org)](https://www.freebsd.org/cgi/man.cgi?query=sysctlbyname&apropos=0&sektion=0&manpath=FreeBSD+10.1-RELEASE&arch=default&format=html)
  * [sysctlbyname(3) manual page (lemoda.net)](https://nxmnpg.lemoda.net/3/sysctlbyname)
  * [sysctl, sysctlbyname (qnx.com)](http://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_lib_ref/s/sysctl.html)
  * [sysctlbyname.3 (daemon-systems.org)](https://www.daemon-systems.org/man/sysctlbyname.3.html)

## 其他

### iOS中 属性列表 Property List = plist

* [Introduction to Property Lists (apple.com)](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html#//apple_ref/doc/uid/10000048i)


### C语言相关开发整理和心得

#### gcc

编译时-Wxxx的参数：

* [Warning Options (Using the GNU Compiler Collection (GCC))](https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html)

#### clang

编译时参数：

* [Clang Compiler User’s Manual — Clang 13 documentation (llvm.org)](https://clang.llvm.org/docs/UsersManual.html#id66)
* [Clang command line argument reference — Clang 13 documentation (llvm.org)](https://clang.llvm.org/docs/ClangCommandLineReference.html)
