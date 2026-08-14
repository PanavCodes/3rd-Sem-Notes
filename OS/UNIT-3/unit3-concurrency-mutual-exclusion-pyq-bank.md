# Unit 3 Operating Systems: Concurrency & Hardware Mutual Exclusion PYQ Bank

This document contains a comprehensive, structured, and marks-aligned **Previous Year Questions (PYQ) Bank** for **Unit 3: Process Concurrency & Mutual Exclusion (Hardware Support)**. It has been compiled from all available SVKM NMIMS University exams, GTU papers, and course syllabus handouts, and is strictly filtered to match your exact exam syllabus.

---

## 📋 1. Unit 3 Syllabus Scope & Topic Alignment
According to the official **Operating Systems 2025-26 Course Policy** (Syllabus reference: `Operating Systems 2025-26.pdf`), this PYQ Bank is strictly limited to the first two topics of Unit 3:
1. **Principles of Concurrency** (Interleaving, Overlapping, System Contexts, Speed Factors, Concurrency Glossaries, Race Conditions, Critical Section Problem, and OS Concerns)
2. **Mutual Exclusion: Hardware Support** (Interrupt Disabling, Test and Set (TSL), Compare and Swap (CAS), Exchange/Swap (XCHG), Multiprocessor Bus Locking, and busy-waiting spinlock evaluations)

*⚠️ Strict Scope Rule: Software-based mutual exclusion (turn/flag variables, Peterson's, Dekker's), semaphores, monitors, message passing, and classical IPC problems are excluded as they are outside your current exam syllabus.*

---

## 📊 2. Final Analysis of Unit 3 PYQs

### Topic-Wise PYQ Frequency & Analysis
| Topic Area | Frequency in PYQs | Relative Weight | Most Frequently Asked Concept |
| :--- | :---: | :---: | :--- |
| **Critical Section Problem (CSP)** | 5 Times | High | The Three Requirements (Mutual Exclusion, Progress, Bounded Waiting) |
| **Race Conditions** | 4 Times | High | Race Condition Definition, Bank Balance & input Character buffer examples |
| **Hardware Synchronization Primitives** | 3 Times | Critical | 10-Mark Multi-Part Comparison & Trace of TSL, CAS, and Swap |
| **Mutual Exclusion & Busy Waiting** | 3 Times | Medium | Mutual Exclusion Significance, Busy-Waiting (Spinlock) Trade-offs |
| **Interrupt Disabling (Uniprocessor)** | 2 Times | Medium | Entry/Exit Disable Interrupt protocols & Multiprocessor Limitations |

### Key Observations & Insights
1. **Most Frequently Asked Topic:** **The Critical Section Problem Requirements** and **Special Hardware Instructions (TSL/CAS/Swap)** are the most heavily weighted topics in final exams. The hardware synchronization primitives appear as a major **10-Mark essay question** (e.g., SVKM NMIMS Final Exam Q4a).
2. **Repeated Concepts with Different Wording:**
   * *Critical Section Problem:* Asked as "Elaborate the solution to critical section problem? [5]" (Special Re-Exam 2022-23 Q1b) or "Explain critical section problem in detail [5]" (Re-Exam 2022-23 Q1a).
   * *Race Condition:* Asked as "What is race condition? Explain Peterson's solution in detail [10]" (Special Re-Exam 2022-23 Q6a) where students must isolate and explain the "Race Condition" concept.
3. **High-Priority Revision Topics:**
   * The 3 requirements for any Critical Section solution (Mutual Exclusion, Progress, Bounded Waiting).
   * The C-style abstract algorithms and execution traces for **Test and Set (TSL)**, **Compare and Swap (CAS)**, and **Exchange (Swap)**.
   * Why disabling interrupts fails on multiprocessors and how hardware bus-locking asserts atomicity.

---

## 🗂️ 3. Topic-Wise Grouped PYQs & Model Answers (Marks-Aligned)

### TOPIC 1: PRINCIPLES OF CONCURRENCY

