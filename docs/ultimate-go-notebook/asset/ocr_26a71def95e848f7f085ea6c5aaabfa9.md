cores). Threads also maintain their own state to allow for the safe, local, and independent execution of their instructions.

The OS scheduler is responsible for making sure cores are not idle if there are Threads that can be executing. It must also create the illusion that all the Threads that can execute are executing at the same time. In the process of creating this illusion, the scheduler needs to run Threads with a higher priority over lower priority Threads. However, Threads with a lower priority can't be starved of execution time. The scheduler also needs to minimize scheduling latencies as much as possible by making quick and smart decisions.

A lot goes into the algorithms to make this happen, but luckily there are decades of work and experience the industry is able to leverage. To understand all of this better, it's good to describe and define a few concepts that are important.

# Executing Instructions

The program counter (PC), which is sometimes called the instruction pointer (IP), is what allows the Thread to keep track of the next instruction to execute. In most processors, the PC points to the next instruction and not the current instruction.