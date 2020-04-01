# Memory-Fragmentation 内存碎片

## Reference
https://baike.baidu.com/item/%E5%86%85%E5%AD%98%E7%A2%8E%E7%89%87


## Definition
采用分区式存储管理的系统，在储存分配过程中产生的、不能供用户作业使用的主存里的小分区称成“内存碎片”。

## 内存分配
内存分配有静态分配和动态分配两种。
### 静态分配
 静态分配在程序**编译链接时**分配的大小和使用寿命就已经确定。

### 动态分配
应用上要求操作系统可以提供给**进程运行时申请和释放任意大小内存的功能**，这就是内存的动态分配。

## 内存碎片如何产生？
内存碎片分为内部碎片和外部碎片。

### 内部碎片 Internal Memory Fragmentation
内部碎片就是已经被分配出去（能明确指出属于哪个进程）却不能被利用的内存空间。

因为所有的内存分配必须起始于可被 4、8 或 16 整除（视处理器体系结构而定）的地址或者因为MMU的分页机制的限制，决定内存分配算法仅能把预定大小的内存块分配给客户。

假设当某个客户请求一个 43 字节的内存块时，因为没有适合大小的内存，所以它可能会获得 44字节、48字节等稍大一点的字节，因此由所需大小四舍五入而产生的多余空间就叫内部碎片。

### 外部碎片 External Memory Fragmentation

外部碎片指的是还没有被分配出去（不属于任何进程），但由于太小了无法分配给申请内存空间的新进程的内存空闲区域。

假设有一块一共有100个单位的连续空闲内存空间，范围是0~99。如果你从中申请一块内存，如10个单位，那么申请出来的内存块就为0~9区间。这时候你继续申请一块内存，比如说5个单位大，第二块得到的内存块就应该为10~14区间。如果你把第一块内存块释放，然后再申请一块大于10个单位的内存块，比如说20个单位。因为刚被释放的内存块不能满足新的请求，所以只能从15开始分配出20个单位的内存块。