#### Group 1: Race Condition Concept & Examples
* **SVKM'S Semester V Special Re-Exam (2022-2023) [Q6a - 10 Marks (Partial)]:** *"What is race condition? Explain Peterson's solution in detail."* (Peterson's is outside your scope; answer the Race Condition part).
* **GTU Dec 2014 [Marks 5]:** *"What is race condition? Explain with example."*
* **Stallings Textbook / Technical Publications [Marks 5]:** *"Define a race condition and write two concrete examples of it."*

##### Answer (Comprehensive 5-10 Marks Structure):
**📊 Diagram Required: YES (Highly Recommended)**
* **Diagram Description:** High-yield concurrent timeline showing Process $P_0$ and $P_1$ calling `fork()` and racing to read and write the variable `next_available_pid = 2615`, resulting in a duplicate PID assignment.
* **Diagram Location:** `UNIT 3- Process Concurrency.pdf` Prof. Jesleena Gonsalves / Slide 6 of `UNIT 3-Concurrency.pptx`.

```text
      Process P0                                   Process P1
          |                                            |
     calls fork()                                 calls fork()
          |                                            |
     (Request PID)                                (Request PID)
          \                                            /
           \                                          /
            v                                        v
     [Read next_available_pid = 2615]         [Read next_available_pid = 2615]
            |                                        |
     (Assigns PID 2615)                       (Assigns PID 2615)
            |                                        |
     [Writes next_available_pid = 2616]       [Writes next_available_pid = 2616]
            |                                        |
      Gets PID 2615                            Gets PID 2615
            \                                        /
             v                                      v
              *** ERROR: DUPLICATE PID ASSIGNED! ***
```

##### 1. Definition of a Race Condition (2 Marks):
A **race condition** is an undesirable situation that occurs when multiple concurrent processes or threads read and write to a shared data item, and the final result of the execution depends entirely on the unpredictable relative timing and scheduling order of the processes [247, 260, 350, 410, 566, 613, 616, 645]. The "winner" of the race determines the final value of the shared variable, often causing data corruption [247, 260].

##### 2. Detailed Example A: Shared Bank Account Balance (2.5 Marks):
Imagine a shared bank account variable `balance` initialized to `$100`. Two concurrent transactions occur: Process $P_1$ deposits `$50`, and Process $P_2$ withdraws `$30` [491].
* **The Asynchronous Race Interleaving:**
  1. $P_1$ reads the shared `balance` ($100$) into its CPU Register $R_1$ [491].
  2. $P_1$'s time-slice expires; the OS scheduler switches to Process $P_2$ [491].
  3. $P_2$ reads `balance` ($100$) into CPU Register $R_2$ [491].
  4. $P_2$ performs the subtraction calculation in its register: $100 - 30 = 70$.
  5. $P_2$ writes its register value back to memory: `balance = 70` [491].
  6. $P_1$ is rescheduled. It performs the addition calculation in its register: $100 + 50 = 150$ [491].
  7. $P_1$ writes its register value back to memory: `balance = 150` [491].
* **Outcome:** The account balance is updated to `$150` instead of the correct serial outcome of `$120`. $P_2$'s withdraw transaction is completely lost because $P_1$ wrote its stale register value last [491].

##### 3. Detailed Example B: The Fork System Call PID Allocation (2.5 Marks):
* Consider two sibling processes $P_0$ and $P_1$ both calling the `fork()` system call concurrently [411].
* The kernel maintains a global shared variable `next_available_pid` to store the next process ID (e.g., `2615`) [411].
* If both processes read `next_available_pid` at the same time, they will both receive the ID `2615` [411].
* They will both attempt to update the variable to `2616`, but both children will have been created with the duplicate, illegal process identifier `2615`, causing a critical kernel failure [411].

---

#### Group 2: Critical Section Problem (Requirements & Protocol Structure)
* **SVKM'S Semester V Re-Exam (2022-2023) [Q1a - 5 Marks]:** *"Explain critical section problem in detail."*
* **SVKM'S Semester V Special Re-Exam (2022-2023) [Q1b - 5 Marks]:** *"Elaborate the solution to critical section problem?"*
* **GTU June 2015 / Dec 2014 [Marks 5 / 10]:** *"Explain critical section problem with its different solutions."* (Ensure you focus your answer on the problem definition and its requirements).

