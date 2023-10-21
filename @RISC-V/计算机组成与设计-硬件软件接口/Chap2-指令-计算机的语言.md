### 第 2 章 - 指令: 计算机的语言

#### 2.8 计算机硬件对过程的支持
![寄存器用途](https://s2.loli.net/2023/10/21/qiFMoDuTBJj3W6n.png)

栈指针 `x8 (fp)` 类似于 x86 的 `rbp`, 不过 `fp` 的使用不是必须的.  
保存寄存器的方法是压栈, 过程可以概括为 `addi`, `sd` ... `ld`, `addi`.  

![栈帧结构](https://s2.loli.net/2023/10/21/XrOCHP3GjcYL5pQ.png)  
