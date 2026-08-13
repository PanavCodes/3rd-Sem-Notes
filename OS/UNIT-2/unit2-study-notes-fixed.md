# Unit 2 Study Notes: Process and Process Scheduling

**Title of Unit 2:** Process and Process Scheduling  
**Primary Teaching Source:** `UNIT2-process.pptx`  
**Syllabus Reference:** `Operating Systems 2025-26.pdf`  
**Course Policy Mapping:** Unit 2 (Process Description, PCB, Threads, Thread Management, Process vs. Thread Comparison, Types of Schedulers, CPU Scheduling Algorithms)

---

## 📋 UNIT 2 SYLLABUS COVERAGE MAP & AUDIT

This coverage map ensures that every single official curriculum topic and PowerPoint slide is accounted for, fully integrated, and thoroughly taught in these study notes.

### 1. Curriculum Coverage Mapping

| Course Policy Topic / Subtopic               | Correlating PPT Slide / Section            | Status in These Notes | Reference Location    |
| :---------------------------------------------------- | :---------------------------------------------------- | :-------------------: | :-------------------- |
| **Process Description (Concepts & Definition)**       | Slide 2: Process Concept; Slide 3: Process vs Program |   **Fully Covered**   | Module 1, Section 1.1 |
| **Process Memory Layout**                             | Slide 4: Process in Memory                            |   **Fully Covered**   | Module 1, Section 1.2 |
| **Process State & Transitions**                       | Slide 5: Diagram of Process State                     |   **Fully Covered**   | Module 1, Section 1.3 |
| **Process Control Block (PCB)**                       | Slide 6: Process Control Block (PCB)                  |   **Fully Covered**   | Module 1, Section 1.4 |
| **Operations: Process Creation & Termination**        | Slide 7: Process Creation / Termination               |   **Fully Covered**   | Module 2, Section 2.1 |
| **Context Switching**                                 | Slide 8: Context Switch                               |   **Fully Covered**   | Module 2, Section 2.2 |
| **Scheduling Queues**                                 | Slide 9: Scheduling Queues                            |   **Fully Covered**   | Module 3, Section 3.1 |
| **Types of Schedulers (Long, Short, Medium-Term)**    | Slide 10: Schedulers                                  |   **Fully Covered**   | Module 3, Section 3.2 |
| **Scheduling Criteria (Objectives & Formulas)**       | Slide 11: Scheduling Criteria                         |   **Fully Covered**   | Module 3, Section 3.3 |
| **FCFS Scheduling Algorithm**                         | Slides 12-13: FCFS Scheduling                         |   **Fully Covered**   | Module 4, Section 4.1 |
| **SJF Scheduling Algorithm (Non-Preemptive)**         | Slide 14: Shortest Job First (SJF)                    |   **Fully Covered**   | Module 4, Section 4.2 |
| **SRTF Scheduling Algorithm (Preemptive SJF)**        | Slide 15: Shortest-Remaining-Time-First               |   **Fully Covered**   | Module 4, Section 4.3 |
| **Priority Scheduling (Preemptive & Non-Preemptive)** | Slide 16: Priority Scheduling                         |   **Fully Covered**   | Module 4, Section 4.4 |
| **Round Robin (RR) Scheduling Algorithm**             | Slide 17: Round Robin (RR)                            |   **Fully Covered**   | Module 4, Section 4.5 |
| **Threads (Definition & Lightweight Process)**        | Slide 18: What are Threads?                           |   **Fully Covered**   | Module 5, Section 5.1 |
| **Process vs. Thread (Comprehensive Table)**          | Slide 19: Process vs Thread                           |   **Fully Covered**   | Module 5, Section 5.2 |
| **User-Level v/s Kernel-Level Threads**               | Slide 20: Types of Threads                            |   **Fully Covered**   | Module 5, Section 5.3 |
| **Multithreading Models**                             | Slide 21: Multithreading Models                       |   **Fully Covered**   | Module 5, Section 5.4 |

---

## 🧠 MODULE 1: PROCESS CONCEPT & DESCRIPTION

### 1.1 Process Definition & Concept

- ⭐ **Must Remember (Definition):** A **process** is defined as a **"program in execution"**. While a program is a passive, static collection of instructions stored on disk, a process is an active, dynamic entity loaded in memory, executing sequentially under operating system management.
- 🧠 **Must Understand (Key Distinctions):**
  - **Program (Passive Entity):** An executable file (like `bin/ls` or `text_editor.exe`) residing on secondary storage (disk). It requires no active resources other than disk storage.
  - **Process (Active Entity):** Created when an executable file is loaded into main memory (RAM). It possesses a program counter specifying the next instruction to execute, along with an execution context, CPU registers, variables, and assigned system resources (memory, open files, and I/O devices).
  - **One Program, Multiple Processes:** A single program can spawn several distinct processes. For example, if multiple users run the same web browser program, or a single user opens multiple browser windows, each instance operates as an independent process with its own unique state, stack, and data segments.
- ✍️ **Exam Focus:** Explain how a program becomes a process. (A program becomes a process when its binary image is loaded into main memory, a Process Control Block is allocated, memory segments are mapped, and the program counter is initialized to the first executable instruction).

---

### 1.2 Memory Layout of a Process

When a program is loaded into RAM and transformed into an active process, the operating system partitions its logical address space into five distinct sections:

```
+------------------------------------+  <- High Address (e.g., 0xFFFFFFFF)
|         OS Kernel Space (1 GB)     |  <- Restricted space for OS kernel code/data
+------------------------------------+  <- 0xC0000000 (User-Kernel Boundary)
|          Stack Segment             |  <- Grows downwards (towards lower addresses)
|                |                   |
|                v                   |
|        [ Unallocated Space ]       |
|                ^                   |
|                |                   |
|          Heap Segment              |  <- Grows upwards (allocated via malloc/new)
+------------------------------------+
|          BSS Segment               |  <- Uninitialized static/global variables (filled with 0)
+------------------------------------+
|          Data Segment              |  <- Explicitly initialized static/global variables
+------------------------------------+
|          Text Segment              |  <- Executable binary code / Program instructions
+------------------------------------+  <- Low Address (e.g., 0x08048000)
```

1.  **Text Section (Code Segment):**
    - Contains the executable machine language instructions (binary code) of the program.
    - Typically read-only and shareable among multiple instances to prevent accidental self-modification.
2.  **Data Section:**
    - Contains global variables and static variables that are explicitly initialized by the programmer at compilation.
3.  **BSS Section (Block Started by Symbol):**
    - Contains all global and static variables that are uninitialized or initialized to zero. The operating system automatically fills this region with zeros during process startup.
4.  **Heap Segment:**
    - Reserved memory for dynamic allocation during process runtime (e.g., `malloc()` in C, `new` in C++ or Java).
    - Managed manually by the programmer (or garbage collector) and grows upwards toward higher memory addresses.
5.  **Stack Segment:**
    - Used for temporary data storage during function (or method) execution.
    - Stores function parameters, return addresses (to resume previous code blocks), and local variables defined inside function blocks.
    - Grows downwards toward lower memory addresses.
    - _Note on Stack-Heap Collision:_ A **Segmentation Fault** occurs if the stack and heap grow to overlap, exhausting the process's logical address space.
    - _Note on Architecture Dependency:_ The 3 GB User Space / 1 GB Kernel Space memory split and the `0xC0000000` boundary are standard for 32-bit x86 Linux virtual memory layouts, but are highly implementation-dependent. On 64-bit architectures or other operating systems, different splits, sizes, and layout boundaries are used.

