1. read types of OS from copy
2. https://www.javatpoint.com/process-vs-thread


>  Any solution to the critical section problem must satisfy three requirements:
- ****Mutual Exclusion****: If a process is executing in its critical section, then no other process is allowed to execute in the critical section.
- ****Progress****: If no process is executing in the critical section and other processes are waiting outside the critical section, then only those processes that are not executing in their remainder section can participate in deciding which will enter the critical section next, and the selection can not be postponed indefinitely.
- **Bounded Waiting**: A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted.

3. semaphores: https://www.geeksforgeeks.org/semaphores-in-process-synchronization/
4. 