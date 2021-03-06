# C++内存管理

## 1.内存分配方式

C++中内存分为5个区：
- **堆**：用于程序的内存动态分配，使用malloc从堆上分配内存，使用free释放已分配的内存。
- **栈**：栈内存的分配运算置于处理器的指令集中，效率很高，单容量有限。
- **自由存储区**：C++基于new操作符的一个抽象概念，凡是通过new操作进行内存申请的，该内存既为自由存储区。
- **全局/静态存储区**：在编译的时候已经分配好的，在整个程序运行期间都存在。如全局变量、静态变量。
- **常量存储区**：比较特殊的存储区，存放常量（const），不允许修改。

## 2.常见的内存错误及解决方法

#### 2.1 内存分配未成功，却使用了它。

在使用内存之前**检查指针是否为NULL**:
- 如果指针p是函数的参数，那么在函数的入口处用assert(p!=NULL)进行检查。
- 如果是用malloc来申请内存，应该用if(p==NULL) 或if(p!=NULL)进行防错处理。
- 如果是用new来申请内存，申请失败是会抛出异常，所以应该捕捉异常来进行放错处理。

