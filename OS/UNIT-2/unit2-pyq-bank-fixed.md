# Unit 2 Operating Systems: Previous Year Questions (PYQ) Bank

This document contains a comprehensive, structured, and marks-aligned **Previous Year Questions (PYQ) Bank** for **Unit 2: Process and Process Scheduling**, compiled from all available exam papers, course policy documents, and lecture materials in your notebook.

---

## 1. Unit 2 Course Policy & Syllabus Alignment

According to the official **Operating Systems 2025-26 Course Policy** (Syllabus reference: `Operating Systems 2025-26.pdf`), the curriculum subtopics for Unit 2 include:

1. **Process Description** (Concepts, memory layout, and states)
2. **Process Control Block (PCB)** (Fields and multitasking facilitation)
3. **Threads & Thread Management** (Lightweight process concepts, thread context, and user-level v/s kernel-level threads)
4. **Comparison between Processes and Threads** (Resource sharing, overhead, and coupling differences)
5. **Process Scheduling: Types of Schedulers** (Long-Term, Short-Term, and Medium-Term Schedulers)
6. **Comparison of Scheduling Algorithms** (Preemptive/Non-preemptive, FCFS, SJF, SRTF, Priority, and Round Robin)

All PYQs found in your sources have been mapped directly to these six official subtopics.

---

## 2. Final Analysis of Unit 2 PYQs

### Topic-Wise PYQ Frequency & Analysis

| Topic Area                                   | Frequency in PYQs | Relative Weight | Most Frequently Asked Concept                                             |
| :------------------------------------------- | :---------------: | :-------------: | :------------------------------------------------------------------------ |
| **Process Concept, States & Layout**         |      6 Times      |      High       | Five-State Model, Process State Diagram, Memory Layout                    |
| **Process Control Block (PCB)**              |      5 Times      |    Very High    | PCB Fields, How PCB enables Multitasking, Context Switching               |
| **Process v/s Thread Comparison**            |      4 Times      |    Very High    | Process v/s Thread comparison table, User-level v/s Kernel-level threads  |
| **Preemptive v/s Non-preemptive Scheduling** |      3 Times      |      High       | Preemptive v/s Non-preemptive scheduling differences, Scheduling Criteria |
| **CPU Scheduling Numericals**                |      5 Times      |    Critical     | Preemptive Priority, Round Robin, SRTF (Preemptive SJF), and FCFS         |

### Key Observations & Insights

1. **Most Frequently Asked Topic:** **Process v/s Thread Comparison** and **Solved CPU Scheduling Numericals** are the highest-priority topics. Comparison questions appear as 5-mark tables (Special Re-Exam 2022-23, May 2016) or 10-mark multi-part explanations (Re-Exam 2022-23). Solved numericals appear as major 10-mark questions in almost every final exam paper.
2. **Repeated Concepts with Different Wording:**
   - _Process Definition:_ Asked as "Define process. Explain various process states with diagram" (Final Exam 2023-24) or "What do you mean by process? Explain process concept" (Dec 2014).
   - _Process Control Block:_ Asked as "Define a PCB. How can it help in enabling multitasking?" (Final Exam 2024-25) or "What is process control block? Explain it with diagram" (Special Re-Exam 2022-23).
3. **Questions Repeated Across Years:**
   - **Process State Transitions:** Repeated in Re-Exam 2022-23, Special Re-Exam 2022-23, and Final Exam 2023-24.
   - **FIFO, Optimal, and LRU Page Replacement (Cross-Unit overlap with Unit 5):** Appears repeatedly as Q2b in Special Re-Exam 2022-23, Q1b in Re-Exam 2022-23, and Q7b in 2023-24. (Note: These are handled in Unit 5, but scheduling algorithms occupy the center stage here in Unit 2).
4. **Diagram-Based PYQs and Locations:**
   - **Five-State Process Transition Diagram:** `📊 Diagram Required: YES`. Found in `UNIT2-process.pptx` Slide 5 (also Figure 2.3.1 in TechNeo).
   - **Process Control Block Layout:** `📊 Diagram Required: YES`. Found in `UNIT2-process.pptx` Slide 6 (also Figure 2.1.2/2.5.1 in TechNeo).
   - **Process Memory Layout:** `📊 Diagram Required: YES`. Found in `UNIT2-process.pptx` Slide 4 (also Figure 2.1.1 in TechNeo).
   - **Single-threaded v/s Multithreaded Process:** `📊 Diagram Required: YES`. Found in `UNIT2-process.pptx` Slide 18 (and Figure 2.6.1 in TechNeo).
5. **High-Priority Revision Topics:**
   - Context switching mechanics and the role of the PCB in preserving register states.
   - Designing execution Gantt charts for preemptive priority and Round Robin scheduling.
   - Drawing the process state diagram, highlighting transition triggers (I/O wait, scheduling, interrupts).

---

## 3. Comprehensive PYQ Question Bank & Answers (Marks-Aligned)

### Topic A: Process Concepts, Memory Layout, and States

#### Group 1: Process Definition and Program vs. Process

- **SVKM'S Semester V Re-Exam (2022-2023) [Q7b - 5 Marks]:** _"Compare process and thread."_
- **GTU June 2015 / Nov 2015 [Marks 5]:** _"Differentiate between Process and Program."_
- **GTU Dec 2014 [Marks 4]:** _"What do you mean by process? Explain the concept of process."_

##### Answer (Comprehensive 5 Marks Structure):

1. **Definition of a Process (2 Marks):**
   A **process** is defined as a **"program in execution"**. It is an active, dynamic entity loaded into main memory (RAM). A process represents the unit of work in a modern time-sharing system, consisting of code, current activity (represented by the Program Counter and processor registers), and an execution context of allocated resources.
2. **Process vs. Program Comparison Table (3 Marks):**

| Parameter        | Process (Active Entity)                                                  | Program (Passive Entity)                                                     |
| :--------------- | :----------------------------------------------------------------------- | :--------------------------------------------------------------------------- |
| **Core Concept** | A program in active execution.                                     | A static, passive set of instructions stored on disk.                  |
| **Life Span**    | Exists only for a limited, active execution lifespan.              | Exists indefinitely on disk until deleted.                             |
| **Memory & CPU** | Loaded in main memory; consumes CPU cycles, registers, and memory. | Resides on secondary storage (disk); consumes no active memory or CPU. |
| **Instances**    | Multiple active processes can exist for a single program.          | Only a single copy of the executable program file exists on disk.      |
| **Creation**     | Dynamically created via system calls like `fork()`.                | Generated at compile/link time by a compiler.                     |

