# NS和CF


iOS底层和内部：

底层有两套东西：

* `NS`开头的 = `NextStep`
  * 比如
    * `NSString`
* `CF`开头的 = `CoreFoundation`
  * 比如
    * `CFStringRef`

有些变量是可以相互互换使用的 == `toll-free bridged`

比如：

* `CFStringRef` == `NSString*`
* `CFURLRef` == `NSURL*`


详见：

* [CFStringRef | Apple Developer Documentation](https://developer.apple.com/documentation/corefoundation/cfstringref?language=objc)
* [CFURL | Apple Developer Documentation](https://developer.apple.com/documentation/corefoundation/cfurl?language=objc)
* [NSURL | Apple Developer Documentation](https://developer.apple.com/documentation/foundation/nsurl?language=objc)

以及相关部分的变量的互相转换的写法是：

iOS中的：`NSString`/`NSString*` 和 `CFStringRef` 的互相转换：

* MRC
  ```objc
  CFStringRef aCFString = (CFStringRef)aNSString;

  NSString *aNSString = (NSString *)aCFString;
  ```
* ARC
  ```objc
  CFStringRef aCFString = (__bridge CFStringRef)aNSString;

  NSString *aNSString = (__bridge NSString *)aCFString;
  ```

## 常用小技巧

* 判断`CFStringRef`是否以某个字符串开头
  ```objc
  CFStringRef prefixFile = (__bridge CFStringRef)@"file://";
  CFStringHasPrefix(someCFStringRef, prefixFile)
  ```
* 判断`CFURLRef`是否为空
  ```objc
  if (someCFURLRef != NULL){
  ```
* `CFURLRef`转`NSURL*`
  ```objc
  NSURL* someNSURL = (NSURL*)someCFURLRef;
  ```
* 从NSURL获取url字符串NSString
  ```objc
  NSString* someUrlNsStr = [someNSURL absoluteString];
  ```

### 去hook某个函数时的相关完整代码

```c
CFURLRef CFURLCreateWithString(CFAllocatorRef allocator, CFStringRef URLString, CFURLRef baseURL);

%hookf(CFURLRef, CFURLCreateWithString, CFAllocatorRef allocator, CFStringRef URLString, CFURLRef baseURL){
    CFStringRef prefixFile = (__bridge CFStringRef)@"file://";
    CFStringRef prefixXCoredata = (__bridge CFStringRef)@"x-coredata://";
    bool shouldOmit = false;
    if (CFStringHasPrefix(URLString, prefixFile)){
        shouldOmit = true;
    } else if (CFStringHasPrefix(URLString, prefixXCoredata)) {
        shouldOmit = true;
    }
//    iosLogInfo("shouldOmit=%d for URLString=%{public}@", shouldOmit, URLString);

    if (baseURL != NULL){
        //    NSString* absUrlStr = [baseURL absoluteString];
        NSURL* baseNsurl = (NSURL*)baseURL;
        NSString* baseAbsUrlStr = [baseNsurl absoluteString];
        CFStringRef baseAbsUrlStrRef = (CFStringRef)baseAbsUrlStr;
        if(!shouldOmit) {
            if (CFStringHasPrefix(baseAbsUrlStrRef, prefixFile)){
                shouldOmit = true;
            } else if (CFStringHasPrefix(baseAbsUrlStrRef, prefixXCoredata)) {
                shouldOmit = true;
            }
//            iosLogInfo("shouldOmit=%d for baseAbsUrlStrRef=%{public}@", shouldOmit, baseAbsUrlStrRef);
        }
    }

    CFURLRef newUrl = %orig;
    if(!shouldOmit) {
        iosLogInfo("allocator=%{public}@, URLString=%{public}@, baseURL=%{public}@ -> urlStr=%{public}@", allocator, URLString, baseURL, newUrl);
    }
    return newUrl;
}
```
