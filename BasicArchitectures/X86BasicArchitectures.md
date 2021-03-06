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
当程序通过处理器管理内存时并不会直接寻址操作物理地址。相反，程序只能使用CPU提供的三种内存访问模式中的一种来管理内存。(程序-内存访问模式一一对应)
1. 平坦内存模式Flat memory model
2. 段模内存式Segmented memory model
3. 实地址模式下的内存模式Real-address mode memory model

![](https://raw.githubusercontent.com/BilibiliRiven/NoteBook/main/BasicArchitectures/MemoryModle.PNG)

* 平坦内存模式下，内存堆对于程序来说，是**一段****连续**的存储空间。程序的代码，数据，堆，栈全部都在这段地址空间存储。线性地址空间通常以字节为单位寻址，寻址范围通常是0~2^32-1。

* 段模内存模式，内存对于程序，是**一组****相互独立**的存储空间。程序需要通过逻辑地址(a logical address)访问想要的字节字节。逻辑地址由，段选择子加偏移构成(logical addresses are often referred to as far pointers)。
IA32架构支持寻址0x3fff(16383)个段，每个段最大寻址为0~2^32-1。

在处理器内部，所有系统定义的段，被映射到处理器的线性地址空间上。
处理器要访问指定地址，就必须将逻辑地址转为线性地址。这种转换对应用程序时透明的。

早期使用段内存模式的根本原因是为了增加程序和系统的稳定性(核心思想是隔离，简单来说将代码放在代码段，数据放在数据段，堆栈放在堆栈段)。如果代码，数据，堆栈，都在同一线性地址下，一旦程序出错导致堆栈异常增长，由于地址连续增长的堆栈极有可能会覆盖相邻的数据或者代码，造成无法挽回的后果。使用段内存模式就可以很好的避免覆盖这种情况的发生。因为堆栈无论如何增长，也只能在堆栈段，影响不了数据段和代码段。

* 实地址模式下的内存模式，是8086处理器的一种内存模式，提供这种模式的原因是为了兼容现存的运行在8086处理器上的程序。实地址模式下CPU会使用一种特殊方法来实现段内存模式。在这种方法下程序和系统使用的线性地址，实际上是由一组段内存(Segmented memory)实现的。每个段最大大小为64KB。这种方法也导致，实地址模式下的线性地址空间的最大容量为2^20即1M。(这种特殊的方法的核心思想就是，让段与段之间的地址没有缝隙)


### Paging and Virtual Memroy页和虚拟内存


### 段寄存器Segment Registers
* 段寄存The segment registers (CS, DS, SS, ES, FS, and GS)用来存放16位段选择子(segment selectors)
* 段选择子A segment selector是一个特殊指针用来指明内存中的一个段

因此要访问特定的段需要特定的段选择子在适当的段寄存器种。

