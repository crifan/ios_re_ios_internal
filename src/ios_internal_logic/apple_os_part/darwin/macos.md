# macOS

* macOS
  * 背景
    * `NeXT`
      * 苹果早期，其创始人乔布斯离开苹果，创办了：`NeXT`
      * `NeXT`公司生产`NeXT`计算机和`NeXTstation`
        * 它们运行在叫做`NeXTSTEP`的操作系统之上
    * `NeXTSTEP`
      * 核心组件
        * `Cocoa`
        * `Mach`
        * `IOKit`
        * `Xcode`的`Interface Builder`
      * 特性
        * 采用 Mach 微内核
        * 使用 Objective-C 作为开发语言
        * 面向对象思想贯穿整个操作系统
        * 设备驱动开发是一个面向对象的框架，叫做 DriverKit
  * 操作系统名称演化历史
    * 概述
      * `Mac OS Classic` -> `Mac OS X` -> `OS X` -> `macOS`
    * 详解
      * `Mac OS Classic`
        * 诞生于苹果，拥有伟大的 GUI 却是一个相对粗糙且很不成熟的操作系统
      * `Mac OS X`
        * 背景
          * `Mac OS Classic`：一个拥有伟大的 GUI 但设计糟糕
          * `NeXTSTEP`：一个设计很棒但 GUI 平淡
        * 融合：`Mac OS Classic` + `NeXTSTEP` => `Mac OS X`
      * `OS X`
        * `OS X`的架构
          * ![os_x_arch](../../../assets/img/os_x_arch.png)
      * `macOS`
    * 表格

| 时间段 | MacOS名称 | 说明 |
| ----- | -------- | ---- |
| 创建 ~ 2001 年 | MachOS Classic	| 古典 MacOS |
| 2001年 ~ 2011 年 | Mach OS X | NeXTSTEP 与 MacOS Classic 合并之后的版本 |
| 2012 年 ~ 2015 年 | OS X | 这是最后一个以猫科动物命名的 OS 版本，此后开始以加州地标命名 |
| 2016 年至今 | macOS | 便于与iOS、tvOS、watchOS 命名统一 |
  * 架构
    * `macOS`架构
      * ![mac_os_arch](../../../assets/img/mac_os_arch.png)

## macOS中查看Darwin版本

* 举例：
  * `macOS v13.6.2`的`Mac M2 Max`中
    * uname相关输出是：
      ```bash
      ➜  ~ uname -v
      Darwin Kernel Version 22.6.0: Thu Nov  2 07:43:25 PDT 2023; root:xnu-8796.141.3.701.17~6/RELEASE_ARM64_T6020
      ```
      * 和：
      ```bash
      ➜  ~ uname -r
      22.6.0
      ```
    * 由此得知：
      * `Darwin`内核的版本是：`22.6.0`
    * 以及相关信息：
      ```bash
      ➜  ~ sw_vers
      ProductName:    macOS
      ProductVersion: 13.6.2
      BuildVersion:   22G320
      ```
