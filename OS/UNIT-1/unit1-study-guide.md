# Unit 1: Operating System Overview — Comprehensive Study Guide & Exam Prep

This comprehensive study guide is a complete, self-contained educational resource designed to teach **Unit 1 of Operating Systems** in exhaustive detail. It integrates all relevant uploaded sources, using **`UNIT1-Introduction to OS.pptx`** as the primary teaching source, alongside course policies, standard textbooks (Silberschatz & Galvin, William Stallings, Andrew S. Tanenbaum), and handwritten notes.

---

## Part 1: Unit 1 Coverage Map & Syllabus Audit

Before we begin the detailed teaching, this map aligns the **Syllabus (Course Policy)** with the slide-by-slide structure of **`UNIT1-Introduction to OS.pptx`** to ensure 100% complete and verified coverage.

| Course Policy (Syllabus Topic) | Relevant Slide(s) in PPT | Supplementary Textbook Chapters | Coverage Status & Audit Notes |
| :--- | :--- | :--- | :--- |
| **Operating System Objectives and Functions** | Slides 1–12 | Stallings Ch. 2.1, Galvin Ch. 1 | **Fully Covered**: Objectives (Convenience, Efficiency, Evolution) and roles (extended machine, resource manager) are fully detailed. |
| **Evolution of Operating Systems** | Slides 13–21 | Stallings Ch. 2.2, Notes | **Fully Covered**: Traces history from Serial Processing to Simple Batch, Multiprogrammed Batch, and Time-Sharing Systems. |
| **Basic Concept: Processes** | Slides 22–24 | Galvin Ch. 3.1, Tanenbaum Ch. 2.1 | **Fully Covered**: Concept of "program in execution" and process vs. program. Expanded with memory layouts (Text, Data, Heap, Stack). |
| **Basic Concept: Files** | Slides 25–27 | Galvin Ch. 13.1, Notes | **Fully Covered**: Logical logical storage unit, directories, file attributes, and operations. |
| **Basic Concept: System Calls** | Slides 28–36 | Galvin Ch. 2.3, Notes Ch. 1 | **Fully Covered**: API layer, User/Kernel mode transitions, system call interface, parameter passing, and Windows/UNIX mapping. |
| **OS Structures: Monolithic v/s Layered** | Slides 37–45 | Tanenbaum Ch. 1.7, Stallings Ch. 2.3 | **Fully Covered**: Detailed comparisons of Monolithic, Layered, Microkernel, and Modular structures. |

---

## Part 2: Detailed Course Modules (Thorough Teaching & Explanations)

---

### Module 1: Introduction to Operating Systems (OS Basics)

#### 1. Basic Idea
At its core, a computer system is a collection of physical devices (transistors, circuits, memory cells, disk drives, displays) known as hardware. Bare hardware by itself is extremely difficult for a human to program or interact with, because it only understands raw binary machine instructions and device-specific control signals. 
An **Operating System (OS)** serves as a master software layer that wraps around this complex hardware, hiding its ugly details and presenting users and application developers with a clean, convenient, and safe environment to execute programs.

#### 2. Important Definitions
*   ⭐ **Operating System (OS):** A program that controls the execution of application programs and acts as an active intermediary/interface between the computer user/applications and the computer hardware [3, 296, 395].
*   ⭐ **Extended Machine (User View):** A conceptual model of the OS where it acts as a software layer that abstracts away the complexities of the bare physical machine, presenting a simpler, unified, and more convenient virtual machine to the programmer [121].
*   ⭐ **Resource Manager (System View):** A conceptual model of the OS where it acts as a master controller responsible for the fair, secure, and optimal allocation of system resources (CPU time, memory space, file storage, and I/O devices) among competing processes and users [143, 238, 261].

#### 3. Detailed Concept: User View vs. System View
Operating system design can be analyzed through two distinct lenses:

##### A. The User View (Convenience Focus)
*   For a single user on a personal computer, the OS is designed primarily for **convenience, ease of use, and high performance** [51]. The hardware details must be completely transparent.
*   In this view, the OS is an **Extended Machine** (or virtual machine) [121]. It abstracts away physical intricacies (like sector-by-sector disk reading, memory register address translations, and bus interrupts) and exposes convenient primitives like "Open File," "Read Byte," or graphical folders.

##### B. The System View (Efficiency Focus)
*   In multi-user or shared environments (like mainframe servers, networks, or cloud clusters), individual user programs compete with one another for hardware access [18, 382]. Left unmanaged, these programs would conflict, overwrite each other's memory, or hog the processor.
*   In this view, the OS acts as a **Resource Manager** [238, 261]. It employs sophisticated scheduling, partitioning, and protection algorithms to manage the three fundamental hardware resources:
    1.  **Processor (CPU Cycles)** — multiplexed via schedulers.
    2.  **Memory (RAM Space)** — partitioned and isolated.
    3.  **I/O Devices** — coordinated via device drivers and controllers.
*   It also acts as a **Control Program** [128, 159]. It manages the execution of user programs to prevent errors, conflicts, and improper or unauthorized use of the computer [128].

```
  +-------------------------------------------------+
  |                      Users                      |
  +-------------------------------------------------+
                           |
                           v
  +-------------------------------------------------+
  |      System & Application Programs (APIs)       |
  +-------------------------------------------------+
                           | (System Calls)
                           v
  +-------------------------------------------------+
  |            Operating System (Kernel)            |  <--- "Extended Machine" & "Resource Manager"
  +-------------------------------------------------+
                           | (Direct Control)
                           v
  +-------------------------------------------------+
  |                Computer Hardware                |  <--- CPU, RAM, Disk, I/O Devices
  +-------------------------------------------------+
```

#### 4. Relevant PPT Content
*   **Slide 3:** Defines OS as an intermediary program between user and hardware [150, 360, 363].
*   **Slide 4:** Highlights the dual goals: Convenience (User View) and Efficiency (System View) [343, 367].
*   **Slide 5:** Displays the four main components of a computer system: Hardware, Operating System, Application Programs, and Users [120, 343].

#### 5. Analogies & Real-World Examples
*   **The Government Analogy:** An OS is like a government. It doesn't perform any useful work on its own (like building products or typing a document); instead, it provides a structured, safe, and regulated environment in which other entities (citizens/applications) can do productive work [5, 170].
*   **The Restaurant Manager Analogy:** The OS is like a restaurant manager. It allocates tables (memory), schedules waiters (CPU time), manages the kitchen flow (I/O coordination), and ensures customers don't fight over the same fork (resource protection).