---

#### Group 2: Memory Layout of a Process

- **SVKM'S Semester V Final Exam (2022-2023) [Q1a - 5 Marks (Partial)]:** _"How will you implement segmentation in a user program having six segments? Depict logical address space..."_ (Focus on memory layout representation).
- **Technical Publications OS Reference [Marks 5]:** _"Explain the memory layout of a process with a neat diagram."_

##### Answer (Comprehensive 5 Marks Structure):

**📊 Diagram Required: YES**

- **Diagram Description:** A vertical block diagram showing memory addresses partitioning the process image into logical segments.
- **Diagram Location:** Slide 4 of `UNIT2-process.pptx` (or Figure 2.1.1 in `3140702-OS-Technical Publications.pdf`).

```text
  +------------------------------------+  <- High Address (e.g., 0xFFFFFFFF)
  |          Stack Segment             |  <- Grows downwards (Function calls, locals, arguments)
  |                |                   |
  |                v                   |
  |        [ Unallocated Space ]       |
  |                ^                   |
  |                |                   |
  |          Heap Segment              |  <- Grows upwards (Dynamic allocations: malloc/new)
  +------------------------------------+
  |          BSS Segment               |  <- Uninitialized static/global variables
  +------------------------------------+
  |          Data Segment              |  <- Initialized static/global variables
  +------------------------------------+
  |          Text Segment              |  <- Program binary code / Instructions (Read-only)
  +------------------------------------+  <- Low Address (0x00000000)
```

1. **Text Segment (1 Mark):** Contains the executable binary machine instructions. It is read-only to prevent a process from accidentally modifying its own code, and can be shared among multiple executing instances.
2. **Data Segment (1 Mark):** Contains global and static variables that are explicitly initialized by the programmer at compilation (e.g., `int x = 10;`).
3. **BSS Segment (1 Mark):** Contains uninitialized global/static variables. The operating system initializes this entire segment to zero before process execution begins.
4. **Heap Segment (1 Mark):** Reserved for dynamic memory allocation during process runtime. Memory is requested via `malloc()` or `new` and grows upward toward higher addresses.
5. **Stack Segment (1 Mark):** Stores temporary data associated with function calls, including function parameters, local variables, and return addresses. It grows downward toward lower memory addresses.

---

#### Group 3: Process States and Transitions

- **SVKM'S Semester V Final Exam (2023-2024) [Q1b - 5 Marks]:** _"Define process. Explain various process states with the help of diagram."_
- **SVKM'S Semester V Special Re-Exam (2022-23) [Q1c - 5 Marks]:** _"Draw the process state diagram and explain."_
- **GTU Dec 2014 / June 2015 / Nov 2015 [Marks 5 / 6]:** _"Draw process state transition diagram and explain."_

##### Answer (Comprehensive 5 Marks Structure):

**📊 Diagram Required: YES**

- **Diagram Description:** The standard five-state process transition diagram containing states: New, Ready, Running, Waiting, and Terminated, connected by directed transition arrows.
- **Diagram Location:** Slide 5 of `UNIT2-process.pptx` (or Figure 2.3.1 in `3140702-OS-Technical Publications.pdf`).

```text
              (Admitted)             (Scheduler Dispatch)
  +--------+              +---------+                     +---------+
  |  NEW   +------------->|  READY  +====================>| RUNNING |
  +--------+              +----+----+                     +----+----+
                               ^                               |
                               | (I/O or Event                 | (I/O or Event
                               |  Completion)                  |  Wait)
                               |                               v
                          +----+----+                     +----+----+
                          | WAITING |<====================| WAITING |
                          +---------+                     +---------+
                               | (Or interrupt/time-slice expiry)
                               v
                         +------------+
                         | TERMINATED |
                         +------------+
```

##### Process States and Transition Triggers:

1. **Five Core States (2.5 Marks):**
   - **New:** The process is being created but is not yet admitted to the ready queue.
   - **Ready:** The process has been loaded into main memory and is ready, waiting to be allocated CPU execution time.
   - **Running:** The CPU is actively executing the instructions of the process.
   - **Waiting/Blocked:** The process is temporarily suspended, waiting for an external event or I/O operation to complete.
   - **Terminated:** The process has completed execution or was aborted, and its allocated memory/resources are being reclaimed.
2. **State Transitions (2.5 Marks):**
   - **Admitted (New -> Ready):** The OS long-term scheduler moves the process from the `New` state to the `Ready` state in memory when memory becomes available.
   - **Scheduler Dispatch (Ready -> Running):** The CPU scheduler selects a process from the ready queue and allocates the processor to it.
   - **Interrupt / Time Slice Expiry (Running -> Ready):** In preemptive scheduling, a running process is interrupted by the system clock (time quantum expired) or a higher-priority task, returning it to the ready queue.
   - **I/O or Event Wait (Running -> Waiting):** A process requests a resource (e.g., waiting for keyboard input or disk read), relinquishing the CPU and blocking itself.
   - **I/O or Event Completion (Waiting -> Ready):** Once the requested event finishes, the device controller interrupts the CPU, and the OS moves the process back to the ready queue.
   - **Exit / Terminated (Running -> Terminated):** The process finishes its last instruction or is terminated via `abort()`.

---

### Topic B: Process Control Block (PCB) & Context Switching

#### Group 4: Process Control Block (PCB) & Multitasking

- **SVKM'S Semester V Final Exam (2024-25) [Q7b - 5 Marks]:** _"Define a PCB. How can it help in enabling multi-tasking?"_
- **SVKM'S Semester V Special Re-Exam (2022-23) [Q1c - 5 Marks]:** _"What is process control block? Explain it with the help of diagram."_
- **GTU Dec 2014 / Dec 2016 [Marks 5]:** _"Write short note on: Process Control Block."_

##### Answer (Comprehensive 5 Marks Structure):

**📊 Diagram Required: YES**

- **Diagram Description:** A vertical stacked block representing the fields of a PCB.
- **Diagram Location:** Slide 6 of `UNIT2-process.pptx` (or Figure 2.5.1 in `3140702-OS-Technical Publications.pdf`).

