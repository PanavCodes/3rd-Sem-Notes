# Unit 1 Operating Systems: Previous Year Questions (PYQ) Bank

This document contains a comprehensive, structured, and marks-aligned **Previous Year Questions (PYQ) Bank** for **Unit 1: Operating System Overview**, compiled from all available exam papers and course syllabus policies in your notebook.

---

## 1. Unit 1 Course Policy & Syllabus Alignment
According to the official **Operating Systems 2025-26 Course Policy**, the syllabus checklist for Unit 1 includes:
1. **Operating system objectives and functions** (Convenience, Efficiency, Ability to evolve)
2. **Evolution of operating systems** (Serial Processing, Simple Batch, Multiprogrammed Batch, Time-Sharing/Multitasking)
3. **Basic concepts of OS**: Processes, Files, and System calls
4. **OS Architectural Structures**: Layered structure v/s Monolithic structure of OS (with Microkernel and Modular extensions)

All PYQs found in your sources have been mapped directly to these four official subtopics.

---

## 2. Final Analysis of Unit 1 PYQs

### Topic-Wise PYQ Frequency & Analysis
| Topic Area | Frequency in PYQs | Relative Weight | Most Frequently Asked Concept |
| :--- | :---: | :---: | :--- |
| **OS Objectives, Views, and Services** | 4 Times | High | Abstract Views (Resource Manager vs. Extended Machine) & OS Services |
| **Dual-Mode Operation** | 2 Times | High | User Mode v/s Kernel Mode with Transition Diagram |
| **Evolution of Operating Systems** | 3 Times | Medium | Resident Monitors (Simple Batch) & Third Generation OS |
| **OS Architectural Structures** | 4 Times | Very High | Layered v/s Monolithic Architecture & Kernel/Shell |
| **Basic Concepts (System Calls)** | 2 Times | Medium | Process Management & File Management System Calls |

### Key Observations & Insights
1. **Most Frequently Asked Topic:** **Layered v/s Monolithic OS Architecture** is the absolute high-priority question, appearing across multiple semesters (Special Re-Exam 2022-23, Re-Exam 2023-24, Final Exam 2024-25) with marks ranging from 5 to 10 marks.
2. **Repeated Concepts with Different Wording:** 
   * *OS Objectives and Views:* Asked as "What is OS & give functions" (GTU Winter-13) and "Explain objectives and functions" (GTU Summer-14) or "Discuss various OS views" (May 2015).
   * *OS Services:* Asked as "Explain services provided by OS" (5 Marks) and "Explain OS services with suitable diagram" (10 Marks, 2024-25 Final).
3. **Questions Repeated Across Years:**
   * **Dual Mode Operation:** Repeated in both the main and alternate versions of the Semester V Final Exam (2024-25).
   * **Monolithic v/s Layered Structure:** Repeated across 2022-23 (Special Re-Exam), 2023-24, and 2024-25.
4. **Diagram-Based PYQs and Locations:**
   * **Dual Mode Transition:** Shown on Slide 12 of `UNIT1-Introduction to OS.pptx` and in Chapter 1 of the Silberschatz textbook.
   * **OS Services View:** Shown on Slide 15 of `UNIT1-Introduction to OS.pptx` (and Figure 1.1 in TechNeo / Figure 1-1 in Darshan OS notes).
   * **Monolithic vs. Layered Architecture:** Found in Section 1.7 of `UNIT1-Introduction to OS.pptx`.

---

## 3. Comprehensive PYQ Question Bank & Answers (Marks-Aligned)

### Topic A: Operating System Objectives, Functions, Views, and Dual-Mode

#### Group 1: OS Definition, Objectives, and Functions
* **GTU Winter-13 [Marks 4]:** *"What is operating system? Give functions of operating system."*
* **GTU Summer-14 [Marks 7]:** *"Explain the objectives and functions of operating systems."*
* **GTU June-2015 / Nov-2015 [Marks 5]:** *"Explain different views of Operating system."*
* **TechNeo Review / Review Questions [Marks 2]:** *"What is operating system?"*

##### Answer (Detailed 5-7 Marks Structure):
1. **Definition of an OS (2 Marks):**
   An **Operating System (OS)** is system software that acts as an intermediary between a computer user and the computer hardware. It is a collection of programs that manages hardware resources (CPU, memory, storage, I/O devices) and provides a common execution environment for application software.