---

### 1.3 Process States & Transitions

- ⭐ **Must Remember (The Five-State Model):** As a process executes, its state changes to reflect its current activity. The standard five states are:
  1.  **New:** The process is in the process of being created but has not yet been loaded into main memory.
  2.  **Ready:** The process is loaded in main memory and is waiting to be allocated a processor (CPU).
  3.  **Running:** The CPU is currently executing the process's instructions.
  4.  **Waiting / Blocked:** The process is temporarily unable to execute because it is waiting for an external event to occur (such as an I/O operation completion, signal reception, or child process termination).
  5.  **Terminated:** The process has finished executing its instructions and its resources are being deallocated by the OS.

#### 📊 Diagram: The Five-State Transition Model

```
      (Admitted)            (Scheduler Dispatch)
  New ----------> Ready ----------------------------> Running
                    ^                                    |
                    |                                    |
                    |   (Time slice expired / Interrupt)  |
                    |------------------------------------|
                    |                                    |
                    |           (I/O Completion)         | (I/O or Event Wait)
                    |---------------- Waiting <----------|
                                                         |
                                                         v (Exit)
                                                     Terminated
```

#### Step-by-Step Transition Workflows:

1.  **New ➔ Ready (Admitted):** The operating system finishes creating the process control structures (PCB) and loads the process binary image into RAM, placing it into the **Ready Queue**.
2.  **Ready ➔ Running (Scheduler Dispatch):** The short-term CPU scheduler selects this process from the Ready Queue and assigns it to an available CPU core, beginning execution.
3.  **Running ➔ Ready (Interrupt / Preemption):** If the process is running and its allotted time quantum expires (in preemptive scheduling like Round Robin) or a higher-priority process arrives, the CPU forcibly halts it, shifting it back to the **Ready Queue** to wait its turn again.
4.  **Running ➔ Waiting (I/O or Event Wait):** The running process requests an operation that cannot complete immediately (such as reading from disk or waiting for a socket). It relinquishes CPU control and moves to a **Waiting/Blocked Queue** associated with that event.
5.  **Waiting ➔ Ready (I/O or Event Completion):** Once the requested I/O completes or the event occurs, the hardware interrupts the OS, which shifts the process out of the Waiting Queue and places it back in the **Ready Queue** (it cannot jump directly to Running).
6.  **Running ➔ Terminated (Exit):** The process finishes executing its final statement or executes an exit system call (like `exit()`), triggering the OS to reclaim its memory and mark its state as terminated.

---

### 1.4 Process Control Block (PCB)

- ⭐ **Must Remember (Definition):** To manage processes and support multiprogramming, the operating system maintains a central registry called the **Process Table**. Each process is represented in this table by a dedicated structure called the **Process Control Block (PCB)**, which stores all information needed to track, schedule, and execute that process.

#### 📊 Diagram: Structure of a Process Control Block

```
+------------------------------------+
|              Pointer               | -> Links to next PCB in ready/device list
+------------------------------------+
|           Process State            | -> New, Ready, Running, Waiting, Terminated
+------------------------------------+
|            Process ID              | -> Unique numerical identifier (PID)
+------------------------------------+
|          Program Counter           | -> Address of next instruction to execute
+------------------------------------+
|            CPU Registers           | -> Save state of registers (Accumulator, etc.)
+------------------------------------+
|       CPU Scheduling Info          | -> Priority, scheduling queue pointers
+------------------------------------+
|       Memory Management Info       | -> Page tables, base/limit registers
+------------------------------------+
|        Accounting Information      | -> CPU time used, time limits, account numbers
+------------------------------------+
|        I/O Status Information      | -> List of open files, allocated devices
+------------------------------------+
```

#### Detailed PCB Fields & Purpose:

- **Pointer:** Points to other PCBs in ready lists or device queues to allow the OS to maintain chain-linked scheduling queues.
- **Process State:** Records whether the process is currently new, ready, running, waiting, or terminated.
- **Process ID (PID):** A unique integer value assigned by the operating system at process creation used for system calls (like `kill(PID)`) and parent-child tracking.
- **Program Counter (PC):** Indicates the memory address of the very next instruction to be fetched and executed for this process. This must be saved when the process is suspended.
- **Registers:** CPU registers (accumulators, index registers, stack pointers, general-purpose registers, program status words) that must be saved during interrupts so the process can resume execution seamlessly later.
- **CPU Scheduling Information:** Includes process priority levels, pointers to scheduling queues, and other scheduling algorithm-specific parameters.
- **Memory Management Information:** Contains pointers to the page tables, segment tables, or base and limit register values that define the physical boundaries of the process's memory space.
- **Accounting Information:** Tracks the total CPU time consumed, wall-clock time elapsed, remaining execution time limits, and parent process account billing numbers.
- **Status Information (I/O Status):** Keeps track of allocated hardware devices, a table of open file descriptors, and pending signals.

---

## ✍️ MODULE 2: OPERATIONS ON PROCESSES & CONTEXT SWITCHING

### 2.1 Process Creation & Termination

Processes can create new processes dynamically during execution, establishing hierarchical parent-child relationships.

#### 2.1.1 Process Creation Workflow

- 🧠 **Must Understand (Unix/Linux Process Creation):** In Unix and Linux systems, process creation is implemented using two fundamental system calls: `fork()` and `exec()`.
  1.  **`fork()` System Call:**
      - Creates an exact duplicate of the parent process, called the **child process**.
      - The child process inherits the parent's logical address space, program counter, open files, and environment variables.
      - _Return Value Difference:_ To allow the parent and child code paths to diverge, `fork()` returns a **unique value to each**:
        - Returns **`0` to the child process**.
        - Returns the **Process ID (PID) of the child process to the parent process**.
        - Returns a **negative value** if process creation failed.
      - _Crucial Misconception Warning:_ Calling `fork()` does **not** automatically suspend the parent process. The parent and child processes execute concurrently. The parent is only suspended if it explicitly calls `wait()` or `waitpid()` afterward.
  2.  **`exec()` System Call:**
      - Replaces the logical memory space of the child process with a completely new binary executable file loaded from disk.
      - Initializes the program counter to the first executable statement of the new program, wiping out the parent code clone.
  3.  **`wait()` System Call:**
      - The parent process often calls `wait()` (or `waitpid()`) to block itself in the waiting queue until the child process completes execution and terminates.
      - Once the child terminates, the parent process resumes, picking up the child's exit status.

```
       Parent Process
             |
         calls fork()
             |
     +-------+-------+
     |               |
   (PID > 0)       (PID = 0)
     |               |
  Parent          Child calls exec("new_program")
  blocks             |
  in wait()       Child runs new executable
     |               |
     |            terminates (calls exit())
     |               |
     |<--------------+
  Parent resumes
```

#### 2.1.2 Process Termination causes:

1.  **Normal Exit (Voluntary):** The process finishes executing its instructions successfully and executes an `exit()` system call to notify the OS (e.g., returning `0` from `main()`).
2.  **Error Exit (Voluntary):** The process encounters an error conditions and exits gracefully, returning an error code (e.g., `exit(1)` when a file cannot be opened).
3.  **Fatal Error (Involuntary):** The operating system terminates the process forcibly because it performed an illegal action. Common triggers include:
    - _Arithmetic Exception:_ E.g., dividing an integer by zero.
    - _Memory Violations (Segmentation Fault):_ E.g., attempting to read or write to logical memory addresses outside its allocated bounds (like accessing index `-1` or a null pointer).
    - _Privilege Violation:_ Attempting to execute highly privileged instructions in User Mode.
4.  **Killed by another Process (Involuntary):** Another process with appropriate permissions executes a system call (like `kill(PID)`) to terminate it. Often used by parent processes to terminate children if they exceed their resource limits or are no longer needed.

---

### 2.2 Context Switching

- ⭐ **Must Remember (Definition):** A **context switch** is the mechanism by which the operating system saves the state (context) of a currently executing process on the CPU and restores the saved state of another process to resume its execution.
- 🧠 **Must Understand (Context Switch Workflow):**
  When the short-term scheduler decides to switch CPU execution from Process $P_1$ to Process $P_2$:
  1.  An interrupt or system call stops Process $P_1$ mid-execution.
  2.  The kernel saves $P_1$'s current instruction pointer, CPU registers, stack pointer, and memory bounds inside $P_1$'s **Process Control Block ($PCB_1$)**.
  3.  The kernel changes $P_1$'s state in $PCB_1$ from _Running_ to _Ready_ or _Waiting_.
  4.  The kernel selects $P_2$ from the Ready Queue and sets its state in $PCB_2$ to _Running_.
  5.  The kernel retrieves $P_2$'s saved registers, program counter, and memory registers from $P_2$'s **Process Control Block ($PCB_2$)**.
  6.  The CPU starts executing Process $P_2$ at the exact location indicated by its restored program counter.

```
   Process P1           Operating System Kernel           Process P2
       |                           |                          |
   Executing                       |                          |
       |                           |                          |
   [Interrupt] ------------------->|                          |
   (Suspended)                 Save state to PCB1             |
       |                       (registers, PC, stack)         |
       |                           |                          |
       |                       Schedule next                  |
       |                           |                          |
       |                       Load state from PCB2           |
       |                       (registers, PC, stack)         |
       |                           |                          |
       |                           +----------------------> Executing
```

- ✍️ **Exam Focus (System Overhead):** Why is context switching considered overhead?
  - Context switching is purely a housekeeping operation.
  - During a context switch, the CPU does **no useful user-level computation**.
  - The time required for context switching typically ranges from 1 to several hundred microseconds, which is a major performance bottleneck in heavily loaded multiprogramming environments.
  - Hardware designers combat this overhead by adding multiple register sets on the CPU (allowing a context switch to become a simple pointer change from one register set to another) and using modern thread architectures.
  - _Performance Note on Caches & TLB:_ Process context switches require flushing the Translation Lookaside Buffer (TLB) unless the processor supports hardware tagging like Address Space Identifiers (ASID). This flushing, combined with "cache pollution" (where the CPU's L1/L2/L3 caches are emptied of the old process's data), forces the CPU to fetch data from slow main memory, significantly adding to the context-switch overhead.
  - _Historical/Hardware Note:_ Some architectures, like the VAX, support direct hardware context swapping through single instructions like `svpctx` (save process context) and `ldpctx` (load process context) to/from a PCB in memory. Most modern CPU architectures (like x86 and ARM) do not have single context-switching instructions and instead perform context saving and restoring through software routines in the OS kernel.

---

## 📊 MODULE 3: PROCESS SCHEDULERS & SCHEDULING CRITERIA

### 3.1 Scheduling Queues

The operating system uses several queues to manage processes as they transition between states:

1.  **Job Queue:** Contains all processes in the system. It reside on disk (secondary memory), waiting for the long-term scheduler to admit them.
2.  **Ready Queue:** Resides in main memory (RAM). It holds all processes that are ready to run and waiting for CPU allocation. This queue is usually implemented as a linked list of PCBs.
3.  **Device Queues:** A collection of independent queues associated with specific physical hardware or I/O devices (e.g., Disk I/O Queue, Network Card Queue). If a process is blocked waiting for I/O, it resides in the device queue of that respective hardware.

---

### 3.2 Types of Schedulers

The operating system employs three distinct types of schedulers, categorized by how frequently they are invoked and their main objective:

| Feature                        | Long-Term Scheduler (Job Scheduler)                             | Short-Term Scheduler (CPU Scheduler)                             | Medium-Term Scheduler (Swapping Scheduler)                                       |
| :----------------------------- | :-------------------------------------------------------------------- | :--------------------------------------------------------------------- | :------------------------------------------------------------------------------- |
| **Primary Role**               | Selects processes from the disk pool and loads them into RAM.   | Selects ready processes from RAM and assigns them to the CPU.    | Swaps processes in/out of main memory to disk (virtual memory).                  |
| **Invocation Frequency**       | Very low (seconds/minutes); runs only when a process exits or enters. | Extremely high (milliseconds); must be incredibly fast.          | Medium (as memory demands change).                                               |
| **Degree of Multiprogramming** | **Directly controls** the number of processes in main memory.   | Has no direct control over the number of active processes.             | **Reduces** the degree of multiprogramming if memory is exhausted.               |
| **Process Balance**            | Balances the mix of I/O-bound and CPU-bound processes.                | Schedules CPU-bound or ready processes directly on the processor core. | Frees RAM by moving idle or blocked processes to swap space (secondary storage). |
| **Performance Overhead**       | Slow execution is tolerable because of low invocation rates.          | Must incur **minimal overhead** to prevent slowing the CPU.      | Moderate overhead due to disk read/write operations (swapping).                  |

---

### 3.3 CPU Scheduling Objectives & Formulas

To evaluate the performance of different CPU scheduling algorithms, we use several standard criteria:

1.  **CPU Utilization ($\%$):**
    - The percentage of time the CPU is actively performing useful work (ranging from 0% to 100%).
2.  **Throughput ($T$):**
    - The number of completed processes executed per unit of time (e.g., 5 jobs per minute).
3.  **Completion Time ($CT$):**
    - The exact wall-clock time at which a process finishes executing its final instruction.
4.  **Turnaround Time ($TAT$):**
    - The total elapsed time from process submission (Arrival Time) to its completion.
      $\mathbf{TAT = CT - AT}$
5.  **Waiting Time ($WT$):**
    - The total time a process spends waiting in the Ready Queue.
      $\mathbf{WT = TAT - BT}$
    - _Alternate Formula (Preemptive Scenarios):_ $\mathbf{WT = \text{Start Time} - \text{Arrival Time} + \text{Remaining Wait Times during preemptive pauses}}$.
6.  **Response Time ($RT$):**
    - The elapsed time from process submission (Arrival Time) until the CPU produces its **very first execution response**.
      $\mathbf{RT = \text{Time of First CPU Response} - \text{Arrival Time}}$
7.  **Fairness:**
    - Ensuring that every process gets a fair share of CPU time and no process suffers from starvation.

---

## 🧮 MODULE 4: STUDY OF SCHEDULING ALGORITHMS & SOLVED NUMERICALS

### 4.1 First-Come, First-Served (FCFS) Scheduling

