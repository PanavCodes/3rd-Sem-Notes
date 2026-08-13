# Unit 2 Operating Systems: CPU Scheduling Numericals Master Guide
**Course Policy Mapping:** Unit 2 (Process and Process Scheduling - CPU Scheduling Algorithms)  
**Primary Course Sources:** `UNIT2-process.pptx`, `ANS_Final-Exam_Operating Systems(702CO1C002)_Semester V_2024-2025.pdf`, `Operating_System__Sem-V__Year_2022-23__Special_Re_Exam_GF1XGRiPQ3.pdf`

---

## 📘 SECTION 1: MASTER NUMERICAL METHODOLOGY & EQUATIONS

To solve any uniprocessor CPU scheduling numerical correctly in a university exam, you must first memorize the core definitions, formulas, and scheduling metrics.

### 1.1 Key Performance Metrics & Equations
These formulas are universal and do not change regardless of the scheduling algorithm being used:

1. **Completion Time ($CT$):** The absolute wall-clock time at which a process completes its execution burst and exits the CPU.
2. **Turnaround Time ($TAT$):** The total time a process spends in the system from arrival to completion.
   $$\mathbf{TAT = CT - AT}$$
3. **Waiting Time ($WT$):** The total time a process spends waiting in the ready queue before getting CPU service.
   $$\mathbf{WT = TAT - BT}$$
   *Alternatively (for preemptive algorithms with multiple execution gaps)*:
   $$WT = \text{Total duration of all waiting intervals in Ready Queue}$$
4. **Response Time ($RT$):** The elapsed time from when a process first arrives in the ready queue to the moment it gets the CPU for the first time.
   $$\mathbf{RT = \text{First CPU Start Time} - AT}$$
5. **Average Averages:**
   $$\text{Average Waiting Time (AWT)} = \frac{\sum WT}{\text{Number of Processes}}$$
   $$\text{Average Turnaround Time (ATAT)} = \frac{\sum TAT}{\text{Number of Processes}}$$

---

### 1.2 Step-by-Step Problem-Solving Approach
When presented with a CPU scheduling table under exam conditions, always follow this rigorous execution sequence:
1. **Analyze the Protocol Rules:** Check if the algorithm is **Preemptive** (running jobs can be forcibly interrupted by newcomers) or **Non-Preemptive** (once scheduled, jobs run to completion uninterrupted).
2. **Confirm Priority Orientation:** For Priority problems, verify if smaller integers mean higher priority (e.g., nice levels where Priority $1 > 5$) or if larger integers mean higher priority (standard in some systems). *Unless explicitly stated otherwise, standard academic exams use smaller values for higher priority*.
3. **Draft the Chronological Decision Timeline:** Draw an empty timeline. Run a mental clock starting at $t = 0$. At each step, list which processes have arrived ($AT \le t$) and are still incomplete.
4. **Construct the Ready Queue:** Track which processes are in the Ready state. For Round Robin, maintain a formal First-In, First-Out (FIFO) queue, strictly appending preempted processes *behind* newly arrived processes at the exact same tick.
5. **Draw the Gantt Chart:** Fill in execution blocks chronologically. Ensure each segment represents:
   $$\text{Block Length} = \text{Duration of Continuous CPU Service}$$
6. **Determine Completion Times ($CT$):** Read the completion boundaries from your Gantt chart left-to-right.
7. **Calculate $TAT$, $WT$, and $RT$ Row-by-Row:** Fill in the columns process-by-process, explaining each mathematical subtraction to prevent arithmetic slip-ups.
8. **Double-Check Your Math:** Ensure that:
   $$\sum BT = \text{End Time of Gantt Chart} - \text{Total CPU Idle Time}$$

---

## 🧮 SECTION 2: WORKED NUMERICALS (STEP-BY-STEP SOLUTIONS)

---

### 2.1 First-Come, First-Served (FCFS) Scheduling

#### 📝 Problem 1: FCFS with Arrivals & The Convoy Effect
* **Source:** `UNIT2-process.pptx` Slide 12-13 / `CPU-Scheduling-and-Algorithm- (1) (1).pdf` Example 3
* **Question Text:** *Consider the processes $P_1, P_2, P_3, P_4$ given in the below table, arriving for execution in the same order, with given Arrival Time and Burst Time. Illustrate scheduling, draw the Gantt chart, and calculate Turnaround and Waiting times.*
| Process | Arrival Time (AT) | Burst Time (BT) |
| :---: | :---: | :---: |
| **$P_1$** | 0 | 8 |
| **$P_2$** | 1 | 4 |
| **$P_3$** | 2 | 9 |
| **$P_4$** | 3 | 5 |

##### 🧠 How to Approach this Problem:
1. **Identify Algorithm:** First-Come, First-Served (FCFS). This is **non-preemptive**.
2. **Scheduling Rule:** The process that requests the CPU first (earliest Arrival Time) is served first.
3. **Execution Steps:**
   * At $t = 0$: $P_1$ has arrived. Since no other process is ready, $P_1$ takes the CPU and runs for its full burst of 8 ms (from $t = 0 \to 8$).
   * At $t = 8$: $P_1$ completes. During its run, $P_2, P_3, P_4$ have all arrived in the Ready Queue. Since FCFS is non-preemptive, we schedule them strictly in order of arrival: $P_2 \to P_3 \to P_4$.
   * $P_2$ runs from $t = 8 \to 12$.
   * $P_3$ runs from $t = 12 \to 21$.
   * $P_4$ runs from $t = 21 \to 26$.

