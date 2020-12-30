# Introduction of Operation system

Assembly language(汇编语言)

An operating system is a program that manages the computer hardware.

It aslo acts as a bridge between computer user and computer hardware to help software application to perform some tasks with computer hardware. Eg: I/O operation Resources Like CPU(central processing unit), Memory.

### the function of OS:

- an interface  between user & hardware
- Allocation of Resources
- Management of Memory, Security

### General-purpose computer system

- It consists of  one or more CPUs and a number of device controllers connected through a common bus that provides access to shared memory.
- Each device controller is in charge of a specific type of device
- The CPU and the device controllers can execute econcurrently, competing for memory cycles
- Since the memory is unlimited and whenever a controller is executed, it will be loaded on the memory. To ensure orderly access to the shared memory, a memory controller is provided whose function is to synchronize access to the memory

### Important terms

1. Bootstrap Program: the initial program that runs when a computer is powered up or rebooted. It must know how to load the OS and start executing that system. It must locate and load into memory the OS kernel

2. System Call: Software may trigger an interrupt by executing a special operation called System Call.

** When the CPU is interrupted, it stops what it is doing and immediately transfers execution to a fixed location to execute the service routine first.
The interrupt service routine executes.
On completion, the CPU resumes the interrupted computation.

### Storage structure

From top to  down, from small storage size to large storage size, the access time increase: Registers -> Cache -> Main memory -> Electronic Disk -> Magnetic Disk -> Optical Disk -> Magnetic tapes

Register: store data in bit 0 or 1, be accessed very quickly

Cache: speed  slowly than Register

RAM: Main memory

#### Main memory

RAM : anything that loaded on your computer, it must be loaded on main memory.  A software application will be installed on the second memory(Electronic Disk and after it), when you double click it, it will be loaded on your main memory then get executed.

More RAM, your computer speed will be faster.

![Screen Shot 2020-12-12 at 3.56.26 PM](/Users/liukun/Desktop/Screenshot/Screen Shot 2020-12-12 at 3.56.26 PM.png)



#### I/O Structure

Storage is only one of many types of I/O devices within a computer

Typically, operating systems havea device  driver fro each device controller,

This device driver understands the device controller and provide an uniform interface to the device to therest of the operating system.

#### How an I/O operation works

- When a CPU send a I/O request to device, the device driver will load  the appropriate registers for the specific I/O requests within the device controller.
- Then the device controller will examine the content of these registers to determine which action that CPU want me to do 
- the device controller will start to transfer some necessary data from the device to its local buffer
- Once the transfer of data is complete, the device controller informs the device driver via an interrupt that it has finished its operation
- The device driver return control to the operating system.

The above method will produce high overhead(经常性的开支) because the CPU will always  be interrupted.

##### DMS: direct memory Access

the device controller will skip CPU and transfer an entire block of data directly to or from its own buffer storage to memory with no intervention by the CPU. In this way only one interrupt is generated per block, to tell the device driver that the operation has completed. While the device controller is performing these operations, the CPU is available to accomplish other works.



### Computer System Architecture

 

![Screen Shot 2020-12-13 at 1.37.12 PM](/Users/liukun/Desktop/Screenshot/Screen Shot 2020-12-13 at 1.37.12 PM.png)

Consists of single processor, multiple processor, Clustered process



### Operating System Structure

- Operating System vary greatly in their makeup internally

- Commonalities:

  - Multiprogramming
    - A single user cannot, in general, keep either the CPU or the I/O devices busy at all times
    - multiprogramming increases CPU utilization by organizing jobs(code and data) so that the CPU always has one to execute: The Job will be loaded on memory, when a job is executed, it will take up CPU and needed I/O devices. Once it is done, he will release the CPU and I/O devices,  and the next job will be able to use them.
  - Time sharing(Multitasking): multiple users will be able to do one thing at the same time, because the CPU is so faster than user input, there will be a time gap for another user to execute his program.
    - CPU executes multiple jobs by swithcing among them
    - Swithes occurs so frequently that  the users can interact with each program while it is running
    - TIme sharing requires an interactive computer system, which provides direct communication between the user and the system.
    - A time-shared operating system allows many users to share the computer simultaneously

  **A program loaded into the memory and excuting is called a "process"**

### Things provided by operating system

1. User interface(Command line Interface, Graphical user interface)

2. Program execution(it must can run a program or a software) 

   - the process :source code -> compiler -> Object code -> Executor-> output

3. I/O Operations: the operating system is like a bridge to receive your input from hardware(keyboard mouse) and to show it or to perform some tasks through output hardware(Monitor and Printer).

4. File System Manipulation(control how files are manipulated[delete, save, rename])

5. Communications(communications among processes)

6. Error Detection(should be aware of the error occured)(Printing something but no paper available, the operating system should detect the error and show user)

7. Resource Allocation

8. Accouting(want to keep track of which user use how much and what kind of resource)

