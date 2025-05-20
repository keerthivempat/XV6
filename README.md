# XV6 Operating System Enhancements

This project enhances the XV6 operating system with additional system calls and scheduling algorithms.

## System Calls

### getSysCount
- Counts how often a specific system call is invoked
- Used via the `syscount <mask> command [args]` program
- Displays count and name of the system call when command completes

### sigalarm & sigreturn
- `sigalarm`: Sets up periodic CPU time alerts for processes
- `sigreturn`: Resets process state after handler execution

## Scheduling Algorithms

The project implements two additional scheduling policies beyond the default round-robin:

### Lottery Based Scheduling (LBS)
- Assigns CPU time proportionally to process ticket counts
- `settickets` system call allows processes to adjust their ticket count
- Includes tie-breaking based on process arrival time

### Multi-Level Feedback Queue (MLFQ)
- Four priority queues with different time slices
- Processes move between queues based on CPU usage
- Features priority boosting to prevent starvation

## Compilation

```
make clean; make qemu                # Default Round Robin
make clean; make qemu SCHEDULER=LBS  # Lottery Based Scheduling
make clean; make qemu SCHEDULER=MLFQ # Multi Level Feedback Queue
```

Press Ctrl+P in XV6 to view process information for debugging.