##### 📊 Gantt Chart:
```
+------------------------+-------+---------------------------+---------------+
|           P1           |  P2   |            P3             |      P4       |
+------------------------+-------+---------------------------+---------------+
0                        8      12                          21              26
```

##### 📋 Row-by-Row Value Derivation:
* **$P_1$:**
  * **$CT$:** Finished execution at **8 ms** (read directly from Gantt Chart).
  * **$TAT$:** $CT - AT = 8 - 0 = \mathbf{8\text{ ms}}$.
  * **$WT$:** $TAT - BT = 8 - 8 = \mathbf{0\text{ ms}}$.
  * **$RT$:** Got CPU first at 0 ms. $0 - AT = 0 - 0 = \mathbf{0\text{ ms}}$.
* **$P_2$:**
  * **$CT$:** Finished execution at **12 ms**.
  * **$TAT$:** $CT - AT = 12 - 1 = \mathbf{11\text{ ms}}$.
  * **$WT$:** $TAT - BT = 11 - 4 = \mathbf{7\text{ ms}}$.
  * **$RT$:** Got CPU first at 8 ms. $8 - AT = 8 - 1 = \mathbf{7\text{ ms}}$.
* **$P_3$:**
  * **$CT$:** Finished execution at **21 ms**.
  * **$TAT$:** $CT - AT = 21 - 2 = \mathbf{19\text{ ms}}$.
  * **$WT$:** $TAT - BT = 19 - 9 = \mathbf{10\text{ ms}}$.
  * **$RT$:** Got CPU first at 12 ms. $12 - AT = 12 - 2 = \mathbf{10\text{ ms}}$.
* **$P_4$:**
  * **$CT$:** Finished execution at **26 ms**.
  * **$TAT$:** $CT - AT = 26 - 3 = \mathbf{23\text{ ms}}$.
  * **$WT$:** $TAT - BT = 23 - 5 = \mathbf{18\text{ ms}}$.
  * **$RT$:** Got CPU first at 21 ms. $21 - AT = 21 - 3 = \mathbf{18\text{ ms}}$.

##### 📝 Complete Calculation Table:
| Process | Arrival Time (AT) | Burst Time (BT) | Priority | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) | Response Time (RT) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 8 | - | 8 | 8 | 0 | 0 |
| **$P_2$** | 1 | 4 | - | 12 | 11 | 7 | 7 |
| **$P_3$** | 2 | 9 | - | 21 | 19 | 10 | 10 |
| **$P_4$** | 3 | 5 | - | 26 | 23 | 18 | 18 |
| **Total** | - | **26** | - | - | **61 ms** | **35 ms** | **35 ms** |

##### 🧮 Compute Averages:
* **Average Waiting Time (AWT):**
  $$\text{AWT} = \frac{0 + 7 + 10 + 18}{4} = \frac{35}{4} = \mathbf{8.75\text{ ms}}$$
* **Average Turnaround Time (ATAT):**
  $$\text{ATAT} = \frac{8 + 11 + 19 + 23}{4} = \frac{61}{4} = \mathbf{15.25\text{ ms}}$$

---

### 2.2 Shortest Job First (SJF) [Non-Preemptive]

#### 📝 Problem 2: SJF with Varying Arrival Times
* **Source:** `B136_OS_Exp-4.pdf` Task 2 Problem 1 / `Exp4 SJF.docx`
* **Question Text:** *Accept the list of processes: Process ID, Arrival Time, Burst Time. Sort processes by Arrival Time. For each process calculate Completion, Turnaround, and Waiting Times using Shortest Job First (SJF) algorithm.*
| Process | Arrival Time (AT) | Burst Time (BT) |
| :---: | :---: | :---: |
| **$P_1$** | 2 | 4 |
| **$P_2$** | 4 | 2 |
| **$P_3$** | 5 | 1 |
| **$P_4$** | 10 | 3 |

##### 🧠 How to Approach this Problem:
1. **Identify Algorithm:** Shortest Job First (SJF), non-preemptive.
2. **Scheduling Rule:** Select the arrived process with the shortest burst time. If there is a tie, use FCFS (earliest arrival).
3. **Execution Steps:**
   * **At $t = 0 \to 2$:** No processes have arrived. The CPU is **IDLE** for 2 ms.
   * **At $t = 2$:** $P_1$ arrives with $BT = 4$. Since it is the only process, it executes immediately and runs to completion (runs $2 \to 6$ ms).
   * **At $t = 6$:** $P_1$ completes. During its execution, $P_2$ (arrived at 4, $BT=2$) and $P_3$ (arrived at 5, $BT=1$) have entered the ready queue.
   * **SJF Decision Point ($t=6$):** Compare bursts of ready processes: $P_3 (BT=1)$ vs. $P_2 (BT=2)$. Since $P_3$ has the shorter burst, **select $P_3$**. $P_3$ runs from $t = 6 \to 7$ ms.
   * **At $t = 7$:** $P_3$ completes. The ready queue contains only $P_2 (BT=2)$. $P_4$ has not arrived yet ($AT=10$). Schedule $P_2$, which runs from $t = 7 \to 9$ ms.
   * **At $t = 9 \to 10$:** Ready queue is empty. The CPU is **IDLE** for 1 ms.
   * **At $t = 10$:** $P_4$ arrives with $BT = 3$. It executes immediately, running from $t = 10 \to 13$ ms.

