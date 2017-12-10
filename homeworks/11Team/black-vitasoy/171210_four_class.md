## 堆栈
- 堆栈先进后出,例:进1->2->3,出3->2->1
## 堆栈操作
- 显示操作堆栈(push和pop),INT,CALL,(LEAVE,RET,RETE,IRET)指令跳转
## push和pop(寄存器,段寄存器,内存单元,x,y,z)
	push ax (压入堆栈)
	pop ax(弹出并传到x段寄存器)
	push ds
	pop ds(y)
	push [0]
	pop [0](z)
##### 并以字为单元
## 作业
	push eax(1)
	push ebx(2)
	pop eax(把2中的数据压入eax)
	pop ebx(把2中的数据压入ebx)

	