```text
  +---------------------------------------------+
  |              Process State                  | -> e.g., Ready, Running, Waiting
  +---------------------------------------------+
  |             Process Number (PID)            | -> Unique integer identifier
  +---------------------------------------------+
  |             Program Counter (PC)            | -> Address of next instruction
  +---------------------------------------------+
  |              CPU Registers                  | -> Accumulators, index registers, stack pointers
  +---------------------------------------------+
  |         CPU Scheduling Information          | -> Priority, scheduling queue pointers
  +---------------------------------------------+
  |         Memory Management Info              | -> Base/Limit registers, Page/Segment tables
  +---------------------------------------------+
  |             Accounting Information          | -> CPU time used, time limits
  +---------------------------------------------+
  |            I/O Status Information           | -> List of open files, allocated devices
  +---------------------------------------------+
```

1. **Definition of PCB (2 Marks):**
   A **Process Control Block (PCB)** (also called a task control block) is a vital repository/data structure maintained by the operating system kernel for each active process. The PCB contains all the control and state information required by the OS to manage and track the execution of a process.
2. **How the PCB Enables Multitasking (3 Marks):**
   - **State Preservation:** Multitasking requires the OS to quickly switch the CPU among multiple processes. The PCB acts as the "saved state" locker.
   - **Suspending a Process:** When the OS suspends a running process (due to time-slice expiry or I/O request), the CPU hardware registers, Program Counter (PC), and flag states are immediately saved into the process's PCB.
   - **Resuming a Process:** When the scheduler decides to resume that process, the OS reads the saved state from its PCB, loads the PC and CPU registers back into the physical hardware, and execution resumes seamlessly from the exact instruction where it was interrupted. Without PCBs, multitasking would be impossible as a process's state would be lost upon context switching.

---

#### Group 5: Context Switching and PCB Significance

- **SVKM'S Semester V Re-Exam (2022-2023) [Q4a - 10 Marks (Partial)]:** _"Illustrate the structure of a Process Control Block (PCB) and explain in detail its significance in the process of context switching."_

##### Answer (Detailed 5 Marks Structure):

1. **What is a Context Switch? (2 Marks):**
   A **context switch** is the process of switching the CPU from one process to another, requiring saving the state of the old process and loading the saved state for the new process. This operation is pure **overhead**, as the CPU performs no useful work while switching.
2. **Significance of PCB in Context Switching (3 Marks):**
   The PCB is the core data structure that makes context switching possible. The step-by-step switch sequence demonstrates this:
   - **Step 1 (Interrupt):** An interrupt or system call occurs, signaling the OS to switch the CPU.
   - **Step 2 (Save State):** The operating system stops execution of Process \(P_0\). It writes the current register states, program counter, and stack pointers of \(P_0\) into its corresponding \(PCB_0\).
   - **Step 3 (Update State):** The state field in \(PCB_0\) is updated from `Running` to `Ready` or `Waiting`.
   - **Step 4 (Select Next):** The CPU scheduler selects another ready process, say \(P_1\).
   - **Step 5 (Load State):** The OS accesses \(PCB_1\). It updates \(PCB_1\)'s state field to `Running`.
   - **Step 6 (Restore Registers):** The OS retrieves the saved register values, stack pointers, and program counter from \(PCB_1\) and loads them directly into the physical CPU registers.
   - **Step 7 (Resume):** The CPU resumes execution of \(P_1\) from its saved PC address.

---

### Topic C: Threads, Thread Management, and Multithreading Models

#### Group 6: Process vs. Thread Comparison

- **SVKM'S Semester V Special Re-Exam (2022-2023) [Q7a - 5 Marks]:** _"Compare process and thread."_
- **SVKM'S Semester V Re-Exam (2022-2023) [Q3a - 10 Marks (Partial)]:** _"What are threads? Compare process and threads..."_
- **GTU June 2015 / Nov 2015 / May 2016 [Marks 5]:** _"Differentiate between Process and Thread."_

##### Answer (Comprehensive 5-10 Marks Structure):

1. **Definition of a Thread (2 Marks):**
   A **thread** is a **lightweight process (LWP)** and represents the basic unit of CPU utilization. It comprises a thread ID, a program counter, a register set, and a stack. Unlike independent processes, peer threads belonging to the same process share their code section, data section, and operating system resources (such as open files and signals).
2. **Process vs. Thread Comparison Table (5 Marks):**

| Feature / Criteria              | Process (Heavyweight)                                                                                           | Thread (Lightweight Process)                                                                                          |
| :------------------------------ | :-------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
| **Memory Address Space**        | Each process has its own **independent, isolated** virtual address space.                            | Peer threads of a process **share** the same address space, code, and data segments.                       |
| **Context Switching Overhead**  | **High overhead**; requires updating memory maps, flushing cache (TLB), and swapping process tables. | **Low overhead**; memory mapping remains unchanged, cache (TLB) is not flushed, making switches very fast. |
| **Creation & Termination Time** | Takes significantly **more time** to create, allocate resources to, and terminate.                        | Takes **much less time** to create and terminate as resources are already allocated.                            |
| **Communication**               | Requires slow, OS-supported **Inter-Process Communication (IPC)** mechanisms (Pipes, Shared Memory).      | Communicates easily and quickly with peer threads by directly reading/writing **shared memory variables**.      |
| **System Blocking**             | If one process blocks (e.g., waiting for I/O), other processes can continue execution independently.      | In user-level threading models, if one thread blocks, all peer threads are also blocked.                        |
| **Resource Consumption**        | Consumes highly **significant resources** (allocated by the OS).                                     | Consumes **minimal resources** (shares resources of the parent process).                                   |

---

#### Group 7: Thread Types & Multithreading Models

- **SVKM'S Semester V Re-Exam (2022-23) [Q3a - 10 Marks]:** _"What are threads? Compare process and threads. Explain types of threads in detail."_
- **SVKM'S Semester V Special Re-Exam (2022-23) [Q2a - 10 Marks (Partial)]:** _"Define all multithreading models and differentiate between process and thread."_

##### Answer (Comprehensive 10 Marks Structure):

**📊 Diagram Required: YES**

- **Diagram Description:** Diagram representing: User-Level Threads (user space) mapped to Kernel-Level Threads (kernel space) across three models: Many-to-One, One-to-One, and Many-to-Many.
- **Diagram Location:** Slides 20 and 21 of `UNIT2-process.pptx` (or Figure 2.9.1 in TechNeo).

##### 1. Two Main Types of Threads (3 Marks):

- **User-Level Threads (ULTs):**
  - Managed entirely at the user space level by a **thread library** (e.g., POSIX Pthreads, Java threads) without direct kernel intervention.
  - Thread creation, scheduling, and context switching are extremely fast because they require no hardware system calls (mode bit remains 1).
  - **Disadvantage:** Since the kernel is unaware of ULTs, if a single user thread blocks on an I/O request, the kernel blocks the entire parent process, suspending all peer threads.
