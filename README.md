# MFQ

Changed xv6 scheduler from the basic Round Robin algorithm to using the MFQ algorithm.

<br/>
The MFQ has been implemented with the following requirements:

* 4 priority levels: 3, 2, 1, and 0 with 3 being the highest priority and 0 being the lowest priority <br/>
* Priority Level 3 must have a time quantum of 200 ms (2 priority ticks))
* Level 2 must have a time quantum of 400 ms (4 timer ticks)
* Level 1 must have 800 ms time quantum.
* Level 0 must have 1600 ms time quantum.
* New processes always being at priority level 3 
* Whenever a timer interrupt occurs, the currently running process is considered to have used 1 entire time tick.
* If a process has used its full quantum at priority levels 3, 2, or 1, then its priority must be reduced by one level.
* If a process changes to the SLEEPING state (e.g., from calling sleep() or from a blocking call), then it is not considered to have used the current time tick, and will not change priority levels.
* If a process becomes runnable and it is higher priority than the currently running process, then that process will be chosen to run at the next timer interrupt.
* When the scheduler runs, it will always pick a runnable process from the highest priority level available.