##### 📊 Gantt Chart:
```
+--------+--------------------+-------+-------+--------+---------------+
|  IDLE  |         P1         |  P3   |  P2   |  IDLE  |      P4       |
+--------+--------------------+-------+-------+--------+---------------+
0        2                    6       7       9       10              13
```

##### 📋 Row-by-Row Value Derivation:
* **$P_1$:**
  * **$CT$:** Completed at **6 ms** (read directly from Gantt Chart).
  * **$TAT$:** $CT - AT = 6 - 2 = \mathbf{4\text{ ms}}$.
  * **$WT$:** $TAT - BT = 4 - 4 = \mathbf{0\text{ ms}}$.
  * **$RT$:** First started at 2 ms. $2 - AT = 2 - 2 = \mathbf{0\text{ ms}}$.
* **$P_2$:**
  * **$CT$:** Completed at **9 ms**.
  * **$TAT$:** $CT - AT = 9 - 4 = \mathbf{5\text{ ms}}$.
  * **$WT$:** $TAT - BT = 5 - 2 = \mathbf{3\text{ ms}}$.
  * **$RT$:** First started at 7 ms. $7 - AT = 7 - 4 = \mathbf{3\text{ ms}}$.
* **$P_3$:**
  * **$CT$:** Completed at **7 ms**.
  * **$TAT$:** $CT - AT = 7 - 5 = \mathbf{2\text{ ms}}$.
  * **$WT$:** $TAT - BT = 2 - 1 = \mathbf{1\text{ ms}}$.
  * **$RT$:** First started at 6 ms. $6 - AT = 6 - 5 = \mathbf{1\text{ ms}}$.
* **$P_4$:**
  * **$CT$:** Completed at **13 ms**.
  * **$TAT$:** $CT - AT = 13 - 10 = \mathbf{3\text{ ms}}$.
  * **$WT$:** $TAT - BT = 3 - 3 = \mathbf{0\text{ ms}}$.
  * **$RT$:** First started at 10 ms. $10 - AT = 10 - 10 = \mathbf{0\text{ ms}}$.

##### 📝 Complete Calculation Table:
| Process | Arrival Time (AT) | Burst Time (BT) | Priority | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) | Response Time (RT) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **$P_1$** | 2 | 4 | - | 6 | 4 | 0 | 0 |
| **$P_2$** | 4 | 2 | - | 9 | 5 | 3 | 3 |
| **$P_3$** | 5 | 1 | - | 7 | 2 | 1 | 1 |
| **$P_4$** | 10 | 3 | - | 13 | 3 | 0 | 0 |
| **Total** | - | **10** | - | - | **14 ms** | **4 ms** | **4 ms** |

##### 🧮 Compute Averages:
* **Average Waiting Time (AWT):**
  $$\text{AWT} = \frac{0 + 3 + 1 + 0}{4} = \frac{4}{4} = \mathbf{1.0\text{ ms}}$$
* **Average Turnaround Time (ATAT):**
  $$\text{ATAT} = \frac{4 + 5 + 2 + 3}{4} = \frac{14}{4} = \mathbf{3.5\text{ ms}}$$
* **Total CPU Idle Time:**
  $$\text{Idle Time} = \text{Gap } (0 \to 2) + \text{Gap } (9 \to 10) = 2\text{ ms} + 1\text{ ms} = \mathbf{3\text{ ms}}$$

---

### 2.3 Shortest Remaining Time First (SRTF / Preemptive SJF)

#### 📝 Problem 3: SRTF with Frequent Preemptions
* **Source:** `UNIT2-process.pptx` Slide 15 / `B136_OS_Exp-4.pdf` Task 2 Problem 2
* **Question Text:** *Consider processes $P_1, P_2, P_3, P_4$ with Arrival Time and Burst Time. Draw the preemptive SJF Gantt chart and calculate average Waiting and Turnaround times.*
| Process | Arrival Time (AT) | Burst Time (BT) |
| :---: | :---: | :---: |
| **$P_1$** | 0 | 8 |
| **$P_2$** | 1 | 4 |
| **$P_3$** | 2 | 9 |
| **$P_4$** | 3 | 5 |