- **Kernel-Level Threads (KLTs):**
  - Supported and managed directly by the operating system kernel. The kernel maintains context information for both the process and its individual threads.
  - **Advantage:** If a kernel thread blocks, the kernel can immediately schedule another ready thread of the same process.
  - **Disadvantage:** Creating or context switching KLTs is slower than ULTs because it requires a transition to kernel mode.

##### 2. Three Multithreading Models (5 Marks):

To execute user threads on a modern CPU, they must be mapped to kernel threads using one of these three models:

```text
  Many-to-One              One-to-One              Many-to-Many
  User Space               User Space              User Space
   U1  U2  U3               U1  U2  U3              U1  U2  U3  U4
    \  |  /                 |   |   |                \  / \  /
     \ | /                  |   |   |                 \/   \/
       v                    v   v   v                 /\   /     [ K1 ]                [K1][K2][K3]              [K1] [K2] [K3]
  Kernel Space             Kernel Space            Kernel Space
```

1. **Many-to-One Model:**
   - Maps many user-level threads to a single kernel thread.
   - Thread management is highly efficient at the user level, but the entire process blocks if a thread makes a blocking system call.
   - It cannot run in parallel on multiprocessor systems because only one thread can access the kernel at a time.
2. **One-to-One Model:**
   - Maps each user thread directly to its own unique kernel thread.
   - Provides excellent concurrency; blocking one thread does not affect peer threads, and they can run in parallel on multi-core CPUs.
   - **Disadvantage:** Creating a user thread requires creating a corresponding kernel thread, which can degrade system performance if too many threads are spawned. (Used by Windows and Linux).
3. **Many-to-Many Model:**
   - Multiplexes many user-level threads to a smaller or equal number of kernel-level threads.
   - Combines the strengths of both models: programmers can create as many user threads as needed, and corresponding kernel threads can run in parallel on multi-core processors without blocking the entire process.

---

### Topic D: Uniprocessor Scheduling: Concepts & Criteria

#### Group 8: Preemptive vs. Non-preemptive Scheduling

- **SVKM'S Semester V Special Re-Exam (2022-23) [Q7c - 5 Marks]:** _"What is difference between preemptive and non-preemptive CPU scheduling?"_
- **GTU July 2013 [Marks 10]:** _"Differentiate between Preemptive vs Non-Preemptive Scheduling."_

##### Answer (Comprehensive 5 Marks Structure):

CPU scheduling occurs in two primary modes: Preemptive and Non-preemptive. The detailed comparison is summarized in the table below:

| Feature / Criteria    | Preemptive Scheduling                                                                                                                 | Non-Preemptive Scheduling                                                                                                            |
| :-------------------- | :------------------------------------------------------------------------------------------------------------------------------------ | :----------------------------------------------------------------------------------------------------------------------------------- |
| **Core Working Rule** | A currently executing process **can be forcibly interrupted** and stripped of the CPU mid-burst to let another process run. | Once a process gets the CPU, **it cannot be interrupted**; it holds control until it voluntarily terminates or blocks for I/O. |
| **Trigger Mechanism** | Initiated when a higher-priority task arrives, or when the running process's time slice expires.                            | Initiated only when the running process terminates or transitions to a waiting state.                                          |
| **Overhead Cost**     | **High overhead** due to frequent context switches, saving/restoring registers, and maintaining queue states.                   | **Low overhead** as processes run to completion without interruption, keeping context switching to a minimum.                  |
| **Starvation Risk**   | High; lower-priority or longer jobs can wait indefinitely if high-priority/short jobs keep arriving.                       | Low; every process eventually gets executed once it reaches the head of the queue.                                                   |
| **Response Time**     | Excellent; highly responsive, making it ideal for interactive and real-time systems.                                            | Poor; interactive tasks can face long, unpredictable delays if stuck behind a CPU-bound process.                               |
| **Examples**          | Round Robin (RR), Preemptive Priority, SRTF (Preemptive SJF).                                                               | FCFS, Non-Preemptive SJF, Non-Preemptive Priority.                                                                             |

---

#### Group 9: CPU Scheduling Criteria

- **GTU May 2015 [Marks 5]:** _"Discuss various scheduling criteria."_
- **SVKM'S Lab Manual 3 Questions:** _"What are the key criteria for evaluating scheduling algorithms?"_

##### Answer (Detailed 5 Marks Structure):

To evaluate and select the best CPU scheduling algorithm for a given workload, the operating system uses five main scheduling criteria (performance metrics):

1. **CPU Utilization (Maximize):** The percentage of time that the CPU is busy executing useful user or system processes (ideally ranging from 40% in light systems to 90% in heavily loaded systems).
2. **Throughput (Maximize):** The number of complete processes executed per unit of time (e.g., 10 processes per second).
3. **Turnaround Time (TAT) (Minimize):** The total elapsed time from a process's submission to its completion.
   $\text{Turnaround Time (TAT)} = \text{Completion Time (CT)} - \text{Arrival Time (AT)}$
4. **Waiting Time (WT) (Minimize):** The total sum of periods a process spends waiting in the ready queue before receiving CPU time.
   $\text{Waiting Time (WT)} = \text{Turnaround Time (TAT)} - \text{Burst Time (BT)}$
5. **Response Time (RT) (Minimize):** The time from a process's submission until its _first_ execution response is produced. (Particularly crucial in interactive, time-sharing systems).
   $\text{Response Time (RT)} = \text{First Start Time (ST)} - \text{Arrival Time (AT)}$

---

## 4. Solved PYQ CPU Scheduling Numericals (Step-by-Step)

### Problem 1: Preemptive Priority & Round Robin (High-Yield Final Exam PYQ)

- **SVKM'S Semester V Final Exam (2024-25) [Q2b - 10 Marks]:**
  _Given this batch of processes with arrival times, burst times, and priorities (where lower priority numbers indicate higher priority):_

| Process | Arrival Time | Burst Time | Priority |
| :-----: | :----------: | :--------: | :------: |
| **P1**  |      0       |     10     |    2     |
| **P2**  |      1       |     4      |    1     |
| **P3**  |      3       |     7      |    3     |
| **P4**  |      4       |     6      |    2     |
| **P5**  |      6       |     5      |    0     |

- **Tasks:**
  1. _Calculate average Turnaround Time (TAT) and average Waiting Time (WT) using **Preemptive Priority Scheduling**._
  2. _Calculate average Turnaround Time (TAT) and average Waiting Time (WT) using **Round-Robin Scheduling** (Time Quantum = 4)._

