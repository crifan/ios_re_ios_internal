# 函数签名

TODO：

* 【整理】iOS逆向心得：Block的invoke函数的签名signature的含义
  * 把如何动态调试查看函数签名的内容整理过来
* 【已解决】iOS逆向：__block_literal_global

---

* `函数签名`=`function signature`
  * 举例
    * `v8@?0`
      * 函数定义：`void ^();`
    * `v12@0:4@8`
      * 函数定义：`- (void) setSomething:(id) anObject;`

## 举例详解

调试某个ObjC的`block`时：

```c
(lldb) reg r x0
      x0 = 0x000000014726ef70
(lldb) po 0x000000014726ef70
<__NSMallocBlock__: 0x14726ef70>
 signature: "v32@?0@"NSError"8@16@"TTHttpResponse"24"
 invoke   : 0x111735758 (/private/var/containers/Bundle/Application/1FFDC079-CC8A-4219-955A-E01C73207969/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore`-[MKMapView(AWEMap) awe_screenScope])
 copy     : 0x108c97674 (/private/var/containers/Bundle/Application/1FFDC079-CC8A-4219-955A-E01C73207969/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore`+[AWELaunchMainPlaceholder _generateBootLoaderLogs])
 dispose  : 0x108c9767c (/private/var/containers/Bundle/Application/1FFDC079-CC8A-4219-955A-E01C73207969/Aweme.app/Frameworks/AwemeCore.framework/AwemeCore`+[AWELaunchMainPlaceholder _generateBootLoaderLogs])
```

可以看到：

* 函数签名: `v32@?0@"NSError"8@16@"TTHttpResponse"24`
  * 对应的函数定义其实是：`void ^(NSError *, id, TTHttpResponse *);`

继续查看Block详情中，也有Signature相关属性：

```c
(lldb) po _Block_has_signature(0x14726ef70)
0x0000000000000001

(lldb) po _Block_signature(0x14726ef70)
0x0000000107067dd6
```
