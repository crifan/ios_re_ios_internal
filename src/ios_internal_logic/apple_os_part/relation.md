# 关系总结

此次给Apple操作系统常见概念的关系：

* `iOS`
* `macOS`
* `Darwin`
* `XNU`
* `Mach`
* `BSD`/`FreeBSD`
* `IOKit`

做个总结：

* Apple的不同平台有不同操作系统：`iPhone`的`iOS`、`Mac`的`macOS`等等
  * `iOS`、`macOS`等系统的内核，都是：`Darwin`
    * `Darwin` = `XNU` + 其他
      * `XNU` = `Mach` + `BSD`/`FreeBSD` + `IOKit`
* 内核关系类比
  * `Ubuntu`
    * `Ubuntu`是**平台**(`plaftorm`)
      * `Linux + GNU` 是**操作系统**(`OS`)
        * `Linux`是**内核**(`kernel`)
  * `macOS`
    * `macOS`是**平台**(`plaftorm`)
      * `Darwin` 是**操作系统**(`OS`)
        * `XNU`是**内核**(`kernel`)
* 概念范围
  * 文字
    * `iOS` > `Darwin`
    * `macOS` > `Darwin`
    * `Darwin` > `XNU`
    * `XNU` > `Mach`
    * `XNU` > `BSD`/`FreeBSD`
    * `XNU` > `IOKit`

## 最终总结

* 苹果操作系统的架构 = Apple OS Architecture
  * 离线查看
    * 精简版
      * ![apple_os_arch_overview](../../assets/img/apple_os_arch_overview.jpg)
    * 完整版
      * ![apple_os_arch](../../assets/img/apple_os_arch.jpg)
  * 在线浏览
    * [苹果操作系统的架构 | ProcessOn免费在线作图](https://www.processon.com/view/link/67132a93e62924419e34ce08)