2. **Three Core OS Objectives (3 Marks):**
   * **Convenience:** Making the computer system convenient and easy to use for the user by hiding the raw complexity of the physical hardware (Extended Machine view).
   * **Efficiency:** Allowing computer system resources to be used in an efficient, optimized manner (Resource Manager view).
   * **Ability to Evolve:** Constructed in such a way as to permit the effective development, testing, and introduction of new system functions without interfering with existing services.
3. **Two Primary Functional Views of an OS (2 Marks):**
   * **User View (The Extended/Virtual Machine):** The OS presents the user with a clean, abstract, and easy-to-use interface, hiding messy hardware details like disk track seeking or physical register programming.
   * **System View (The Resource Manager & Control Program):** The OS acts as a manager of system resources, multiplexing hardware resources in **time** (allocating CPU slices) and **space** (allocating RAM partitions) among competing processes, while controlling program execution to prevent errors and improper use.

---

#### Group 2: Dual Mode Operation (High-Yield Concept)
* **Semester V Final Exam (2024-2025) [Q1a - 5 Marks]:** *"What do you mean by Dual mode Operation in OS? Explain with suitable diagram?"*
* **Semester V Special Re-Exam (2022-2023) [Q1a - 5 Marks]:** *"What do you mean by Dual mode Operation in OS? Explain with suitable diagram?"*

##### Answer (Comprehensive 5 Marks Structure):
**📊 Diagram Required: YES**
* **Diagram Description:** User space to Kernel space transition triggered by a system call/interrupt, setting the mode bit to 0 (Kernel mode), executing the privileged service, resetting the mode bit to 1 (User mode), and returning to user space.
* **Diagram Location:** Figure 1.1.1/1.1.2 in `3140702-OS-Techanical Publications.pdf` (or `UNIT1-Introduction to OS.pptx` Slide 12 / Silberschatz Chapter 1).

```text
       +---------------------------------------------+
       |                  USER SPACE                 |
       |                                             |
       |   +-------------------+                     |
       |   |   User Program    |                     |
       |   +---------+---------+                     |
       |             | (System Call / Trap)          |
       |             v                               |
 Mode  |       [Set Mode Bit = 0]                    |
 Boundary - - - - - - - - - - - - - - - - - - - - - -|
       |             | (Interrupt/Trap Service)      |
       |             v                               |
       |   +---------+---------+                     |
       |   |    Kernel OS      |                     |
       |   +---------+---------+                     |
       |             |                               |
       |       [Set Mode Bit = 1]                    |
       |             v (Return from System Call)     |
       |                  KERNEL SPACE               |
       +---------------------------------------------+
```

1. **What is Dual-Mode Operation? (2 Marks):**
   To ensure proper execution of the operating system and to prevent user programs from crashing the system or modifying other programs, modern CPUs support **Dual-Mode Operation** using a hardware **mode bit** (typically a register bit):
   * **User Mode (Mode Bit = 1):** The CPU executes instructions on behalf of the user application. In this mode, certain instructions (privileged instructions) are prohibited, and access to direct hardware or system memory is restricted.
   * **Kernel/Monitor/System/Supervisor Mode (Mode Bit = 0):** The CPU executes with complete access to all hardware resources and instructions. The operating system kernel runs in this mode.
2. **Transition Mechanism (2 Marks):**
   * Whenever a user program requires a hardware resource (like reading a file or allocating memory), it must issue a **trap** or **system call (software interrupt)**.
   * The hardware automatically switches the mode bit from `1` to `0` (Kernel Mode) and transfers control to a fixed address in the OS interrupt vector.
   * The OS executes the requested privileged operation safely, resets the mode bit back to `1` (User Mode), and transfers control back to the user program.
3. **Privileged Instructions (1 Mark):**
   Instructions that could cause harm (such as disabling hardware interrupts, direct I/O manipulation, modifying page tables, or altering the base/limit memory protection registers) are designated as **privileged instructions** and can *only* be executed in Kernel Mode. If a user program tries to run them, the hardware generates a trap (exception) to the OS, terminating the program.

---

### Topic B: Evolution of Operating Systems

#### Group 3: Historical Operating System Generations
* **FYIT Sem 1 Exam (Nov-2016) [Q1a - 5 Marks]:** *"Explain third generation operating systems."*
* **Semester V Re-Exam (2022-2023) [Q7a - 7 Marks]:** *"What do you understand by bare machine and resident Monitor?"*

##### Answer (Detailed 5-7 Marks Structure):
1. **Bare Machine Concept (2 Marks):**
   * In the earliest days of computing (First Generation: 1940s-1950s), computers had **no operating system**. 
   * Programmers interacted directly with the **bare hardware** using console lights, toggle switches, and plugboards.
   * There was no software abstraction layer; a single user had completely dedicated access to the machine.