##### 🧠 How to Approach this Problem:
1. **Identify Algorithm:** Shortest Remaining Time First (SRTF), which is the **preemptive** version of SJF.
2. **Scheduling Rule:** At every arrival or completion event, compare the remaining burst times of all ready processes. Select the one with the smallest remaining burst time. If there is a tie, use FCFS (earliest arrival).
3. **Decision-by-Decision Selection Walkthrough:**
   * **At $t = 0$:** Only **$P_1$** has arrived (remaining $BT = 8$). It starts running.
   * **At $t = 1$:** **$P_2$** arrives with $BT = 4$.
     * *Remaining $BT$ for $P_1$* $= 8 - 1 = 7$.
     * *Compare remaining:* $P_2 (BT=4)$ vs. $P_1 (\text{rem}=7)$.
     * *Decision:* $P_2$'s burst is shorter ($4 < 7$). **Preempt $P_1$ and schedule $P_2$**.
   * **At $t = 2$:** **$P_3$** arrives with $BT = 9$.
     * *Remaining $BT$ for $P_2$* $= 4 - 1 = 3$.
     * *Compare remaining:* $P_2 (3)$ vs. $P_1 (7)$ vs. $P_3 (9)$.
     * *Decision:* $P_2$ has the shortest remaining time. **Continue executing $P_2$**.
   * **At $t = 3$:** **$P_4$** arrives with $BT = 5$.
     * *Remaining $BT$ for $P_2$* $= 3 - 1 = 2$.
     * *Compare remaining:* $P_2 (2)$ vs. $P_4 (5)$ vs. $P_1 (7)$ vs. $P_3 (9)$.
     * *Decision:* $P_2$ remains shortest. **Continue executing $P_2$**.
   * **At $t = 5$:** $P_2$ finishes its remaining 2 ms burst and completes.
     * *Compare remaining:* $P_4 (5)$ vs. $P_1 (7)$ vs. $P_3 (9)$.
     * *Decision:* $P_4 (BT=5)$ is shortest. **Schedule $P_4$** (runs from $5 \to 10$ ms).
   * **At $t = 10$:** $P_4$ completes execution.
     * *Compare remaining:* $P_1 (\text{rem}=7)$ vs. $P_3 (BT=9)$.
     * *Decision:* $P_1 (7)$ is shorter. **Schedule $P_1$** (runs from $10 \to 17$ ms).
   * **At $t = 17$:** $P_1$ completes execution.
     * *Only $P_3$ remains* (remaining $BT = 9$). **Schedule $P_3$** (runs from $17 \to 26$ ms).
   * **At $t = 26$:** $P_3$ completes. All jobs completed.

##### 📊 Gantt Chart:
```
+-----+---------------+-----------+---------------------+-----------------------+
| P1  |      P2       |    P4     |         P1          |          P3           |
+-----+---------------+-----------+---------------------+-----------------------+
0     1               5          10                    17                      26
```

##### 📋 Row-by-Row Value Derivation:
* **$P_1$:**
  * **$CT$:** Read directly from Gantt Chart. $P_1$ finally finishes execution at **17 ms**.
  * **$TAT$:** $CT - AT = 17 - 0 = \mathbf{17\text{ ms}}$.
  * **$WT$:** $TAT - BT = 17 - 8 = \mathbf{9\text{ ms}}$.
  * **$RT$:** First got the CPU at $t = 0$. $0 - AT = 0 - 0 = \mathbf{0\text{ ms}}$.
* **$P_2$:**
  * **$CT$:** Finishes execution at **5 ms**.
  * **$TAT$:** $CT - AT = 5 - 1 = \mathbf{4\text{ ms}}$.
  * **$WT$:** $TAT - BT = 4 - 4 = \mathbf{0\text{ ms}}$.
  * **$RT$:** First got CPU at $t=1$. $1 - AT = 1 - 1 = \mathbf{0\text{ ms}}$.
* **$P_3$:**
  * **$CT$:** Finishes execution at **26 ms**.
  * **$TAT$:** $CT - AT = 26 - 2 = \mathbf{24\text{ ms}}$.
  * **$WT$:** $TAT - BT = 24 - 9 = \mathbf{15\text{ ms}}$.
  * **$RT$:** First got CPU at $t=17$. $17 - AT = 17 - 2 = \mathbf{15\text{ ms}}$.
* **$P_4$:**
  * **$CT$:** Finishes execution at **10 ms**.
  * **$TAT$:** $CT - AT = 10 - 3 = \mathbf{7\text{ ms}}$.
  * **$WT$:** $TAT - BT = 7 - 5 = \mathbf{2\text{ ms}}$.
  * **$RT$:** First got CPU at $t=5$. $5 - AT = 5 - 3 = \mathbf{2\text{ ms}}$.

##### 📝 Complete Calculation Table:
| Process | Arrival Time (AT) | Burst Time (BT) | Priority | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) | Response Time (RT) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 8 | - | 17 | 17 | 9 | 0 |
| **$P_2$** | 1 | 4 | - | 5 | 4 | 0 | 0 |
| **$P_3$** | 2 | 9 | - | 26 | 24 | 15 | 15 |
| **$P_4$** | 3 | 5 | - | 10 | 7 | 2 | 2 |
| **Total** | - | **26** | - | - | **52 ms** | **26 ms** | **17 ms** |

##### 🧮 Compute Averages:
* **Average Waiting Time (AWT):**
  $$\text{AWT} = \frac{9 + 0 + 15 + 2}{4} = \frac{26}{4} = \mathbf{6.5\text{ ms}}$$
* **Average Turnaround Time (ATAT):**
  $$\text{ATAT} = \frac{17 + 4 + 24 + 7}{4} = \frac{52}{4} = \mathbf{13.0\text{ ms}}$$

---

### 2.4 Priority Scheduling

