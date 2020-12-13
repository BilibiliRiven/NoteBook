# X86BasicArchitectures.md

## 基本概念Basic Conception

### CPU运行模式
IA32架构CPU支持三种模式。
1. 实地址模式real-address mode
2. 保护模式protected mode
3. 系统管理模式 system management mode

模式决定CPU可以执行的指令以及支持的架构特性。

* 保护模式是处理工作最常见的一种状态。CPU在这种状态下能够以一种受保护且多任务的环境来运行8086软件。（Windows Linux这类操作系统，就工作在保护模式之上，通过保护模式提供的架构特性，来实现多任务，和异常处理）
* 实地址模式，可以理解为8086处理器环境的一种扩展(例如实地址支持切换到保护模式和系统管理模式)，处理器通常在加电和重启时进入实地址模式。

### IA-32 Memory Models
当程序通过处理器管理内存时并不会直接寻址操作物理地址。相反，程序通过CPU提供的三种内存访问模式来管理内存。
1. 平坦内存模式Flat memory model
2. 段模内存式Segmented memory model
3. 实地址模式下的内存模式Real-address mode memory model

![avatar][https://github.com/BilibiliRiven/NoteBook/blob/main/BasicArchitectures/MemoryModle.PNG]

* 平坦模式下，内存堆对于程序来说，是**一段****连续**的存储空间。程序的代码，数据，堆，栈全部都在这段地址空间存储。线性地址空间通常以字节为单位寻址，寻址范围通常是0~2^32-1。

* 段模内存式，内存对于程序，是**一组****相互独立**的存储空间。程序需要通过逻辑地址(a logical address)访问想要的字节字节。逻辑地址由，段选择子加偏移构成(logical addresses are often referred to as far pointers)。
IA32架构支持寻址0x3fff(16383)个段，每个段最大寻址为0~2^32-1。


* 实地址模式下的内存模式，参考手册 IA-32 Memory Models




### 段寄存器Segment Registers
* 段寄存The segment registers (CS, DS, SS, ES, FS, and GS)用来存放16位段选择子(segment selectors)
* 段选择子A segment selector是一个特殊指针用来指明内存中的一个段

因此要访问特定的段需要特定的段选择子在适当的段寄存器种。