2. **Resident Monitor Concept (2 Marks):**
   * To solve the massive waste of CPU time between jobs (Second Generation: 1950s-1960s), the **Simple Batch Operating System** was introduced using a program called the **Resident Monitor**.
   * The resident monitor was always resident in main memory. It automated the transition from one job to the next.
   * Jobs were grouped together on magnetic tapes. The resident monitor read each job, loaded it, executed it, and immediately loaded the next job without operator intervention, using a **Job Control Language (JCL)**.
3. **Third Generation Operating Systems (3 Marks):**
   * **Timeline:** Late 1960s to 1970s (marked by the introduction of the IBM System/360).
   * **Key Innovations:** **Multiprogramming** and **Time-Sharing**.
   * **How Multiprogramming Works:** Instead of keeping only one job in memory, multiple jobs are kept in main memory simultaneously. When the currently running job has to wait for an I/O operation to complete, the CPU does not sit idle; the OS switches the CPU to another ready job.
   * **How Time-Sharing Works:** An extension of multiprogramming where the CPU is multiplexed among multiple users using rapid **round-robin time slicing (quantum clocks)**. Users interact with the machine simultaneously via active terminals, creating the illusion of a dedicated personal system.

---

### Topic C: Operating System Services & System Calls

#### Group 4: OS Services Implementation
* **Semester V Final Exam (2024-2025) [Q4a - 10 Marks]:** *"Operating systems provide an environment for execution of programs and, offers services to programs and users. Justify the statement by explaining the operating system services with suitable diagram?"*
* **Semester V Re-Exam (2023-24) [Q2a - 10 Marks]:** *"Draw a labelled view of Operating System services and describe each service in detail."*
* **Semester V Special Re-Exam (2022-2023) [Q2a - 10 Marks (Partial)]:** *"Explain any five services provided by Operating System."*

##### Answer (Comprehensive 10 Marks Structure):
**📊 Diagram Required: YES**
* **Diagram Description:** A layered diagram showing: Bottom Layer = Hardware; Middle Layer = Operating System (Kernel Services); Top Layer = User Interface (CLI, GUI) and User Applications. The communication link between the user layer and OS layer is formed by System Calls.
* **Diagram Location:** Slide 15 in `UNIT1-Introduction to OS.pptx` (or Figure 1-1 in Darshan OS notes).

```text
  +-------------------------------------------------------------+
  |              USER APPLICATIONS / USER PROGRAMS              |
  +-------------------------------------------------------------+
  |             USER INTERFACES (CLI / GUI / Shell)              |
  +-------------------------------------------------------------+
  |============ SYSTEM CALL INTERFACE (System Calls) ===========|
  +-------------------------------------------------------------+
  |                  OPERATING SYSTEM SERVICES                  |
  |  - Program Execution         - File System Manipulation     |
  |  - I/O Operations            - Communications (IPC)         |
  |  - Error Detection           - Resource Allocation          |
  |  - Accounting                - Protection & Security        |
  +-------------------------------------------------------------+
  |                      COMPUTER HARDWARE                      |
  +-------------------------------------------------------------+
```

##### Detailed Explanation of Operating System Services:
Operating system services are designed to provide convenience to the programmer and system administrator. They can be divided into two main categories:

##### 1. Services that help the user / execute programs:
1. **Program Execution:** The OS must load program instructions and data into main memory, allocate CPU registers, set up execution structures, run the program, handle runtime execution errors, and cleanly terminate execution.
2. **I/O Operations:** A running program may require physical I/O (such as reading from disk, outputting to display, or sending data to a printer). For efficiency and protection, user programs cannot access hardware devices directly; the OS provides safe interfaces to perform these operations.
3. **File-System Manipulation:** Programs need to read, write, create, delete, list, search, and manage permissions on files and directories. The OS maps these logical files to physical disk blocks.
4. **Communications:** Processes often need to exchange information. This is achieved via two main mechanisms managed by the OS:
   * **Shared Memory:** Multiple processes map a common region of their address spaces for fast data exchange.
   * **Message Passing:** The OS manages message packets sent between processes over an inter-process communication (IPC) channel.
5. **Error Detection:** The OS constantly monitors the system for potential hardware errors (such as memory parity errors or power failures) and software errors (such as arithmetic overflow or out-of-bounds memory access) and takes appropriate corrective action.