#### 📝 Problem 4: Preemptive Priority Scheduling (University Exam Blueprint)
* **Source:** `QP_Final-Exam_Operating Systems(702CO1C002)_Semester V_2024-2025.pdf` Q1b, `unit2-pyq-bank.md` Problem 1 Part I
* **Question Text:** *Given this batch of processes with arrival times, burst times, and priorities (where lower priority numbers indicate higher priority): Calculate average Turnaround Time (TAT) and average Waiting Time (WT) using Preemptive Priority Scheduling.*
| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
| :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 10 | 2 |
| **$P_2$** | 1 | 4 | 1 |
| **$P_3$** | 3 | 7 | 3 |
| **$P_4$** | 4 | 6 | 2 |
| **$P_5$** | 6 | 5 | 0 |

##### 🧠 How to Approach this Problem:
1. **Identify Algorithm:** Preemptive Priority Scheduling.
2. **Key Rule:** At any arrival or completion event, the running process is preempted if a newly arrived process has a strictly higher priority (lower priority number).
3. **Tie-Breaker:** FCFS (earliest arrival time).
4. **Decision-by-Decision Selection Walkthrough:**
   * **At $t = 0$:** Only **$P_1$** has arrived (PR=2). It starts executing.
   * **At $t = 1$:** **$P_2$** arrives with $PR = 1$.
     * *Compare priorities:* $P_2 (PR=1)$ vs. $P_1 (PR=2)$.
     * *Decision:* $P_2$ has higher priority. **Preempt $P_1$ and execute $P_2$**.
     * *Remaining $BT$ for $P_1$* $= 10 - 1 = 9$ ms.
   * **During $t = 1 \to 5$:** $P_2$ executes.
     * At $t = 3$, $P_3$ (PR=3) arrives. Since $PR=3 < P_2(PR=1)$, $P_3$ waits.
     * At $t = 4$, $P_4$ (PR=2) arrives. It also waits since $PR=2 < P_2(PR=1)$.
     * At $t = 5$, $P_2$ completes its 4 ms burst and terminates.
   * **At $t = 5$:** Compare ready processes: $P_1$ (PR=2, rem=9), $P_4$ (PR=2, rem=6), $P_3$ (PR=3, rem=7).
     * *Decision:* $P_1$ and $P_4$ are tied for highest priority ($PR = 2$). FCFS tie-breaker selects **$P_1$** (arrival $0 < 4$). $P_1$ starts running.
   * **At $t = 6$:** **$P_5$** arrives with $PR = 0$.
     * *Compare priorities:* $P_5 (PR=0)$ vs. $P_1 (PR=2)$.
     * *Decision:* $P_5$ has highest priority. **Preempt $P_1$ and execute $P_5$**.
     * *Remaining $BT$ for $P_1$* $= 9 - 1 = 8$ ms.
   * **During $t = 6 \to 11$:** $P_5$ executes its full 5 ms burst uninterrupted (no process with $PR < 0$ exists) and completes at $t=11$.
   * **At $t = 11$:** Compare ready processes: $P_1$ (PR=2, rem=8), $P_4$ (PR=2, rem=6), $P_3$ (PR=3, rem=7).
     * *Decision:* $P_1$ and $P_4$ are tied ($PR = 2$). Schedule **$P_1$** (earliest arrival). $P_1$ runs from $t = 11 \to 19$, completing its remaining 8 ms burst.
   * **At $t = 19$:** Compare ready processes: $P_4$ (PR=2, rem=6) vs. $P_3$ (PR=3, rem=7).
     * *Decision:* Schedule **$P_4$** ($PR=2$). $P_4$ runs from $t = 19 \to 25$ and completes.
   * **At $t = 25$:** Only **$P_3$** (PR=3, rem=7) remains. It runs from $t = 25 \to 32$, completing at $t=32$.

##### 📊 Gantt Chart:
```
+----+---------+----+--------------+---------+---------+---------------+
| P1 |   P2    | P1 |      P5      |   P1    |   P4    |      P3       |
+----+---------+----+--------------+---------+---------+---------------+
0    1         5    6             11        19        25              32
```

##### 📋 Row-by-Row Value Derivation:
* **$P_1$:**
  * **$CT$:** Finishes final execution block at **19 ms**.
  * **$TAT$:** $CT - AT = 19 - 0 = \mathbf{19\text{ ms}}$.
  * **$WT$:** $TAT - BT = 19 - 10 = \mathbf{9\text{ ms}}$.
  * **$RT$:** First got CPU at $t = 0$. $0 - AT = 0 - 0 = \mathbf{0\text{ ms}}$.
* **$P_2$:**
  * **$CT$:** Completed at **5 ms**.
  * **$TAT$:** $CT - AT = 5 - 1 = \mathbf{4\text{ ms}}$. *(Note: Written as 4 in handwritten sheet, verified as CT-AT: 5-1=4)*.
  * **$WT$:** $TAT - BT = 4 - 4 = \mathbf{0\text{ ms}}$.
  * **$RT$:** First got CPU at $t=1$. $1 - AT = 1 - 1 = \mathbf{0\text{ ms}}$.
* **$P_3$:**
  * **$CT$:** Completed at **32 ms**.
  * **$TAT$:** $CT - AT = 32 - 3 = \mathbf{29\text{ ms}}$.
  * **$WT$:** $TAT - BT = 29 - 7 = \mathbf{22\text{ ms}}$.
  * **$RT$:** First got CPU at $t=25$. $25 - AT = 25 - 3 = \mathbf{22\text{ ms}}$.