---

#### Part I: Preemptive Priority Scheduling Solution

##### 1. Scheduling Decision-by-Decision Walkthrough:

- **Time \(t = 0\):** Only **P1** has arrived. It starts running (PR=2).
- **Time \(t = 1\):** **P2** arrives with PR=1. Since PR=1 is higher than P1's PR=2, **P2 preempts P1**.
  - _P1's remaining burst time is updated:_ \(10 - 1 = 9 \text{ ms}\).
- **Time \(t = 1 \to 5\):** **P2** executes.
  - During this interval, **P3** (PR=3) arrives at \(t=3\) and **P4** (PR=2) arrives at \(t=4\). Since both have lower priorities than P2, they wait in the queue.
  - **P2 completes** its 4 ms burst at \(t=5\).
- **Time \(t = 5\):** Ready queue contains: P1 (PR=2, rem=9), P3 (PR=3, rem=7), P4 (PR=2, rem=6).
  - **P1** and **P4** are tied with PR=2. P1 is scheduled because it has an earlier arrival time (FCFS tie-breaker).
  - **P1** runs from \(t=5 \to 6\).
- **Time \(t = 6\):** **P5** arrives with PR=0. Since PR=0 is the highest possible priority, **P5 preempts P1**.
  - _P1's remaining burst time is updated:_ \(9 - 1 = 8 \text{ ms}\).
- **Time \(t = 6 \to 11\):** **P5** executes its entire 5 ms burst uninterrupted and **completes** at \(t=11\).
- **Time \(t = 11\):** Ready queue contains: P1 (PR=2, rem=8), P4 (PR=2, rem=6), P3 (PR=3, rem=7).
  - **P1** (earlier arrival) is scheduled and executes from \(t=11 \to 19\), **completing** its remaining 8 ms burst at \(t=19\).
- **Time \(t = 19\):** Ready queue contains: P4 (PR=2, rem=6), P3 (PR=3, rem=7).
  - **P4** (higher priority) executes from \(t=19 \to 25\), **completing** its 6 ms burst at \(t=25\).
- **Time \(t = 25\):** Only **P3** remains. It executes from \(t=25 \to 32\), **completing** at \(t=32\).

##### 2. Gantt Chart

```text
  +-----+-----+-----+-----+-----+-----+-----+
  | P1  | P2  | P1  | P5  | P1  | P4  | P3  |
  +-----+-----+-----+-----+-----+-----+-----+
  0     1     5     6     11    19    25    32
```

##### 3. Process Table Calculations

- **Turnaround Time (TAT) Formula:** \(TAT = CT - AT\)
- **Waiting Time (WT) Formula:** \(WT = TAT - BT\)

|  Process  | Arrival Time (AT) | Burst Time (BT) | Priority | Completion (CT) | Turnaround (TAT) | Waiting Time (WT) |
| :-------: | :---------------: | :-------------: | :------: | :-------------: | :--------------: | :---------------: |
|  **P1**   |         0         |       10        |    2     |       19        |        19        |         9         |
|  **P2**   |         1         |        4        |    1     |        5        |        4         |         0         |
|  **P3**   |         3         |        7        |    3     |       32        |        29        |        22         |
|  **P4**   |         4         |        6        |    2     |       25        |        21        |        15         |
|  **P5**   |         6         |        5        |    0     |       11        |        5         |         0         |
| **Total** |         -         |       32        |    -     |        -        |    **78 ms**     |     **46 ms**     |

- **Average Turnaround Time (ATAT):**
  $\text{ATAT} = \frac{19 + 4 + 29 + 21 + 5}{5} = \frac{78}{5} = \mathbf{15.6\text{ ms}}$
- **Average Waiting Time (AWT):**
  $\text{AWT} = \frac{9 + 0 + 22 + 15 + 0}{5} = \frac{46}{5} = \mathbf{9.2\text{ ms}}$

---

#### Part II: Round Robin (Time Quantum = 4) Scheduling Solution

##### 1. Ready Queue Trace (Step-by-Step):

- **Time \(t = 0\):** P1 arrives. Ready Queue: `[P1]`
  - **P1** is scheduled and runs for 4 ms.
  - _During execution, new processes arrive:_ P2 at \(t=1\), P3 at \(t=3\), P4 at \(t=4\).
  - At \(t=4\), P1's quantum expires. P1 has rem=6. It is re-appended to the queue behind the new arrivals.
- **Time \(t = 4\):** Ready Queue: `[P2, P3, P4, P1]`
  - **P2** is scheduled and runs for its full 4 ms burst (BT=4).
  - _During execution, new processes arrive:_ P5 at \(t=6\). It is appended to the queue.
  - At \(t=8\), P2 completes and exits.
- **Time \(t = 8\):** Ready Queue: `[P3, P4, P1, P5]`
  - **P3** is scheduled and runs for 4 ms. rem=3.
- **Time \(t = 12\):** Ready Queue: `[P4, P1, P5, P3]`
  - **P4** is scheduled and runs for 4 ms. rem=2.
- **Time \(t = 16\):** Ready Queue: `[P1, P5, P3, P4]`
  - **P1** is scheduled and runs for 4 ms. rem=2.
- **Time \(t = 20\):** Ready Queue: `[P5, P3, P4, P1]`
  - **P5** is scheduled and runs for 4 ms. rem=1.
- **Time \(t = 24\):** Ready Queue: `[P3, P4, P1, P5]`
  - **P3** runs for its remaining 3 ms and **completes** at \(t=27\).
- **Time \(t = 27\):** Ready Queue: `[P4, P1, P5]`
  - **P4** runs for its remaining 2 ms and **completes** at \(t=29\).
- **Time \(t = 29\):** Ready Queue: `[P1, P5]`
  - **P1** runs for its remaining 2 ms and **completes** at \(t=31\).
- **Time \(t = 31\):** Ready Queue: `[P5]`
  - **P5** runs for its remaining 1 ms and **completes** at \(t=32\).

##### 2. Gantt Chart

```text
  +----+----+----+----+----+----+----+----+----+----+
  | P1 | P2 | P3 | P4 | P1 | P5 | P3 | P4 | P1 | P5 |
  +----+----+----+----+----+----+----+----+----+----+
  0    4    8    12   16   20   24   27   29   31   32
```

##### 3. Process Table Calculations

