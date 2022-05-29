# ---- [ ASM EXAMPLE FILE ] ----



# SIMPLE LOOP
	* C version:
					```cpp
					int main(int argc, char *argv[])
					{
						int i;
						for (i=0; i< 10; i++)
							printf("Hello, world!\n");
						return 0;
					}
					```
	* ASM:
	```asm
   0x00005555555551f5 <+0>:     push   rbp
	 0x00005555555551f6 <+1>:     mov    rbp,rsp
	 0x00005555555551f9 <+4>:     sub    rsp,0x20
	 0x00005555555551fd <+8>:     mov    DWORD PTR [rbp-0x14],edi
	 0x0000555555555200 <+11>:    mov    QWORD PTR [rbp-0x20],rsi
=> 0x0000555555555204 <+15>:    mov    DWORD PTR [rbp-0x4],0x0					// for (int = 0;
   0x000055555555520b <+22>:    jmp    0x55555555521d <main+40>
   0x000055555555520d <+24>:    lea    rdi,[rip+0xdec]        					# 0x555555556000	Load Effective Adress(load rip register to rdi)
	 0x0000555555555214 <+31>:    call   0x555555555020 <puts@plt>
	 0x0000555555555219 <+36>:    add    DWORD PTR [rbp-0x4],0x1					// i++
	 0x000055555555521d <+40>:    cmp    DWORD PTR [rbp-0x4],0x9					// i < 10
	 0x0000555555555221 <+44>:    jle    0x55555555520d <main+24>					// if i <= 10 return to main+24
	 0x0000555555555223 <+46>:    mov    eax,0x0
	 0x0000555555555228 <+51>:    leave																		// End of for Loop
	 0x0000555555555229 <+52>:    ret
	```