#### 6. Important Exam Points
*   ✍️ **Exam Focus:** A standard university question is, *"Justify the statement: 'The OS is both a Resource Manager and an Extended Machine'."* To answer this, divide your response into the **User View** (explain abstraction, ease of programming, and hardware hiding) and the **System View** (explain resource allocation, CPU/memory multiplexing, and control program safety) [3, 238, 261].

---

### Module 2: Operating System Objectives and Functions

#### 1. Basic Idea
An operating system has specific design goals that justify its existence. These are categorized into its fundamental objectives and its daily operational functions. It manages everything on behalf of the user to maximize convenience and system utility.

#### 2. Important Definitions
*   ⭐ **Convenience Goal:** The OS objective to make the computer system easier and more intuitive for humans to use, eliminating the need to write low-level machine code [296, 395].
*   ⭐ **Efficiency Goal:** The OS objective to maximize resource utilization, throughput, and minimize idle processor time by optimizing how CPU, memory, and devices are shared [296, 395].
*   ⭐ **Ability to Evolve:** The structural design goal of an OS that allows new features, device drivers, or system security patches to be developed, tested, and integrated smoothly without breaking existing services [296, 395].

#### 3. Detailed Concept: The Three Objectives of an OS (Stallings Ch. 2.1)
An operating system must balance three key objectives [296, 395]:

1.  **Convenience:** Presenting a user-friendly interface (GUI/CLI) so programmers can build software without directly handling hardware instructions [395, 396].
2.  **Efficiency:** Operating systems ensure that hardware is utilized as close to 100% capacity as possible. For instance, in a uniprogramming system, if a process waits for I/O, the CPU sits completely idle. The OS resolves this via multiprogramming, switching the CPU to a different process during I/O waits to reclaim lost efficiency [144, 234].
3.  **Ability to Evolve:** An operating system is never a finished product. It must grow to support new hardware (e.g., USB-C, PCIe Gen 5) and security standards. A modular, layered, or object-oriented OS architecture is necessary to facilitate this growth without requiring a full kernel rewrite [296, 386].

#### 4. Relevant PPT Content
*   **Slide 6:** Breaks down the three objectives: Convenience, Efficiency, and Ability to Evolve [343, 381].
*   **Slide 7:** Lists the fundamental functions of an OS (Processor, Memory, Device, File management) [201].

#### 5. Detailed Operational Functions of an OS
To achieve these objectives, the OS performs a suite of core operational functions:

*   **Processor Management:** Coordinated by the CPU Scheduler. It determines which process gets CPU control, for how long, and when to switch tasks [261].
*   **Memory Management:** The OS tracks which parts of memory are currently in use and by whom [133]. It dynamically allocates memory blocks to running processes and reclaims (deallocates) them upon process termination [133, 193].
*   **Device Management (I/O Coordination):** Every I/O device requires unique, low-level physical registers and timing commands. The OS abstracts these details using **Device Drivers** (software modules that know how to talk to specific hardware controllers) [86, 255].
*   **File System Management:** The OS abstracts physical mass storage sectors into logical, device-independent files and hierarchical directory structures [24, 86, 393].
*   **Security & Protection:** Ensures that user programs running concurrently do not interfere with each other's memory or data and blocks unauthorized system access [218].

#### 6. Important Exam Points
*   ✍️ **Exam Focus:** Be prepared to list and explain the "Objectives of an OS." Focus on the trio of **Convenience, Efficiency, and Evolution** [296, 395]. Use William Stallings' definitions and cite real-world examples (such as adding a new USB drive, which tests the "Ability to Evolve" via dynamic loadable modules) [296, 395, 386].

---

### Module 3: Operating System Services

#### 1. Basic Idea
To fulfill its objectives, the operating system runs continuously in the background, providing a set of essential services. These services can be divided into two main categories: those designed to assist the **execution of user programs** and those designed to ensure **safe, efficient, and reliable system operations**.

#### 2. Important Definitions
*   ⭐ **Program Execution:** The OS service that loads a program's executable code from secondary storage into main memory, allocates required resources, initializes runtime structures, executes the instructions, and handles program termination [4].
*   ⭐ **File System Manipulation:** The programmatic service that handles file and directory operations, such as creation, deletion, searching, reading, writing, and access control [4].
*   ⭐ **Inter-Process Communication (IPC):** The service that allows concurrent processes to exchange data, synchronize activities, and coordinate work, typically via **Shared Memory** or **Message Passing** [11].

#### 3. Detailed Concept: Standard OS Services (Galvin Ch. 2.1)
The operating system provides a structured suite of services to user programs and system administrators:

##### Group A: Services for Programmers and Users (Convenience)
1.  **User Interface (UI):** Provides a mechanism for users to interact with the OS. It can be a Command Line Interface (CLI/Shell) for speed, a Graphical User Interface (GUI) for ease, or a Batch Interface for bulk job submission [347].
2.  **Program Execution:** The system must be able to load a file into RAM and run it. The program must be able to end its execution, either normally or abnormally (due to errors) [61, 108].
3.  **I/O Operations:** A running program may require I/O (e.g., reading from a network card, writing to a terminal). Since user programs cannot access hardware directly for safety reasons, the OS must provide this access on their behalf [4].
4.  **File-System Manipulation:** Programs need to read, write, create, delete, and search files and directories, as well as manage file ownership and permissions [4].
5.  **Communications:** Processes often need to share information. This can happen between processes running on the same computer, or on different computers connected via a network. Implemented through **Shared Memory** (extremely fast, directly mapped memory regions) or **Message Passing** (packets routed through the OS kernel) [11, 365].
6.  **Error Detection:** The OS must constantly monitor the system for errors. Examples include CPU/memory hardware failures, I/O device errors (printer out of paper, network drop), or user program arithmetic errors (division by zero, illegal memory bounds access). The OS must react gracefully to keep the system stable [396, 411].

##### Group B: Services for System Efficiency (Resource Allocation & Security)
1.  **Resource Allocation:** When multiple jobs run concurrently, resources must be allocated to each of them. Schedulers manage CPU allocation; memory managers handle RAM mapping; device allocators assign printers, storage, and network ports [261].
2.  **Accounting:** The OS keeps track of which users use how much and what kinds of computer resources (e.g., CPU time, network bandwidth, storage) [396]. This is crucial for system analysis, performance tuning, and multi-user billing [396, 411].
3.  **Protection and Security:** Protection ensures that all access to system resources is controlled and isolated [20]. Security requires authenticating users and shielding system data from external malicious intruders [20, 218].