* **$P_4$:**
  * **$CT$:** Completed at **25 ms**.
  * **$TAT$:** $CT - AT = 25 - 4 = \mathbf{21\text{ ms}}$.
  * **$WT$:** $TAT - BT = 21 - 6 = \mathbf{15\text{ ms}}$.
  * **$RT$:** First got CPU at $t=19$. $19 - AT = 19 - 4 = \mathbf{15\text{ ms}}$.
* **$P_5$:**
  * **$CT$:** Completed at **11 ms**.
  * **$TAT$:** $CT - AT = 11 - 6 = \mathbf{5\text{ ms}}$.
  * **$WT$:** $TAT - BT = 5 - 5 = \mathbf{0\text{ ms}}$.
  * **$RT$:** First got CPU at $t=6$. $6 - AT = 6 - 6 = \mathbf{0\text{ ms}}$.

##### 📝 Complete Calculation Table:
| Process | Arrival Time (AT) | Burst Time (BT) | Priority | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) | Response Time (RT) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 10 | 2 | 19 | 19 | 9 | 0 |
| **$P_2$** | 1 | 4 | 1 | 5 | 4 | 0 | 0 |
| **$P_3$** | 3 | 7 | 3 | 32 | 29 | 22 | 22 |
| **$P_4$** | 4 | 6 | 2 | 25 | 21 | 15 | 15 |
| **$P_5$** | 6 | 5 | 0 | 11 | 5 | 0 | 0 |
| **Total** | - | **32** | - | - | **78 ms** | **46 ms** | **37 ms** |

##### 🧮 Compute Averages:
* **Average Waiting Time (AWT):**
  $$\text{AWT} = \frac{9 + 0 + 22 + 15 + 0}{5} = \frac{46}{5} = \mathbf{9.2\text{ ms}}$$
* **Average Turnaround Time (ATAT):**
  $$\text{ATAT} = \frac{19 + 4 + 29 + 21 + 5}{5} = \frac{78}{5} = \mathbf{15.6\text{ ms}}$$ *(Note: Re-verified as 15.6 ms)*

---

### 2.5 Round Robin Scheduling

#### 📝 Problem 5: Round Robin with $Time Quantum = 4$ ms (Evolving Ready Queue Tracking)
* **Source:** `QP_Final-Exam_Operating Systems(702CO1C002)_Semester V_2024-2025.pdf` Q1b, `unit2-pyq-bank.md` Problem 1 Part II
* **Question Text:** *Given this batch of processes with arrival times, burst times, and priorities (where lower priority numbers indicate higher priority): Calculate average Turnaround Time (TAT) and average Waiting Time (WT) using Round Robin Scheduling with Time Quantum = 4.*
| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
| :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 10 | 2 |
| **$P_2$** | 1 | 4 | 1 |
| **$P_3$** | 3 | 7 | 3 |
| **$P_4$** | 4 | 6 | 2 |
| **$P_5$** | 6 | 5 | 0 |

##### 🧠 How to Approach this Problem:
1. **Identify Algorithm:** Round Robin (RR) with Time Quantum $q = 4$. This is **inherently preemptive**.
2. **Scheduling Rule:** Maintain a strict FIFO queue. Schedule the process at the head for at most $q$ units.
3. **Queue Ingestion Rule (Simultaneous Events):** At the exact tick a process's time slice expires, if other processes arrive at that same tick, **the newly arrived processes are added to the Ready Queue first**, followed by the preempted running process.

##### 🔄 Step-by-Step Evolving Ready Queue Trace:
* **Clock $t = 0$:** $P_1$ arrives.
  * *Ready Queue ($RQ$):* $[P_1]$
  * *Action:* **Run $P_1$** (for $\min(BT, q) = \min(10, 4) = 4$ ms).
* **Clock $t = 1$:** $P_2$ arrives. $RQ$ absorbs $P_2 \to [P_2]$
* **Clock $t = 3$:** $P_3$ arrives. $RQ$ absorbs $P_3 \to [P_2, P_3]$
* **Clock $t = 4$:** $P_1$'s slice expires (rem BT = 6). Sibling $P_4$ arrives at $t=4$ exactly.
  * *Enqueueing Rule:* Add new arrival $P_4$ first, then append preempted $P_1$.
  * *Ready Queue ($RQ$):* $[P_2, P_3, P_4, P_1]$
  * *Action:* **Run $P_2$** (for $\min(4, 4) = 4$ ms).
* **Clock $t = 6$:** $P_5$ arrives and joins queue tail. $RQ \to [P_3, P_4, P_1, P_5]$
* **Clock $t = 8$:** $P_2$ finishes its burst and exits.
  * *Ready Queue ($RQ$):* $[P_3, P_4, P_1, P_5]$
  * *Action:* **Run $P_3$** (for $\min(7, 4) = 4$ ms).
* **Clock $t = 12$:** $P_3$'s slice expires (rem BT = 3). Append to tail.
  * *Ready Queue ($RQ$):* $[P_4, P_1, P_5, P_3]$
  * *Action:* **Run $P_4$** (for $\min(6, 4) = 4$ ms).
