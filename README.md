# cocoapods-demo
Cocoapods config optimize


## 静态库
多个 目标文件的集合
Windows 的 .lib
Linux 和 iOS 下的 .a
iOS独有的.framework。

### 优势
提供的是目标文件, 所以不需要重新编译, 只需要链接即可
加载 App 速度更快, 因为在编译时已经进行了链接, 启动时不需要进行二次查找启动
### 缺点:
浪费内存和磁盘空间，模块更新困难

## 动态库

动态库并不会在编译时编译到app中, app只会存储指向动态库的引用。等到程序启动时，动态库才会被真正加载进来。
根据载入时间 (load time)将动态库分为两种:

动态链接库: 通过dyld程序在app启动时将加载动态库
动态加载库: app启动后再使用dlopen来懒加载动态库(iOS不支持, MacOS支持)

MacOS/iOS: .tbd, .dylib 或封装成 .framework, xcframework
Linux: .so
Windows: .dll


### 优势
动态库不需要在编译时置入 app 中, 因此理论上app体积会更小, 而且可以做到动态库内容不需要重新编译即可获得最新功能
###缺点:会导致一些性能损失。但是可以优化，比如延迟绑定(Lazy Binding)技术

可以前往MacOS系统路径 /usr/lib 文件夹查看系统的动态库.

参考链接：https://juejin.cn/post/7237661384996569125