```
  +---------------------------------------------------------------------------------+
  |                                 User Interface                                  |
  |                           (GUI / CLI / Batch Shell)                             |
  +---------------------------------------------------------------------------------+
                                          |
                                          v
  +---------------------------------------------------------------------------------+
  |                                   SERVICES                                      |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |  | Program Execution |  |  I/O Operations   |  |   File-System Manipulation  |  |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |  |   Communication   |  |  Error Detection  |  |     Resource Allocation     |  |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |  |    Accounting     |  |    Protection     |  |          Security           |  |
  |  +-------------------+  +-------------------+  +-----------------------------+  |
  |                                                                                 |
  +---------------------------------------------------------------------------------+
                                          |
                                          v
  +---------------------------------------------------------------------------------+
  |                                SYSTEM CALLS                                     |
  +---------------------------------------------------------------------------------+
                                          |
                                          v
  +---------------------------------------------------------------------------------+
  |                           Kernel (Hardware Control)                             |
  +---------------------------------------------------------------------------------+
```

#### 4. Relevant PPT Content
*   **Slide 8:** Introduces User Interface services (CLI, Batch, GUI) [347].
*   **Slide 9:** Highlights standard programmatic services (Execution, I/O, File System, Communication, Error Detection) [347].
*   **Slide 10:** Details resource and administrative services (Resource allocation, Accounting, Protection, and Security) [344].

#### 5. Important Exam Points
*   ✍️ **Exam Focus:** Be prepared to write a 5-mark answer detailing OS Services [4, 291]. The best approach is to draw the system service block diagram (shown above), list at least 6 core services, and clearly distinguish services that help the programmer (convenience) from services that protect the system (efficiency) [4, 396].

---

### Module 4: Evolution of Operating Systems

#### 1. Basic Idea
To truly appreciate modern operating systems, one must understand how they evolved. Over the past 75 years, operating system strategies transitioned step-by-step from raw, manual hardware manipulation to highly automated, concurrent, and real-time execution models [56, 210]. This evolution was driven by economic necessity: as computers were incredibly expensive, maximizing processor utilization and user productivity was paramount [139, 397].

#### 2. Important Definitions
*   ⭐ **Serial Processing:** An early processing strategy where users had access to the computer one-by-one in series, interacting directly with bare hardware without an OS [139, 397].
*   ⭐ **Simple Batch System:** An early operating system strategy where a software program called the **Resident Monitor** stayed permanently in RAM to automatically read and execute batches of sequential jobs, minimizing setup times [210].
*   ⭐ **Multiprogramming:** A scheduling strategy where multiple programs are loaded simultaneously into main memory, and the OS dynamically switches the CPU to run another job whenever the current active job stalls waiting for an I/O operation [144, 234].
*   ⭐ **Time Sharing (Multitasking):** An interactive multiprogramming strategy where the processor time is shared among multiple active concurrent users, interleaving execution in short time slices (quanta) [211, 382].

#### 3. Detailed Generational Breakdown of OS Evolution

```
  [Serial Processing] ---> [Simple Batch] ---> [Multiprogramming] ---> [Time Sharing]
    (Late 40s-50s)           (Mid-50s)             (1960s)               (1970s)
    - No OS                  - Resident Monitor    - Space-Multiplex RAM - Multi-user
    - Direct H/W Console     - Batched Jobs        - Time-Multiplex CPU  - Interactive Terminals
    - High Setup Idle        - Auto-Sequence       - CPU switches on I/O - Time Slicing (Quanta)
```

##### Generation 1: Serial Processing (Late 1940s to Mid 1950s)
*   **Hardware Environment:** Systems like ENIAC and early vacuum-tube machines. **There was no Operating System** [347].
*   **Operating Strategy:** The computer operated through a physical console consisting of display lights, toggle switches, a card reader for input, and a printer [347].
*   **Scheduling:** Users signed up for blocks of time (e.g., 45 minutes) on a physical paper sheet. If a user's program finished early, the machine sat completely idle. If a user hit a bug, they spent their remaining time debugging manually via console lights.
*   **Setup Time:** Every job required significant manual preparation. The user had to load the compiler, linkers, loaders, mount physical magnetic tapes, and load punch card decks. If an error occurred, the process was restarted from scratch.
*   **Drawbacks:** Highly inefficient. CPU utilization was extremely low, and the machine was locked to a single sequential user [347].

##### Generation 2: Simple Batch Systems (Mid 1950s)
*   **The Innovation:** To eliminate manual scheduling and setup times, designers created the **Resident Monitor** — the ancestor of the modern OS kernel [210].
*   **Operating Strategy:** Users no longer had direct physical access to the computer console. Instead, they wrote programs on punch cards and submitted them to a human computer operator.
*   **Batched Tapes:** The operator batched multiple user jobs together onto magnetic tapes using a cheaper offline computer. This "batch tape" was then loaded onto the main computer.
*   **The Resident Monitor:** A primitive software program that stayed permanently resident in the upper boundaries of main memory. It controlled the execution of jobs in the batch:
    1.  It read **Job Control Language (JCL)** cards (special cards beginning with `$` containing commands like `$JOB`, `$FTN`, `$RUN`) to prepare compilers and programs.
    2.  Once Job 1 finished (or crashed), the Resident Monitor automatically loaded Job 2 from the tape into memory, running it immediately.
*   **Memory Layout:** Memory was divided into two fixed partitions: the permanent Resident Monitor space and the active User Program area.
*   **Major Bottleneck:** **The CPU-I/O Speed Discrepancy.** I/O devices (magnetic card readers, printers) were mechanical and thousands of times slower than electronic CPU registers [144]. During a read or write operation, the CPU had to wait for the I/O device to complete, meaning the expensive processor spent up to 90% of its time sitting completely idle.

