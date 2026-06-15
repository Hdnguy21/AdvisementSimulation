# Advisement Simulation

## Course Context
Built for ACO350 (Systems Programming) at Arizona State University. The assignment required completing a partially implemented C source file by writing the full multi-threaded synchronization logic for both the professor and student processes.

## Tech Stack
- **Language:** C
- **Libraries:** POSIX Pthreads (`pthread_t`, `pthread_create`, `pthread_join`), POSIX Semaphores (`sem_t`, `sem_init`, `sem_wait`, `sem_post`)
- **Tools:** GNU Compiler Collection (gcc), GNU Make, Linux CLI, SSH on ASU remote cluster servers

## What It Does
Simulates a real-world multi-threaded waiting room system where a professor conducts advising sessions with arriving students. Student threads check for available chairs, wait using semaphores, and safely exit if no seats are available — all without race conditions or deadlocks.

## Key Technical Features
- **Dynamic Thread Allocation:** Creates one persistent professor thread and a configurable cascade of staggered student threads
- **Critical Section Protection:** Binary semaphore (`accessHallSeats`) acts as a mutex lock protecting the shared seat count variable
- **Semaphore Handshaking:** Three semaphores (`professorReady`, `studentReady`, `studentDone`) orchestrate step-by-step consultation synchronization between threads
- **Bounded Resource Handling:** Student threads safely exit when no chairs are available rather than blocking indefinitely
- **Timed Simulation:** Random microsecond delays (`usleep`) simulate dynamic arrival rates and varying discussion lengths

## How to Run
```bash
# Compile
make

# Run with input file
./advisement < sim1.txt
```

## Concepts Demonstrated
- Concurrency and multithreading in C
- Semaphore-based thread synchronization and mutual exclusion
- Deadlock avoidance through proper semaphore ordering
- Race condition prevention on shared memory
- Resource-bounded system design
