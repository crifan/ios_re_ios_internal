# iOS底层机制逆向心得

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

## objc_msgSend

* 【未解决】IDA中如何解析objc_msgSend函数调用
* 【整理】iOS逆向和IDA使用心得：调用objc_msgSend时传递给MLPlayerItemQOEErrorEvent的initWithError:fatal:absoluteTime:的参数不够

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
