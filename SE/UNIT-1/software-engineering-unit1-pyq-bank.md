# Software Engineering – Unit 1 Previous Year Question (PYQ) Bank

This document compiles, groups, and answers every Previous Year Question (PYQ) from university final exams, re-exams, and internal tests related strictly to **Unit 1: Importance of Software Engineering, Legacy Software, and Software Myths**. 

---

## Part 1: Topic-Wise PYQ Analysis & Statistics

### 1. Topic-Wise PYQ Frequency
The following table shows the frequency of exam questions across the three primary syllabus divisions of Unit 1, based on NMIMS B.Tech (Computer/IT) and Re-Exam papers (2013–2026):

| Topic | Sub-Topics Covered | Number of Occurrences | Exam Focus Level |
| :--- | :--- | :---: | :--- |
| **1. Importance of SE** | Program vs. Product, Software Deterioration, Bathtub Curve, Reliability, Categories of Software, Generic vs. Customized | 11 | 🔥 **Very High** |
| **2. Legacy Software** | Definition, Characteristics, Reasons for Retaining, Challenges of Maintenance & Evolution | 8 | 🔥 **Very High** |
| **3. Software Myths** | Management Myths (Adding People/Hardware), Customer Myths (Fuzzy Objectives/Flexibility), Practitioner Myths (Quality/Code-Only) | 7 | ⭐ **High** |

---

### 2. High-Priority Repeated Concepts
*   **Software Deterioration vs. Hardware Wear-Out (The Bathtub Curve):** This is the single most tested concept in Unit 1. It regularly appears as a 5-mark short note or a 10-mark comparison. Drawing the failure curves is **mandatory**.
*   **Legacy Software Maintenance Challenges:** This question frequently appears as a compulsory 5-mark question (Q1) in final exam papers, focusing on why legacy systems are costly and risky to evolve.
*   **Customer Myth of Software Flexibility & Cost of Change:** Tested as a statement-justification question (True/False with explanation), focusing on how the cost of accommodating changes grows exponentially over time.
*   **Generic vs. Bespoke (Customized) Software:** Tested on both the definitions and the business/revenue implications for software houses.

---

### 3. Comprehensive Unit 1 PYQ Exam Map

| Paper Name / Exam Year | Q. No. | Marks | Syllabus Mapping | Priority Class |
| :--- | :---: | :---: | :--- | :--- |
| **B.Tech Sem-V Final Exam (Dec 2025)** | Q1(a) | 5M | Legacy Software Maintenance Challenges | 🔥 **Very Important** |
| **B.Tech Sem-V Re-Exam (Feb 2025)** | Q1(a) | 5M | Software Engineering & System Reliability | ⭐ **Important** |
| **B.Tech Sem-V Final Exam (Dec 2024)** | Q1(a) | 5M | Software Deterioration vs. Hardware Wear-Out | 🔥 **Very Important** |
| **B.Tech Sem-V Re-Exam (Feb 2024)** | Q1(a) | 5M | Categories: Generic vs. Custom Software Revenue | 🔥 **Very Important** |
| **B.Tech Sem-V Final Exam (Nov 2023)** | Q3(b) | 10M | Characteristics of Software vs. Hardware | ⭐ **Important** |
| **B.Tech Sem-V Re-Exam (Jan 2023)** | Q1(a) | 5M | Customer Myth: Flexibility & Requirements Change | 🔥 **Very Important** |
| **B.Tech Sem-V Final Exam (Nov 2022)** | Q1(a) | 5M | Practitioner Myth: Quality of Running Programs | 🔥 **Very Important** |
| **B.Tech Sem-V Final Exam (Nov 2022)** | Q1(d) | 5M | Concept of Legacy Software | ⭐ **Important** |
| **B.Tech Sem-V Re-Exam (May 2017)** | Q7(a) | 4M | Characteristics of Software | 🟡 **Moderate** |
| **B.Tech Sem-V Re-Exam (Dec 2016)** | Q2(b) | 6M | Program vs. Product & Legacy Software Evolution | 🔥 **Very Important** |
| **B.Tech Sem-V Re-Exam (Dec 2014)** | Q1(a) | 5M | Need & Importance of Software Engineering | ⭐ **Important** |
| **B.Tech Sem-V Re-Exam (Dec 2014)** | Q6(a) | 10M | Categories & Application Domains of Software | 🔥 **Very Important** |
| **Saksham Internal Exams (2018)** | Short Q1 | 2M | What is software? | 🟡 **Moderate** |
| **Saksham Internal Exams (2018)** | Short Q2 | 3M | Software Characteristics vs. Other Products | 🟡 **Moderate** |
| **Saksham Internal Exams (2018)** | Short Q3 | 3M | What is the bathtub curve? | ⭐ **Important** |
| **Saksham Internal Exams (2018)** | Short Q4 | 3M | Distinguish: Program vs. Software Product | ⭐ **Important** |
| **Saksham Internal Exams (2018)** | Short Q5 | 2M | Goals of Software Engineering | 🟡 **Moderate** |
| **Saksham Internal Exams (2018)** | Long Q1 | 10M | Software Crisis: Symptoms, Causes, Solutions | ⭐ **Important** |
| **Saksham Internal Exams (2018)** | Long Q4 | 10M | Classification & Categories of Software | ⭐ **Important** |