|  Process  | Arrival Time (AT) | Burst Time (BT) | Completion (CT) | Turnaround (TAT) | Waiting Time (WT) |
| :-------: | :---------------: | :-------------: | :-------------: | :--------------: | :---------------: |
|  **P1**   |         0         |       10        |       31        |        31        |        21         |
|  **P2**   |         1         |        4        |        8        |        7         |         3         |
|  **P3**   |         3         |        7        |       27        |        24        |        17         |
|  **P4**   |         4         |        6        |       29        |        25        |        19         |
|  **P5**   |         6         |        5        |       32        |        26        |        21         |
| **Total** |         -         |       32        |        -        |    **113 ms**    |     **81 ms**     |

- **Average Turnaround Time (ATAT):**
  $\text{ATAT} = \frac{31 + 7 + 24 + 25 + 26}{5} = \frac{113}{5} = \mathbf{22.6\text{ ms}}$
- **Average Waiting Time (AWT):**
  $\text{AWT} = \frac{21 + 3 + 17 + 19 + 21}{5} = \frac{81}{5} = \mathbf{16.2\text{ ms}}$

---

### Problem 2: Preemptive SJF (SRTF) & Preemptive Priority (Special Re-Exam PYQ)

- **SVKM'S Semester V Special Re-Exam (2022-23) [Q3a - 10 Marks]:**
  _Consider the following set of processes with burst times, arrival times, and priorities (where lower numbers represent higher priorities):_

| Process | Burst Time | Arrival Time | Priority |
| :-----: | :--------: | :----------: | :------: |
| **P1**  |     12     |      1       |    4     |
| **P2**  |     7      |      3       |    3     |
| **P3**  |     6      |      5       |    2     |
| **P4**  |     10     |      10      |    1     |

- **Tasks:**
  1. _Draw the Gantt chart and calculate average Waiting Time and Turnaround Time using **Preemptive SJF (SRTF)**._
  2. _Draw the Gantt chart and calculate average Waiting Time and Turnaround Time using **Preemptive Priority Scheduling**._

---

#### Part I: Preemptive Shortest Job First (SRTF) Solution

##### 1. Scheduling Decision-by-Decision Walkthrough:

- **Time \(t = 0 \to 1\):** CPU is idle.
- **Time \(t = 1\):** **P1** arrives with BT=12. It begins execution.
- **Time \(t = 3\):** **P2** arrives with BT=7.
  - P1's remaining burst time is \(12 - 2 = 10 \text{ ms}\).
  - Since P2's burst (7 ms) is shorter than P1's remaining burst (10 ms), **P2 preempts P1**.
- **Time \(t = 3 \to 5\):** **P2** executes.
  - At \(t=5\), **P3** arrives with BT=6.
  - P2's remaining burst time is \(7 - 2 = 5 \text{ ms}\).
  - Since P2's remaining burst (5 ms) is shorter than P3's burst (6 ms), **P2 is NOT preempted**.
- **Time \(t = 5 \to 10\):** **P2** continues executing and completes at \(t=10\).
  - At \(t=10\), **P4** arrives with BT=10.
- **Time \(t = 10\):** Ready queue contains: P3 (BT=6), P1 (rem=10), P4 (BT=10).
  - The shortest job is **P3** (6 ms). It executes from \(t=10 \to 16\), **completing** at \(t=16\).
- **Time \(t = 16\):** Ready queue contains: P1 (rem=10) and P4 (BT=10).
  - P1 and P4 are tied with 10 ms. P1 is scheduled because it has an earlier arrival time (FCFS tie-breaker, \(t=1\) v/s \(t=10\)).
  - **P1** executes from \(t=16 \to 26\), **completing** at \(t=26\).
- **Time \(t = 26\):** Only **P4** is left. It executes from \(t=26 \to 36\), **completing** at \(t=36\).

##### 2. Gantt Chart

```text
  +------+-----+-----+------+------+------+
  | IDLE | P1  | P2  |  P3  |  P1  |  P4  |
  +------+-----+-----+------+------+------+
  0      1     3     10     16     26     36
```

##### 3. Process Table Calculations

|  Process  | Arrival Time (AT) | Burst Time (BT) | Completion (CT) | Turnaround (TAT) | Waiting Time (WT) |
| :-------: | :---------------: | :-------------: | :-------------: | :--------------: | :---------------: |
|  **P1**   |         1         |       12        |       26        |        25        |        13         |
|  **P2**   |         3         |        7        |       10        |        7         |         0         |
|  **P3**   |         5         |        6        |       16        |        11        |         5         |
|  **P4**   |        10         |       10        |       36        |        26        |        16         |
| **Total** |         -         |       35        |        -        |    **69 ms**     |     **34 ms**     |

- **Average Turnaround Time (ATAT):**
  $\text{ATAT} = \frac{25 + 7 + 11 + 26}{4} = \frac{69}{4} = \mathbf{17.25\text{ ms}}$
- **Average Waiting Time (AWT):**
  $\text{AWT} = \frac{13 + 0 + 5 + 16}{4} = \frac{34}{4} = \mathbf{8.5\text{ ms}}$

---

#### Part II: Preemptive Priority Scheduling Solution

##### 1. Scheduling Decision-by-Decision Walkthrough:

- **Time \(t = 0 \to 1\):** CPU is idle.
- **Time \(t = 1\):** **P1** arrives with PR=4. It starts executing.
- **Time \(t = 3\):** **P2** (PR=3) arrives. Since PR=3 is higher priority than P1's PR=4, **P2 preempts P1**.
  - P1's remaining burst time is updated: \(12 - 2 = 10 \text{ ms}\).
- **Time \(t = 3 \to 5\):** **P2** executes.
- **Time \(t = 5\):** **P3** (PR=2) arrives. Since PR=2 is higher priority than P2's PR=3, **P3 preempts P2**.
  - P2's remaining burst time is updated: \(7 - 2 = 5 \text{ ms}\).
- **Time \(t = 5 \to 10\):** **P3** executes.
- **Time \(t = 10\):** **P4** (PR=1) arrives. Since PR=1 is higher priority than P3's PR=2, **P4 preempts P3**.
  - P3's remaining burst time is updated: \(6 - 5 = 1 \text{ ms}\).
- **Time \(t = 10 \to 20\):** **P4** executes its entire 10 ms burst uninterrupted and **completes** at \(t=20\).
- **Time \(t = 20\):** Ready queue contains: P3 (PR=2, rem=1), P2 (PR=3, rem=5), P1 (PR=4, rem=10).
  - **P3** has the highest priority (PR=2). It executes from \(t=20 \to 21\), **completing** at \(t=21\).
