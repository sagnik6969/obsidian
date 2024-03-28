1. read types of OS from copy
2. https://www.javatpoint.com/process-vs-thread


>  Any solution to the critical section problem must satisfy three requirements:
- ****Mutual Exclusion****: If a process is executing in its critical section, then no other process is allowed to execute in the critical section.
- ****Progress****: If no process is executing in the critical section and other processes are waiting outside the critical section, then only those processes that are not executing in their remainder section can participate in deciding which will enter the critical section next, and the selection can not be postponed indefinitely.
- **Bounded Waiting**: A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted.

3. semaphores: https://www.geeksforgeeks.org/semaphores-in-process-synchronization/

#### Swapping
Swapping is **a technique used by operating systems to move less frequently used memory pages from RAM to a hard disk**..

#### Segmentation
In Operating Systems, Segmentation is a memory management technique in which the memory is divided into the variable size parts. Each part is known as a segment which can be allocated to a process. The details about each segment are stored in a table called a segment table. Segment table is stored in one (or many) of the segments.

Segment table contains mainly two information about segment:
1. Base: It is the base address of the segment
2. Limit: It is the length of the segment.

#### demand paging
Demand paging in os is **a technique in which pages are loaded from disk into main memory only when they are needed, i.e., demanded by the program**.


#### Virtual memory
**enable a computer to compensate for physical memory shortages, temporarily transferring data from random access memory (RAM) to disk storage**.
https://www.javatpoint.com/os-virtual-memory