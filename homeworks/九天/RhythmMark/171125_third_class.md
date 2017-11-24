#### 第三次学习任务-划重点

----

> #### 操作内存

----

1. mov指令

|指令|对象 |例子 |
|:-:|:-:|:-:|
|mov|寄存器、 数据 |mov ax,8888 |
 |mov|   寄存器、  寄存器    |   mov bx,ax   |
|  mov |  寄存器、  内存单元   | mov ax,[0]
 | mov  | 内存单元、寄存器     |  mov [0],ax  
|  mov  | 段寄存器、寄存器    |    mov ds,ax

- 方括号里面的表达式指定的不是立即数，而是偏移量。
- 如mov ax,[0]在实模式，DS:0中的那个字会被装入AX。
- 复习：DS为数据段，AX为寄存器EAX的低16位。
- 方括号中可以使用加减，如

----
2. 描述内存宽度的操作符

|  操作符 | 意义  |例|
| :------------:| :------------:|:--:|
|  byte ptr | 一个字节（8-bit，1 byte）  |
|  word ptr | 一个字（16-bit）  |mov word ptr [100h],01234h
|  dword ptr | 一个双字（32-bit）  |

- mov ax,es:[di+bp]：[16*es+di+bp]

2. 串操作
- CLD与STD是用来操作方向标志位DF（Direction Flag）。
- CLD（clear direction）使DF复位，即DF=0;STD（set direction）使DF置位，即DF=1.用于串操作指令中。
- REP（REPeat)，重复
- 某些指令可以加上REP前缀，这些指令通常被叫做串操作指令。
- STOS（STOre into String） 存入串指令 
- stosb, stosw： Stores a byte, word.
- STOSD(Store String Data), 存储字符串数据
- STOSD指令将EAX的内容保存到ES:DI，同时在DI上加/减4；STOSB和STOSW分别作1字节或1字的操作，在DI上加/减的数是1或2。

- 其他详细指令说明见[教程](https://github.com/DigBullTech-Michael/ctf_re/blob/master/tutorials/171122_3rd.md)


