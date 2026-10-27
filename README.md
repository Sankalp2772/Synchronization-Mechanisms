# Experiment 5: Synchronization Mechanisms in Parallel Programs

## Objective
To implement and compare synchronization mechanisms in parallel programs, including race conditions, critical sections, atomic operations, barriers, semaphores, and locks.

## Technologies Used
- Ubuntu Linux
- C Programming
- GCC Compiler
- OpenMP
- POSIX Threads (Pthreads)
- POSIX Semaphores

## Programs Implemented

| Program | Description |
|---|---|
| `race.c` | Demonstrates a race condition |
| `critical.c` | Uses OpenMP critical sections |
| `atomic.c` | Uses atomic operations |
| `barrier.c` | Demonstrates barrier synchronization |
| `semaphore.c` | Uses POSIX threads and semaphores |
| `compare_sync.c` | Compares execution time and correctness |

## Benchmark Results

Workload: 10,000,000 shared counter increments.

| Mechanism | Threads | Final Count | Correctness | Time (s) |
|---|---:|---:|---|---:|
| None | 1 | 10000000 | Correct | 0.0046 |
| Critical | 1 | 10000000 | Correct | 0.1128 |
| Atomic | 1 | 10000000 | Correct | 0.0655 |
| Lock | 1 | 10000000 | Correct | 0.1106 |
| None | 2 | 5389513 | Incorrect | 0.0129 |
| Critical | 2 | 10000000 | Correct | 0.4182 |
| Atomic | 2 | 10000000 | Correct | 0.2018 |
| Lock | 2 | 10000000 | Correct | 0.4185 |
| None | 4 | 4209638 | Incorrect | 0.0157 |
| Critical | 4 | 10000000 | Correct | 0.5492 |
| Atomic | 4 | 10000000 | Correct | 0.1978 |
| Lock | 4 | 10000000 | Correct | 0.5776 |
| None | 8 | 2055329 | Incorrect | 0.0161 |
| Critical | 8 | 10000000 | Correct | 0.7106 |
| Atomic | 8 | 10000000 | Correct | 0.2322 |
| Lock | 8 | 10000000 | Correct | 0.6193 |

## Key Observations
- Unsynchronized updates resulted in incorrect counter values with multiple threads.
- Critical sections and locks maintained correctness but experienced contention.
- Atomic operations were faster than critical sections and locks in the multithreaded tests.
- Barrier synchronization ensured that all threads reached a synchronization point before proceeding.
- Semaphore synchronization protected access to a shared counter.

## Conclusion
The experiment demonstrated the importance of synchronization in parallel programs. Atomic operations offered a good balance of correctness and performance for simple shared-variable updates, while critical sections and locks introduced additional overhead under contention.

## Compilation Commands

```bash
gcc race.c -fopenmp -o race
gcc critical.c -fopenmp -o critical
gcc atomic.c -fopenmp -o atomic
gcc barrier.c -fopenmp -o barrier
gcc semaphore.c -pthread -o semaphore
gcc compare_sync.c -fopenmp -o compare_sync
```

## Execution

Run the programs using `./race`, `./critical`, `./atomic`, `./barrier`, `./semaphore`, and `./compare_sync` after compilation.
