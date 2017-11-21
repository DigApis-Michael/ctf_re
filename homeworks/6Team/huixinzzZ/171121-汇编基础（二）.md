## 练习
>  by  huixinzzZ

把寄存器全部设置成0的状态，然后执行下面的代码：

    mov eax,0a1234h			;将十六进制数0a1234h送入eax
    mov bx,ax			;将ax内容送入bx
    mov ah,bl			;将bl内容送入ah
    mov al,bh			;将bh内容送入al
思考此时EAX的内容是多少?  
答：

1. reg32，32-bit寄存器，如EAX、EBX等。
2. reg16，16-bit寄存器，如AX，BX等。
3. reg8？，8-bit寄存器，如AL，BH等。
![image](https://camo.githubusercontent.com/35f51ec32b4ab2558fde0fc959d3c226ba3106fc/687474703a2f2f6d306e737433722e6d652f7573722f75706c6f6164732f323031372f31312f323930353138323336392e706e67)

`0a1234h` -> `eax`   十六进制a1234=  **1010 0001 0010 0011** 0100  

`ax` -> `bx`        低16bit 0~15位  ax=`1010 0001` `0010 0011`     



`bl` -> `ah`    低位0~7位  bl=`1010 0001`  b的低位转给a的高位

`bh` -> `al`    高位8~15位 bh=`0010 0011`  b的高位转给a的低位

最终eax的内容是**0010 0011 1010 0001** 0100

