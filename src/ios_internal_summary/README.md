# iOS底层机制逆向心得

此处整理，iOS逆向时，涉及到iOS的底层机制方面的，心得和经验总结。

## 通用

TODO：

* 【整理】编程基础知识：函数Prologue开场白和函数Epilogue结尾
* 【整理】iOS逆向心得：给函数加了hook同时加断点会导致EXC_BREAKPOINT的崩溃
* 【已解决】iOS逆向心得：类没有setXxx函数但是有属性xxx
* 【整理】iOS逆向调试心得：ObjC或ARM中从偏移量中取值的不同写法

* 【已解决】iOS中的caddr_t类型的定义
  * TODO：
    * 把各种iOS逆向期间，涉及的各种类型的定义，也整理过来

## iOS内核和底层机制

TODO：

* iOS内核和底层机制
  * 【整理】iPhone相关名词：xnu的含义
  * 【或许解决】iPhone中所用的dyld是哪个版本
  * 【整理】苹果的动态库链接器：dyld
  * 【整理】苹果的二进制格式Mach-O的详细定义
  * 【记录】研究XCode中iOS的app的ALSR相关配置
  * 【整理】dyld相关：dyld_shared_cache动态库共享缓存
  * 【整理】Mac和iOS中的Sandbox沙箱
  * 【已解决】研究iOS中app的目录的UUID类的值和app名称如何映射
  * 【未解决】iOS的app的启动流程启动过程
