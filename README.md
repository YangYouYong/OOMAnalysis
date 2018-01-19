# OOMAnalysis

analysis of OOMDetector

> 浅读腾讯开源[OOMDetecor](https://github.com/Tencent/OOMDetector) 
> 内存泄漏检测源码

hook NSObject alloc add address to global hasmap

检测泄漏:
遍历global hasmap
扫描vm_region 标记是否泄漏
泄漏原理如下:

```
(vm_region == null && object find in stack) -> leak?

(vm_region == null && !(object find in stack) && (address object can get object isa pointer)) -> leak?

```