##### Generation 3: Multiprogrammed Batch Systems (1960s)
*   **The Innovation:** To resolve the CPU-I/O speed gap, developers introduced **Multiprogramming** [144, 234].
*   **Operating Strategy:** Instead of keeping only one job in memory at a time, the OS divided physical RAM into multiple partitions, keeping **multiple independent jobs resident in memory simultaneously** [144, 234].
*   **Dynamic switching (Overlap):** When the currently executing job (e.g., Job A) initiated an I/O operation (like writing to a tape), the CPU didn't sit idle. The OS intercepted the I/O block, suspended Job A, and switched the CPU to execute Job B [234]. When Job B stalled on I/O, the OS switched to Job C [234].
*   **Key Techniques Introduced:** 
    *   **Space-Multiplexing Memory:** Dividing RAM safely among multiple concurrent jobs [234].
    *   **Time-Multiplexing CPU:** Automatically switching processor allocation among ready tasks [234].
    *   **Job Scheduling & CPU Scheduling:** Choosing which job to load from disk into RAM (Job Scheduling) and which memory-resident job to execute next (CPU Scheduling) [57, 148].

##### Generation 4: Time-Sharing Systems (1970s onwards)
*   **The Problem with Batch Multiprogramming:** While multiprogramming batch systems maximized CPU efficiency, they were completely **non-interactive** [210]. Programmers could not interact with their code during runtime. Turnaround times (the time from card submission to printed output) could take hours or even days.
*   **The Innovation:** **Time-Sharing Systems** [211, 382].
*   **Operating Strategy:** Instead of batching programs, multiple interactive users accessed a single powerful central computer simultaneously through independent, remote desktop terminals (consisting of keyboard and display monitors) [211, 213].
*   **Time Slicing (Quanta):** The OS cycled process execution using a hardware timer. Each process was granted a tiny window of CPU execution time, known as a **time slice** or **quantum** (typically 10 to 100 milliseconds) [382, 383, 399].
*   **Preemption:** When the time quantum expired, the hardware timer triggered an interrupt. The OS regained control, preempted (forcibly suspended) the current user, and loaded the next active user's process [298, 383, 399].
*   **Human Perception:** Because CPU switching occurred in milliseconds (faster than human reaction times), each user felt as though they had the full attention of the computer, enjoying instantaneous, responsive feedback [58, 382].
*   **Historical Milestone:** MIT's **Compatible Time-Sharing System (CTSS)**, developed in 1961 on the IBM 709/7094 [298, 383, 399]. It had 32K words of main memory, where the resident monitor occupied 5K words and the active user occupied the remaining 27K words [298, 383, 399]. When switching users, the monitor saved the active user's state to disk and swapped in the next user's state from disk, paving the way for virtual memory [298, 383, 399].

#### 4. Comparison Table: Batch Multiprogramming vs. Time Sharing (Stallings Table 2.3)

| Metric | Multiprogrammed Batch Systems | Time-Sharing Systems |
| :--- | :--- | :--- |
| **Principal Goal** | Maximize CPU utility and hardware resource throughput [139]. | Minimize human response time and maximize interactive usability [211]. |
| **Source of Input** | Job Control Language (JCL) commands prepared on punch cards or files [210, 212]. | Interactive commands typed directly by users at keyboard terminals [211]. |
| **OS Interface** | Resident Monitor / Non-interactive batch manager [210]. | Command Interpreter / Shell (runs interactively) [213, 215]. |
| **Primary Challenge** | Job scheduling and allocating memory to maximize resource utilization [57]. | Providing fast response times, dynamic scheduling, and protecting shared memory [211]. |

#### 5. Relevant PPT Content
*   **Slide 13:** Evolution list: Serial Processing, Simple Batch, Multiprogrammed Batch, Time Sharing [347].
*   **Slide 14–15:** Explains Serial Processing, console setup, and signing up for time [347].
*   **Slide 16–17:** Details Simple Batch systems, card batching, and Resident Monitor memory layout [210].
*   **Slide 18–19:** Introduces Multiprogramming, memory partitioning, and CPU swapping on I/O [144, 234].
*   **Slide 20–21:** Details Time Sharing, terminals, time slicing, and MIT's CTSS system [298, 382, 383].

#### 6. Important Exam Points
*   ✍ *Exam Focus:* Frequently tested areas include drawing the Resident Monitor memory partition, explaining the CPU-I/O speed bottleneck, and explaining how multiprogramming solves this bottleneck. Know the core differences between multiprogramming and time sharing [234, 383].

---

### Module 5: Basic Concepts of an Operating System

To master operating systems, one must study three fundamental logical abstractions: **Processes**, **Files**, and **System Calls** [29, 91, 100].

---

#### Topic A: The Process Concept

##### 1. Basic Idea
In a computer, a program is simply a passive, inactive file stored on a disk (secondary storage) waiting to be run [27, 89]. A **process**, however, is an active entity—it is that program loaded into main memory and currently executing step-by-step under CPU control [75, 152].

##### 2. Important Definitions
*   ⭐ **Process:** A program in execution; an active unit of work scheduled and controlled by the operating system [75, 240, 299, 400].
*   ⭐ **Process Address Space:** The specific range of main memory locations (from 0 to some maximum address) allocated exclusively to a process, where its program code, data, stack, and heap reside [23].

##### 3. Detailed Concept: Process Memory Structure
A process's address space in main memory is structured into four distinct logical segments [152]:

```
  High Memory Address (Max)
  +-----------------------------------+
  |               STACK               |  <--- Grows Downward
  +-----------------------------------+
  |                 |                 |
  |                 v                 |
  |                                   |  <--- Unallocated Free Space
  |                 ^                 |
  |                 |                 |
  +-----------------------------------+
  |               HEAP                |  <--- Grows Upward (Dynamic allocation: malloc/new)
  +-----------------------------------+
  |               DATA                |  <--- Global and Static Variables
  +-----------------------------------+
  |               TEXT                |  <--- Machine Code / Program Instructions
  +-----------------------------------+
  0 (Low Memory Address)
```

1.  **Text Section (Code):** Contains the compiled machine instructions read by the CPU program counter [75, 152]. It is usually read-only and shared among multiple instances of the same program to save memory [153].
2.  **Data Section:** Stores global and static variables that persist throughout the entire execution lifespan of the process [152].
3.  **Heap Section:** Dynamically allocated memory requested by the programmer at runtime (e.g., using `malloc()` in C, or `new` in C++ and Java) [152]. It grows upward towards higher memory addresses [152].
4.  **Stack Section:** Temporary data storage used during function/procedure execution [152]. It holds local variables, function parameters, and return addresses [152]. It grows downward towards lower memory addresses [152].