---

## Part 2: Solved PYQ Bank (Categorized by Syllabus Topics)

---

### Category A: Importance of Software Engineering

#### Concept A.1: Software Definition, Program vs. Product, & Goals of SE

##### 1. Grouped Questions (Program vs. Software Product & Goals)
*   **Differentiate between a Program and Software.** (NMIMS Re-Exam, Dec 2016, Q2b - Part 1, 3M)
*   **Distinguish between a program and a software product.** (Saksham Exam, 2018, Short Q4, 3M)
*   **Define Software Engineering and list the goals of software engineering.** (BCA Sem-IV Exam, 2022, Q1a/b, 4M)
*   **What is software? Define software.** (Saksham Exam, 2018, Short Q1 / TechMax Q1.1.1 & Q1.2.2, 2M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slide 4 / Ch. 1 PPT)

*   **Software Definition:** 
    According to the **IEEE**, software is a collection of computer programs, procedures, rules, and associated documentation and data. It is not merely the source code itself, but the entire configuration [Slide 4].
    $$\text{Software} = \text{Programs (Code)} + \text{Documents} + \text{Data}$$
    Where:
    1.  **Programs:** Provide desired features, functions, and performance when executed [Slide 4].
    2.  **Documents:** Describing the system structure, user manuals, and tutorials to guide installation and operation [Slide 4].
    3.  **Data:** Data structures that enable the programs to adequately manipulate and process information [Slide 4].

*   **Goals of Software Engineering:**
    1.  To develop software that is **maintainable** (can evolve to meet changing customer needs) [Slide 5].
    2.  To ensure the software is **dependable** (trustworthy, safe, and secure) [Slide 5].
    3.  To optimize software **efficiency** (avoiding wasteful use of system resources such as memory and processor cycles) [Slide 5].
    4.  To achieve high **usability** (accessible, easy to learn, and understandable for its target users) [Slide 5].
    5.  To deliver quality software **on-time** and **within budget** [Slide 10].

*   **Program vs. Software Product Comparison:**

| Parameter | Program (Amateur/Individual) | Software Product (Professional) |
| :--- | :--- | :--- |
| **Primary User** | Developed for use by the creator or a local hobbyist [Slide 4]. | Intended for use by a broad market or a specific external customer [Slide 4]. |
| **Development Team** | Typically written by a single programmer or hobbyist [Slide 4]. | Developed by teams of specialists working collaboratively [Slide 6]. |
| **Documentation** | Generally undocumented, lacking operational guides. | Includes system/user documentation, manuals, and websites [Slide 4]. |
| **Quality & Lifecycle** | Minimal focus on standards; rarely maintained or upgraded. | Engineered to meet quality standards and maintained throughout its life [Slide 4]. |
| **Components** | Consists strictly of isolated source code. | Consists of an integrated configuration of programs, data structures, and docs [Slide 4]. |

---

#### Concept A.2: Software Characteristics, Deterioration, & Hardware Bathtub Curve

##### 2. Grouped Questions (Software Deterioration & bathtub Curve)
*   **How does the concept of software deterioration differ from hardware wear out, and what are the primary factors that contribute to software deterioration over time?** (NMIMS Final Exam, Dec 2024, Q1a, 5M)
*   **Explain the characteristics of the software in detail and compare with hardware.** (NMIMS Final Exam, Nov 2023, Q3b, 10M)
*   **Write a short note on: Characteristics of Software and explain the bathtub curve.** (NMIMS Re-Exam, May 2017, Q7a / Saksham Exam, 2018, Short Q2 & Q3, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 10-12 / Pressman Ch. 1, Figure 1.2)

⭐ **Must Remember:** Software does **not** wear out in the physical sense. It **deteriorates** due to the side effects of continuous modifications and upgrades [Slide 10].

*   **Characteristics of Software vs. Hardware:**
    1.  **Software is developed or engineered; it is not manufactured in the classical sense:** Although similarities exist between software development and hardware manufacturing, the processes are fundamentally different. Hardware manufacturing is loaded with production-related quality issues that are non-existent for software. Software quality is entirely established in the design, coding, and verification phases [Slide 10].
    2.  **Software doesn't "wear out":** Hardware exhibits a physical wear-out phase caused by environmental friction, temperature, dust, and vibration. Software is a logical system element and does not experience physical degradation [Slide 10].
    3.  **Software is custom-built rather than assembled from components:** While the hardware industry is highly standardized around off-the-shelf integrated circuits, most software projects are still developed "from scratch." Although the industry is moving toward component-based software reuse, custom coding remains dominant [Slide 10].

