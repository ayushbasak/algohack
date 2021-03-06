# Operating Systems
### Notes
___

#### Topics for Discussion
- [.] Types of OS
- [.] Process States
- [.] User Mode / Kernel Mdoe
- [.] Process Scheduling Algos
	- [.] FCFS
	- [.] SJF
	- [.] SRJF
	- [.] RR
	- [.] Pre-emptive Priority Scheduling
- [ ] Process Synchronization
	- [.] Producer Consumer Problem
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
- [.] File System
- [.] Disk Scheduling Algorithms
	- FCFS
	- SSTF
	- SCAN
	- LOOK
	- C SCAN
	- C LOOK
-  [ ] File Management | Security 


___
### Introduction
<img src="https://www.tutorialspoint.com/operating_system/images/conceptual_view.jpg" width="400"></img>

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

### Process States
<img src="https://www.tutorialspoint.com/assets/questions/media/60253/process%20states.jpg" width="400"></img>
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

### User Mode | Kernel Mode
<img src="https://www.tutorialspoint.com/assets/questions/media/11194/User%20Mode%20vs%20Kernel%20Mode.PNG" width="400"></img>

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
<img src="https://static.javatpoint.com/difference/images/process-vs-thread3.png" width="400"></img>

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

#### User Level Thread | Kernel Level Thread
| ULT | KLT |
| --- | --- |
| implemented by users | implemented by OS |
| easy | complicated |
| Less context switching | More context switching |
| if one ULT performs blocking, entire process is blocked | on blocking, another thread continues execution |
| dependent threads | independent thread |

___

### Process Scheduling Algorithms
- Pre-emptive
	- SRTF (Shortest Remaining Time First)
	- Round Robin
	- Priority Based
- Non Pre-emptive
	- FCFS (First Come First Serve)
	- SJF (Shortest Job First)
	- Highest Response Ratio Next (HRRN)
	- Multilevel Queue

__Pre-emptive__: Process switching from ready state to running state.
__Non Pre-emptive__: Process switching only when one process terminates

__Arrival Time__: point of time when process enters ready queue.

__Burst Time__: Time required for process to execute.

__Completion Time__: point of time when process completes.

__Turnaround Time__: Completion Time - Arrival Time

__Waiting Time__: Turn Around Time - Burst Time

__Response Time__: Point of time when process get CPU access for the first time - Arrival Time


#### First Come First Serve (FCFS)
Advantages
- Non Prem-emptive
- easy to implement

Disadvantages:
- Inefficient | High waiting time
- Non pre-emptive algorithm runs till completion 

#### Shortest Job First (SJF)
Advantages:
- __minimum average waiting time among all scheduling algorithms__
- Non Pre-emptive
- Greedy Algorithm

Disadvantages:
- Can cause starvation

#### Shortest Remaining Time First (SRTF)
Advantages:
- pre-emptive version of SJF
- faster than SJF

Disadvantages:
- context switching is more

#### Round Robin
Time Quantum: period of time of which process is allowed to run in pre-emptive method

Advantages:
- pre-emptive
- implementable in real world [does not depend on burst time]
- no starvation
- all jobs get fair allocation of CPU

Disadvantages:
- higher time quantum -> higher response time
- Lower time quantum -> high context switching


#### Priority Scheduling
Advantages:
-	low number -> higher priority
-	for same priority, FCFS is followed

Disadvantages:
- difficult to decide which processes are given higher priority
- Low priority process is lost if PC crashes


___

### Process Synchronization Algorithms
1. Co-operative: one process affects execution of another process
2. Independent: one process does not affect execution of another process

__Race condtition__: when two or more processes are accessing the same resource.

#### Producer Consumer Problem
- producer creates data and stores in shared buffer
- consumer consumes data from shared buffer

___

### File System
File Allocation Methods

#### Continous allocation
Advantages:
- easy to implement
- excellent read performance

Disadvantages:
- disk will be fragmented (external fragmentation)
- difficult to grow file

#### Linked Allocation
Advantages:
- no external fragmentation
- changeable file size possible

Disadvantages:
- overhead of maintaining pointer in very disk block
- if pointer of any block is lost, file becomes truncated
- only sequential access of file is possible

#### Indexed Allocation
Advantages:
- direct access possible
- no external fragmentation

Disadvantages:
- overhead of pointer
- multilevel index
___

### Disk Scheduling Algorithms
Hark Disk Architechture

<img src="https://static.studytonight.com/operating-system/images/secondary-storage-1.png" width="400"></img>

__Platters -> Surfce -> Tracks -> Sectors -> Data__

Disk Access Times:
__Seek Time__: time taken by R/W head to reach desired track

__Rotation Time__: time taken for one full rotation

__Rotational Latency__: Time taked to reach desired sector

__Transfer Time__: Data to be transfered / Transfer Rate

__Transfer Rate__: # of heads x capacity of one track x # of rotations in one second

#### First Come First Serve (FCFS)
Advantages:
- every request gets  fair chance

Disadvantages:
- inefficient, very high seek time

#### Shortest Seek Time First (SSTF)
Advantages:
- Average Response Time decreases
- Throughput increases

Disadvantages:
- Overhead to calculate seek time 
- can cause starvation
- high variance of seek time

#### SCAN
go in one direction -> till the very last

Advantages:
- No starvation
- better than FCFS

Disadvantages:
- Not fair, as recently visited positions by head have longest waiting time

#### LOOK
- move to larger value
- same as scan, except head does not move to the very last

#### CSCAN and CLOOK
- circular scan, look
- return to 0, do not scan when returning
___