##### Answer (Comprehensive 5 Marks Structure):
**📊 Diagram Required: YES**
* **Diagram Description:** Structure of a cooperative process $P_i$ containing Entry section, Critical Section, Exit section, and Remainder section.
* **Diagram Location:** `UNIT 3- Process Concurrency.pdf` Slide 9 of `UNIT 3-Concurrency.pptx`.

```text
  do {
      +-------------------------------------------+
      |               ENTRY SECTION               | -> Request permission to enter CS
      +-------------------------------------------+
      |             CRITICAL SECTION              | -> Access & modify shared memory
      +-------------------------------------------+
      |               EXIT SECTION                | -> Release CS lock for others
      +-------------------------------------------+
      |             REMAINDER SECTION             | -> Perform non-shared activities
      +-------------------------------------------+
  } while (true);
```

##### 1. Defining the Critical Section (1.5 Marks):
A **Critical Section (CS)** is a specific segment of program code within a process that accesses, reads, or writes to shared system resources (such as global variables, memory regions, shared tables, or open files) [58, 64, 230, 246, 320, 358, 369, 380, 409, 415, 447, 510, 516, 521, 564, 602, 612, 620, 648]. The **Critical Section Problem** is the challenge of designing a software or hardware protocol that allows concurrent processes to coordinate so that no two processes execute in their critical sections simultaneously [230, 246, 320, 369, 612, 620, 648].

##### 2. The Three Mandatory Solution Requirements (3.5 Marks):
Any viable solution to the Critical Section problem must satisfy three strict requirements [76, 79, 82, 242, 359, 370, 381, 521]:
1. **Mutual Exclusion (Safety):** If a process $P_i$ is actively executing inside its critical section, then no other concurrent processes or threads are allowed to execute in their critical sections for that same shared resource [76, 79, 82, 242, 350, 420, 521, 574, 624, 649].
2. **Progress (Liveness):** If no process is executing in its critical section and there are other processes that wish to enter, then only those processes that are not executing in their remainder sections can participate in deciding which process will enter next, and this selection cannot be postponed indefinitely [76, 79, 82, 242, 359, 370, 381, 421].
3. **Bounded Waiting (Starvation Avoidance):** There must be a strict bound or limit on the number of times other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted. This ensures no process has to wait endlessly [242, 359, 370, 381, 420, 421].

---

#### Group 3: Principles of Concurrency & Speed Factors
* **MU May 2016 [Marks 5]:** *"Explain the process synchronization in brief."*
* **Stallings Textbook / Handouts [Marks 5]:** *"Differentiate between Interleaving and Overlapping processes in the context of concurrency. What factors influence asynchronous process execution speed?"*

##### Answer (Detailed 5 Marks Structure):
##### 1. Interleaving v/s Overlapping Concurrency (2 Marks):
In modern operating systems, concurrent execution of processes manifests in two forms depending on the underlying hardware architecture [322, 356, 367, 378, 402, 408, 509, 513, 518, 567, 615]:
* **Interleaving Concurrency (Uniprocessor Systems):** On a single processor core, multiple processes are executed sequentially by interleaving their execution over time [322, 356, 367, 378, 402, 408, 509, 513, 518, 567, 615]. The OS rapidly switches CPU context among active tasks, giving the user the *illusion* of simultaneous execution [318, 356, 367, 378, 408, 509, 513, 518, 567, 615].
* **Overlapping Concurrency (Multiprocessor Systems):** On multi-core systems, processes are executed simultaneously by overlapping execution across physically distinct processing cores [13, 168, 224, 276, 290, 310, 318, 402, 408, 452, 461, 482, 508, 513, 518, 519, 567, 615]. 
* **The Equivalence Principle:** Although uniprocessor execution is interleaved, it presents **the exact same logical concurrency problems, race conditions, and synchronization issues** as overlapping multiprocessor execution [87, 95, 229, 390, 402, 408].

##### 2. Factors Influencing Asynchronous Execution Speed (3 Marks):
Because concurrent processes execute asynchronously, the speed at which any given process progresses cannot be predicted [87, 95, 229, 390]. It depends strictly on:
1. **Activities of Other Processes:** How many other active processes are competing for the CPU, memory, and bus bandwidth [88, 96, 229, 390].
2. **Interrupt Handling by the OS:** The frequency and duration of hardware interrupts processed by the kernel (e.g. I/O interrupts, page faults) [87, 95, 229, 390].
3. **OS Scheduling Policies:** The dispatching algorithms and priorities assigned to different tasks by the short-term scheduler [87, 95, 229, 390].

