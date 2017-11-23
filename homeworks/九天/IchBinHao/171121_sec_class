#练习
-
把寄存器全部设置成0的状态，然后执行下面的代码：
>mov eax,0a1234h			;将十六进制数0a1234h送入eax
>
>mov bx,ax			;将ax内容送入bx
>
>mov ah,bl			;将bl内容送入ah
>
>mov al,bh			;将bh内容送入al

思考此时EAX的内容是多少?


##答

使用逐步分析的方式来解答：
>mov eax,0a1234h			;将十六进制数0a1234h送入eax

此时 eax的值为  0a1234h

>mov bx,ax ;将ax内容送入bx

eax的最高16位不变，低16中的1234h送入bx中

>mov ah,bl ;将bl内容送入ah

bx为1234h，所以bl为12，执行后ax为1212h

>mov al,bh ;将bh内容送入al

bh为34，执行后ax为3412h。

所以最终eax寄存器的值为**3412h**

