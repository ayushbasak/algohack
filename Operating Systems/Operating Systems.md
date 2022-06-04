# Operating Systems
### Notes
___

#### Topics for Discussion
- [ ] Types of OS
- [ ] Process States
- [ ] User Mode / Kernel Mdoe
- [ ] Process Scheduling Algos
	- FCFS
	- SJF
	- SRJF
	- RR
	- Pre-emptive Priority Scheduling
- [ ] Process Synchronization
	- Producer Consumer Problem
	- Printer Spooler Problem
	- Critical Section Problem
	- Semaphores
	- Dining Philosophers Problem
	- DEADLOCK
	- Deadlock Handling Methods
	- Deadlock Avoidance [Banker's Algorithm]
- [ ] Memory Management
	- Internal | Fixed Size Partitioning
	- Variable Size Paritioning
	- Paging
	- Virtual Memory | Page Fault
- [ ] Disk Management
	- Disk Scheduling Algorithms
		- FCFS
		- SSTF
		- SCAN
		- LOOK
		- C SCAN
		- C LOOK
-  [ ] File Management | Security 


___
### Introduction
![](https://www.tutorialspoint.com/operating_system/images/conceptual_view.jpg)

### Types of OS
- Batch OS
- Multi Programmed
	- Non Preemptive
	- 
- Multi Tasking
- Real Time OS
- Distributed
- Clustered
- Time Sharing

#### Process States
![[Pasted image 20220604132958.png]]
- Long Time Scheduler: New to Ready state
- Short Term Scheduler: Ready to Running
- Running to Wait: IO / Event wait request
- Medium Term Scheduler: Wait queue full -> Secondary Memory
- Terminated: Deallocation

__System Call Services__
Go from User Mode to Kernel Mode:
- Process Creation and Management
- Main memory management
- File System Access / Management
- Device / IO Handling
- Networking

__fork()__
- create a child process
	- 0 -> child process
	- +ive process -> parent
	- -1 child not created

```c
main () {
	fork();
	printf("Hello World!");
}
```

Total Processes in nested fork(): __2<sup>n</sup> - 1__

#### User Mode | Kernel Mode
![[Pasted image 20220604135407.png]]

__Kernel Mode__
- program has unrestricted access to system resources
- entire OS can stop if interrupt occurs
- more privilege
- 0 bit kernel mode

__User Mode__
- a single proces fails if interrupt occurs
- unprivileged
- all proceses get separate virtual address space
- 1 bit user mode

#### Process | Threads
![[Pasted image 20220604140024.png]]

| Process | Threads |
| --- | --- |
| Program in execution | Segment of Process |
| Longer to create and terminate | Shorter to Create and Terminate|
| Higher Context Switching Time | Shorter Context Switching Time |
| Isolated Processes | Threads share memory |
| Heavyweight | Lightweight |
| Process switching requires system call | No system call required |
| Blocking does not affect other process | If one user level thread is blocked, all user level threads are blocked |
| Has its own Control Block, Stack and Address space | Has parent process's PCB, thread control block, stack and common address space |