- **Basic Idea:** The process that requests the CPU first is allocated the CPU first. It is a simple, **non-preemptive** scheduling algorithm managed as a FIFO (First-In, First-Out) queue.
- **Tie-Breaker:** Earliest Arrival Time ($AT$), followed by alphabetical Process ID.
- _Note on Conventions:_ Sorting ties alphabetically or by Process ID is a standard classroom convention used for resolving exam questions. Real operating systems tie-break based on the exact clock arrival sequence, FIFO queue insertion order, or other internal scheduler metrics.

#### Solved Problem 1: All Processes Arrive at Time 0 ($AT = 0$)

Consider processes $P_1$, $P_2$, $P_3$ arriving at $AT = 0$ with the following burst times:

- $P_1$: $BT = 24$ ms
- $P_2$: $BT = 3$ ms
- $P_3$: $BT = 3$ ms

---

##### **Scenario A: Arrival Order is $P_1, P_2, P_3$**

**1. Create the Gantt Chart:**

```
+------------------------------------+-------+-------+
|                 P1                 |  P2   |  P3   |
+------------------------------------+-------+-------+
0                                   24      27      30
```

**2. Solve for individual times:**

- **$CT$:** $P_1 = 24$, $P_2 = 27$, $P_3 = 30$
- **$TAT$ ($CT - AT$):**
  - $P_1 = 24 - 0 = 24$ ms
  - $P_2 = 27 - 0 = 27$ ms
  - $P_3 = 30 - 0 = 30$ ms