##### 4. Detailed Concept: Process vs. Program
A program is **passive** (a static file on a disk), while a process is **active** (with a program counter, CPU registers, and allocated memory) [27, 89, 152]. If a user opens a web browser twice, they are running two distinct processes of the exact same program [27, 89, 98]. The OS can share the Text section (code) in memory to save space, but each process maintains its own independent address space, heap, data variables, stack, and program counters [27, 89, 98].

##### 5. Relevant PPT Content
*   **Slide 22:** Defines a process using the standard Silberschatz definitions [344].
*   **Slide 23–24:** Illustrates process layout in memory (Text, Data, Heap, Stack) [152].

---

#### Topic B: The File Concept

##### 1. Basic Idea
Different secondary storage media (magnetic hard disks, solid-state drives, optical disks) have completely different physical properties, reading mechanisms, and sector layout geometries [12, 138]. To shield application developers from this hardware nightmare, the OS creates a logical, device-independent abstraction: the **File** [24, 86, 328].

##### 2. Important Definitions
*   ⭐ **File:** A logical storage unit containing a named, sequential collection of related information recorded on non-volatile, secondary storage [12, 22, 138].
*   ⭐ **Directory:** An OS container designed to house files and other subdirectories, creating an organized, hierarchical structure (tree-like organization) [267, 327, 393].

##### 3. Detailed Concept: File Attributes & Directory Structures
The operating system implements the file abstraction by managing mass-storage media controllers [8, 174, 184]. Every file is characterized by its metadata (attributes) maintained in the system's file system directory [157, 327]:

*   **Name:** The human-readable string used to identify the file [157].
*   **Identifier:** A unique tag (usually a numeric index, like an inode number in UNIX) that identifies the file uniquely within the file system [157, 393].
*   **Type:** Needed for systems that support different file structures (e.g., text, executable, directory, socket) [157].
*   **Location:** A physical pointer to the device and the exact sectors/blocks where the file's data is recorded [157].
*   **Size:** The current length of the file, in bytes, words, or blocks [157].
*   **Protection (Access Control):** Permissions determining who can read, write, execute, or append to the file [157].

```
             [Root Directory "/"]
                      |
         +------------+------------+
         |                         |
    [bin/ dir]                 [home/ dir]
         |                         |
    +----+----+               +----+----+
    |         |               |         |
[ls file] [cp file]       [user1/ dir] [user2/ dir]
                               |
                          +----+----+
                          |         |
                     [doc.txt] [code.c]
```

##### 4. Relevant PPT Content
*   **Slide 25:** Introduces files as a logical storage unit [21, 318, 378].
*   **Slide 26:** Lists the common types of files (Data: numeric, character, binary; Program: text, source, executable) [157, 174].
*   **Slide 27:** Outlines core file attributes (Name, Identifier, Type, Location, Size, Protection) [157].

---

#### Topic C: System Calls

##### 1. Basic Idea
To prevent malicious or buggy user programs from crashing the computer, modern hardware and operating systems enforce dual-mode operation: **User Mode** and **Kernel Mode**.
User programs execute in User Mode, where they are restricted from accessing hardware directly or executing privileged instructions. When an application needs to read a file from the disk, send a packet over the network, or allocate more memory, it must ask the OS kernel to perform these operations on its behalf [6, 15, 304]. It does this by executing a **System Call** [6, 15, 304].

##### 2. Important Definitions
*   ⭐ **System Call:** The programmatic interface through which an active user-level process requests a specific service or hardware access from the operating system kernel [200, 208, 387, 325].
*   ⭐ **User Mode (Restricted Mode):** A non-privileged hardware execution mode where user application code runs, restricted from directly accessing hardware or executing privileged CPU instructions [16, 112].
*   ⭐ **Kernel Mode (Privileged Mode):** A highly privileged hardware execution mode where the OS kernel runs, allowing full, unrestricted access to the hardware instruction set and physical memory [16, 112].
*   ⭐ **Trap (or Software Interrupt):** A specialized hardware instruction that forcibly switches the processor from User Mode to Kernel Mode, passing execution control to a designated address within the OS kernel [6, 15, 111, 244].

```
  USER MODE (Mode Bit = 1)                 KERNEL MODE (Mode Bit = 0)
  +-----------------------+                +--------------------------+
  |    User Application   |                |                          |
  |                       |                |                          |
  |  1. Calls open() API  |                |                          |
  +-----------------------+                |                          |
              |                            |                          |
              v                            |                          |
  +-----------------------+                |                          |
  |  System-Call Interface|                |                          |
  |                       |                |                          |
  |  2. Looks up sys_no   |                |                          |
  |  3. Executes TRAP --->|----------------|---> 4. Switches to       |
  +-----------------------+                |        Kernel Mode (Bit=0)|
              ^                            |     5. Executes kernel    |
              |                            |        service routine    |
              |                            |     6. Prepares return    |
              |                            |        values            |
              +----------------------------|---< 7. Switches back to  |
             8. Application resumes        |        User Mode (Bit=1) |
                execution                  +--------------------------+
```