##### 2. Services that ensure efficient system operation:
6. **Resource Allocation:** When multiple users or processes are running simultaneously, the OS allocates CPU cycles, main memory, file storage, and I/O devices to ensure high utilization and fairness.
7. **Accounting:** The OS tracks which users/processes use how many resources, and for how long. This is essential for system billing, profiling, and performance tuning.
8. **Protection and Security:** 
   * **Protection:** Ensuring that all access to system resources is controlled and that processes cannot interfere with each other.
   * **Security:** Authenticating users (via logins/passwords) and protecting physical I/O devices against unauthorized external access.

---

#### Group 5: System Calls Function and Classification
* **Semester V Re-Exam (2023-2024) [Q1a - 5 Marks]:** *"Explain system calls in brief."*
* **FYIT Sem 1 Exam (Nov-2016) [Q1b - 5 Marks]:** *"List and explain system calls for process management."*

##### Answer (Detailed 5 Marks Structure):
1. **What is a System Call? (2 Marks):**
   System calls provide the **programming interface** to the services made available by the operating system. They are typically written in C or C++ (or assembly). For assembly-level programs, they are triggered by software interrupts or trap instructions. Application programmers rarely write direct system calls; instead, they use **Application Programming Interfaces (APIs)** (such as the Win32 API for Windows or the POSIX API for UNIX/Linux), which wrap the system calls for portability.
2. **The 3 Methods of Parameter Passing to System Calls (1.5 Marks):**
   Because user programs run in user space and system calls execute in kernel space, parameters must be passed across the mode boundary using three main methods:
   * **Registers:** The simplest method where parameters are loaded directly into CPU registers. This is fast but limited by the number of registers.
   * **Block/Table in Memory:** If parameters exceed registers, they are stored in a block or table in main memory, and the address of the block is passed as a parameter in a CPU register (used by Linux).
   * **System Stack:** Parameters are pushed onto the system stack by the user program, and popped off by the operating system kernel.
3. **Classification & Process Management System Calls (1.5 Marks):**
   System calls are categorized into five main areas:
   * **Process Control:** e.g., `fork()` to create a child process, `exit()` to terminate, `wait()` or `waitpid()` to wait for a child to complete.
   * **File Management:** e.g., `open()`, `read()`, `write()`, `close()`.
   * **Device Management:** e.g., `ioctl()`, `read()`, `write()`.
   * **Information Maintenance:** e.g., `getpid()`, `time()`.
   * **Communications:** e.g., `pipe()`, `shmget()`, `socket()`.

---

### Topic D: Operating System Structural Architectures

#### Group 6: OS Structures (Monolithic vs. Layered)
* **Semester V Final Exam (2024-2025) [Q1a - 5 Marks]:** *"Compare and contrast the layered and monolithic structures of operating systems. Analyze their respective advantages and disadvantages in terms of modularity, performance, and maintainability."*
* **Semester V Special Re-Exam (2022-23) [Q3a - 10 Marks]:** *"Differentiate between layered v/s monolithic structure of operating system?"*

##### Answer (Comprehensive 5-10 Marks Structure):
To answer this high-priority comparative question, we construct a highly structured comparison table across multiple evaluation criteria:

| Comparison Parameter | Monolithic OS Structure | Layered OS Structure |
| :--- | :--- | :--- |
| **Architectural Concept** | The entire operating system runs as a single, large program in a single address space (Kernel Mode). All procedures can call any other procedure directly. | The OS is broken down into a hierarchy of smaller, distinct layers (Layer 0 to Layer N). Layer 0 is the Hardware; Layer N is the User Interface. |
| **Interaction Rule** | Any module can interact with any other module without formal interfaces, bypassing security checks for speed. | Each layer can *only* invoke services provided by the layer immediately below it (Layer i-1) and provide services to the layer above it. |
| **Modularity & Separation** | **Very Poor.** There is no clean separation of concerns; the system is highly coupled. | **Excellent.** High modularity because each layer is designed as an independent abstract data type. |
| **Performance (Execution Speed)** | **Exceptional.** Very low execution overhead because procedure calls occur within the same address space without context switching or boundary crossings. | **Poor.** High performance penalty because a user request must traverse multiple layers, triggering multiple function boundary crossings (nested layered overhead). |
| **Maintainability & Debugging** | **Extremely Difficult.** A bug in any single component (such as a device driver) can corrupt kernel memory and crash the entire system. | **Much Easier.** Debugging is simplified. Layer 0 is verified first, then Layer 1 is built and tested using only Layer 0 services, allowing incremental verification. |
| **Modifiability / Extensibility** | **Difficult.** Adding a new feature or modifying an existing protocol requires recompiling and rebuilding the entire monolithic kernel. | **Easier.** Modifying a single layer is simple as long as its public interfaces to the layers above and below remain unchanged. |
| **Examples** | Traditional UNIX, MS-DOS, Early Linux. | THE Multiprogramming System (Dijkstra), MS-DOS (partially layered). |

