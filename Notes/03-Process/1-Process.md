# Process

1. Process Control Block
2. Process state

## Process Control Block
We can think of a process as consisting of three components:
- **An executable program**
- **The associated data need by the program (variables, work space, buffers, etc.)**
- **The execution context of the program**

At any given point in time, while the program is executing, this process can be uniquely characterized by a number of elements, including the following:
- **Identifier.**
- **State.**
- **Priority.**
- **PC (program counter).**
- **Memory pointers:** Includes pointers to the program code and data associated with this process, plus any memory blocks shared with other processes.
- **Context data:** These are data that are present in registers in the processor while the process is executing.
- **IO status information:** Includes outstanding IO requests, IO devices assigned to this process, a list of files in use by the process and so on.
- **Accounting information:** May include the amount of processor time and clock time used, time limits, account numbers, and so on.

刚刚列出来的元素被存在一个叫**进程控制块Process Control Block, PCB**的数据结构中。这个数据结构被OS创建和管理。


## Process State 