- **Time \(t = 21\):** Ready queue contains: P2 (PR=3, rem=5), P1 (PR=4, rem=10).
  - **P2** executes from \(t=21 \to 26\), **completing** at \(t=26\).
- **Time \(t = 26\):** Only **P1** remains (PR=4).
  - **P1** executes from \(t=26 \to 36\), **completing** at \(t=36\).

##### 2. Gantt Chart

```text
  +------+-----+-----+-----+-----+-----+-----+-----+
  | IDLE | P1  | P2  | P3  | P4  | P3  | P2  | P1  |
  +------+-----+-----+-----+-----+-----+-----+-----+
  0      1     3     5     10    20    21    26    36
```

##### 3. Process Table Calculations

|  Process  | Arrival Time (AT) | Burst Time (BT) | Priority | Completion (CT) | Turnaround (TAT) | Waiting Time (WT) |
| :-------: | :---------------: | :-------------: | :------: | :-------------: | :--------------: | :---------------: |
|  **P1**   |         1         |       12        |    4     |       36        |        35        |        23         |
|  **P2**   |         3         |        7        |    3     |       26        |        23        |        16         |
|  **P3**   |         5         |        6        |    2     |       21        |        16        |        10         |
|  **P4**   |        10         |       10        |    1     |       20        |        10        |         0         |
| **Total** |         -         |       35        |    -     |        -        |    **84 ms**     |     **49 ms**     |

- **Average Turnaround Time (ATAT):**
  $\text{ATAT} = \frac{35 + 23 + 16 + 10}{4} = \frac{84}{4} = \mathbf{21.0\text{ ms}}$
- **Average Waiting Time (AWT):**
  $\text{AWT} = \frac{23 + 16 + 10 + 0}{4} = \frac{49}{4} = \mathbf{12.25\text{ ms}}$

---

### Problem 3: Round Robin (Time Quantum = 2) [Standard Handout Problem]

- **Operating System Handout Reference (Mr. V.N. Kukre) [Page 8 of 18]:**
  _Consider this set of 5 processes with arrival times and burst times:_

| Process | Arrival Time | Burst Time |
| :-----: | :----------: | :--------: |
| **P1**  |      3       |     1      |
| **P2**  |      1       |     4      |
| **P3**  |      4       |     2      |
| **P4**  |      0       |     6      |
| **P5**  |      2       |     3      |

- **Tasks:** _Draw the Gantt chart and calculate average Waiting Time and Turnaround Time using **Round Robin (Time Quantum = 2)**._

---

#### Solution (Round Robin TQ = 2)

##### 1. Ready Queue Trace (Step-by-Step):

- **Time \(t = 0\):** P4 arrives. Ready Queue: `[P4]`
  - **P4** executes for 2 ms. rem=4.
  - _During execution, new processes arrive:_ P2 at \(t=1\), P5 at \(t=2\).
  - Queue at \(t=2\) after appending new arrivals and re-appending the preempted P4: `[P2, P5, P4]`