9. Protection and Security 

   

   ### System Calls

   When you want to perform some tasks as kernal mode, you probably can use system calls to access the resources of the operating system(file) .

   

   #### Type:

   - process control
     - End, abort
     - load, execute
     - create process, terminate process
     - get process attributes, set process attributes
     - wait for time
     - wait event, signal event
     - allocate and free memory
   - File Manipulation
     - Create file, delete file
     - Open, close
     - read, write
     - get file attributes, set file attributes
   - Device Management
     - request device, release device
     - Read, write reposition
     - get device attributes
     - logically attach or detach devices
   - Information Maintenance
     - Get time or date, set  time or date
     - get system data
     - get process, file, or device attributes
   - Communications
     - create, delete communication connection
     - Send, receive messages
     - transfer status information
     - attach or detach remote devices

   

   ### System programs

   - File management
     - create delete copy rename print(outer part of a file)
   - Status information
     - Date
   - file modification
     - inner part of a file. Then content of files
   - Programming-language support(such as C, C++, Java, VB and perl)
     - compilers
     - Assemblers
     - Debuggers
     - Interpreters
   - Program loading and execution
     - Once a program is assembled or compiled, it must be loaded into memory to be executed
   - Communications
     - Creating virtual connextions among processes, users, and computer systems.
     - Allowing users to send messages to one another's screens

## Operating System Design & Implementation

### Design Goals

 Defining Goals and specification

- Choice of hardware
- Type of System

Mechanisms and Policies:

- Mechanisms determine how to do something

- Policies determine what will be done

One important principle is to **Separation of policy from mechanism**

### Structure of operating System

#### Monolithic Structure

|                           | The user                                                     |                                   |
| ------------------------- | ------------------------------------------------------------ | --------------------------------- |
|                           | Shells and  Commands,  Compilers and Interpreters, System libraries |                                   |
|                           | System- call interface to the kernel                         |                                   |
| Signal, terminal handling | File System swapping block I/O system                        | CPU scheduling, page repplacement |
|                           | Kernel interface to the hardware                             |                                   |
|                           | Hardware                                                     |                                   |

### Layered Structure

Layer N user interface

Layer 1

Layer 0 Hardware

Every layer have different functionalities, we can focus on a specific layer to debug if we found a bug on a specific layer. A layer can use only the layers below itself, it will issue a system call if it wants to use the hardware layer.

### Microkernels





## Virtual Machine

Defination: The fundamental idea behind a virtual machine is to  abstract the hardware of a single computer  into several different  execution environments, thereby creating the illusion that each separate execution environment is running its own private computer.

### Operating system Generation & System Boot

## Process and Thread

Process is a program in execution

A thread is the unit of execution within a process. A process can have anywhere from just one thread to many threads. 

- Process means a program is in execution, whereas thread means a segment of a process.
- A Process is not Lightweight, whereas Threads are Lightweight.
- A Process takes more time to terminate, and the thread takes less time to terminate.
- Process takes more time for creation, whereas Thread takes less time for creation.
- Process likely takes more time for context switching whereas as Threads takes less time for context switching.
- A Process is mostly isolated, whereas Threads share memory.
- Process does not share data, and Threads share data with each other.

## Bandwidth and latency

