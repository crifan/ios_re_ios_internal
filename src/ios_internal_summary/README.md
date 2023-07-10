# iOS底层机制逆向心得

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

---

此处整理，iOS逆向时，涉及到iOS的底层机制方面的，心得和经验总结。

## 通用

* 【整理】编程基础知识：函数Prologue开场白和函数Epilogue结尾
* 【整理】iOS逆向心得：给函数加了hook同时加断点会导致EXC_BREAKPOINT的崩溃
* 【已解决】iOS逆向心得：类没有setXxx函数但是有属性xxx
* 【整理】iOS逆向调试心得：ObjC或ARM中从偏移量中取值的不同写法

* 【已解决】iOS中的caddr_t类型的定义
  * TODO：
    * 把各种iOS逆向期间，涉及的各种类型的定义，也整理过来

## 动态调试

* 【已解决】iOS逆向心得：如何从对x8的adrp和ldr计算出对应的qword字符串值
* 【整理】iOS逆向调试心得：bool等变量类型
* 【整理】iOS逆向心得：变量类型是bool类型

## po

* 【整理】iOS逆向心得：当iPhone锁屏时Xcode中lldb的po会卡死
* 【整理】iOS逆向心得：po异常时NSString的字符串无法像char*一样打印出来
* 【整理】iOS逆向调试心得：po不是对象实例但可以看到是哪个类

## 类

* 【整理】iOS逆向心得：类的属性字段偏移量计算要加上isa的父类
* 【整理】iOS逆向心得：打印ObjC类的属性
* 【已解决】iOS逆向：写hook代码时打印出类的私有属性变量值的类型
* 【整理】iOS逆向调试心得：给类的属性去设置值以及如何计算类的属性的偏移量
* 【整理】iOS逆向心得：通过查看类的地址保存的值找到值和属性字段的偏移量和对应关系

## 函数

* 【整理】iOS逆向调试心得：bl函数调用和返回常见逻辑
* 【整理】iOS逆向心得：ObjC函数调用时参数顺序和汇编代码中寄存器传递的参数顺序不一致
* 【整理】iOS逆向lldb调试心得：iOS的ObjC的无名汇编跳板函数
  * 相关
    * 【已解决】clang中的__cdecl和支持哪些调用规范
    * 【已解决】微软的调用规范的参数传递和命名规范
    * 【已解决】iOS中调用asm汇编关键字：asm __asm __asm__和volatile __volatile__
    * 【已解决】XCode的断点条件判断中如何获取iOS的ObjC函数的参数值
