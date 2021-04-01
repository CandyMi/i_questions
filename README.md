# 大厂的经典面试题


## 常见面试题精解


## 1. 什么是`系统调用`? `系统调用`的过程是什么? 为什么不直接提供的`普通调用`?

  定义: `系统调用`是由操作系统实现提供的一套`内核与应用`之间的接口标准;
  
  (glibc)的执行过程:
  
  * 调用`int $0x80`产生软中断信号;

  * 交换用户空间与内核空间的堆、栈与寄存器信息:

  * 根据系统调用表调用内核函数并且执行;

  * 恢复用户空间堆栈, 将执行结果放入寄存器;

  * 切换回之前的用户空间, 返回结果给调用方法; 

  存在的理由:

  * 不同进程之间的数据安全与系统(内核)稳定性问题; 

  * 更好的抹平不同硬件之间的兼容性问题;

## TCP的`连接握手`为什么是3次？ `连接关闭`为什么是4次？

  连接握手: 

  1. `2次握手`无法解决数据包超时导致的死锁问题;

  2. `4次握手`无法解决数据包超时导致的脏数据包问题;

  连接挥手:

  1. 可以确认双方都能进入`FIN_WAIT`状态;

  2. 可以确保双方都能完成`剩余数据的收/发`;