- [Latency](https://www.keycdn.com/support/what-is-latency) is the amount of **time it takes for data to travel from one point to another**. It is dependent on the physical distance that data must travel through cords, networks and the like to reach its destination.
- [Bandwidth](https://www.keycdn.com/support/identify-bandwidth-usage) is the **rate of data transfer for a fixed period of time**. Bandwidth, as its name implies, is the width of a communication band. The wider the communication band, the more data that can flow through it simultaneously.

### Process State

- As a process executes, it changes state.

- The state of a process is defined in part by the current activity of that  process.

  #### State:

  - New: the process is being created.
  - Running:Instructions are being executed.
  - Waiting: The process is waiting for some events to occur(I/O completion or reception of a signal)
  - Ready: The process is waiting to be assigned  to a processor.
  - Terminated: The process has finished execution.



### Process Control Block

- Process ID
- Process state: above states
- Process number:
- Program counter: address of the next line is going to be executed for a process
- CPU Registers: tells us what addresses are  used in current process.
- CUP scheduling information: Many processes are waiting for being executed, it will determine which one will been executed.
- Memory limits
- List of open files
- Accounting information:
- I/O status information

### Porcess Scheduling

The objective of multiprogramming is to have some process running at all times, to maximize CPU utilization.

The objective of time sharing is to switch the CPU among processes so frequently that users can interact with each program while it is running.

To meet these objectives, the process scheduler selects an available process (the processes that are in the ready state) for program execution on the CPU.

**Job Queue**: as processes enter the system, they are put into a job queue, which consists of all process  in the system.

Ready queue: The processes that are residing in main memory and are ready and waiting to execute are kept on a list called the ready queue.



### Operations on Processes

A process may create several new processes, via a create-process system call, during the course of execution

The creating process is called a parent process, and the nwe processes are called the children of that process.

Each of these new processes may in turn craete other processes, forming a tree of processes.

#### when a process creates a new process, two possibilities exist in terms of execution:

1. The parent continues to execute concurrently within children.
2. The parent waits until some or all of its children have terminated.

#### There are also two possibilities in terms of the address space of the nwe process:

1. The child process is a duplicate of the parent process(it has the same program and data as the parent).
2. The child process has a new program loaded into it.



### Interprocess Communication

Processes executing concurrently in the operating system may be either independent processes or cooperating processes.

#### Information sharing

#### Computation speedup

#### Modularity

#### Convenience



Cooperating processes require an interprocess communication(IPC mechanisum that will allow them to exchange data and information)

two fundamental models of interprocess communication:

1. Shared memory 

   - a region of memory that is shared by cooperating processes is established. Processes can then exchange information by reading and writing data to the shared region.(临界区)

2. Message passing

   In the message passing model, communication takes place by means of messages exchanged between the cooperating processes.![Screen Shot 2020-12-19 at 1.31.11 PM](/Users/liukun/Documents/Screen/Screen Shot 2020-12-19 at 1.31.11 PM.png)

#### Shared Memory Systems

- Interprocess communication using shared memory requires communicating processes to establish a region of shared memory.
- Typically, a shared- memory region resides in the address space of the process creating the shared-memory segment.
- Other processes that wish to communicate using this shared-memory segment must attach it to their address space.
- Normally, the operating system tries to prevent one process from accessing another process's memory.
- Shared memory requires that two or more processes agree to remove this restriction.

Two kinds of buffers:

- ​		Unbounded buffer: Place no practical limit on the size of the buffer. The consumer may have to wait for new items, but the producer can always produce new items.
- ​        Bound buffer: Assumes  fixed buffer size. In this case, the consumer must wait if the buffer is empty, and the producer must wait if the buffer is full.

#### Message-Passing Systems

Message passing provides a mechanism to allow processes to communicate and to synchronize their actions without sharing the same address space and is particularly useful in a distributed environment, where the communicating processes may reside on different computers connected by a network.

A message-passing facility provides at least two operations:

- Send(message)
- Receive(message)

If processee P and Q want to communicated, they must send messages to and receive messages from each other. A communication link must exist between them.



### Sockets: Used for Communication in Client-Server Systems

A socket is defined as an endpoiint for communication.

A pair of processes communicating over a network employ a pair of sockets- one for each process.

A socket is identified by an IP address concatenated with a port number.

The erver waits for invoming client requests by listening t o a specified port. Once a request is received, the server accepts a connection from the client socket to complete the connection.

Servers implementing specific services (such as telnet, ftp, and http) listen to well-known ports

All ports below 1024 are considered well known; we can use them to implement standard services.



### Threads

A thread is a basic unit of CPU utilization.

It comprises  a thread ID, a program counter a register set and  a stack.

It shared with other threads belonging to the same process tis code section, data section, and other operating-system resources.



![Screen Shot 2020-12-30 at 3.32.09 PM](/Users/liukun/Documents/Screen/Screen Shot 2020-12-30 at 3.32.09 PM.png)



#### Multithreaded Programming Benefits

- Responsiveness: Multithreading an interactive application may allow a program to continue to run even if part of it is blocked, thereby increasing responsiveness to the user.
- Resource sharing: Threads share the memory and the resources of the process to which they belong. The benefit  of sharing code and data is the it allows an application to have several different threads of activity within the same address space.
- Economy: AAllocating memory and resources for process creation is costly. Because threads share resources of the process to which they belong, it is more economical to create and context-switch threads.
- Utilization of multiprocessor architectures: The benefits of multithreading can be greatly increased in a multiprocessor architecture, where threads mayb be running in parallel on different processors.

### Multithreading Models and Hyperthreading

Types of threads:

1. User Threads : Supported above the kernel and are managed without kernel support.
2. Kernel Threads: Supported and managed directly by the operating system

**Ultimately, there must exist a relationship between user threads and kernel threads**

#### Many to one model:

- Many user threads to one kernel thread
- Thread management is done by the thread library in user space, so it is efficient.

Disadvantages:

- The entire process will block if a thread makes a blocking system call.
- Because only one thread can zccess the kernel at a time, multiple threads are unable to run in parallel on multiproccessor.

#### One to One model:

- Maps each user thread to a kernel thread.
- Allows multiple threads to run in parallel on multiprocessors.

#### Many to Many model:

- Multiplexes many user-level threads to a smaller or equal number of kernel threads
- The number of kernel threads may be  specific to either a particular application or a particular machine
- When  a thread performs a blocking system call, the kernel can schedule another thread for execution.

### Hyperthreading(Simultaneous Multithreading)

Hyperthreaded systems allow their processor cores resources to become multiple logical processors for performance.



#### The fork() and exec() System Calls

Based on linux system.

Fork(): the fork() system call is used to create a separate, duplicate process with different process id.

Exec(): When a exec() system call is invoked, the program specified in the parameter to exec() will replace the entire process.