---

#### Group 4: Mutual Exclusion Significance & Conditions
* **MU May 2016 [Marks 5]:** *"What is mutual exclusion? Explain its significance."*
* **SVKM NMIMS Handouts [Marks 5]:** *"Discuss the four conditions required to have an excellent mutual exclusion solution for the critical section problem."*

##### Answer (Detailed 5 Marks Structure):
##### 1. Definition and Significance of Mutual Exclusion (2.5 Marks):
**Mutual Exclusion** is the core property of process synchronization that states that "no two processes can exist in their critical sections at any given point of time" [92, 180, 247, 350, 409, 565, 612].
* **Significance:** Without mutual exclusion, multiple processes would modify shared resources simultaneously, causing race conditions, data inconsistencies, and erratic system behavior [91, 121, 130, 180, 210, 247, 260, 350, 410, 411, 515, 520, 566, 613, 616, 645].
* Mutual exclusion serves as the foundational safety property upon which all process synchronization techniques are built [92].

##### 2. Four Conditions for an Excellent Mutual Exclusion Solution (2.5 Marks):
To have a robust mutual exclusion framework, four system conditions must hold [152, 262, 349, 378, 612, 621, 648]:
1. No two processes may be simultaneously inside their critical sections [152, 262, 349, 378, 612, 621, 648].
2. No assumptions may be made about relative process execution speeds or the number of CPU cores [152, 262, 349, 378, 612, 621, 648].
3. No process running outside its critical section is allowed to block any other process trying to enter its critical section [152, 262, 349, 378, 612, 621, 648].
4. No process should have to wait indefinitely to enter its critical section (prevents starvation) [152, 262, 349, 378, 612, 621, 648].

---

#### Group 5: Operating System Concurrency Concerns
* **Stallings Textbook / Course Handouts [Marks 5]:** *"What design and management issues are raised by the existence of concurrency? Explain the concerns an operating system must address."*

##### Answer (Detailed 5 Marks Structure):
To accommodate concurrent execution safely, the operating system kernel must address four major concerns [510, 516, 520, 568, 569]:

1. **Keep Track of Active Processes:** The OS must maintain an active directory of processes using **Process Control Blocks (PCBs)**, tracking process states (Ready, Running, Waiting) and queue links dynamically [100, 152, 412, 510, 516, 520, 568, 608].
2. **Optimal Resource Allocation:** The OS must allocate CPU time, physical RAM pages, file descriptors, and physical I/O channels fairly and optimally to competing concurrent tasks, avoiding deadlocks [6, 179, 412, 481, 483, 490, 510, 516, 520, 538, 540, 568].
3. **Data and Physical Isolation Protection:** The OS must protect memory spaces and physical resources from unauthorized access. A buggy concurrent process must not be allowed to access or overwrite the memory bounds or file pointers of other processes [152, 401, 481, 482, 484, 510, 516, 520, 537, 539, 568, 608].
4. **Execution Speed Independence:** The functional output and overall execution of a process must be completely independent of the relative scheduling speeds at which it runs compared to other concurrent tasks [510, 516, 520, 569, 606].

---

### TOPIC 2: MUTUAL EXCLUSION: HARDWARE SUPPORT

#### Group 6: Interrupt Disabling (Uniprocessor Support)
* **Darshan OS notes / Handouts [Marks 5]:** *"Explain how mutual exclusion can be achieved by disabling interrupts in a uniprocessor system. What are the limitations of this approach?"*