* **Clock $t = 16$:** $P_4$'s slice expires (rem BT = 2). Append to tail.
  * *Ready Queue ($RQ$):* $[P_1, P_5, P_3, P_4]$
  * *Action:* **Run $P_1$** (for $\min(6, 4) = 4$ ms).
* **Clock $t = 20$:** $P_1$'s slice expires (rem BT = 2). Append to tail.
  * *Ready Queue ($RQ$):* $[P_5, P_3, P_4, P_1]$
  * *Action:* **Run $P_5$** (for $\min(5, 4) = 4$ ms).
* **Clock $t = 24$:** $P_5$'s slice expires (rem BT = 1). Append to tail.
  * *Ready Queue ($RQ$):* $[P_3, P_4, P_1, P_5]$
  * *Action:* **Run $P_3$** (for its remaining burst of 3 ms).
* **Clock $t = 27$:** $P_3$ completes and exits.
  * *Ready Queue ($RQ$):* $[P_4, P_1, P_5]$
  * *Action:* **Run $P_4$** (for its remaining burst of 2 ms).
* **Clock $t = 29$:** $P_4$ completes and exits.
  * *Ready Queue ($RQ$):* $[P_1, P_5]$
  * *Action:* **Run $P_1$** (for its remaining burst of 2 ms).
* **Clock $t = 31$:** $P_1$ completes and exits.
  * *Ready Queue ($RQ$):* $[P_5]$
  * *Action:* **Run $P_5$** (for its remaining burst of 1 ms).
* **Clock $t = 32$:** $P_5$ completes and exits. All processes done.

##### 📊 Gantt Chart:
```
+----+----+----+----+----+----+----+----+----+----+
| P1 | P2 | P3 | P4 | P1 | P5 | P3 | P4 | P1 | P5 |
+----+----+----+----+----+----+----+----+----+----+
0    4    8   12   16   20   24   27   29   31   32
```

##### 📋 Row-by-Row Value Derivation:
* **$P_1$:**
  * **$CT$:** Finishes final block at **31 ms**.
  * **$TAT$:** $CT - AT = 31 - 0 = \mathbf{31\text{ ms}}$.
  * **$WT$:** $TAT - BT = 31 - 10 = \mathbf{21\text{ ms}}$.
  * **$RT$:** First got CPU at $t = 0$. $0 - AT = 0 - 0 = \mathbf{0\text{ ms}}$.
* **$P_2$:**
  * **$CT$:** Finishes at **8 ms**.
  * **$TAT$:** $CT - AT = 8 - 1 = \mathbf{7\text{ ms}}$.
  * **$WT$:** $TAT - BT = 7 - 4 = \mathbf{3\text{ ms}}$.
  * **$RT$:** First got CPU at $t=4$. $4 - AT = 4 - 1 = \mathbf{3\text{ ms}}$.
* **$P_3$:**
  * **$CT$:** Finishes at **27 ms**.
  * **$TAT$:** $CT - AT = 27 - 3 = \mathbf{24\text{ ms}}$.
  * **$WT$:** $TAT - BT = 24 - 7 = \mathbf{17\text{ ms}}$.
  * **$RT$:** First got CPU at $t=8$. $8 - AT = 8 - 3 = \mathbf{5\text{ ms}}$.
* **$P_4$:**
  * **$CT$:** Finishes at **29 ms**.
  * **$TAT$:** $CT - AT = 29 - 4 = \mathbf{25\text{ ms}}$.
  * **$WT$:** $TAT - BT = 25 - 6 = \mathbf{19\text{ ms}}$.
  * **$RT$:** First got CPU at $t=12$. $12 - AT = 12 - 4 = \mathbf{8\text{ ms}}$.
* **$P_5$:**
  * **$CT$:** Finishes at **32 ms**.
  * **$TAT$:** $CT - AT = 32 - 6 = \mathbf{26\text{ ms}}$.
  * **$WT$:** $TAT - BT = 26 - 5 = \mathbf{21\text{ ms}}$.
  * **$RT$:** First got CPU at $t=20$. $20 - AT = 20 - 6 = \mathbf{14\text{ ms}}$.

##### 📝 Complete Calculation Table:
| Process | Arrival Time (AT) | Burst Time (BT) | Priority | Completion Time (CT) | Turnaround Time (TAT) | Waiting Time (WT) | Response Time (RT) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **$P_1$** | 0 | 10 | 2 | 31 | 31 | 21 | 0 |
| **$P_2$** | 1 | 4 | 1 | 8 | 7 | 3 | 3 |
| **$P_3$** | 3 | 7 | 3 | 27 | 24 | 17 | 5 |
| **$P_4$** | 4 | 6 | 2 | 29 | 25 | 19 | 8 |
| **$P_5$** | 6 | 5 | 0 | 32 | 26 | 21 | 14 |
| **Total** | - | **32** | - | - | **113 ms** | **81 ms** | **30 ms** |

##### 🧮 Compute Averages:
* **Average Waiting Time (AWT):**
  $$\text{AWT} = \frac{21 + 3 + 17 + 19 + 21}{5} = \frac{81}{5} = \mathbf{16.2\text{ ms}}$$