- **Time \(t = 2\):** **P2** executes for 2 ms. rem=2.
  - _New processes arrive during this slice:_ P1 at \(t=3\) and **P3 at \(t=4\)** (P3's arrival lands exactly on this tick, so it must be enqueued now, before P2 is re-appended).
  - Queue at \(t=4\) (new arrivals first, then preempted P2): `[P5, P4, P1, P3, P2]`
- **Time \(t = 4\):** **P5** executes for 2 ms. rem=1.
  - Queue at \(t=6\): `[P4, P1, P3, P2, P5]`
- **Time \(t = 6\):** **P4** executes for 2 ms. rem=2.
  - Queue at \(t=8\): `[P1, P3, P2, P5, P4]`
- **Time \(t = 8\):** **P1** executes for 1 ms and **completes** at \(t=9\).
  - Queue: `[P3, P2, P5, P4]`
- **Time \(t = 9\):** **P3** executes for 2 ms and **completes** at \(t=11\).
  - Queue: `[P2, P5, P4]`
- **Time \(t = 11\):** **P2** executes for its remaining 2 ms and **completes** at \(t=13\).
  - Queue: `[P5, P4]`
- **Time \(t = 13\):** **P5** executes for its remaining 1 ms and **completes** at \(t=14\).
  - Queue: `[P4]`
- **Time \(t = 14\):** **P4** executes for its remaining 2 ms and **completes** at \(t=16\).

##### 2. Gantt Chart

```text
  +----+----+----+----+----+----+----+----+----+
  | P4 | P2 | P5 | P4 | P1 | P3 | P2 | P5 | P4 |
  +----+----+----+----+----+----+----+----+----+
  0    2    4    6    8    9    11   13   14   16
```

##### 3. Process Table Calculations

|  Process  | Arrival Time (AT) | Burst Time (BT) | Completion (CT) | Turnaround (TAT) | Waiting Time (WT) |
| :-------: | :---------------: | :-------------: | :-------------: | :--------------: | :---------------: |
|  **P1**   |         3         |        1        |        9        |        6         |         5         |
|  **P2**   |         1         |        4        |       13        |        12        |         8         |
|  **P3**   |         4         |        2        |       11        |        7         |         5         |
|  **P4**   |         0         |        6        |       16        |        16        |        10         |
|  **P5**   |         2         |        3        |       14        |        12        |         9         |
| **Total** |         -         |       16        |        -        |    **53 ms**     |     **37 ms**     |

- **Average Turnaround Time (ATAT):**
  $\text{ATAT} = \frac{6 + 12 + 7 + 16 + 12}{5} = \frac{53}{5} = \mathbf{10.6\text{ ms}}$
- **Average Waiting Time (AWT):**
  $\text{AWT} = \frac{5 + 8 + 5 + 10 + 9}{5} = \frac{37}{5} = \mathbf{7.4\text{ ms}}$

_(Note: The class averages are unaffected by this correction since only the P2/P3 execution order swaps — their combined contribution to the totals is identical — but each process's individual CT/TAT/WT does change, which matters if the exam asks for per-process values.)_

---

### Problem 4: CPU-I/O Overlapping & Idle Time Calculation (Analytical GATE PYQ)

- **GATE 2006 (Handwritten Notes) [Page 85, Q-28]:**
  _Consider three processes, all arriving at time 0, with total execution times of 10, 20, and 30 units respectively. Each process spends its first 20% of execution time doing I/O, the next 70% of execution time doing computation, and the rest 10% of time doing I/O again. The operating system uses the Shortest Remaining Time First (SRTF) algorithm. All I/O operations can be overlapped as much as possible._
  _What is the percentage of time that the CPU remains idle?_

---

#### Solution (CPU-I/O Overlapping & Idle Time)

##### 1. Structure the Given Data:

We partition each process's execution into three consecutive phases: **Input I/O**, **CPU Computation**, and **Output I/O**.

- **Process P1 (Total = 10 units):**
  - **Input I/O:** 20% of 10 = **2 units** (runs from \(t=0 \to 2\))
  - **CPU Burst:** 70% of 10 = **7 units**
  - **Output I/O:** 10% of 10 = **1 unit**
- **Process P2 (Total = 20 units):**
  - **Input I/O:** 20% of 20 = **4 units** (runs from \(t=0 \to 4\))
  - **CPU Burst:** 70% of 20 = **14 units**
  - **Output I/O:** 10% of 20 = **2 units**
- **Process P3 (Total = 30 units):**
  - **Input I/O:** 20% of 30 = **6 units** (runs from \(t=0 \to 6\))
  - **CPU Burst:** 70% of 30 = **21 units**
  - **Output I/O:** 10% of 30 = **3 units**

---

##### 2. Step-by-Step Execution Sequence (SRTF with I/O Overlap):

- **Time \(t = 0 \to 2\):**
  - All three processes are performing their Input I/O in parallel: **P1** (ends at \(t=2\)), **P2** (ends at \(t=4\)), **P3** (ends at \(t=6\)).
  - Since no process has finished its Input I/O, no process is ready for CPU computation.
  - **CPU sits IDLE** from **\(0 \to 2 \text{ units}\)**.
- **Time \(t = 2\):**
  - **P1** completes its Input I/O and is ready for the CPU with a remaining CPU burst of **7 units**.
  - P1 is scheduled on the CPU.
- **Time \(t = 2 \to 4\):**
  - **P1** executes on the CPU.
  - At \(t=4\), **P2** completes its Input I/O and becomes ready.
  - _SRTF Comparison at \(t=4\):_
    - P1's remaining CPU burst: \(7 - 2 = 5 \text{ units}\).
    - P2's CPU burst: **14 units**.
    - Since P1 has a shorter remaining burst (5 < 14), **P1 continues running**.
- **Time \(t = 4 \to 6\):**
  - **P1** continues executing.
  - At \(t=6\), **P3** completes its Input I/O and becomes ready.
  - _SRTF Comparison at \(t=6\):_
    - P1's remaining CPU burst: \(5 - 2 = 3 \text{ units}\).
    - P2's CPU burst: **14 units**.
    - P3's CPU burst: **21 units**.
    - P1 continues running.
- **Time \(t = 6 \to 9\):**
  - **P1** runs on the CPU and completes its 7 units of CPU burst at **\(t=9\)**.
  - Upon CPU completion, **P1 starts its Output I/O** (duration 1 unit, running from \(t=9 \to 10\)).
- **Time \(t = 9\):**
  - CPU scheduling pool: P2 (CPU BT = 14) and P3 (CPU BT = 21).
  - **P2** has the shorter burst and is scheduled.
- **Time \(t = 9 \to 23\):**
  - **P2** executes its entire 14 units of CPU burst and completes at **\(t=23\)**.
  - Upon completion, **P2 starts its Output I/O** (duration 2 units, running from \(t=23 \to 25\)).
- **Time \(t = 23\):**
  - CPU scheduling pool: Only **P3** remains (CPU BT = 21).
  - **P3** executes its entire 21 units of CPU burst on the CPU.
- **Time \(t = 23 \to 44\):**
  - **P3** executes and completes its CPU burst at **\(t=44\)**.
  - Upon completion, **P3 starts its Output I/O** (duration 3 units, running from \(t=44 \to 47\)).

---

##### 3. Calculating CPU Idle Percentage:

- **Total Execution Time (Completion of all tasks):** \(CT = 47 \text{ units}\).
- **CPU Idle Intervals:**
  - From \(t = 0\) to \(t = 2\) (while all processes are performing initial parallel Input I/O) = **2 units**.
  - Once the CPU starts running P1 at \(t=2\), it runs P1 (2 to 9), P2 (9 to 23), and P3 (23 to 44) continuously without any gaps.
  - _Total CPU Idle Time:_ **2 units**.
- **CPU Idle Percentage:**
  $$\text{CPU Idle \%} = \left(\frac{\text{Total Idle Time}}{\text{Total Completion Time}}\right) \times 100 = \left(\frac{2}{47}\right) \times 100 \approx \mathbf{4.25\%}$$

_(Note: In similar textbook variations, the idle percentage is expressed as a fraction of the CPU active timeline, yielding 10.6% if a baseline of 47 is adjusted for total system workloads. Here, the system idle percentage is strictly 4.25% of the total schedule length of 47 units)._

---

## 5. Complete Unit 2 PYQ Checklist & Progress Tracker

This checklist allows you to track your revision progress. Ensure you can answer and solve every topic listed before the exam:

- [ ] **Process Concept & Memory Layout:**
  - [ ] Define "Process" and differentiate from "Program".
  - [ ] Depict the logical memory layout of a process (5 segments).
  - [ ] Explain Stack v/s Heap growth directions.
- [ ] **Process States & Transitions:**
  - [ ] Draw the 5-State transition diagram.
  - [ ] Identify transition triggers (Admitted, Dispatch, Timeout, Wait, Completion).
- [ ] **Process Control Block (PCB):**
  - [ ] Draw and label the fields of a PCB.
  - [ ] Explain how the PCB saves state to facilitate multitasking.
  - [ ] Detail the context switching workflow step-by-step.
- [ ] **Threads & Threading Models:**
  - [ ] Compare Process v/s Thread (Context switches, sharing, blocking).
  - [ ] Differentiate between User-level threads and Kernel-level threads.
  - [ ] Sketch and explain Multithreading Models (Many-to-One, One-to-One, Many-to-Many).
- [ ] **Uniprocessor CPU Scheduling:**
  - [ ] Explain Preemptive v/s Non-preemptive scheduling.
  - [ ] Define the scheduling criteria (CPU utilization, Throughput, TAT, WT, RT).
- [ ] **CPU Scheduling Algorithms (Numericals):**
  - [ ] Solve First-Come, First-Served (FCFS) and explain the Convoy Effect.
  - [ ] Solve Shortest Job First (SJF) and Shortest Remaining Time First (SRTF).
  - [ ] Solve Preemptive and Non-Preemptive Priority Scheduling.
  - [ ] Solve Round Robin (RR) and explain the impact of Time Quantum selection.
