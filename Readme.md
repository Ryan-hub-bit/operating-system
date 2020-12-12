# Introduction of Operation system

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

### important terms
1. Bootstrap Program: the initial program that runs when a computer is powered up or rebooted. It must know how to load the OS and start executing that system. It must locate and load into memory the OS kernel

2. System Call: Software may trigger an interrupt by executing a special operation called System Call.

** When the CPU is interrupted, it stops what it is doing and immediately transfers execution to a fixed location to execute the service routine first.
The interrupt service routine executes.\\
On completion, the CPU resumes the interrupted computation.# operating-system
