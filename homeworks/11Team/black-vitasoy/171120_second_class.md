## x86寄存器
1. **十进制整数** `1234d`
2. **十六进制** `0ffffh` , *若开头数字可省略0*
3. **二进制数** `1010110b`
4. **八进制数** `777q` *调节器默认使用十六进制表示整数*

- reg32,32-bit寄存器,如EAX,EBX;
- reg16,********   , 如AX,BX;
- reg 8, *******    ,如AL,BH;
- imm32, 32-bit立即数,常数;
- imm16, 16-bit立即数;
- imm8,  ............;

#### mov,move,将数据发送到寄存器
	mov eax,ebx; 将ebx内容送入eax;
	mov eax,010h 表示在EAX寄存器载入00000010h
#### xchg指令
	xchg ebx,ecx,表示ebx与ecx的数值交换
#### 递减指令
	inc reg(8,16,32)
	dec reg(8,16,32)
#### add指令
	add reg32,reg32/imm(8,16,32)
* reg(x) + reg(y) or imm(y) = reg(x)

#### lea指令
- 将一个进地址指针写入到指定寄存器
	lea ax,buf 将存储器buf所指的地址传输给ax
	lea reg16,mem16
reg16必须是16位通用寄存器,mem16必须是存储器,mem16的偏移地址传递给reg16,mov传`内容`,lea传`地址`

#### rep,stos指令
```
lea edi,[ebh-ocoh]
mov exc,30h
mov eax,0CCCCh
rep stos dword ptr es:[edi]
```
- REP指令可以是任何字符串指令（CMPS、LODS、MOVS、SCAS、STOS）的前缀。 REP能够引发其后的字符串指令被重复，只要ECX的值不为0，重复就会继续。每一次字符串指令执行后，ECX的值都会减小。
- STOS(store into string)意思是把EAX的内容拷贝到一个目的地址。 用法：stos dst，dst是一个目的地址，例如stos dword ptr es:[edi]。dword ptr（强制转换成dword格式）前缀是告诉stos，一次拷贝双字（4个字节）到目的地址

#### 逻辑运算 
	AND(CF),OR(PF),XOR(AF),TEST(ZF),NOR(OF)(为标志位)
<http://blog.csdn.net/betabin/article/details/7306347>
#### cmp
第一操作数减去第二操作数,影响标志位
< http://laokaddk.blog.51cto.com/368606/284280>
#### 指令跳转
- 无条件:JMP
- 根据CX,ECX寄存器:JCXZ（CX为0则跳转）、JECXZ（ECX为0则跳转）
- EFLAGS寄存器的标志位跳转

#### intel 80386
保护模式,分段机制,进入保护模式,能提供更好的保护和大的寻址空间
#### 种类模式
- 实模式,只能访问1M以下的常规内存
- 保护模式,既能实现资源共享又能保证代码和数据的安全和保密及任务的隔离
- 8086模式,运行在保护模式中的实模式,为了在32位保护模式执行纯16位程序
#### 模式区别
- 实模式访问真正的物理地址
- 保护模式,是程序的虚拟地址要由操作系统转为物理地址

## 作业
把寄存器全部设置成0的状态，然后执行下面的代码：
`mov eax,0a1234h`			将十六进制数0a1234h送入eax

`mov bx,ax`			将ax内容送入bx

`mov ah,bl`			将bl内容送入ah

`mov al,bh`           将bh内容送入al

思考此时EAX的内容是多少?
0xa1234h = 00000000000010100001001000110100b
1. eax = 00000000000010100001001000110100
2. bx = ax = 0001001000110100b
	 - eax = 00000000000010100001001000110100
	 - ebx = 00000000000000000001001000110100
3. ah = b1 , eax = 00000000000010100011010000110100
	ebx 不变
4. al = bh = 00010010
- eax = 00000000000010100011010000010010
### 总结: eax 是存储32位的寄存器,ax是16位,ah(high)代表后16位的高八位,al(low)后16位的后八位

>参考第九组,RhythmMark