- **$WT$ ($TAT - BT$):**
  - $P_1 = 24 - 24 = 0$ ms
  - $P_2 = 27 - 3 = 24$ ms
  - $P_3 = 30 - 3 = 27$ ms

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{0 + 24 + 27}{3} = \mathbf{17.0\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{24 + 27 + 30}{3} = \mathbf{27.0\text{ ms}}$

---

##### **Scenario B: Arrival Order is $P_2, P_3, P_1$**

**1. Create the Gantt Chart:**

```
+-------+-------+------------------------------------+
|  P2   |  P3   |                 P1                 |
+-------+-------+------------------------------------+
0       3       6                                   30
```

**2. Solve for individual times:**

- **$CT$:** $P_2 = 3$, $P_3 = 6$, $P_1 = 30$
- **$TAT$ ($CT - AT$):**
  - $P_2 = 3 - 0 = 3$ ms
  - $P_3 = 6 - 0 = 6$ ms
  - $P_1 = 30 - 0 = 30$ ms
- **$WT$ ($TAT - BT$):**
  - $P_2 = 3 - 3 = 0$ ms
  - $P_3 = 6 - 3 = 3$ ms
  - $P_1 = 30 - 24 = 6$ ms

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{0 + 3 + 6}{3} = \mathbf{3.0\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{3 + 6 + 30}{3} = \mathbf{13.0\text{ ms}}$

---

#### 🧠 Concept: The Convoy Effect

- **Definition:** The **Convoy Effect** is a scheduling phenomenon where short processes are forced to wait for long periods of time in the ready queue behind a single, highly resource-intensive, CPU-bound process.
- **Impact:** As demonstrated by comparing Scenario A ($\text{Avg WT} = 17$ ms) with Scenario B ($\text{Avg WT} = 3$ ms), having the longest process execute first severely inflates the average waiting time and turnaround times, leading to sluggish system performance.

---

#### Solved Problem 2: FCFS with Varying Arrival Times

Consider the following set of 4 processes:

|  Process  | Arrival Time ($AT$) | Burst Time ($BT$) |
| :-------: | :-----------------: | :---------------: |
| **$P_1$** |          0          |         8         |
| **$P_2$** |          1          |         4         |
| **$P_3$** |          2          |         9         |
| **$P_4$** |          3          |         5         |

**1. Create the Gantt Chart:**
Since FCFS is non-preemptive, we schedule processes strictly by their arrival time order: $P_1 \to P_2 \to P_3 \to P_4$.

```
+------------------------+-------+---------------------------+---------------+
|           P1           |  P2   |            P3             |      P4       |
+------------------------+-------+---------------------------+---------------+
0                        8      12                          21              26
```

**2. Solve for individual times:**

- **$P_1$:** $CT = 8$, $TAT = 8 - 0 = 8$ ms, $WT = 8 - 8 = 0$ ms.
- **$P_2$:** $CT = 12$, $TAT = 12 - 1 = 11$ ms, $WT = 11 - 4 = 7$ ms.
- **$P_3$:** $CT = 21$, $TAT = 21 - 2 = 19$ ms, $WT = 19 - 9 = 10$ ms.
- **$P_4$:** $CT = 26$, $TAT = 26 - 3 = 23$ ms, $WT = 23 - 5 = 18$ ms.

**3. Summarize in a Table:**

| Process ID | Arrival Time ($AT$) | Burst Time ($BT$) | Completion ($CT$) | Turnaround ($TAT$) | Waiting ($WT$) |
| :--------: | :-----------------: | :---------------: | :---------------: | :----------------: | :------------: |
| **$P_1$**  |          0          |         8         |         8         |         8          |       0        |
| **$P_2$**  |          1          |         4         |        12         |         11         |       7        |
| **$P_3$**  |          2          |         9         |        21         |         19         |       10       |
| **$P_4$**  |          3          |         5         |        26         |         23         |       18       |

**4. Compute Averages:**

- $\text{Average Waiting Time} = \frac{0 + 7 + 10 + 18}{4} = \frac{35}{4} = \mathbf{8.75\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{8 + 11 + 19 + 23}{4} = \frac{61}{4} = \mathbf{15.25\text{ ms}}$

---

### 4.2 Shortest Job First (SJF) - Non-Preemptive Scheduling

- **Basic Idea:** Associate the length of each process's next CPU burst with the process. When the CPU becomes free, the operating system selects the process with the **shortest burst time**.
- **Tie-Breaker:** FCFS (earliest Arrival Time).
- _Note:_ Non-preemptive means that once a process gets the CPU, it runs uninterrupted to completion.

#### Solved Problem 3: All Processes Arrive at Time 0 ($AT = 0$)

Consider the processes:

- $P_1$: $BT = 5$ ms
- $P_2$: $BT = 2$ ms
- $P_3$: $BT = 6$ ms
- $P_4$: $BT = 4$ ms

**1. Create the Gantt Chart:**
Sort by Burst Time: $P_2 (2) \to P_4 (4) \to P_1 (5) \to P_3 (6)$.

```
+-------+-----------+--------------------+-----------------------+
|  P2   |    P4     |         P1         |          P3           |
+-------+-----------+--------------------+-----------------------+
0       2           6                   11                      17
```

**2. Solve for individual times:**

- **$CT$:** $P_2 = 2$, $P_4 = 6$, $P_1 = 11$, $P_3 = 17$
- **$TAT$ ($CT - AT$):**
  - $P_2 = 2$, $P_4 = 6$, $P_1 = 11$, $P_3 = 17$
- **$WT$ ($TAT - BT$):**
  - $P_2 = 2 - 2 = 0$ ms
  - $P_4 = 6 - 4 = 2$ ms
  - $P_1 = 11 - 5 = 6$ ms
  - $P_3 = 17 - 6 = 11$ ms

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{6 + 0 + 11 + 2}{4} = \frac{19}{4} = \mathbf{4.75\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{11 + 2 + 17 + 6}{4} = \frac{36}{4} = \mathbf{9.0\text{ ms}}$

---

#### Solved Problem 4: Non-Preemptive SJF with Arrival Times

Consider the processes:

| Process ID | Arrival Time ($AT$) | Burst Time ($BT$) |
| :--------: | :-----------------: | :---------------: |
| **$P_1$**  |          0          |        10         |
| **$P_2$**  |          1          |         5         |
| **$P_3$**  |          2          |         8         |
| **$P_4$**  |          3          |        15         |

**Step-by-Step Chronological Allocation:**

- **At $t = 0$:** Only **$P_1$** has arrived. It starts running (Grows from $0 \to 10$ ms).
- **During $0 \to 10$ ms:** All other processes arrive ($P_2$ at $1$, $P_3$ at $2$, $P_4$ at $3$).
- **At $t = 10$:** $P_1$ completes execution. The ready queue contains: $P_2 (BT=5)$, $P_3 (BT=8)$, and $P_4 (BT=15)$. The shortest job is **$P_2$**, so it runs (Grows from $10 \to 15$ ms).
- **At $t = 15$:** $P_2$ completes. The ready queue contains $P_3 (BT=8)$ and $P_4 (BT=15)$. Shortest job is **$P_3$**, which executes (Grows from $15 \to 23$ ms).
- **At $t = 23$:** $P_3$ completes. **$P_4$** executes (Grows from $23 \to 38$ ms).

**1. Create the Gantt Chart:**

```
+------------------------+-------+---------------+-------------------------------+
|           P1           |  P2   |      P3       |              P4               |
+------------------------+-------+---------------+-------------------------------+
0                        10      15              23                              38
```

**2. Solve for individual times:**

- **$P_1$:** $CT = 10$, $TAT = 10 - 0 = 10$ ms, $WT = 10 - 10 = 0$ ms.
- **$P_2$:** $CT = 15$, $TAT = 15 - 1 = 14$ ms, $WT = 14 - 5 = 9$ ms.
- **$P_3$:** $CT = 23$, $TAT = 23 - 2 = 21$ ms, $WT = 21 - 8 = 13$ ms.
- **$P_4$:** $CT = 38$, $TAT = 38 - 3 = 35$ ms, $WT = 35 - 15 = 20$ ms.

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{0 + 9 + 13 + 20}{4} = \frac{42}{4} = \mathbf{10.5\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{10 + 14 + 21 + 35}{4} = \frac{80}{4} = \mathbf{20.0\text{ ms}}$

---

### 4.3 Shortest Remaining Time First (SRTF / Preemptive SJF)

- **Basic Idea:** When a new process arrives with a shorter remaining burst time than the currently executing process, the running process is **immediately preempted** and context-switched back to the ready queue.
- **Tie-Breaker:** FCFS.

#### Solved Problem 5: Preemptive SJF / SRTF

Consider the processes:

| Process ID | Arrival Time ($AT$) | Burst Time ($BT$) |
| :--------: | :-----------------: | :---------------: |
| **$P_1$**  |          0          |         8         |
| **$P_2$**  |          1          |         4         |
| **$P_3$**  |          2          |         9         |
| **$P_4$**  |          3          |         5         |

##### **Step-by-Step Ready Queue Tracking Workflow:**

- **At $t = 0$:** $P_1$ arrives with $BT = 8$. It is scheduled immediately.
- **At $t = 1$:** $P_2$ arrives with $BT = 4$.
  - _Remaining time for $P_1$_ = $8 - 1 = 7$ ms.
  - _Compare:_ $P_2$'s remaining BT ($4$) < $P_1$'s remaining BT ($7$).
  - _Action:_ **Preempt $P_1$**. Schedule $P_2$.
- **At $t = 2$:** $P_3$ arrives with $BT = 9$.
  - _Remaining time for $P_2$_ = $4 - 1 = 3$ ms.
  - _Compare:_ $P_2$ ($3$) vs. $P_1$ ($7$) vs. $P_3$ ($9$).
  - _Action:_ $P_2$ remains shortest. Continue execution.
- **At $t = 3$:** $P_4$ arrives with $BT = 5$.
  - _Remaining time for $P_2$_ = $3 - 1 = 2$ ms.
  - _Compare:_ $P_2$ ($2$) vs. $P_4$ ($5$) vs. $P_1$ ($7$) vs. $P_3$ ($9$).
  - _Action:_ $P_2$ remains shortest. Continue.
- **At $t = 5$:** $P_2$ completes execution (it ran uninterrupted from $t=1$ to $t=5$, its full $4$ ms burst).
  - _Compare remaining:_ $P_4$ ($5$) vs. $P_1$ ($7$) vs. $P_3$ ($9$).
  - _Action:_ $P_4$ is shortest. Schedule $P_4$ (runs from $5 \to 10$ ms).
- **At $t = 10$:** $P_4$ completes.
  - _Compare remaining:_ $P_1$ ($7$) vs. $P_3$ ($9$).
  - _Action:_ $P_1$ is shortest. Schedule $P_1$ (runs from $10 \to 17$ ms).
- **At $t = 17$:** $P_1$ completes.
  - _Only process remaining:_ $P_3$ ($9$).
  - _Action:_ Schedule $P_3$ (runs from $17 \to 26$ ms).
- **At $t = 26$:** $P_3$ completes.

**1. Create the Gantt Chart:**

```
+-----+---------------+-----------+---------------------+-----------------------+
| P1  |      P2       |    P4     |         P1          |          P3           |
+-----+---------------+-----------+---------------------+-----------------------+
0     1               5          10                    17                      26
```

**2. Solve for individual times:**

- **$CT$:** $P_2 = 5$, $P_4 = 10$, $P_1 = 17$, $P_3 = 26$.
- **$TAT$ ($CT - AT$):**
  - $P_1 = 17 - 0 = 17$ ms
  - $P_2 = 5 - 1 = 4$ ms
  - $P_3 = 26 - 2 = 24$ ms
  - $P_4 = 10 - 3 = 7$ ms
- **$WT$ ($TAT - BT$):**
  - $P_1 = 17 - 8 = 9$ ms
  - $P_2 = 4 - 4 = 0$ ms
  - $P_3 = 24 - 9 = 15$ ms
  - $P_4 = 7 - 5 = 2$ ms

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{9 + 0 + 15 + 2}{4} = \frac{26}{4} = \mathbf{6.5\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{17 + 4 + 24 + 7}{4} = \frac{52}{4} = \mathbf{13.0\text{ ms}}$

---

### 4.4 Priority Scheduling

- **Basic Idea:** A priority (integer) is associated with each process, and the CPU is allocated to the process with the **highest priority**.
- ⭐ **Must Remember (Standard Rule):** In standard textbook exercises, a **smaller integer indicates a higher priority** (e.g., Priority 1 is higher than Priority 5).
- _Note on Priority Conventions:_ The "smaller integer = higher priority" convention is standard in most academic textbooks (e.g., Silberschatz) and traditional UNIX nice values (where nice -20 is high and 19 is low). However, many production operating systems use the opposite convention. For instance, in Windows and Linux real-time scheduling, a larger integer represents a higher priority.
- **Tie-Breaker:** FCFS (earliest Arrival Time).
- **Preemptive Variant:** If a newly arrived process has higher priority than the currently running process, preemption occurs.
- **Non-Preemptive Variant:** Higher priority process is simply placed at the head of the ready queue.

#### Solved Problem 6: Non-Preemptive Priority Scheduling

Consider the processes arriving at $AT = 0$:

- $P_1$: $BT = 10$, $PR = 3$ (Normal Priority)
- $P_2$: $BT = 1$, $PR = 1$ (Highest Priority)
- $P_3$: $BT = 2$, $PR = 4$ (Lowest Priority)
- $P_4$: $BT = 1$, $PR = 5$ (Super Low Priority)
- $P_5$: $BT = 5$, $PR = 2$ (High Priority)

**1. Create the Gantt Chart:**
Sort by Priority: $P_2 (PR=1) \to P_5 (PR=2) \to P_1 (PR=3) \to P_3 (PR=4) \to P_4 (PR=5)$.

```
+---+-------+-----------------------+-------+---+
|P2 |  P5   |          P1           |  P3   |P4 |
+---+-------+-----------------------+-------+---+
0   1       6                      16      18  19
```

**2. Solve for individual times:**

- **$CT$:** $P_2 = 1$, $P_5 = 6$, $P_1 = 16$, $P_3 = 18$, $P_4 = 19$.
- **$TAT$ ($CT - AT$):**
  - $P_2 = 1 - 0 = 1$ ms
  - $P_5 = 6 - 0 = 6$ ms
  - $P_1 = 16 - 0 = 16$ ms
  - $P_3 = 18 - 0 = 18$ ms
  - $P_4 = 19 - 0 = 19$ ms
- **$WT$ ($TAT - BT$):**
  - $P_1 = 16 - 10 = 6$ ms
  - $P_2 = 1 - 1 = 0$ ms
  - $P_3 = 18 - 2 = 16$ ms
  - $P_4 = 19 - 1 = 18$ ms
  - $P_5 = 6 - 5 = 1$ ms

**3. Compute Averages:**

- $\text{Average Waiting Time} = \frac{6 + 0 + 16 + 18 + 1}{5} = \frac{41}{5} = \mathbf{8.2\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{16 + 1 + 18 + 19 + 6}{5} = \frac{60}{5} = \mathbf{12.0\text{ ms}}$

---

#### 🧠 Concept: Starvation and Aging

- **The Starvation Problem:** A major drawback of priority scheduling is **Starvation** (Indefinite Blocking). In a heavily loaded system, a continuous stream of high-priority processes arriving in the queue will permanently block low-priority processes, denying them CPU execution indefinitely.
- **The Aging Solution:** **Aging** is a dynamic prioritization technique used to resolve starvation. The operating system periodically increases the priority of ready processes that have been waiting in the queue for a long time. For example, a process with Priority 20 could have its priority increased by 1 every 15 minutes of wait time. Over time, its priority will eventually become high enough to guarantee CPU execution.

---

### 4.5 Round Robin (RR) Scheduling

- **Basic Idea:** Designed specifically for time-sharing systems, RR allocates CPU control as a circular queue, providing each ready process with a tiny, fixed interval of CPU execution time called a **Time Quantum ($q$)** (typically 10-100 ms).
- **Workflow:**
  - A running process executes for at most 1 Time Quantum.
  - If its remaining burst is less than $q$, it terminates voluntarily, relinquishing the CPU.
  - If its burst exceeds $q$, the CPU interrupts it, saves its context, moves it back to the tail of the Ready Queue, and executes the next process from the queue head.

#### Solved Problem 7: Round Robin with Time Quantum $q = 2$ ms

Consider the processes arriving at $AT = 0$:

- $P_1$: $BT = 2$ ms
- $P_2$: $BT = 1$ ms
- $P_3$: $BT = 8$ ms
- $P_4$: $BT = 4$ ms
- $P_5$: $BT = 5$ ms

##### **Chronological Execution Trace (Ready Queue tracking):**

- **Initial Queue:** $[P_1, P_2, P_3, P_4, P_5]$ (Arrival Order)

1.  **$t = 0 \to 2$:** **$P_1$** executes. $BT = 2$, so it completes execution at $t=2$ and exits.  
    _Queue status:_ $[P_2, P_3, P_4, P_5]$
2.  **$t = 2 \to 3$:** **$P_2$** executes. $BT = 1$ (less than $q=2$), so it completes execution at $t=3$ and exits.  
    _Queue status:_ $[P_3, P_4, P_5]$
3.  **$t = 3 \to 5$:** **$P_3$** executes for 2 ms. Remaining $BT = 8 - 2 = 6$. It is preempted at $t=5$ and appended to Ready Queue.  
    _Queue status:_ $[P_4, P_5, P_3]$
4.  **$t = 5 \to 7$:** **$P_4$** executes for 2 ms. Remaining $BT = 4 - 2 = 2$. It is preempted at $t=7$ and appended.  
    _Queue status:_ $[P_5, P_3, P_4]$
5.  **$t = 7 \to 9$:** **$P_5$** executes for 2 ms. Remaining $BT = 5 - 2 = 3$. It is preempted at $t=9$ and appended.  
    _Queue status:_ $[P_3, P_4, P_5]$
6.  **$t = 9 \to 11$:** **$P_3$** executes for 2 ms. Remaining $BT = 6 - 2 = 4$. Appended.  
    _Queue status:_ $[P_4, P_5, P_3]$
7.  **$t = 11 \to 13$:** **$P_4$** executes for 2 ms. Remaining $BT = 2 - 2 = 0$. It completes at $t=13$ and exits.  
    _Queue status:_ $[P_5, P_3]$
8.  **$t = 13 \to 15$:** **$P_5$** executes for 2 ms. Remaining $BT = 3 - 2 = 1$. Appended.  
    _Queue status:_ $[P_3, P_5]$
9.  **$t = 15 \to 17$:** **$P_3$** executes for 2 ms. Remaining $BT = 4 - 2 = 2$. Appended.  
    _Queue status:_ $[P_5, P_3]$
10. **$t = 17 \to 18$:** **$P_5$** executes for 1 ms. Remaining $BT = 1 - 1 = 0$. Completes at $t=18$ and exits.  
    _Queue status:_ $[P_3]$
11. **$t = 18 \to 20$:** **$P_3$** executes for final 2 ms. Remaining $BT = 2 - 2 = 0$. Completes at $t=20$ and exits.

**1. Create the Gantt Chart:**

```
+-----+---+-------+-------+-------+-------+-------+-------+-------+---+-------+
| P1  |P2 |  P3   |  P4   |  P5   |  P3   |  P4   |  P5   |  P3   |P5 |  P3   |
+-----+---+-------+-------+-------+-------+-------+-------+-------+---+-------+
0     2   3       5       7       9      11      13      15      17  18      20
```

**2. Solve for individual times:**

- **$CT$:** $P_1 = 2$, $P_2 = 3$, $P_4 = 13$, $P_5 = 18$, $P_3 = 20$.
- **$TAT$ ($CT - AT$):**
  - $P_1 = 2 - 0 = 2$ ms
  - $P_2 = 3 - 0 = 3$ ms
  - $P_3 = 20 - 0 = 20$ ms
  - $P_4 = 13 - 0 = 13$ ms
  - $P_5 = 18 - 0 = 18$ ms
- **$WT$ ($TAT - BT$):**
  - $P_1 = 2 - 2 = 0$ ms
  - $P_2 = 3 - 1 = 2$ ms
  - $P_3 = 20 - 8 = 12$ ms
  - $P_4 = 13 - 4 = 9$ ms
  - $P_5 = 18 - 5 = 13$ ms

**3. Summarize in a Table:**

| Process ID | Arrival Time ($AT$) | Burst Time ($BT$) | Completion ($CT$) | Turnaround ($TAT$) | Waiting ($WT$) |
| :--------: | :-----------------: | :---------------: | :---------------: | :----------------: | :------------: |
| **$P_1$**  |          0          |         2         |         2         |         2          |       0        |
| **$P_2$**  |          0          |         1         |         3         |         3          |       2        |
| **$P_3$**  |          0          |         8         |        20         |         20         |       12       |
| **$P_4$**  |          0          |         4         |        13         |         13         |       9        |
| **$P_5$**  |          0          |         5         |        18         |         18         |       13       |

**4. Compute Averages:**

- $\text{Average Waiting Time} = \frac{0 + 2 + 12 + 9 + 13}{5} = \frac{36}{5} = \mathbf{7.2\text{ ms}}$
- $\text{Average Turnaround Time} = \frac{2 + 3 + 20 + 13 + 18}{5} = \frac{56}{5} = \mathbf{11.2\text{ ms}}$

---

## 🧵 MODULE 5: THREAD CONCEPTS & THREAD MANAGEMENT

### 5.1 Thread Definition & Lightweight Process

- ⭐ **Must Remember (Definition):** A **thread** is the basic unit of CPU utilization. It represents a single sequential flow of execution within a larger parent process. It is often called a **Lightweight Process (LWP)**.
- 🧠 **Must Understand (Thread Model):**
  - A traditional (heavyweight) process possesses a single, dedicated thread of control.
  - A modern multi-threaded process contains several concurrent threads running in parallel, executing different or identical parts of the program instructions.
  - **Shared Resources:** Threads belonging to the same process **share its physical logical address space (code and data segments) and OS resources** (such as open files, file descriptors, and signals).
  - **Private Resources:** To execute independently, each thread maintains its own private:
    - Unique Thread ID
    - Program Counter (PC)
    - CPU Register Set (register state)
    - Stack segment (local variables and function call history)

```
        Single-Threaded Process                   Multi-Threaded Process
+------------------------------------+    +------------------------------------+
|  Code   |   Data    |  Open Files  |    |  Code   |   Data    |  Open Files  |
+------------------------------------+    +------------------------------------+
| Registers | Stack | thread-1       |    | thread1 | thread2 | thread3        |
+------------------------------------+    | Regs/   | Regs/   | Regs/          |
                                          | Stack   | Stack   | Stack          |
                                          +------------------------------------+
```

---

### 5.2 Process vs. Thread (Comprehensive Comparison Table)

✍️ **Exam Focus:** This is a highly frequent, 10-mark examination question.

| Parameter / Feature        | Process                                                                        | Thread                                                                                              |
| :------------------------- | :---------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------ |
| **Basic Definition**       | An independent program in execution (Heavyweight Process).                      | A basic, lightweight unit of CPU utilization within a process.                                      |
| **Resource Allocation**    | Allocated independent memory and hardware resources by the OS.                  | Shares the parent process's memory space and OS resources.                                         |
| **Address Space Sharing**  | Completely isolated; does not share memory with other processes.                    | Shares code, data segments, and global variables with sibling threads.                             |
| **Context Switching Time** | **High overhead**; heavier to context-switch as it requires memory pointer updates. | **Low overhead**; very fast context-switch because memory maps are preserved.                           |
| **Creation & Termination** | Takes significant system time and resources to spawn or terminate.                  | Extremely fast and cheap to create and destroy.                                                    |
| **Fault Isolation**        | **High fault isolation**. If one process crashes, other running processes are unaffected. | **Low isolation**. If one thread performs an illegal action (e.g., segfault), the **entire process crashes**. |
| **Communication**          | Requires heavy Inter-Process Communication (IPC) (e.g., pipes, message queues).           | Communicates easily by reading/writing to shared variables directly.                                          |
| **CPU Utilization**        | Slower to utilize parallel multicore CPUs due to process isolation.                       | High multicore utilization; different threads run on different cores in parallel.                       |

---

### 5.3 Types of Threads

Threads are divided into two classifications depending on which layer of the system supports and manages them:

1.  **User-Level Threads:**
    - Implemented and managed at the application layer by a user-space **thread library** (e.g., POSIX Pthreads, Java threads) without any operating system kernel awareness or direct support.
    - _Pros:_ Extremely fast to create and context-switch because no transition to privileged Kernel Mode is required. High execution portability.
    - _Cons:_ If a single user-level thread executes a blocking system call (e.g., waiting for disk I/O), the **entire process is blocked**, including all other ready threads. This is because the OS kernel is unaware of individual threads and schedules the process as a single unit.
2.  **Kernel-Level Threads:**
    - Created and managed directly by the operating system kernel (e.g., Windows threads, Linux native threads).
    - _Pros:_ If one kernel thread blocks, the kernel can schedule other ready threads of that same process for CPU execution. Supports parallel execution on multiprocessor/multicore systems.
    - _Cons:_ Slower to create and manage because every thread operation requires a kernel system call transition.

---

### 5.4 Multithreading Models

To execute user-level threads, they must be mapped to physical kernel-level threads supported by the OS. This mapping uses three standard models:

#### 1. Many-to-One Model

- **Mapping:** Maps many user-level threads to a single kernel thread.
- **Working:** Thread management is handled entirely in user space.
- **Drawback:** If any thread executes a blocking system call, the entire process blocks. Because only one thread can access the kernel at a time, multiple threads cannot run in parallel on multicore processors.

#### 2. One-to-One Model

- **Mapping:** Maps each individual user-level thread to its own dedicated kernel thread.
- **Working:** Overcomes the blocking issue; if one thread blocks, others continue executing. Allows threads to run in parallel on multiprocessors.
- **Drawback:** Spawning a user thread requires creating a corresponding kernel thread, which can degrade application performance if thread quantity is not restricted. (Used by Windows and Linux).
- _Modern Implementation Note:_ Although three models exist conceptually, almost all modern general-purpose operating systems (including Linux, Windows, macOS, and Android) have moved almost exclusively to the One-to-One multithreading model because of its superior performance on modern multicore processors and the reduction of complex user-space scheduling libraries.

#### 3. Many-to-Many Model

- **Mapping:** Multiplexes many user-level threads to a smaller or equal number of kernel-level threads.
- **Working:** Provides the best of both worlds. Developers can create as many user threads as needed, and the corresponding kernel threads can execute in parallel on multicore systems. If a thread performs a blocking call, the kernel can schedule another thread on a different kernel-level mapping.

---

## ✍️ EXAM-FOCUSED REVISION POINTS

### Key Equations to Memorize:

1.  **Turnaround Time ($TAT$):**  
    $TAT = CT - AT$
2.  **Waiting Time ($WT$):**  
    $WT = TAT - BT$
3.  **Response Time ($RT$):**  
    $RT = \text{First CPU Start Time} - AT$
4.  **CPU Utilization ($\%$):**  
    $\text{Utilization} = \frac{\text{Total CPU Active Time}}{\text{Total Session Time}} \times 100\%$
5.  **Throughput ($T$):**  
    $Throughput = \frac{\text{Number of completed processes}}{\text{Total Execution Time}}$

### Core Revision Terminology:

- **Program vs. Process:** Passive file on disk vs. active executing instance in memory.
- **Process Table:** OS central directory containing a PCB for every running process.
- **PCB:** Context record storing registers, program counter, state, memory boundaries, and priority.
- **Preemption:** Forcibly suspending a running process to run another process, preventing CPU monopolization.
- **Degree of Multiprogramming:** The number of active processes kept in main memory simultaneously.
- **Convoy Effect:** FCFS performance bottleneck where short processes wait behind a long process.
- **Starvation:** Low-priority tasks waiting indefinitely because high-priority tasks keep arriving.
- **Aging:** Preventing starvation by slowly increasing a waiting process's priority over time.
- **LWP:** Lightweight Process, another name for a thread.
- **Context Switch Overhead:** Time spent saving/loading register states; registers, page maps, and CPU caches must be flushed, during which no user work is completed.

---

## 📝 UNIVERSITY EXAM PRACTICE QUESTIONS

### Short-Answer Questions (2 Marks)

#### Q1. Define a Process.

**Answer:** A process is defined as a program under execution. It is an active entity loaded in RAM, consisting of executable machine instructions, a program counter, CPU registers, a stack, and dynamic data segments.

#### Q2. Explain the Convoy Effect in brief.

**Answer:** The Convoy Effect occurs under FCFS scheduling when short processes wait in the ready queue behind a single long-running, CPU-bound process. This significantly increases the average waiting and turnaround times of the entire system.

#### Q3. What is the role of a Program Counter in a process's memory space?

**Answer:** The Program Counter holds the memory address of the next machine instruction to be executed for the process. During context switching, this value is saved in the PCB so the process can resume from the exact location it was preempted.

#### Q4. Differentiate between stack and heap memory of a process.

**Answer:** Stack memory stores temporary data associated with function calls, including function parameters, return addresses, and local variables (grows downwards). Heap memory is reserved for dynamic memory allocation at runtime via `malloc()` or `new` (grows upwards).

---

### Analytical & Essay Questions (5 to 10 Marks)

#### Q5. Explain the Process Control Block (PCB). Draw its block structure and discuss any five fields.

**Answer:** (For full credit, reproduce the block structure diagram from Section 1.4). The PCB is the central data structure used by the OS to represent a process. Five key fields include:

1.  **Process ID (PID):** A unique numerical identifier assigned to the process.
2.  **Program Counter (PC):** The memory address of the next instruction to execute.
3.  **Process State:** Records the process's current state (New, Ready, Running, etc.).
4.  **CPU Registers:** Holds the context of registers (accumulators, pointers) when suspended.
5.  **Memory Management Information:** Contains base/limit registers or page table pointers.

#### Q6. Compare User-Level Threads and Kernel-Level Threads across five distinct parameters.

**Answer:**

```
+------------------+------------------------------------+------------------------------------+
| Parameter        | User-Level Threads                 | Kernel-Level Threads               |
+------------------+------------------------------------+------------------------------------+
| Supported By     | User-space libraries (Pthreads)    | OS Kernel directly.          |
| Context Switch   | Very fast; no kernel mode change   | Slow; requires system call transition|
| Blocking Effect  | One blocked thread blocks process  | One blocked thread doesn't block OS |
| Creation speed   | Extremely fast                     | Slower                             |
| Hardware Support | Cannot use parallel processors     | Can run on parallel multicore cores|
+------------------+------------------------------------+------------------------------------+
```

---

## 🔍 UNIT 2 SYSTEM VERIFICATION CHECKLISTS

To verify full academic preparation, use these checklists to confirm that all slides and Course Policy topics are accounted for.

### 1. Slide-by-Slide PPT Checklist

- [x] **Slide 1: Title Page** ➔ _Fully Covered_ (Syllabus reference block)
- [x] **Slide 2: Process Concept** ➔ _Fully Covered_ (Module 1, Section 1.1)
- [x] **Slide 3: Process vs Program** ➔ _Fully Covered_ (Module 1, Section 1.1)
- [x] **Slide 4: Process in Memory** ➔ _Fully Covered_ (Module 1, Section 1.2 Memory Layout)
- [x] **Slide 5: Diagram of Process State** ➔ _Fully Covered_ (Module 1, Section 1.3 State transitions)
- [x] **Slide 6: Process Control Block (PCB)** ➔ _Fully Covered_ (Module 1, Section 1.4 PCB layout)
- [x] **Slide 7: Operations: Process Creation / Termination** ➔ _Fully Covered_ (Module 2, Section 2.1)
- [x] **Slide 8: Context Switch** ➔ _Fully Covered_ (Module 2, Section 2.2 Switch trace)
- [x] **Slide 9: Scheduling Queues** ➔ _Fully Covered_ (Module 3, Section 3.1)
- [x] **Slide 10: Schedulers** ➔ _Fully Covered_ (Module 3, Section 3.2 Comparison)
- [x] **Slide 11: Scheduling Criteria** ➔ _Fully Covered_ (Module 3, Section 3.3 Objectives)
- [x] **Slide 12: FCFS Scheduling Algorithm** ➔ _Fully Covered_ (Module 4, Section 4.1 Scenario A)
- [x] **Slide 13: FCFS Scheduling Algorithm (Cont.)** ➔ _Fully Covered_ (Module 4, Section 4.1 Scenario B)
- [x] **Slide 14: Shortest Job First (SJF)** ➔ _Fully Covered_ (Module 4, Section 4.2 Solved Problem 3)
- [x] **Slide 15: Shortest-Remaining-Time-First** ➔ _Fully Covered_ (Module 4, Section 4.3 Solved Problem 5)
- [x] **Slide 16: Priority Scheduling** ➔ _Fully Covered_ (Module 4, Section 4.4 Solved Problem 6)
- [x] **Slide 17: Round Robin (RR)** ➔ _Fully Covered_ (Module 4, Section 4.5 Solved Problem 7)
- [x] **Slide 18: What are Threads?** ➔ _Fully Covered_ (Module 5, Section 5.1 Definition)
- [x] **Slide 19: Process vs Thread** ➔ _Fully Covered_ (Module 5, Section 5.2 Detailed Table)
- [x] **Slide 20: Types of Threads** ➔ _Fully Covered_ (Module 5, Section 5.3 Types)
- [x] **Slide 21: Multithreading Models** ➔ _Fully Covered_ (Module 5, Section 5.4 Mapping models)

### 2. Course Policy Syllabus Checklist

- [x] **Process Description** ➔ _Fully Covered_ (Syllabus Duration: 06 Hours)
- [x] **Process Control Block** ➔ _Fully Covered_ (Detailed fields and purpose)
- [x] **Threads** ➔ _Fully Covered_ (LWP and multithread models)
- [x] **Thread Management** ➔ _Fully Covered_ (User vs. Kernel comparison)
- [x] **Comparison between Processes and Threads** ➔ _Fully Covered_ (Unified comparison matrix)
- [x] **Process Scheduling Types** ➔ _Fully Covered_ (Schedulers and scheduling criteria)
- [x] **Comparison of Scheduling Algorithms** ➔ _Fully Covered_ (FCFS, SJF, SRTF, Priority, RR solved step-by-step)