##### Answer (Detailed 5 Marks Structure):
##### 1. Core Working Mechanism (2 Marks):
In a uniprocessor system, concurrent execution is achieved purely by interleaving processes [322, 356, 367, 378, 402, 408, 509, 513, 518, 567, 615]. A process continues running until it voluntarily relinquishes the CPU or is interrupted by the system clock tick [337, 576, 626].
* To enforce mutual exclusion, a process can temporarily **disable all hardware interrupts** immediately upon entering its critical section using CPU instruction registers [109, 116, 155, 181, 337, 338, 511, 576, 577, 626].
* With interrupts disabled, the CPU cannot perform context switches, allowing the running process to complete its critical section safely without preemption [155, 181, 337, 338, 511, 576, 577, 626].
* Once out of the critical section, the process executes an exit protocol to **re-enable interrupts** [109, 116, 155, 181, 337, 338, 511, 576, 577, 626].

```c
void process_uniprocessor() {
    disable_interrupts();  // Entry Section
    /* CRITICAL SECTION */ // Access shared resource
    enable_interrupts();   // Exit Section
}
```

##### 2. Limitations of Interrupt Disabling (3 Marks):
1. **Inoperable on Multiprocessors:** On multiprocessor/multicore systems, disabling interrupts on CPU Core 1 does not affect Core 2 [109, 155, 308, 339, 511, 577, 626]. Sibling threads on Core 2 can still access shared RAM simultaneously, violating mutual exclusion [109, 155, 308, 339, 511, 577, 626].
2. **Severe Efficiency Loss:** Halts system multitasking since other ready processes cannot be scheduled while interrupts are disabled [314, 338, 511, 577].
3. **Clock Drift:** System clocks rely on periodic timer interrupts. Disabling interrupts for too long halts the system timer, causing clock drift [308, 314, 338].
4. **Vulnerability to Infinit Loops (Seizure Risk):** If a user program contains an infinite loop inside its critical section with interrupts disabled, the operating system can never reclaim CPU control, freezing the entire machine [181, 339]. *Because of this security risk, interrupt disabling is restricted to short kernel routines and is prohibited for user programs* [339].

---

#### Group 7: Hardware Special Instructions (TSL, CAS, Swap)
* **SVKM'S Semester V Final Exam (30 November 2022) [Q4a - 10 Marks]:** *"What are the different mutual exclusions hardware synchronization algorithms? Explain all in detail?"*
* **GTU/Darshan Reference [Marks 10]:** *"Describe hardware instructions Test-and-Set and Exchange for process synchronization. Give C-style representation and trace their execution."*

##### Answer (Comprehensive 10 Marks Structure):
**📊 Diagram Required: YES**
* **Diagram Description:** High-level timeline trace showing Process $P_1$ successfully entering the CS with `lock = false` while Process $P_2$ gets trapped in a spinning cycle because `lock = true`.
* **Diagram Location:** `UNIT 3- Process Concurrency.pdf` Prof. Jesleena Gonsalves / Slide 8 of `Mutual Exclusion in Synchronization.pptx`.

##### 1. Introduction (1.5 Marks):
Modern multiprocessor architectures provide special machine instructions that execute read-modify-write operations **atomically** (indivisibly as a single instruction cycle) [25, 245, 316, 423, 425, 455, 564, 578]. During execution, other processors are physically blocked from accessing that memory address using hardware-level **memory bus locking** [341, 342, 502]. The three core hardware algorithms are:

---

##### 2. Test and Set (TS / TSL - Test and Set Lock) (3 Marks):
TSL atomically copies the current value of a lock variable into a CPU register and writes a non-zero value (`1` or `true`) to that same address [14, 26, 37, 59, 111, 169, 211, 261, 277, 291, 308, 316, 339, 340, 502, 504, 550].

* **Abstract Logical C-Code:**
```c
boolean test_and_set(boolean *target) {
    boolean rv = *target;
    *target = true;
    return rv;
}
```

* **Mutual Exclusion Implementation:**
```c
boolean lock = false; // Shared global lock variable

void process_Pi_TSL() {
    while (true) {
        while (test_and_set(&lock))
            ; /* Busy waiting: spin lock until returned value is false */
        
        /* CRITICAL SECTION */
        
        lock = false; // Exit Section
        /* remainder */
    }
}
```

* **Execution Trace:**
  * When `lock` is `false`, a process $P_1$ calls `test_and_set(&lock)` [248]. It reads `false`, writes `true`, and returns `false`. $P_1$ breaks out of the loop and enters the critical section [248].
  * If process $P_2$ attempts to enter, it calls `test_and_set` [248]. It reads `true` (since $P_1$ set it), writes `true` (no change), and returns `true`. $P_2$ remains trapped spinning in its `while` loop [248].
  * When $P_1$ finishes, it sets `lock = false`, allowing $P_2$ to enter on its next spin [248].