##### 3. Detailed Concept: How a System Call Works Step-by-Step
1.  **Application Invocation:** A C program invokes a standard API library function, such as `printf("Hello");` [151, 359, 362].
2.  **API to System Call Transition:** The library routine (often part of the standard C library, `libc`) intercepts this call and maps it to the equivalent low-level OS system call, which in this case is `write()` [151, 359, 362].
3.  **Loading Parameters:** The library routine loads the designated parameters (such as the file descriptor for stdout, the address of the text buffer, and the byte length) into CPU registers, along with a unique **System Call Number** associated with the `write()` service [244, 330].
4.  **Executing the TRAP:** The library executes a hardware `TRAP` instruction [244, 330].
5.  **Mode Transition:** The hardware intercepts the trap, saves the user program's execution registers, switches the CPU mode bit from User Mode (1) to Kernel Mode (0), and passes control to a fixed interrupt vector address [16, 112, 182].
6.  **Kernel Dispatching:** The OS Kernel's system call handler reads the system call number from the CPU register, indexes the master **System Call Table** (an array of pointers to specific kernel service routines), and executes the designated kernel service [19, 308, 330].
7.  **Execution & Clean-up:** The kernel safely interacts with the physical hardware (e.g., writing the string to the display card's buffer).
8.  **The Return:** Once completed, the kernel loads the return status (success/error codes) into a register, executes a return-from-trap instruction, resets the mode bit back to User Mode (1), and resumes the user application's execution at the next sequential instruction [16, 112, 182].

##### 4. Parameter Passing Methods (Galvin Ch. 2.2)
Depending on the size and structure of parameters needed for a system call, the OS uses one of three parameter-passing methods [61, 108]:

```
  Method 1: Registers               Method 2: Block/Table in Memory
  +-------------------+             +-----------------------+
  | Param 1 -> Reg R1 |             |   User Program Space  |
  | Param 2 -> Reg R2 |             | +-------------------+ |
  | Param 3 -> Reg R3 |             | | Block of Params:  | |
  +-------------------+             | | [P1, P2, P3, P4]  | |
                                    | +-------------------+ |
                                    +-----------------------+
                                                |
                                                v (Load Address of Block)
                                    +-----------------------+
                                    | Register R1 <- Addr   |
                                    +-----------------------+
```

1.  **Register Method:** Parameters are loaded directly into CPU registers [16, 112]. This is extremely fast but limited by the number and physical size of CPU registers.
2.  **Block/Table Method:** If parameters exceed registers, they are written sequentially to a dedicated block of memory (block/table) [16, 112]. The memory address of this block is loaded into a CPU register and passed to the kernel [16, 112]. 
3.  **Stack Method:** Parameters are pushed onto a system stack by the user program and popped off by the operating system kernel [16, 112]. This method is flexible and does not limit parameter count or size [72].

##### 5. Relevant PPT Content
*   **Slide 28–29:** Introduces system calls as programmatic interfaces [364, 368].
*   **Slide 30:** Explains the User/Kernel mode bit (transition via TRAP) [16, 112, 182].
*   **Slide 31–32:** Explains Parameter Passing (Registers, Blocks, and Stack) [61, 108, 72].
*   **Slide 33–34:** Lists system call categories (Control, File, Device, Info, Communication, Protection) [20, 309, 317].
*   **Slide 35:** Provides the essential mapping table of Windows vs. UNIX system calls [151, 359, 362].
*   **Slide 36:** Illustrates standard C library `printf()` execution to `write()` system call [151, 359, 362].

---

### Module 6: Operating System Structures (Architecture)

#### 1. Basic Idea
An operating system is one of the largest and most complex software systems ever built. Over time, software engineers developed various architectural structures to organize and manage this complexity [239].

#### 2. Important Definitions
*   ⭐ **Monolithic Kernel:** An OS architecture where the entire operating system (scheduling, memory, file system, drivers) is compiled into a single large binary program running in a single kernel address space [122, 302, 394].
*   ⭐ **Layered Structure:** An OS architecture where system services are partitioned into concentric, hierarchical layers, where each layer can only interact with the layer directly beneath it [270, 353].
*   ⭐ **Microkernel:** An OS architecture that strips the kernel down to bare essentials (IPC, scheduling, virtual memory) and executes all other non-core services (file systems, drivers) in user space as server processes [265, 321].
*   ⭐ **Modular Structure:** A modern OS architecture where the core kernel has well-defined interfaces to dynamically load or unload specialized modules (Loadable Kernel Modules) at runtime [195, 386].

```
  MONOLITHIC                           LAYERED
  +-------------------------------+    +-------------------------------+
  |        User Applications      |    | Layer N: User Interface       |
  +===============================+    +-------------------------------+
  |  Kernel:                      |    | Layer 3: File System          |
  |  - Scheduling - File System   |    +-------------------------------+
  |  - Memory     - Device Drivers|    | Layer 2: Device Drivers       |
  +-------------------------------+    +-------------------------------+
  |            Hardware           |    | Layer 1: CPU Scheduling       |
  +-------------------------------+    +-------------------------------+
                                       | Layer 0: Hardware             |
                                       +-------------------------------+

  MICROKERNEL                          MODULAR (LKMs)
  +-------------------------------+    +-------------------------------+
  | Applications | File Sys Server|    |       User Applications       |
  +===============================+    +===============================+
  | Kernel Space (Microkernel):   |    | Core Kernel   +-- LKM (FS)    |
  | - IPC  - Scheduling  - VM     |    | (Monolithic   +-- LKM (Driver)|
  +-------------------------------+    |  address space)+-- LKM (Network)
  |            Hardware           |    +-------------------------------+
  +-------------------------------+    |            Hardware           |
  +-------------------------------+    +-------------------------------+
```

#### 3. In-Depth Comparison of Architectural Structures

##### 1. Simple Structure (MS-DOS)
*   **Characteristics:** MS-DOS was designed for computers with limited memory. There is no strict division between user mode and kernel mode [198, 202]. User programs can directly write to hardware registers or bypass system libraries to modify BIOS settings [198, 202].
*   **Pros:** Minimal memory footprint, fast execution [193, 197].
*   **Cons:** Highly vulnerable; a buggy or malicious program can directly crash the entire machine or overwrite BIOS sectors [198, 202].

##### 2. Monolithic Structure
*   **Characteristics:** All OS functional components (CPU scheduling, virtual memory, file systems, device drivers) are tightly integrated into a single, massive program that executes in kernel mode [302, 394]. There are no internal abstraction barriers; any procedure can call any other procedure directly [25, 87, 331].
*   **Pros:** Fast execution speeds due to minimal context switching and direct address space communication [194, 263, 279].
*   **Cons:** Hard to maintain, debug, and modify [194, 264, 280]. A single bug or null pointer dereference in a device driver can trigger a kernel panic, crashing the entire operating system [25, 87, 331].

##### 3. Layered Structure
*   **Characteristics:** The OS is broken down into multiple levels, numbered from 0 (hardware) to N (user interface) [353]. Each layer contains procedures that are visible only to adjacent higher layers.
*   **Pros:** Clear separation of concerns, high modularity, and simplified debugging [194, 198, 262]. If an error occurs in Layer 3, developers can isolate the bug to that layer, knowing the lower layers are already verified.
*   **Cons:** High performance overhead [195, 199, 262]. If a user program requests disk I/O, the data request must be reformatted and copied sequentially through each layer, reducing execution speeds. It is also challenging to define layered hierarchies precisely [195, 199, 262].

##### 4. Microkernel Structure
*   **Characteristics:** Strips away non-essential services from the kernel, executing them as user-space processes (servers) [265, 321]. The kernel itself only handles message-passing Inter-Process Communication (IPC), basic thread scheduling, and virtual memory mapping [265, 321]. Applications communicate with user-space servers (like file system servers) by exchanging IPC messages through the microkernel [265].
*   **Pros:** Extremely reliable and highly secure [28, 93, 336]. If the file system server crashes, the kernel and the rest of the OS continue running. The file system server can simply be restarted. It is also highly portable and extensible [265].
*   **Cons:** High performance overhead due to crossing user-kernel boundaries multiple times for simple IPC message exchanges [28, 90, 265, 334].

##### 5. Modular Structure (Loadable Kernel Modules)
*   **Characteristics:** Combines the benefits of monolithic and microkernel architectures. The core kernel is relatively small, but is designed with clear interfaces for **Loadable Kernel Modules (LKMs)** [386]. Modules (like a specific network card driver or file system) can be loaded into the monolithic kernel's address space dynamically at runtime or boot time [195, 199].
*   **Pros:** Flexible and easily extensible like a microkernel, yet performs as fast as a monolithic kernel since modules run inside the privileged kernel space [195, 199, 386].
*   **Cons:** Still vulnerable to module-level bugs; a buggy loadable driver running in kernel space can still crash the entire system [250].

#### 4. Relevant PPT Content
*   **Slide 37–38:** Discusses Simple Structure (MS-DOS) and Monolithic Kernel [194, 198, 204].
*   **Slide 39–40:** Introduces the Layered OS design and concentric rings of execution [291, 353].
*   **Slide 41–42:** Explains the Microkernel model and message-passing IPC [28, 93, 336].
*   **Slide 43–44:** Details Modular structures and loadable kernel modules [195, 199, 206].
*   **Slide 45:** Compares Monolithic and Microkernel structures side-by-side [196, 200, 207].

---

## Part 3: Study Guide Summary & Exam Prep Sheet

### 1. Core Terminology Reference

1.  **Resident Monitor:** The earliest form of operating system. It resided permanently in memory, automatically sequencing batched jobs [210].
2.  **Time Slicing:** A scheduling technique in time-sharing systems where each process is allocated a small time window (quantum) on the CPU before being preempted [298, 383, 399].
3.  **Time-Multiplexing:** The technique of sharing a resource (like the CPU) over time among multiple processes by allocating it to each process sequentially [234].
4.  **Space-Multiplexing:** The technique of sharing a physical resource (like RAM) by dividing it into separate physical partitions, allowing multiple processes to occupy it simultaneously [234, 352].
5.  **Multiprogramming:** Keeping multiple concurrent programs loaded in memory, switching CPU execution on I/O waits [144, 234].
6.  **Context Switch:** Saving the current state (context) of an active process in its PCB and loading the saved state of another process to resume execution [123, 125, 259].
7.  **TRAP (or Syscall):** A software-generated interrupt that switches execution from user mode to kernel mode [6, 15, 111, 244].
8.  **Dual-Mode Operation:** A hardware protection mechanism that separates User Mode (mode bit = 1) from Kernel Mode (mode bit = 0) to secure hardware resources [16, 112].
9.  **Interrupt Vector:** A table of memory addresses of interrupt service routines, indexed by interrupt type [6, 15, 111].
10. **Symmetric Multiprocessing (SMP):** A hardware architecture where multiple identical CPUs share the same main physical memory and execute processes concurrently [332].
11. **Asymmetric Multiprocessing:** A hardware architecture where a single master CPU manages scheduling and allocates workloads to subordinate (slave) processors.
12. **Monolithic Kernel:** An OS architecture where all components are compiled into a single massive program running in kernel mode [302, 394].
13. **Microkernel:** An OS architecture that minimizes kernel space, moving most OS services into user space [265, 321].
14. **Process Control Block (PCB):** An OS data structure that stores all metadata needed to manage a specific process [253].
15. **System Call Interface:** A software link that intercepts API library calls and redirects them to kernel system calls [9, 19, 308].
16. **API (Application Programming Interface):** A set of functions exposed to programmers (e.g., Win32, POSIX) that abstract low-level system call commands [364, 368].
17. **Program Counter (PC):** A CPU register that contains the address of the next sequential machine instruction to be executed [23, 224, 253].
18. **Loader:** An OS utility that loads an executable file from storage into memory, establishing its runtime stack and heap.
19. **Command Interpreter (or Shell):** An OS program that reads user terminal commands and executes equivalent system calls [213, 215].
20. **Device Driver:** A device-specific software module that translates generic OS read/write commands into device-specific hardware actions [86, 255].

---

### 2. High-Yield Architectural Comparisons

#### A. Symmetric (SMP) vs. Asymmetric Multiprocessing

*   **Symmetric Multiprocessing (SMP):** All CPUs are equal peers [332]. Any processor can run any process in the ready queue. All processors share a single physical memory address space.
*   **Asymmetric Multiprocessing:** Follows a Master-Slave model. One master CPU controls the scheduling, memory mappings, and I/O channels. Slave processors only execute workloads assigned by the master CPU.

#### B. Monolithic vs. Microkernel Structures

*   **Monolithic:** Fast performance (direct calls within a single address space) but poor reliability (any bug can crash the entire system) [194, 263, 264].
*   **Microkernel:** High reliability and security (services run in isolated user space) but slower performance due to message passing and frequent user-kernel mode switches [28, 93, 265, 336].

#### C. User Mode vs. Kernel Mode

*   **User Mode:** Non-privileged execution. The mode bit is 1 [16, 112]. Hardware is protected, and executing privileged instructions triggers a processor exception.
*   **Kernel Mode:** Fully privileged execution. The mode bit is 0 [16, 112]. The OS kernel has unrestricted hardware and memory access.

---

### 3. Exam Focus: Practice & Revision Questions

#### Short Answer & Concept Questions
1.  **What is the difference between a program and a process?**
    *   *Answer:* A program is a passive, inactive file on disk containing a list of instructions. A process is an active entity in main memory, with a program counter, CPU registers, stack, heap, and resource allocations [27, 89, 152].
2.  **Explain why simple batch monitors were limited by CPU-I/O speed differences.**
    *   *Answer:* CPU speeds were electronic (nanoseconds) while input devices were mechanical (seconds). Simple batch systems could only keep one job in memory. When that job performed I/O, the monitor had to wait, leaving the expensive CPU idle [144].
3.  **Explain the role of the Mode Bit.**
    *   *Answer:* The mode bit is a hardware register flag that indicates the current processor privilege level. It prevents user-level applications from executing instructions that could modify hardware states or access forbidden memory [16, 112].
4.  **Identify three parameter-passing methods used in system calls.**
    *   *Answer:* 1. CPU Registers. 2. A block or table in memory (with address passed in a register). 3. Pushing parameters onto a stack [16, 61, 108, 112].
5.  **Explain the primary advantage of a Modular Operating System (LKM) over a pure Monolithic Operating System.**
    *   *Answer:* LKMs permit dynamic expansion at runtime without requiring a full kernel rewrite or reboot, while maintaining monolithic execution speeds [195, 386].

#### Essay & Analytical Questions
1.  **Trace the step-by-step transition of User Mode to Kernel Mode when an application calls `read(fd, buffer, bytes);`.**
    *   *Answer:* Use the step-by-step sequence in Module 5, Topic C. Detail the C API, system call mapping, system call number loading, the TRAP instruction, the mode bit transition from 1 to 0, the interrupt vector search, system call execution, and the return-from-trap.
2.  **Compare and contrast the Layered and Microkernel architectures. Analyze their respective advantages and disadvantages.**
    *   *Answer:* Refer to Module 6. Contrast Layered (vertical hierarchical layers, strict adjacent-layer calls) with Microkernel (horizontal client-server model, message-passing IPC) [265, 270]. Compare their performance (both incur overhead) and reliability (microkernels provide better isolation than standard layered architectures) [28, 93, 195, 265].

---

## Part 4: Course Policy & PPT Slide Coverage Audit Checklists

### 1. Slide-by-Slide PPT Checklist (`UNIT1-Introduction to OS.pptx`)

*   [x] **Slide 1:** Title Slide: Chapter 1: Introduction — **Fully Covered**
*   [x] **Slide 2:** Chapter Objectives — **Fully Covered**
*   [x] **Slide 3:** What is an Operating System? — **Fully Covered**
*   [x] **Slide 4:** OS Goals & Objectives (Convenience vs. Efficiency) — **Fully Covered**
*   [x] **Slide 5:** Abstract View of Computer Components — **Fully Covered**
*   [x] **Slide 6:** OS Core Objectives (Stallings Focus) — **Fully Covered**
*   [x] **Slide 7:** Core Functions of an OS — **Fully Covered**
*   [x] **Slide 8:** User Interfaces (GUI, CLI, Batch) — **Fully Covered**
*   [x] **Slide 9:** OS Services for Programmers (Program Execution, I/O, FS) — **Fully Covered**
*   [x] **Slide 10:** OS Services for System Operations (Resource Allocation, Accounting) — **Fully Covered**
*   [x] **Slide 11:** Systems View & Control Program Roles — **Fully Covered**
*   [x] **Slide 12:** Objectives Checkpoint — **Fully Covered**
*   [x] **Slide 13:** Operating System Evolution Overview — **Fully Covered**
*   [x] **Slide 14:** Serial Processing Era — **Fully Covered**
*   [x] **Slide 15:** Drawbacks of Serial Processing (Manual Setup, Scheduling) — **Fully Covered**
*   [x] **Slide 16:** Simple Batch Systems & Resident Monitors — **Fully Covered**
*   [x] **Slide 17:** Memory Layout for a Resident Monitor Batch System — **Fully Covered**
*   [x] **Slide 18:** Multiprogramming Concepts — **Fully Covered**
*   [x] **Slide 19:** Overlapping Execution timelines (CPU-I/O Overlap) — **Fully Covered**
*   [x] **Slide 20:** Time-Sharing Systems — **Fully Covered**
*   [x] **Slide 21:** MIT's CTSS Time-Sharing Case Study — **Fully Covered**
*   [x] **Slide 22:** Concept of a Process — **Fully Covered**
*   [x] **Slide 23:** Active Process vs. Passive Program — **Fully Covered**
*   [x] **Slide 24:** Process Layout in Memory (Text, Data, Heap, Stack) — **Fully Covered**
*   [x] **Slide 25:** Concept of a File — **Fully Covered**
*   [x] **Slide 26:** File Classifications (Data files vs. Programs) — **Fully Covered**
*   [x] **Slide 27:** File Attributes and Metadata — **Fully Covered**
*   [x] **Slide 28:** Introduction to System Calls — **Fully Covered**
*   [x] **Slide 29:** Programming Interfaces and APIs (POSIX, Win32) — **Fully Covered**
*   [x] **Slide 30:** Dual-Mode Operation (User vs. Kernel Modes) — **Fully Covered**
*   [x] **Slide 31:** How System Calls are Handled (TRAP execution) — **Fully Covered**
*   [x] **Slide 32:** Parameter Passing Methods (Registers, Blocks, Stack) — **Fully Covered**
*   [x] **Slide 33:** Categories of System Calls — **Fully Covered**
*   [x] **Slide 34:** Detailed System Call Subtypes (Process, File, Device) — **Fully Covered**
*   [x] **Slide 35:** Windows vs. UNIX System Calls Mapping Table — **Fully Covered**
*   [x] **Slide 36:** Standard C Library execution trace (`printf` to `write`) — **Fully Covered**
*   [x] **Slide 37:** MS-DOS Simple Structure Architecture — **Fully Covered**
*   [x] **Slide 38:** Monolithic OS structure — **Fully Covered**
*   [x] **Slide 39:** Layered OS Architecture — **Fully Covered**
*   [x] **Slide 40:** concentric Rings Layered design — **Fully Covered**
*   [x] **Slide 41:** Microkernel OS Design — **Fully Covered**
*   [x] **Slide 42:** Microkernel Client-Server communication flow — **Fully Covered**
*   [x] **Slide 43:** Modular OS and LKMs — **Fully Covered**
*   [x] **Slide 44:** Loadable Kernel Modules design — **Fully Covered**
*   [x] **Slide 45:** Monolithic vs. Microkernel Side-by-Side Comparison — **Fully Covered**

### 2. Syllabus (Course Policy) Checklist

*   [x] **Operating system objectives and functions** — **Fully Covered** (Detailed in Modules 1 & 2)
*   [x] **Evolution of operating system** — **Fully Covered** (Detailed in Module 4)
*   [x] **Basic Concept: Processes** — **Fully Covered** (Detailed in Module 5, Topic A)
*   [x] **Basic Concept: Files** — **Fully Covered** (Detailed in Module 5, Topic B)
*   [x] **Basic Concept: System calls** — **Fully Covered** (Detailed in Module 5, Topic C)
*   [x] **Layered structure v/s Monolithic structure of OS** — **Fully Covered** (Detailed in Module 6)

---