* **Average Turnaround Time (ATAT):**
  $$\text{ATAT} = \frac{31 + 7 + 24 + 25 + 26}{5} = \frac{113}{5} = \mathbf{22.6\text{ ms}}$$

---

## 💡 SECTION 3: EXAM CRASH COURSE SECTIONS

Each of the worked numerical problems above contains a specific set of critical insights you should memorize prior to stepping into your exams.

---

### SJF [Non-Preemptive] Exam Review:
* ⭐ **Formulas:**
  $$\text{Next Burst SJF Decision} = \min(BT_i \text{ for all arrived } AT_i \le t)$$
* 🧠 **Problem-solving approach:** Check arrival boundaries first. Do not schedule a shorter job if it has not arrived yet when the CPU becomes free.
* ⚡ **Shortcut/Trick:** Since this is non-preemptive, once a process is scheduled, you can instantly add its full burst to get the next clock tick without checking intermediate arrivals.
* ⚠️ **Common mistakes:** Bypassing arrival times and scheduling the absolute shortest job in the table at $t=0$, even if it only arrives at a later time.
* ✍️ **Exam-writing method:** Draw a horizontal list representing the active processes in the Ready Queue at each completion boundary to justify your choice.

---

### SRTF [Preemptive SJF] Exam Review:
* ⭐ **Formulas:**
  $$\text{SRTF Next Decision} = \min(\text{Remaining } BT_i \text{ for all } AT_i \le t)$$
* 🧠 **Problem-solving approach:** Check the remaining burst of the running process at *every* tick a new process arrives.
* ⚡ **Shortcut/Trick:** If a newly arrived process has a burst time larger than the remaining burst of the running process, you can safely skip preemption checks and run the process until the next arrival event.
* ⚠️ **Common mistakes:** Forgetting to decrement the remaining burst time of the preempted process when updating the scheduling queue.
* ✍️ **Exam-writing method:** Document each preemption point explicitly (e.g., *"At $t=1$, $P_2$ arrives with $BT=4$, preempting $P_1$ which has 7 ms remaining"*).

---

### Priority Scheduling Exam Review:
* ⭐ **Formulas:**
  $$\text{Highest Priority Selection} = \min(PR_i \text{ for } AT_i \le t \text{ where smaller value } = \text{higher priority})$$
* 🧠 **Problem-solving approach:** Track priority levels dynamically. If a preempted job gets to run again, make sure to resolve ties using arrival order (FCFS).
* ⚡ **Shortcut/Trick:** Group jobs with identical priority levels together and treat them as an FCFS block when no higher-priority processes exist.
* ⚠️ **Common mistakes:** Assuming larger priority numbers mean higher priority without reading the question instructions, or forgetting to resolve priority ties with FCFS arrival times.
* ✍️ **Exam-writing method:** Highlight the FCFS tie-breaker rule clearly in your text if two active processes have the same priority level.

---

### Round Robin Exam Review:
* ⭐ **Formulas:**
  $$\text{Allotted Run Slice} = \min(\text{Remaining } BT, q)$$
* 🧠 **Problem-solving approach:** Always write out the Ready Queue explicitly step-by-step. It is the single most important tool to avoid context ordering mistakes.
* ⚡ **Shortcut/Trick:** If a process finishes before its quantum expires, the next process starts immediately (do not leave the CPU idle or wait for the quantum to finish).
* ⚠️ **Common mistakes:** Appending the preempted running process *before* newly arrived processes that arrive at that exact same tick.
* ✍️ **Exam-writing method:** Draw the evolving queue list $[P_a, P_b, \dots]$ underneath each section of your Gantt chart to demonstrate execution tracking.

---

## 📊 SECTION 4: QUICK REVISION SHEET

| Scheduling Algorithm | Preemptive? | Core Decision Rule | FCFS Arrival Tie-Breaker? | Best Suited For | Key Starvation Risk | Primary Advantage |
| :--- | :---: | :--- | :---: | :--- | :--- | :--- |
| **FCFS** | **No** | Earliest Arrival Time ($AT$) | Yes (PID) | Batch Systems | None | Simplest to implement |
| **SJF (Non-Preemptive)** | **No** | Smallest execution Burst Time ($BT$) | Yes | Batch/Long jobs | Yes (Long jobs) | Minimizes average waiting time |
| **SRTF (Preemptive SJF)** | **Yes** | Smallest remaining burst time | Yes | Interactive systems | Yes (Long jobs) | Mathematically optimal AWT |
| **Priority Scheduling** | **Both** | Highest assigned priority | Yes | Real-Time/Critical | Yes (Low priority) | Guarantees critical task run |
| **Round Robin (RR)** | **Yes** | Cyclic FIFO with fixed Time Quantum ($q$) | Yes | Interactive/Time-Sharing | None | Excellent Response Time |

---

### **University Examination Cheat-Sheet Checklist**
* [x] **Completion Time ($CT$)** read directly from Gantt chart boundary.
* [x] **Turnaround Time ($TAT$)** calculated using $CT - AT$.
* [x] **Waiting Time ($WT$)** calculated using $TAT - BT$.
* [x] **Response Time ($RT$)** calculated using $\text{First CPU Start Time} - AT$.
* [x] **Tie-breakers** applied consistently (FCFS arrival order, then numerical Process ID order).