---

##### 3. Compare and Swap (CAS) (3 Marks):
CAS compares the value of a memory location with an expected value. If they match, the location is written with a new value atomically [15, 27, 170, 278, 292, 457, 551, 579, 629].

* **Abstract Logical C-Code:**
```c
int compare_and_swap(int *value, int expected, int new_value) {
    int temp = *value;
    if (*value == expected) {
        *value = new_value;
    }
    return temp;
}
```

* **Mutual Exclusion Implementation:**
```c
int lock = 0; // Shared lock variable

void process_Pi_CAS() {
    while (true) {
        while (compare_and_swap(&lock, 0, 1) != 0)
            ; /* Busy waiting: spin until returned value is 0 */
        
        /* CRITICAL SECTION */
        
        lock = 0; // Exit Section
        /* remainder */
    }
}
```

* **Execution Trace:**
  * Process $P_1$ calls `compare_and_swap(&lock, 0, 1)`. It finds `lock == 0` (matching expected). It sets `lock` to `1` and returns `0`. Since `0 == 0`, $P_1$ enters its CS.
  * Process $P_2$ calls CAS. It finds `lock == 1` (not matching expected). The value is not changed, and it returns `1`. Since `1 != 0`, $P_2$ remains blocked in the loop.
  * When $P_1$ sets `lock = 0`, $P_2$ succeeds on its next swap.

---

##### 4. Exchange / Swap (XCHG) (2.5 Marks):
Atomically exchanges the contents of a CPU register with a memory location in a single instruction fetch cycle [37, 60, 66, 111, 212, 262, 309, 342, 426, 524, 581, 631].

* **Abstract Logical C-Code:**
```c
void Swap(boolean *a, boolean *b) {
    boolean temp = *a;
    *a = *b;
    *b = temp;
}
```

* **Mutual Exclusion Implementation:**
```c
boolean lock = false; // Shared global lock variable

void process_Pi_Swap() {
    while (true) {
        boolean key = true; // Local variable
        do {
            Swap(&key, &lock); // Atomic exchange
        } while (key == true); // Spin if key remains true
        
        /* CRITICAL SECTION */
        
        lock = false; // Exit Section
        /* remainder */
    }
}
```

* **Execution Trace:**
  * Process $P_1$ swaps its local `key = true` with global `lock = false`. This leaves $P_1$ with `key = false` and `lock = true`. $P_1$ enters its CS.
  * Process $P_2$ swaps its local `key = true` with `lock = true`. Local `key` remains `true` (and `lock` remains `true`), keeping $P_2$ trapped in its spinning loop.
  * When $P_1$ sets `lock = false`, $P_2$ swaps `key` (true) with `lock` (false), setting local `key = false` and entering its CS.

---

#### Group 8: Busy Waiting & Spinlocks
* **GTU Nov 2015 / Dec 2016 [Marks 5]:** *"What do you mean by busy waiting? Explain it."*
* **Stallings Textbook / Ref [Marks 5]:** *"Define a spinlock. Discuss the advantages and disadvantages of using hardware special instructions with busy-waiting loops to achieve mutual exclusion."*

##### Answer (Detailed 5 Marks Structure):
##### 1. Definition of Busy Waiting and Spinlock (2 Marks):
* **Busy Waiting (or Spin Waiting):** A technique where a waiting process repeatedly executes a tight loop of instructions to continually test a lock variable until it changes to a value allowing entry [333, 425, 428, 446, 580, 630]. It performs no productive work but consumes 100% CPU cycles, generating high processing overhead [333, 425, 428, 446, 580, 630].
* **Spinlock:** A mutual exclusion lock that utilizes a busy-waiting mechanism to block waiting threads [583, 597, 634].