*   **Comparing Failure Curves (Deterioration vs. Wear-Out):**

    *   **Hardware Failure Curve (The Bathtub Curve):** 
        Hardware failures follow a classic "U-shaped" bathtub curve. Early in its lifecycle, hardware experiences high failures due to manufacturing defects ("infant mortality"). Once these are resolved, the failure rate stabilizes at a low, constant level for a long time. Eventually, physical parts begin to degrade, causing a steep rise in failures during the "wear-out" phase [Slide 11].
        
    *   **Software Failure Curve (Deterioration due to Change):**
        In theory, software should follow an idealized curve where failures drop rapidly during initial testing and stabilize at a flat, near-zero level forever (since software doesn't wear out).
        However, the **actual curve** of software failure is highly spiked and rises over time. This is because software undergoes constant modifications (to fix bugs, adapt to new environments, or add features). Each change introduces new, undocumented bugs and side effects. These introduce a "spike" in the failure rate. Before the curve can return to the low steady-state, another change is introduced, causing another spike. Over time, the overall baseline failure rate of the software creeps upward, representing structural deterioration [Slide 12].

📊 **Diagram Required: YES**
*   **Diagram Name:** Failure Curves for Hardware (Bathtub Curve) vs. Software Deterioration Curve.
*   **Source:** `Unit-1.pdf` Slides 11 and 12 / Pressman 9th Ed, Ch. 1, Figure 1.2.

```
       HARDWARE FAILURE CURVE (BATHTUB)             SOFTWARE FAILURE CURVE (ACTUAL VS IDEAL)
  Failure                                       Failure
   Rate ^   \                       /            Rate ^   \       /\       /\       /\
        |    \                     /                  |    \     /  \     /  \     /  \  Actual Curve
        |     \                   /                   |     \   / \  \   / \  \   / \  \ (Deterioration)
        |      \_________________/                    |      \_/___\__\_/___\__\_/___\_
        |       Infant    Wear-out                    |        \_______________________ Idealized Curve
        +----------------------------->               +----------------------------->
                     Time                                          Time (Changes)
```

---

#### Concept A.3: Software Engineering Need, System Reliability, & Software Crisis

##### 3. Grouped Questions (Need of SE & Software Crisis)
*   **Explain how software engineering practices contribute to improving system reliability. What are some key practices that directly influence the reliability of a software system?** (NMIMS Re-Exam, Feb 2025, Q1a, 5M)
*   **Why is software engineering important? Explain the need of software engineering.** (NMIMS Re-Exam, Dec 2014, Q1a, 5M)
*   **What are the symptoms of the software crisis? What factors have contributed in the making of the software crisis? What are possible solutions to the software crisis?** (Saksham Exam, 2018, Long Q1, 10M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 5, 23 & Pressman Ch. 1)

*   **Need and Importance of Software Engineering:**
    1.  **Handling Big Projects:** Large enterprise systems cannot be constructed as a series of standalone, amateur programs. Software engineering provides the structured methodology to handle large-scale projects without coordination failures [Slide 23].
    2.  **Cost Management & Predictability:** Software engineering establishes cost-estimation models to avoid massive budget overruns.
    3.  **Reducing Maintenance Overhead:** Over 60% to 80% of all software effort occurs in the maintenance phase. Applying software engineering practices during development significantly reduces future maintenance costs [Slide 24].
    4.  **Improving Quality & Reliability:** Systematic processes ensure the software is highly dependable, safe, and secure [Slide 5].

*   **System Reliability & Contributing Software Engineering Practices:**
    Reliability is the software's ability to perform its intended functions under specified conditions without failure. The key engineering practices that directly influence reliability include:
    1.  **Modularity:** Breaking the system down into small, highly cohesive, and loosely coupled components so that errors in one module do not cascade and crash the entire system [Slide 23].
    2.  **Rigorous Testing (Unit & Integration Testing):** Systematically designing test cases to uncover path, condition, and boundary errors before deployment [Slide 23].
    3.  **Formal Technical Reviews (FTRs):** Applying peer reviews as quality filters to detect logic defects early, which is significantly more cost-effective than running tests [Slide 25].
    4.  **Continuous Integration & Deployment (CI/CD):** Continuously integrating code changes and testing them in an automated manner to identify integration issues early [Slide 23].

*   **The Software Crisis (Historical Context - Birth of SE in 1968):**
    *   **Symptoms:** Projects delivered late, massive cost overruns, unreliable software that was difficult to maintain, and failure to meet the user's actual requirements [Ch. 1 Book / TechMax].
    *   **Causes:** The sudden availability of highly powerful hardware (larger memory and faster CPUs) led to a demand for larger, more complex software. Developers tried to scale up amateur coding habits ("art form") to large systems without engineering principles, leading to failure [Ch. 1 Book].
    *   **Solutions:** Moving away from individual programming styles and adopting a systematic, disciplined, and quantifiable engineering approach—forming the discipline of **Software Engineering** [Slide 10].

---

#### Concept A.4: Categories and Application Domains of Software

##### 4. Grouped Questions (Software Categories & Business Revenue)
*   **Distinguish between generic and customized software products. Which one would generate more revenue for a company? Give the reasons behind your answer.** (NMIMS Re-Exam, Feb 2024, Q1a, 5M)
*   **What are different categories of software? State example of each category.** (NMIMS Re-Exam, Dec 2014, Q6a / Saksham Exam, 2018, Long Q4, 10M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 14-22 / Ch. 1 PPT)

*   **Classification Criteria for Software (The 7 Core Dimensions):**
    According to your slide notes, software can be classified based on these criteria [Slide 14-15]:
    1.  **Purpose:** *System software* (services other programs, e.g., operating systems) vs. *Application software* (solves business needs directly).
    2.  **Platform:** *Native software* (optimized for a single OS) vs. *Cross-platform software* (runs on multiple environments).
    3.  **Deployment:** *Installed software* (on-premise device storage) vs. *Cloud-based software* (remote server, web access).
    4.  **License:** *Proprietary software* (owned by a private company) vs. *Open-source software* (source code publicly available).
    5.  **Development Model:** *Traditional software* (Waterfall model) vs. *Agile software* (iterative, adaptive Scrum/XP).
    6.  **Size:** *Small-scale software* (single user/small group) vs. *Enterprise software* (large organizations).
    7.  **User Interface:** *Graphical User Interface (GUI)* vs. *Command-Line Interface (CLI)*.

*   **11 Application-Based Categories of Software (with Examples):**

| Category | Definition / Characteristics | Examples |
| :--- | :--- | :--- |
| **1. System Software** | Collection of programs written to service other programs; manages computer resources and handles complex hardware-level interactions [Slide 16]. | Operating Systems, Compilers, File Management Utilities, Device Drivers. |
| **2. Application Software** | Standalone programs designed to solve specific business needs and interact with the user directly [Slide 17]. | Word Processors, Spreadsheets, Point-of-Sale (POS) systems. |
| **3. Networking & Web Software** | Provides support for computers to interact with each other and data stores over network backbones or web browsers [Slide 18]. | HTML, PHP, XML, Web server software, encryption packages. |
| **4. Embedded Software** | Resides in Read-Only Memory (ROM) as a part of a larger system to control features under specified conditions [Slide 18]. | Washing machine control software, automotive braking systems, microwave keypad controls. |
| **5. Reservation Software** | Used to store, retrieve, and execute transactional data related to booking, travel, and logistics. | Air travel reservation engines, hotel and car rental booking databases. |
| **6. Business Software** | Multi-user software that facilitates transactions, accounting, and organization-wide business operations. | Inventory management systems, payroll software, banking/hospital databases. |
| **7. Entertainment Software** | Software built for recreation, educational gaming, or interactive learning [Slide 19]. | Computer games, virtual mapping apps, language translators. |
| **8. Artificial Intelligence Software** | Uses non-numerical heuristic algorithms to solve highly complex, unstructured problems [Slide 19]. | Expert systems, neural networks, pattern/voice recognition software, game-playing AI. |
| **9. Scientific/Engg. Software** | Built to execute specialized "number-crunching" algorithms using specific mathematical principles of the field [Slide 20]. | MATLAB, AutoCAD, PSPICE, ORCAD. |
| **10. Utility Software** | Perform highly specific, pinpoint operational tasks; small in scale but vital for system maintenance [Slide 20]. | Anti-virus software, voice recognizers, data compression tools. |
| **11. Document Management** | Used to track, index, manage, and store virtual documents to reduce paper files; features robust version history tracking [Slide 21]. | SharePoint, Google Workspace Doc Indexers, enterprise file archives. |

*   **Generic vs. Customized (Bespoke) Software Comparison & Revenue Analysis:**

*   **Definitions:**
    *   **Generic Software:** Developed by a company to be sold on the open market to a wide range of different customers who adapt their workflow to the software (e.g., Microsoft Office) [Slide 4, 17].
    *   **Customized (Bespoke) Software:** Commissioned and developed for a specific customer under contract to meet their unique, tailored requirements (e.g., a custom military air-defense system) [Slide 4, 17].

*   **Business Revenue Generation Analysis (Which generates more revenue?):**
    *   **The Verdict:** While Customized software generates **immediate, guaranteed high-margin cash flow** per contract, **Generic Software has the potential to generate substantially higher overall revenue** for a company over time.
    *   **Reasons:**
        1.  **Market Scale & Reach:** Generic software can be sold to millions of users on the open market. Once the initial development cost is recovered, the marginal cost of reproducing and distributing additional digital licenses is nearly zero.
        2.  **Scalability:** Customized software has high coordination overhead. To scale revenue, a company must hire more engineers to work on individual client systems. Generic software scales revenue exponentially without a linear increase in staff size.
        3.  **Lock-in and Ecosystems:** Generic platforms (e.g., SaaS models) establish mass subscription models, generating highly predictable recurring revenue streams.

---

### Category B: Legacy Software

#### Concept B.1: Legacy Software Definition & Characteristics

##### 5. PYQ: Explain the concept of Legacy Software. (NMIMS Final Exam, Nov 2022, Q1d, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 31-32 / Ch. 1 PPT)

*   **Definition:** 
    According to Dayani-Fard, **legacy software systems** are older programs developed decades ago that have been continually modified to meet changes in business requirements and computing platforms. A legacy system is defined by its **superseded technology** (outdated languages, libraries, and hardware) combined with its **indispensable nature**—making it highly risky to replace because of its wide operational use [Slide 31].

*   **Core Characteristics of Legacy Software:**
    1.  **Very High Longevity (Lifetime):** These systems remain in active service for 10, 20, or even 30+ years (e.g., mainframe COBOL systems) [Slide 32].
    2.  **High Business Criticality:** They support the core business operations of the enterprise and are deemed "indispensable" [Slide 32].
    3.  **Poor Quality:** They typically exhibit inextensible architectural designs, heavily convoluted code, and obsolete programming constructs [Slide 32].
    4.  **Inadequate Documentation:** The system's specifications are either lost or have not been updated with the changes made over years of maintenance [Slide 32].
    5.  **Lack of Test Archives:** Original test cases and test suites were rarely archived, making testing after modification highly risk-prone.

---

#### Concept B.2: Reasons for Retaining Legacy Systems

##### 6. PYQ: What are the compelling reasons why organizations choose to keep legacy systems instead of replacing them? (Saksham Exam, 2018 / Ch. 1 Notes, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slide 33 / Ch. 1 PPT)

Organizations retain legacy software for five main reasons [Slide 33]:

1.  **Satisfactory Operation:** The system works satisfactorily, meets current baseline user needs, and runs reliably. If the system is not broken, managers see no rational justification to fix or replace it.
2.  **Prohibitive Replacement Costs:** The systems are extremely large and complex. Redesigning and rebuilding a modern equivalent from scratch would require massive capital investment that exceeds potential support-cost savings.
3.  **Retraining Costs and Lost Time:** Replacing a legacy system requires retraining thousands of employees on new software interfaces. The cost of this operational downtime often yields zero immediate benefits.
4.  **Near-Constant Availability Constraints:** Legacy software often powers critical, 24/7 transaction systems (e.g., bank customer accounts, airline reservation networks, air traffic control). These systems cannot be taken out of service, and designing a replacement system with equal reliability is extremely difficult.
5.  **Incomprehensible System Logic:** The inner workings of the system are not well understood. The original designers have long left the company, and the documentation has either been lost or never created. Re-specifying the system's exact functionality is therefore impossible.

---

#### Concept B.3: Challenges of Legacy Software Maintenance & Evolution

##### 7. Grouped Questions (Legacy Maintenance & Evolution)
*   **Explain challenges in maintaining Legacy software.** (NMIMS Final Exam, Dec 2025, Q1a, 5M)
*   **Why does legacy software need to be evolved? State the modes of legacy evolution.** (NMIMS Re-Exam, Dec 2016, Q2b - Part 2, 3M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 32, 34 / Ch. 1 PPT)

*   **Challenges in Maintaining Legacy Software:**
    1.  **Outdated/Obsolete Technology:** These systems rely on ancient programming languages (like COBOL, Fortran) and support software. Finding modern compilers or database connectors is extremely difficult [Passage 145].
    2.  **Lack of Documentation:** Incomplete, missing, or mismatched documentation forces maintenance programmers to treat the source code as the sole, highly complex source of truth [Passage 145].
    3.  **Scarcity of Skilled Personnel:** Younger programmers are not trained in obsolete systems. As senior developers retire, organizations face extreme talent shortages, raising maintenance costs [Passage 145].
    4.  **High Technical Debt (Convoluted Code):** Decades of quick patches and emergency fixes degrade the code's structure, introducing tight coupling and serious side effects when even minor changes are made [Passage 145].
    5.  **Integration and Security Issues:** Legacy software was developed before the internet era, making it vulnerable to modern cyber threats and difficult to interface with modern web-based databases [Passage 145].

*   **Why Legacy Software Must Evolve (The 4 Modes of Evolution):**
    Legacy systems cannot remain frozen; they must undergo changes to preserve business value. Roger Pressman outlines the four core evolutionary reasons [Slide 34]:
    1.  **Adaptation:** The software must be adapted to meet the requirements of new computing environments, such as migrating legacy databases from on-premise mainframe servers to virtualized cloud architectures.
    2.  **Enhancement:** The system must be enhanced to implement new, evolving business rules and requirements (e.g., changes in tax codes, compliance policies).
    3.  **Extension:** The software must be extended to make it interoperable with modern enterprise systems and external databases.
    4.  **Re-architecting:** The software's code and data must be re-architected to make it viable within a modern network-centric or web-based computing environment.

📊 **Diagram Required: YES**
*   **Diagram Name:** Socio-Technical System Layers of Legacy Software.
*   **Source:** `Unit-1.pdf` Slide 33 / Ch. 9 PPT.

```
+-------------------------------------------------+
|               BUSINESS PROCESSES                | (Old ways of doing business)
+-------------------------------------------------+
|              APPLICATION SOFTWARE               | (Convoluted legacy program code)
+-------------------------------------------------+
|       PLATFORM AND INFRASTRUCTURE SOFTWARE      | (Obsolete compilers, databases)
+-------------------------------------------------+
|                SYSTEM HARDWARE                  | (Mainframe, legacy interfaces)
+-------------------------------------------------+
```

---

### Category C: Software Myths

⭐ **Syllabus Rule for Myths:** For any question regarding software myths, structure the response clearly using the **Myth $\rightarrow$ Fact/Reality $\rightarrow$ Explanation $\rightarrow$ Exam Point** format [Syllabus Note].

---

#### Concept C.1: Management Myths

##### 8. PYQ: Explain the standard Management Myths and their accompanying realities. (Saksham Exam, 2018 / Ch. 1 Notes, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 36-39 / Ch. 1 PPT)

###### **Management Myth 1: The Book of Standards**
*   **Myth:** "We already have a book that's full of standards and procedures for building software. Won't that provide my people with everything they need to know?" [Slide 37].
*   **Fact / Reality:** The book of standards may exist, but it is rarely used. Practitioners are often unaware of it, and in most cases, these standards do not reflect modern agile or engineering practices. They are incomplete and fail to improve time-to-delivery [Slide 37].
*   **Explanation:** Rigid, outdated standards create unnecessary bureaucracy. Software engineering requires flexible, streamlined processes rather than heavy, unused rulebooks.
*   **Exam Point:** ✍️ **Do not rely on the mere existence of a standards document. Processes must be continuously updated and actively adopted by the team.**

###### **Management Myth 2: Adding Latest Hardware**
*   **Myth:** "My people have state-of-the-art software development tools; after all, we buy them the newest hardware and fastest computers" [Slide 38].
*   **Fact / Reality:** Having the latest workstation or PC does not guarantee quality development. Standard hardware upgrades have a low impact; instead, Computer-Aided Software Engineering (CASE) tools and design modeling tools are what drive quality and productivity [Slide 38].
*   **Explanation:** Hardware is only the physical platform. Quality software requires the intellectual modeling tools, testing frameworks, and engineering methodologies to guide development.
*   **Exam Point:** ✍️ **Hardware upgrades cannot compensate for poor software engineering methods.**

###### **Management Myth 3: Adding People to Late Projects (The Mongolian Horde)**
*   **Myth:** "If we get behind schedule, we can add more programmers and catch up" [Slide 36].
*   **Fact / Reality:** Adding programmers to a late software project makes it even later (known as **Brooks' Law**) [Slide 36].
*   **Explanation:** Unlike simple mechanical manufacturing, software development is highly communication-intensive. When new people are added, the existing productive team members must stop their work to train and onboard the newcomers. This reduces overall productivity and worsens the schedule delay.
*   **Exam Point:** ✍️ **Adding personnel to a slipping project is counterproductive. Resource scaling must be carefully planned in advance.**

###### **Management Myth 4: Complete Outsourcing Relaxation**
*   **Myth:** "If I decide to outsource the software project to a third party, I can just relax and let that firm build it" [Slide 39].
*   **Fact / Reality:** If an organization does not understand how to manage and control software projects internally, it will invariably struggle and fail when outsourcing them [Slide 39].
*   **Explanation:** An organization must possess internal requirements engineering, project tracking, and quality assurance capabilities to evaluate and guide the third-party contractor.
*   **Exam Point:** ✍️ **Outsourcing does not eliminate the need for strong internal project management.**

---

#### Concept C.2: Customer Myths

##### 9. PYQ: Consider the statement: "Software requirements continually change, but change can be easily accommodated because software is flexible." State True or False with proper justification. (NMIMS Re-Exam, Jan 2023, Q1a, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slide 41 / Ch. 1 PPT)

*   **The Verdict:** **FALSE** [Slide 41].

*   **Syllabus Formatting Mapping:**
    *   **Myth:** "Software requirements continually change, but change can be easily accommodated because software is flexible" [Slide 41].
    *   **Fact / Reality:** It is true that requirements change, but the cost and complexity of accommodating changes grow exponentially over time [Slide 41].
    *   **Explanation:**
        The cost of change is a function of the development phase in which it is introduced:
        1.  **Early Phase (Elicitation/Design):** When a requirement change is requested before design or coding has begun, the cost impact is small. It only requires modifying text or design diagrams.
        2.  **Late Phase (Construction/Testing):** If changes are requested late in the project (when the code is written, databases are structured, and integration testing is underway), the cost grows rapidly. The team must undo committed work, scrap existing design frameworks, and rewrite large sections of code—causing massive upheaval and introducing new defects.
    *   **Exam Point:** ✍️ **The flexibility of software is a double-edged sword. Late-stage changes cause severe schedule delays and budget overruns.**

```
       EXPONENTIAL COST OF REQUIREMENT CHANGE OVER THE LIFECYCLE
  Cost of
  Change ^                                            / (Testing/Deployment)
         |                                           /  Cost grows exponentially!
         |                                          /
         |                                         /
         |                                  ______/ (Construction)
         |                          _______/
         |                 ________/ (Design)
         |  ______________/ (Requirements)
         +------------------------------------------------------------->
                              Project Timeline
```

---

#### Concept C.3: Practitioner’s Myths

##### 10. PYQ: Consider the statement: "Until the software developer gets the program 'running' there is no way of assessing its quality." State True or False with proper justification. (NMIMS Final Exam, Nov 2022, Q1a, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slide 44 / Ch. 1 PPT)

*   **The Verdict:** **FALSE** [Slide 44].

*   **Syllabus Formatting Mapping:**
    *   **Myth:** "Until I get the program 'running' I have no way of assessing its quality" [Slide 44].
    *   **Fact / Reality:** One of the most effective software quality assurance mechanisms can be applied from the very inception of a project—the **Formal Technical Review (FTR)** [Slide 44].
    *   **Explanation:**
        Quality is not checked solely by running tests on executable code. Technical reviews serve as highly effective "quality filters." 
        1.  **Early Detection:** FTRs systematically evaluate work products (such as requirements specifications, database schemas, and architectural drawings) before any code is written.
        2.  **Greater Effectiveness:** Industry data shows that reviews are highly effective for catching architectural, design, and logic defects. Catching a bug during a requirements review is up to 100 times cheaper than fixing it after the code has been written and executed.
    *   **Exam Point:** ✍️ **Static reviews are highly effective quality filters that must be applied throughout the lifecycle, long before dynamic testing.**

##### 11. PYQ: State the common Practitioner's Myths regarding deliverables and documentation, and explain their realities. (Saksham Exam, 2018 / Ch. 1 Notes, 5M)

##### Answer (Authoritative Reference: `Unit-1.pdf` Slides 43, 45-46 / Ch. 1 PPT)

###### **Practitioner Myth 1: Code is the Only Successful Deliverable**
*   **Myth:** "The only deliverable work product for a successful project is the working program" [Slide 45].
*   **Fact / Reality:** A working program is only one part of a complete software configuration. The configuration must include design documents, models, test cases, configuration data, and user manuals to provide guidance and software support [Slide 45].
*   **Explanation:** Without documentation and maintenance records, the system becomes a black box that cannot be debugged, updated, or integrated.
*   **Exam Point:** ✍️ **The final deliverable is a complete, well-documented software configuration, not just an executable file.**

###### **Practitioner Myth 2: Software Engineering Causes Slowdowns**
*   **Myth:** "Software engineering will make us create voluminous and unnecessary documentation and will invariably slow us down" [Slide 46].
*   **Fact / Reality:** Software engineering is not about pushing paper; it is about creating a high-quality product. Better quality reduces **rework**, which results in significantly faster delivery times [Slide 46].
*   **Explanation:** When software is built without engineering discipline, developers spend up to 50% of their time fixing and rewriting broken code. Engineering practices prevent these errors early, avoiding expensive rework and accelerating delivery.
*   **Exam Point:** ✍️ **Quality prevents rework. Reduced rework leads to faster delivery.**

---

## Part 3: Exhaustive Syllabus Compliance & Verification Audit

### 1. Slide-by-Slide Syllabus Coverage Checklist (`Unit-1.pdf` - All 48 Slides)

To ensure no exam-relevant detail from your primary lecture material is missed, here is the verified slide-by-slide checklist mapping all 48 slides to their coverage status in this question bank:

| Slide # | Slide Content / Topic | Coverage Status | Mapping in Solved PYQ Bank |
| :---: | :--- | :---: | :--- |
| **1** | Title Slide: Introduction to Software Engineering | **Fully Covered** | Header Information |
| **2** | Note: supporting material only, refer textbooks | **Fully Covered** | Header disclaimers |
| **3** | Introduction: What is software? What is SE? | **Fully Covered** | Solved Question 1 |
| **4** | What is software? Programs and associated documentation | **Fully Covered** | Solved Question 1 |
| **5** | Attributes of good software: Maintainability, Dependability, Efficiency, Usability | **Fully Covered** | Solved Question 1 (Goals of SE) |
| **6** | Attributes of good software: functionality, performance | **Fully Covered** | Solved Question 1 & 3 |
| **7** | Some Software Characteristics: developed/engineered, not manufactured | **Fully Covered** | Solved Question 2 |
| **8** | Software doesn't wear out in the same sense as hardware | **Fully Covered** | Solved Question 2 |
| **9** | Theory: software does not wear out; Hardware/software upgrades | **Fully Covered** | Solved Question 2 |
| **10** | Reality is more like this (spikes due to changes) | **Fully Covered** | Solved Question 2 (Software failure curve) |
| **11** | Failure curve for hardware (Bathtub curve) | **Fully Covered** | Solved Question 2 (Hardware failure curve) |
| **12** | Software failure curve showing spikes | **Fully Covered** | Solved Question 2 (Software deterioration curve) |
| **13** | Key Principles of SE: Maintenance, Testing, Design Patterns, Agile, CI/CD | **Fully Covered** | Solved Question 3 |
| **14** | Categories of Software: Purpose, Platform, Deployment, License | **Fully Covered** | Solved Question 4 (7 criteria) |
| **15** | Categories of Software: Model, Size, UI | **Fully Covered** | Solved Question 4 (7 criteria) |
| **16** | Types of Software: System Software, Application, Web, Embedded, AI, etc. | **Fully Covered** | Solved Question 4 (11 categories) |
| **17** | System Software & Application Software definitions | **Fully Covered** | Solved Question 4 (11 categories) |
| **18** | Networking & Web Applications Software, Embedded Software | **Fully Covered** | Solved Question 4 (11 categories) |
| **19** | Embedded Software, Entertainment Software, AI Software | **Fully Covered** | Solved Question 4 (11 categories) |
| **20** | Scientific Software, Utility Software | **Fully Covered** | Solved Question 4 (11 categories) |
| **21** | Document Management Software | **Fully Covered** | Solved Question 4 (11 categories) |
| **22** | Based on Copyright: Commercial, Shareware, Freeware, Public Domain | **Fully Covered** | Solved Question 4 (Copyright matrix) |
| **23** | Legacy Software: definition and Dayani-Fard description | **Fully Covered** | Solved Question 5 (Legacy Software) |
| **24** | Characteristics of Legacy Software: Longevity, Business criticality, etc. | **Fully Covered** | Solved Question 5 (Legacy Software) |
| **25** | Organizations have compelling reasons for keeping legacy systems | **Fully Covered** | Solved Question 6 (Retaining Legacy) |
| **26** | Detailed list of 5 reasons for keeping legacy systems | **Fully Covered** | Solved Question 6 (Retaining Legacy) |
| **27** | Maintenance problems: outdated technology, poor documentation | **Fully Covered** | Solved Question 7 (Maintenance challenges) |
| **28** | Maintenance problems: lack of skilled people, high technical debt | **Fully Covered** | Solved Question 7 (Maintenance challenges) |
| **29** | Why must it change? Adaptation, enhancement, extension, re-architecting | **Fully Covered** | Solved Question 7 (Modes of evolution) |
| **30** | Software Myths Introduction: affect managers, customers, practitioners | **Fully Covered** | Solved Questions 8, 9, 10, 11 |
| **31** | Management Myths: Myth 1 (Standards book) | **Fully Covered** | Solved Question 8 (Myth 1) |
| **32** | Management Myths: Myth 1 Reality | **Fully Covered** | Solved Question 8 (Myth 1) |
| **33** | Management Myths: Myth 2 (Latest hardware) | **Fully Covered** | Solved Question 8 (Myth 2) |
| **34** | Management Myths: Myth 2 Reality | **Fully Covered** | Solved Question 8 (Myth 2) |
| **35** | Management Myths: Myth 3 (Adding people) | **Fully Covered** | Solved Question 8 (Myth 3) |
| **36** | Management Myths: Myth 3 Reality | **Fully Covered** | Solved Question 8 (Myth 3) |
| **37** | Management Myths: Myth 4 (Outsourcing) | **Fully Covered** | Solved Question 8 (Myth 4) |
| **38** | Management Myths: Myth 4 Reality | **Fully Covered** | Solved Question 8 (Myth 4) |
| **39** | Customer Myths Introduction | **Fully Covered** | Solved Question 9 |
| **40** | Customer Myths: Myth 1 (General statement of intent) | **Fully Covered** | Solved Question 8 (Customer Myth 1) |
| **41** | Customer Myths: Myth 1 Reality | **Fully Covered** | Solved Question 8 (Customer Myth 1) |
| **42** | Customer Myths: Myth 2 (Flexibility/change) | **Fully Covered** | Solved Question 9 (Customer Myth 2) |
| **43** | Customer Myths: Myth 2 Reality | **Fully Covered** | Solved Question 9 (Customer Myth 2) |
| **44** | Practitioner's Myths: Myth 1 (Work done after code works) | **Fully Covered** | Solved Question 11 (Practitioner Myth 1) |
| **45** | Practitioner's Myths: Myth 1 Reality | **Fully Covered** | Solved Question 11 (Practitioner Myth 1) |
| **46** | Practitioner's Myths: Myth 2 (Assess quality when running) | **Fully Covered** | Solved Question 10 (Practitioner Myth 2) |
| **47** | Practitioner's Myths: Myth 2 Reality | **Fully Covered** | Solved Question 10 (Practitioner Myth 2) |
| **48** | Practitioner's Myths: Myth 3 (Working program is only deliverable) | **Fully Covered** | Solved Question 11 (Practitioner Myth 3) |

---

### 2. Strict Topic-Wise Syllabus Compliance Audit

The following checklist verifies that 100% of the syllabus elements specified in your prompt have been addressed and solved inside this question bank:

*   [x] **Importance of Software Engineering**
    *   [x] Role of Software / Need of Software (Fully addressed in Solved Question 3, covering historical software crisis and goals of SE).
    *   [x] Categories of Software (Fully addressed in Solved Question 4, covering the 7 criteria and 11 distinct application/copyright domains).
*   [x] **Legacy Software**
    *   [x] Definition and characteristics (Fully addressed in Solved Question 5, quoting Dayani-Fard's standard definition and core longevity traits).
    *   [x] Reasons for retaining legacy systems (Fully addressed in Solved Question 6, detailing the 5 core organizational constraints like constant availability).
    *   [x] Case studies/examples (Fully addressed in Solved Questions 5 & 6, highlighting banking systems, airline reservation networks, and air traffic control).
    *   [x] Challenges of legacy software evolution (Fully addressed in Solved Question 7, covering technical debt and the 4 essential evolution pathways).
*   [x] **Software Myths**
    *   [x] Management Myths (Fully addressed in Solved Question 8, mapping all 4 myths using the mandatory Myth $\rightarrow$ Fact $\rightarrow$ Explanation template).
    *   [x] Customer Myths (Fully addressed in Solved Question 8 & 9, covering general objectives and flexibility with the exponential cost-of-change curve).
    *   [x] Practitioner’s Myths (Fully addressed in Solved Question 10 & 11, detailing formal technical reviews, documentation, and lifecycle support).
*   [x] **Syllabus Exclusions**
    *   [x] Confirmed: No questions or content from process models, requirements elicitation, design patterns, testing strategies, or any other Software Engineering unit have been included.