---

#### Group 7: Kernel, Shell, and Microkernel Architecture
* **Semester V Special Re-Exam (2022-2023) [Q2a - 10 Marks (Monolithic vs. Microkernel)]:** *"Explain any five services provided by Operating System. Describe Kernel and its types in detail. Also discuss the limitation of monolithic kernel and how it is overcome."*
* **Semester V Re-Exam (2022-23) [Q5b - 7 Marks]:** *"What do you mean by Kernel? Describe various operations performed by Kernel."*
* **TechNeo Review / June-2015 / Nov-2015 [Marks 5]:** *"Differentiate between kernel and shell."*

##### Answer (Detailed 7-10 Marks Structure):
1. **Differentiating Kernel and Shell (3 Marks):**
   * **Kernel:** The core, heart, and central component of the operating system that runs in hardware Kernel Mode (privileged mode bit = 0). It interacts directly with the computer hardware to manage CPU execution, memory partitions, and physical devices. It is loaded into main memory during system booting and remains there until shutdown.
   * **Shell:** A simple user program that acts as a command-line interpreter or command prompt. It executes in User Mode (Mode Bit = 1). Its primary job is to read commands entered by the user, parse them, and spawn processes (using system calls) to run corresponding programs.

2. **Types of Kernels (3 Marks):**
   * **Monolithic Kernel:** As discussed, all OS services (scheduler, virtual memory manager, file system, device drivers) run together inside a single kernel space.
     * *Limitation:* If any driver crashes, the whole system halts. 
   * **Microkernel:** Overcomes monolithic limitations by moving all non-essential services out of kernel space into **user space** as separate system processes (e.g., file servers, directory servers). The microkernel itself remains tiny, containing *only* essential mechanisms: address space protection, low-level process scheduling, and **Inter-Process Communication (IPC)**.
     * *How it overcomes Monolithic flaws:* It improves reliability (if a file server crashes, it can be restarted in user space without crashing the kernel) and security.
     * *Trade-off:* Performance is reduced due to high IPC execution overhead.

3. **Modern Modular Design (Loadable Kernel Modules - LKM) (2 Marks):**
   * Modern operating systems (like Linux and macOS) use a hybrid approach: **Loadable Kernel Modules (LKM)**.
   * The kernel has a monolithic core but can dynamically load and unload object code (modules, such as a device driver or file system type) into kernel memory *at runtime* as needed, without needing to recompile or reboot the entire system.

---

## 4. Complete Unit 1 Checklist

Verify your preparation using this comprehensive syllabus and PYQ exam readiness checklist:

### A. Syllabus Topic Coverage Checklist
- [x] **Objectives of OS (Convenience, Efficiency, Evolution)** — *Fully Covered in Group 1*
- [x] **Dual Mode Operation (User vs. Kernel mode, Privileged Instructions)** — *Fully Covered in Group 2*
- [x] **Evolution of OS (Bare Machine, Resident Monitors, Multiprogramming, Time-Sharing)** — *Fully Covered in Group 3*
- [x] **OS Services (Program Execution, I/O, File System, IPC, Security)** — *Fully Covered in Group 4*
- [x] **Basic Concepts (Processes, Files, System Calls, stack vs. block parameter passing)** — *Fully Covered in Group 5*
- [x] **OS Structures (Monolithic vs. Layered Architecture)** — *Fully Covered in Group 6*
- [x] **Kernel vs. Shell & Microkernel Architecture** — *Fully Covered in Group 7*

### B. PYQ Source Checklist
- [x] **SVKM NMIMS Final Exam (2024-2025) [Q1a, Q4a]** — *Fully Covered & Mapped*
- [x] **SVKM NMIMS Special Re-Exam (2022-2023) [Q1a, Q2a, Q3a]** — *Fully Covered & Mapped*
- [x] **SVKM NMIMS Re-Exam (2022-2023) [Q5b, Q7a]** — *Fully Covered & Mapped*
- [x] **FYIT Semester 1 Exam (Nov-2016) [Q1a, Q1b]** — *Fully Covered & Mapped*
- [x] **GTU / TechNeo University Questions [Winter-13, Summer-14, June-15, Nov-15]** — *Fully Covered & Mapped*

---