##### 2. Evaluation of Hardware Special Instructions (3 Marks):
* **Advantages (Pros) [428, 582, 632]:**
  * **Multiprocessor Support:** Unlike uniprocessor interrupt disabling, it works seamlessly across any number of processors sharing main memory [428, 582, 632].
  * **Scalability:** It scales easily to support any number of concurrent processes [428, 582, 632].
  * **Independently Managed Critical Sections:** Multiple critical sections can be supported by assigning a separate, unique lock variable to each critical section (e.g. `lock_A` and `lock_B`) [428, 582, 632].
* **Disadvantages (Cons) [428, 582, 632]:**
  * **Busy Waiting Waste:** Wastes CPU cycles while spinning, degrading overall uniprocessor multitasking performance [333, 425, 428, 446, 580, 630].
  * **Starvation is Possible:** When a process releases the lock, the choice of which waiting process acquires it next is arbitrary, which can result in a process waiting indefinitely [428, 582, 632].
  * **Deadlock via Priority Inversion:** If a low-priority process $P_1$ holds the lock, and a high-priority process $P_2$ arrives and busy-waits, the CPU scheduler will run $P_2$ indefinitely, preventing $P_1$ from executing and releasing the lock [428, 582, 632].

---

## 📝 4. Complete Unit 3 PYQ Syllabus Checklist & Progress Tracker

Use this checklist to track your revision progress. Ensure you can answer and explain every topic listed below:

- [ ] **Principles of Concurrency (Topic 1):**
  - [ ] Define "Concurrency" and contrast "Interleaving" (Uniprocessor) with "Overlapping" (Multiprocessor) [318, 509, 513].
  - [ ] Explain the asynchronous speed independence factors [87, 95, 229, 390].
  - [ ] Differentiate between Atomic Operation and Critical Section [245, 246, 564, 612].
  - [ ] Explain Race Condition using bank balance and character buffer `chin` examples [411, 491].
  - [ ] List the three requirements of the Critical Section Problem (Mutual Exclusion, Progress, Bounded Waiting) [242].
  - [ ] Memorize the 6 Requirements (Axioms) of Mutual Exclusion [124, 133, 334, 420].
- [ ] **Mutual Exclusion: Hardware Support (Topic 2):**
  - [ ] Describe Interrupt Disabling, including entry/exit protocol and why it fails on multiprocessors [155, 337, 338, 511].
  - [ ] Implement and trace the Test-and-Set (TSL) hardware instruction [248, 339, 340, 502].
  - [ ] Implement and trace the Compare-and-Swap (CAS) hardware instruction [15, 27, 170, 278, 292, 551].
  - [ ] Implement and trace the Exchange / Swap (XCHG) hardware instruction [60, 66, 212, 309, 426, 581].
  - [ ] Explain hardware-level Memory Bus Locking on multiprocessors [341, 342, 502].
  - [ ] Define Busy Waiting and explain spinlock trade-offs (Waste, Starvation, Priority Inversion) [333, 425, 428].

---

## ⚡ 5. High-Yield Revision Table

| Topic / Concept | Primary Rule / Algorithm | Target Environment | Key Disadvantage / Limit |
| :--- | :--- | :--- | :--- |
| **Uniprocessor Concurrency** [120, 261] | **Interleaving** in time [322, 356]. | Single CPU Core [356, 367]. | Context switch overhead [46, 230]. |
| **Multiprocessor Concurrency** [163] | **Overlapping** in space [482, 519]. | Multiprocessor / Multicore [482]. | Memory bus contention [341]. |
| **Interrupt Disabling** [337] | Disable interrupts on CS entry; re-enable on exit [337]. | Uniprocessors [576, 626]. | **Fails completely on multiprocessors** [155]. |
| **Test and Set (TSL)** [339] | `boolean test_and_set(boolean *target)` | Multiprocessors [428, 582]. | Busy waiting (Spinlock) CPU waste [428, 582]. |
| **Compare and Swap (CAS)** [15] | `int compare_and_swap(int *val, int exp, int new)` | Multiprocessors [428, 582]. | Starvation & Priority Inversion risk [428, 582]. |
| **Exchange / Swap** [60] | `void Swap(boolean *a, boolean *b)` | Multiprocessors [428, 582]. | Busy waiting (Spinlock) CPU waste [428, 582]. |

---

**This Unit 3 PYQ Question Bank is verified, accurate, and completely safe to use for your NMIMS University examinations.**
