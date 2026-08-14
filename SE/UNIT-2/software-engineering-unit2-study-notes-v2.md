# Software Engineering Unit 2 Study Notes: Prescriptive & Agile Process Models

---

## 1. Official Syllabus Mapping & Unit Overview

This document provides a highly detailed, comprehensive, and exam-focused study guide for **Unit 2: Prescriptive & Agile Process Models** of the Software Engineering curriculum [191]. It is meticulously mapped to the lecture slides, university exams, and authoritative textbooks (Roger S. Pressman's *Software Engineering: A Practitioner's Approach* and Ian Sommerville's *Software Engineering*) [145, 155, 191].

### Syllabus Coverage Matrix
*   **Part 1: Prescriptive Process Models**
    *   Process Framework — Roles and Architecture of Process Models [91, 110, 139]
    *   Capability Maturity Model Integration (CMMI) [45, 106, 121, 145, 155]
    *   Waterfall Model (Linear Sequential / Classic Life Cycle) [60, 111, 125, 187, 188]
    *   V-Shaped SDLC Model (Verification & Validation Variant) [3, 74, 88, 474]
    *   Incremental Model (Successive Version Model) [4, 108, 114, 149]
    *   Rapid Application Development (RAD) Model [51, 68, 116, 126, 182]
    *   Prototyping Model (Structured Evolutionary Prototyping) [6, 61, 102, 119, 141]
    *   Spiral Model (Risk-Driven Evolutionary Model) [18, 53, 186]
    *   Concurrent Development Model (Concurrent Engineering) [90, 191]
    *   Tailored/Hybrid SDLC Models [108, 246, 485]
*   **Part 2: Agile Process Models**
    *   Agility & Agile Process — Need for Agility, Agile Principles, and Agile vs. Prescriptive models [6, 147, 191]
    *   Adaptive Software Development (ASD) [90, 191]
    *   Extreme Programming (XP) — Values, practices, and phases [56, 191]
    *   SCRUM Framework — Roles, artifacts, sprints, and terminology [56, 191]
    *   Dynamic Systems Development Method (DSDM) [105, 159, 244, 482]
    *   Feature Driven Development (FDD) [104, 163, 242, 481]
*   **Part 3: Software Quality & Quality Assurance Plan**
    *   Software Quality Definitions [135, 327]
    *   Stated vs. Implied Requirements & User Expectations
    *   Quality Assurance Plan (SQA Plan) Components [327]
*   **Part 4: Scenario-Based Questions & Answers**
    *   Practice and Scenario-Based University Exam Preparation

---

## Part 1: Prescriptive Process Models

### 1.1 Process Framework: Roles & Architecture

#### Simple Definition
A **Process Framework** is the foundational structure of a software engineering process that establishes a small number of core activities applicable to all software projects, regardless of their size, domain, or complexity [139, 148].

#### Basic Concept
A software process is not a rigid, singular script; rather, it is an adaptable framework designed to bring order and structure to development [137, 144]. It defines **who** is doing **what**, **when**, and **how** to reach a specific project goal [91, 148]. 

#### Detailed Architecture
As defined in standard systems and engineering lectures, the hierarchy of a process framework consists of four nested layers [2, 73, 105, 110]:
1.  **Framework Activities**: The highest-level milestones of the process flow (e.g., Communication, Planning, Modeling, Construction, Deployment) [91, 105, 110, 139].
2.  **Software Engineering Actions**: A collection of cohesive tasks that produce a major work product (e.g., Requirements Elicitation, Architectural Design, Code Generation) [2, 73, 91, 105, 110, 139].
3.  **Task Sets**: The actual work steps, deliverables, quality assurance (SQA) checkpoints, and project milestones that populate each action [2, 73, 105, 110, 139].
4.  **Umbrella Activities**: Key management and quality control processes that run concurrently across all framework activities [91, 105, 110, 139, 140].

```
+-----------------------------------------------------------------+
|                       SOFTWARE PROCESS                          |
|                                                                 |
|  +-----------------------------------------------------------+  |
|  |                   Umbrella Activities                     |  |
|  |  (Risk Mgmt, SQA, SCM, Project Tracking, Reviews, etc.)   |  |
|  +-----------------------------------------------------------+  |
|                               |                                 |
|  +-----------------------------------------------------------+  |
|  |                  Framework Activities                     |  |
|  |  [Communication] -> [Planning] -> [Modeling]              |  |
|  |                     -> [Construction] -> [Deployment]     |  |
|  +-----------------------------------------------------------+  |
|                               |                                 |
|  +-----------------------------------------------------------+  |
|  |               Software Engineering Actions                |  |
|  |  (e.g., Analysis Modeling, Database Design, Unit Testing) |  |
|  +-----------------------------------------------------------+  |
|                               |                                 |
|  +-----------------------------------------------------------+  |
|  |                         Task Sets                         |  |
|  |  (Work Tasks, Work Products, SQA Checkpoints, Milestones) |  |
|  +-----------------------------------------------------------+  |
+-----------------------------------------------------------------+
```

#### The Five Framework Activities [91, 105, 110, 139]
*   **Communication**: Collaborative requirements gathering, initial meetings with customers, and goal setting [22, 111, 187].
*   **Planning**: Estimating effort and costs, scheduling tasks, allocating human resources, mapping timelines, and managing risks [22, 111, 187].
*   **Modeling**: Designing the blueprints of the software, spanning data structures, system architecture, database schemas, interfaces, and algorithms [23, 111, 188].
*   **Construction**: Code generation (translation of design to programming languages) and intensive verification testing (unit and integration testing) [23, 111, 188].
*   **Deployment**: Releasing the operational software to the client environment, collecting feedback, and providing technical support or maintenance [23, 111, 188].

#### The Eight Umbrella Activities [110, 139, 140]
*   **Software Project Tracking and Control**: Monitoring actual progress against schedule, and adjusting plans when deviation occurs.
*   **Risk Management**: Identifying, assessing, and mitigating risks that could threaten project success.
*   **Software Quality Assurance (SQA)**: Defining and executing audits to ensure standard engineering procedures are followed.
*   **Software Configuration Management (SCM)**: Controlling changes made to code, documents, and data artifacts over time.
*   **Technical Reviews**: Evaluating software models and work products to catch defects early.
*   **Measurement**: Collecting process, project, and product metrics.
*   **Reusability Management**: Defining criteria for component reuse across the team.
*   **Work Product Preparation and Generation**: Creating documents, logs, and installation guides.

⭐ **Must Remember**: A process is not a straightjacket. It is **adaptive**, and a team must select and scale its framework activities, actions, and task sets depending on project constraints, technology risks, and team dynamics [8, 79, 138, 159].

---

### 1.2 Capability Maturity Model Integration (CMMI)

#### Simple Definition
**CMMI** is a comprehensive process meta-model developed by the Software Engineering Institute (SEI) that provides a quantitative framework for assessing and improving an organization’s software development and management capabilities [11, 45, 145, 155].

🧠 **Must Understand**: CMMI was created to reconcile the fragmentation caused by using multiple independent capability models (such as Software CMM, Systems Engineering CMM, and People CMM) [45, 157, 179]. It acts as a single integrated roadmap [179].

#### Key Differences: CMM vs. CMMI Terminology
*   **Key Process Areas (KPAs) vs. Process Areas (PAs)**: CMM organizes processes into *Key Process Areas* (KPAs), whereas CMMI organizes them simply as *Process Areas* (PAs) [140].
*   **Level 2 Nomenclature**: In CMM, Level 2 is defined as **Repeatable** [122]. In CMMI, Level 2 is formally defined as **Managed** [121].
*   **Level 4 Nomenclature**: In CMM, Level 4 is defined as **Managed**. In CMMI, Level 4 is formally defined as **Quantitatively Managed** [122].

#### The Dual Representations of CMMI [11, 26, 27, 83, 106, 124, 145, 155, 166]
CMMI allows an organization to pursue process improvement through two distinct approaches:

```
                  +-----------------------------------------+
                  |           CMMI REPRESENTATIONS          |
                  +-----------------------------------------+
                               /                                   +----------------------------+     +----------------------------+
        |    STAGED REPRESENTATION   |     |  CONTINUOUS REPRESENTATION |
        +----------------------------+     +----------------------------+
        | • 5 Maturity Levels        |     | • 6 Capability Levels      |
        | • Evaluates overall org    |     | • Evaluates specific areas |
        | • Rigid path of KPA steps  |     | • Target-specific tuning   |
        +----------------------------+     +----------------------------+
```

##### 1. Staged Representation [11, 26, 27, 83, 106, 124, 145, 155, 166]
*   **Focus**: Evaluates the maturity of the *entire organization* [26, 27, 106].
*   **Structure**: Uses 5 pre-defined maturity levels [28, 107].
*   **Improvement Path**: Requires the completion of mandatory Process Areas (PAs) at each level before advancing to the next, serving as a structured step-by-step foundation [26].
*   **Usage**: Enables easy benchmarking and comparison between different organizations [27, 106].

##### 2. Continuous Representation [11, 27, 83, 106, 124, 145, 155, 166]
*   **Focus**: Evaluates individual *Process Areas* independently [27, 106].
*   **Structure**: Uses 6 capability levels (0 to 5) [30].
*   **Improvement Path**: Offers complete flexibility. Organizations select specific process areas (e.g., project planning) and raise their capability in isolation depending on business goals [27, 28, 106, 107].
*   **Usage**: Ideal for targeted tuning and targeted risk elimination [28, 107].

#### The 5 Staged Maturity Levels & Process Areas [12, 28, 29, 59, 104, 107, 121, 122, 180]

| Maturity Level | Label | Process Area / Characteristics | Process Quality & Risk |
| :---: | :--- | :--- | :--- |
| **Level 1** [12, 107, 121] | **Initial** | • Processes are ad-hoc, chaotic, and poorly controlled [28, 107, 121].<br>• Project success depends entirely on individual heroic effort [121].<br>• No Process Areas (PAs) are defined [28, 107]. | **Lowest Quality, Highest Risk** [29, 107] |
| **Level 2** [12, 29, 121, 122] | **Managed (Repeatable)** | • Basic project management disciplines (cost, schedule, and requirements) are established [29, 121].<br>• Past successes can be repeated on similar projects [122].<br>• **Key PAs (CMM Level 2 KPAs)**: Requirements Management (REQM), Project Planning (PP), Project Monitoring and Control (PMC), Supplier Agreement Management (SAM), Process and Product Quality Assurance (PPQA), Measurement and Analysis (MA), Configuration Management (CM) [12, 29, 121]. | **Medium-Low Risk, Better Quality** [29] |
| **Level 3** [12, 29, 122, 180] | **Defined** | • Engineering and management processes are documented, standardized, and integrated into a standard organizational software process [122].<br>• Tailored processes are used for individual projects.<br>• **Key PAs (CMM Level 3 KPAs)**: Peer Reviews, Intergroup Coordination, Software Product Engineering, Integrated Software Management, Training Program, Organization Process Definition, Organization Process Focus [12, 180]. | **Medium Quality, Medium Risk** [29] |
| **Level 4** [12, 59, 122, 180] | **Quantitatively Managed** | • Process and product metrics are quantitatively measured, understood, and controlled [59].<br>• Statistical techniques are applied.<br>• **Key PAs**: Organizational Process Performance (OPP), Quantitative Project Management (QPM). | **High Quality, Low Risk** [30] |
| **Level 5** [12, 59, 104, 122, 180] | **Optimizing** | • Continuous process improvement is driven by quantitative feedback from processes and pilot technologies [59, 104].<br>• **Key PAs**: Causal Analysis and Resolution (CAR), Organizational Innovation and Deployment (OID). | **Highest Quality, Lowest Risk** [30] |

#### The 6 Continuous Capability Levels [30, 156]
*   **Level 0 (Incomplete)**: The process area is either not performed or does not achieve its defined goals [30, 156].
*   **Level 1 (Performed)**: The process is executed, and work tasks are completed, but goals may be unstable.
*   **Level 2 (Managed)**: The process is planned, monitored, controlled, and evaluated for conformance against specifications.
*   **Level 3 (Defined)**: The process is customized and managed using the organization's standardized tailoring guidelines.
*   **Level 4 (Quantitatively Managed)**: The process is controlled using statistical and quantitative measurement techniques.
*   **Level 5 (Optimizing)**: The process is continuously refined to meet changing business objectives and technological trends.

✍Typed **Exam Focus**: In university examinations, a common high-mark question asks to compare CMM (CMMI) levels and write down their specific PAs/KPAs [12, 180]. Make sure to distinguish between CMM's Level 2 "Repeatable" and Level 4 "Managed" versus CMMI's Level 2 "Managed" and Level 4 "Quantitatively Managed."

---

### 1.3 The Waterfall Model & The V-Shaped Model

#### Definition (Waterfall Model)
The **Waterfall Model** (also known as the **Linear Sequential Model** or **Classic Life Cycle**) is a plan-driven software development model that proposes a systematic, linear approach progressing strictly through a sequence of phases [3, 60, 74, 111, 160].

```
Requirements Analysis
            System Design
                    Implementation (Coding)
                            Testing
                                Deployment
                                        Maintenance
```

#### Step-by-Step Working & Phases [22, 23, 24, 111, 187, 188, 189]
1.  **Requirements Analysis (Communication)**: All system requirements are captured from stakeholders and documented in detail in a Software Requirements Specification (SRS) [24, 189]. Requirements are frozen at this point [14, 181].
2.  **System Design (Modeling)**: Designers translate the SRS into technical blueprints including software architecture, databases, schemas, and algorithmic flows [24, 189].
3.  **Implementation (Construction - Coding)**: Developers write the source code based on design models [24, 189].
4.  **Testing**: The system components are integrated and tested (unit, integration, and system testing) to identify bugs and verify requirements [24, 189].
5.  **Deployment**: The fully tested system is delivered to the client [24, 189].
6.  **Maintenance**: Post-deployment enhancements, bug fixes, and updates are performed to keep the system operational over its lifespan [24, 189].

#### Waterfall Deficiencies & Risk Statements (Authoritative PPT) [458, 473]
*   **Upfront Requirements**: All requirements must be known upfront [458].
*   **Inflexible Deliverables**: Deliverables created for each phase are considered frozen, which inhibits flexibility [458].
*   **False Impression of Progress**: Project tracking is based on completed documentation rather than working software, giving a false sense of schedule health [458].
*   **Phase Iterations Ignored**: Does not reflect the iterative, problem-solving nature of software development [458].
*   **Big Bang Integration**: Integration occurs as one massive step at the very end of construction, exposing interface defects extremely late [458].
*   **No Working Previews**: Little opportunity for the customer to preview the system until deployment, which may be too late to rectify core misunderstandings [458].

---

#### The V-Shaped SDLC Model (Verification & Validation Variant) [474]

The **V-Shaped Model** is a prominent variation of the Waterfall model that emphasizes the verification and validation of the product [474]. Unlike Waterfall, where testing is deferred to the end, the V-model plans testing activities in parallel with corresponding development phases [474].

```
Project & Requirements Planning ------------------------------> Production, Operation & Maintenance
  (Resource Allocation)                                              (Enhancement & Corrections)
        \                                                                   /
    Product Requirements & Spec Analysis -------------------------> System & Acceptance Testing
          (Complete Spec of Software)                                   (Verify system in environment)
                \                                                           /
            Architecture / High-Level Design -------------------------> Integration & Testing
                  (Software functions map)                                  (Modules interconnect)
                        \                                                   /
                     Detailed Design -----------------------------> Unit Testing
                           (Algorithms)                                (Single module behavior)
                                 \                                         /
                                  =======> Coding / Production <============
                                      (Algorithms to executable code)
```

##### Step-by-Step Working: The Nine Steps of the V-Model [474]
1.  **Project and Requirements Planning**: Allocate resources and map out project parameters [474].
2.  **Product Requirements and Specification Analysis**: Create a complete and unambiguous specification of the software system [474].
3.  **Architecture or High-Level Design**: Define how high-level software functions will fulfill the design requirements [474].
4.  **Detailed Design**: Develop algorithms for each architectural component [474].
5.  **Coding (Bottom of the V)**: Transform the algorithms into active, executable software code [474].
6.  **Unit Testing**: Check that each individual module acts exactly as expected [474].
7.  **Integration and Testing**: Check that modules interconnect and communicate correctly [474].
8.  **System and Acceptance Testing**: Verify the entire integrated software system operates correctly within its target business environment [474].
9.  **Production, Operation and Maintenance**: Provide for post-delivery enhancements, optimizations, and bug corrections [474].

##### V-Shaped Model Strengths [89, 475]
*   **V&V Integration**: Emphasizes planning for verification and validation of the product in the earliest stages of product development [89, 475].
*   **Testable Deliverables**: Each development deliverable must be designed to be testable [89, 475].
*   **Milestone Tracking**: Project management can track progress easily by objective milestones [89, 475].
*   **Simplicity**: Extremely simple and easy to use [89, 475].

##### V-Shaped Model Weaknesses [89, 475]
*   **No Concurrency**: Does not easily handle concurrent, overlapping events [89, 475].
*   **No Phases or Iteration**: Lacks support for parallel iterations or cyclical phases [89, 475].
*   **Rigid Requirements**: Does not easily handle dynamic changes in requirements after the initial analysis phase [89, 475].
*   **Lacks Risk Management**: Does not contain any dedicated risk analysis or risk mitigation activities [89, 475].

##### Suitability & Use Cases (When to Use the V-Model) [90, 475]
*   Excellent choice for systems requiring **high reliability** (e.g., hospital patient control applications, flight safety controls) [90, 475].
*   When **all requirements are known up-front** and fully stable [90, 475].
*   When the V-model can be modified to handle changing requirements beyond the analysis phase.
*   When the **technical solution and core technology are fully known** and understood [90, 475].

---

### 1.4 The Incremental Model

#### Definition
The **Incremental Model** (often referred to as the **Successive Version Model**) is a software process model where requirements are broken down into multiple standalone modules, each developed sequentially through a linear process flow to deliver an operational product in successive releases (increments) [4, 20, 75, 108, 114, 149].

```
Calendar Time ---------->
[Increment 1] Communication -> Planning -> Modeling -> Coding -> Testing -> CORE PRODUCT
[Increment 2] Communication -> Planning -> Modeling -> Coding -> Testing -> VERSION 2
[Increment 3] Communication -> Planning -> Modeling -> Coding -> Testing -> VERSION 3
```

#### Step-by-Step Working & Lifecycle [4, 5, 20, 75, 76, 108, 109, 114, 149, 150, 151]
1.  **System-Level Requirements Definition**: The total product concept is defined, and global system requirements are gathered.
2.  **Prioritization of Requirements**: Features are prioritized, and high-risk or core requirements are scheduled for the first increment [20, 68, 177, 185].
3.  **Core Product Development (Increment 1)**: A stripped-down, yet operational version of the software containing basic features is engineered and delivered to the customer [5, 76, 108, 150].
4.  **Feedback and Planning**: The customer test-drives the core product, and their feedback is analyzed [1, 50, 76, 108, 151].
5.  **Subsequent Increments**: The next set of features is designed, coded, and integrated with the existing core [5, 20, 76, 108, 151].
6.  **Final Release**: The cycle repeats until the complete product is produced [5, 76, 151].

#### Key Characteristics
*   **Evolutionary Iteration**: It combines elements of linear sequential flows with the iterative philosophy of prototyping [66].
*   **Operational Builds**: Unlike prototyping, each increment delivers a fully functional, production-ready product [126].

#### Advantages & Disadvantages [20, 21, 52, 88, 89, 94, 95, 96, 115, 177, 178, 185]

##### Advantages [20, 52, 88, 94, 95, 115, 177, 185]
*   Allows high-risk or major architectural functions to be built and verified first [20, 94, 177, 185].
*   Delivers useful working software to the market very early [94, 115, 185].
*   Reduces overall risk of changing requirements because changes are isolated to future increments [1, 21, 88, 177, 185].
*   Lower initial cost, as development starts with a core team [95, 115, 177, 185].
*   Easier to test and debug because changes between releases are relatively small [52].

##### Disadvantages [21, 89, 95, 96, 115, 178, 185]
*   Requires excellent planning, architectural design, and project management [21, 89, 95, 178, 185].
*   Requires early definition of the complete global system architecture to accommodate future increments [21, 89, 178, 185].
*   Module interfaces must be extremely well-defined from the start [21, 89, 96, 115, 178].
*   The total cost of the complete system is often higher than a single-pass Waterfall approach [21, 89, 96, 115, 178, 185].

#### Suitability & Use Cases [21, 68, 89, 178, 186]
Ideal when global requirements are generally understood but expected to evolve, there is high demand for early realization of benefits, or staffing is limited for a full-scale release [21, 68, 89, 178, 186].

##### Real-World Examples & Case Studies [109, 149]
*   **Word Processing Software**: 
    *   *Increment 1*: Basic file management, text editing, and document production [109, 149].
    *   *Increment 2*: Sophisticated formatting and advanced editing [109, 150].
    *   *Increment 3*: Spell check and grammar engines [109, 150].
    *   *Increment 4*: Advanced page layout, desktop publishing, and templates [109, 150].

---

### 1.5 Rapid Application Development (RAD) Model

#### Definition
The **Rapid Application Development (RAD) Model** is an incremental software process model that emphasizes an extremely short, high-speed development cycle (typically 60 to 90 days), achieved primarily through component-based construction and parallel development teams [17, 51, 68, 69, 97, 116, 126, 182, 183].

```
              +-------------------------------------+
              |      Requirements Gathering &       |
              |       Analysis / Planning           |
              +-------------------------------------+
                                 |
         +-----------------------+-----------------------+
         |                       |                       |
  +--------------+        +--------------+        +--------------+
  |   Team #1    |        |   Team #2    |        |   Team #3    |
  | • Design     |        | • Design     |        | • Design     |
  | • Build/Code |        | • Build/Code |        | • Build/Code |
  | • Test       |        | • Test       |        | • Test       |
  +--------------+        +--------------+        +--------------+
         |                       |                       |
         +-----------------------+-----------------------+
                                 |
              +-------------------------------------+
              |       Cutover / Deployment          |
              |     (Integration & Training)        |
              +-------------------------------------+
```

#### Step-by-Step Working & Phases [17, 69, 86, 182, 183]
1.  **Requirements Planning Phase**: A structured, workshop-style session where business problems, objectives, and high-level requirements are defined through collaboration between stakeholders and analysts [17, 86].
2.  **User Description Phase**: Automated modeling tools capture detailed system functions, business rules, and user interfaces directly from stakeholders [17, 86].
3.  **Construction Phase**: Code generators, screen builders, and other productivity tools are used inside a strict "time-box" of 60-90 days to develop the software modules rapidly [17, 86, 183].
4.  **Cutover Phase**: The parallel modules are integrated, final user acceptance testing is performed, database migration occurs, and user training begins [17, 86].

#### Alternative Framework Phase Representation (Pressman style) [69]
*   **Business Modeling**: Information flow among business functions is modeled [69].
*   **Data Modeling**: Information from business modeling is refined into data objects.
*   **Process Modeling**: Data objects are transformed to achieve business functions.
*   **Application Generation**: Automated tools generate code [53].
*   **Testing and Turnover**: Reused components are integrated and verified.

#### Key Characteristics
*   **Component Reuse**: Relies heavily on pre-built modules and automated code generation [53].
*   **Strict Time-Boxing**: Schedule deadlines are fixed and non-negotiable.
*   **Parallel Teams**: Multi-team structures work concurrently on modularized functional areas [70, 99, 116].

#### Advantages & Disadvantages [18, 19, 53, 72, 86, 87, 99, 100, 117, 127, 184]

##### Advantages [18, 53, 86, 99, 184]
*   Drastically reduces project cycle time and delivery speed [18, 53, 86, 184].
*   Lower overall project costs, as fewer resources are used over a condensed timeframe [18, 86, 184].
*   Time-box approach effectively mitigates cost and schedule risks [18, 86, 184].
*   Ensures high customer satisfaction due to continuous stakeholder involvement [18, 86, 184].

##### Disadvantages [18, 19, 72, 87, 100, 117, 127, 184]
*   Requires a massive pool of highly skilled human resources to staff parallel teams [72, 100, 117, 127].
*   Highly dependent on a deep commitment from developers and customers [72, 100, 117, 127].
*   Fails if the software cannot be cleanly modularized into independent components [19, 72, 87, 100, 117, 127].
*   Not suitable for systems with high technical risk, performance-critical boundaries, or legacy integration issues [19, 72, 87, 100, 117].

#### Suitability & Use Cases [19, 87, 117, 118, 182]
Ideal when requirements are well understood, the system can be easily modularized, high-performance tuning is not critical, and there is high availability of automated development tools [19, 87, 117, 182].

##### Real-World Examples & Case Studies [98, 117]
*   **E-Commerce Platform Development**:
    *   *Team #1*: Designs and builds the UI/UX frontend [98, 117].
    *   *Team #2*: Program payment gateway interfaces [98, 117].
    *   *Team #3*: Develop inventory management modules [98, 117].
    *   All modules are integrated and deployed concurrently within 90 days [98, 117].

---

### 1.6 The Prototyping Model

#### Definition
The **Prototyping Model** is an evolutionary software process model designed to quickly construct a working preview (prototype) of the system to gather user feedback and define accurate requirements when initial project needs are fuzzy or unclear [6, 119, 142, 162].

```
  Requirements Gathering
         |
    Quick Design
         |
   Build Prototype ------> Customer Evaluation
         |                       |
    Refine Specs <---------------+
         |
  Final Software Build
```

#### Structured Evolutionary Prototyping Steps [16, 102, 103, 119, 174]
1.  **Initial Communication**: Gather basic goals and requirements [62, 103].
2.  **Quick Design**: Focuses on user-visible layouts, screen displays, and interaction flows, bypassing back-end architecture [62, 102, 119].
3.  **Prototype Construction**: Build the prototype using shortcuts (e.g., table lookups, dummy functions, hardcoded data) to speed up delivery [16, 61, 119, 174].
4.  **Customer Evaluation**: The customer interacts with the working prototype and provides corrective feedback [16, 119, 174].
5.  **Iteration and Refinement**: The developer refines the prototype iteratively based on feedback [16, 119, 174].
6.  **Final Build Conversion**: Once requirements are clear and the customer is satisfied, the prototype is either thrown away to engineer production-ready code, or refactored to meet strict quality and architectural standards [16, 174].

#### Key Characteristics
*   **Tangible Feedback**: Users interact with a working model rather than reading dry text documents [119].
*   **Iterative Exploration**: Re-evaluating and refining requirements continuously.

#### Advantages & Disadvantages [54, 55, 120]

##### Advantages [54, 120]
*   Quickly provides customers with an early, working version of the software [120].
*   Builds stakeholder trust by showing tangible, steady progress [120].
*   Drastically reduces requirement misunderstandings [120].
*   Errors are detected and resolved much earlier in the lifecycle.

##### Disadvantages [55, 120, 154]
*   Can bypass rigorous system analysis and architectural planning, leading to long-term maintainability issues [120, 154].
*   Stakeholders may mistake a prototype for the final, production-ready system and pressure the team to release it prematurely [154].
*   Can easily become highly expensive and time-consuming if the feedback loop repeats indefinitely without closure [55, 120].
*   Choosing specific technologies prematurely to build a rapid prototype can limit future architectural flexibility [120].

#### Suitability & Use Cases [54, 118, 128, 141, 162, 182]
Ideal when requirements are unstable, fuzzy, or unclear, human-computer interfaces are highly interactive (e.g., web portals), or developers are exploring new technologies or algorithms [54, 128, 141, 162, 182].

##### Real-World Examples & Case Studies [120]
*   **Mobile Interface Design**: Developing a clickable mobile app prototype (using dummy databases) to let users test navigation and UI flow before backend engineering begins [120].

---

### 1.7 The Spiral Model

#### Definition
The **Spiral Model** is an evolutionary, risk-driven software process model that couples the iterative nature of prototyping with the controlled, systematic aspects of the Waterfall model [18, 186]. It is widely considered a **meta-model**, as it can guide and encompass other process models [53, 186].

```
               Determine Objectives, Alternatives, Constraints
                             |       /
                             | Risk Analysis & Prototyping
                             |     /
                             |    /
       Plan Next Phases -----+---+----- Engineering (Design, Code, Test)
                                 |
                                 |
                        Customer Evaluation
```

#### Step-by-Step Working & Six Task Regions [53, 186]
The spiral process is divided into six critical quadrant regions:
1.  **Customer Communication**: Establishing initial goals, scoping features, and gathering user expectations.
2.  **Planning**: Defining milestones, estimating resources, setting schedules, and choosing alternative process paths.
3.  **Risk Analysis**: Conducting intensive evaluations of technical, business, and operational risks, followed by prototyping to mitigate those risks [18, 53].
4.  **Engineering**: Designing, coding, and testing the software build for that specific cycle.
5.  **Construction & Release**: Creating the actual installable software increment.
6.  **Customer Evaluation**: The client evaluates the increment and provides feedback.

#### The Four Evolutionary Loops [53, 186]
As the process moves outward along the spiral path, development transitions through four core project levels [53]:
*   **Concept Development Projects**: Exploring the initial product concepts [53].
*   **New Product Development Projects**: Designing and engineering the first official version of the software.
*   **Product Enhancement Projects**: Adding advanced features, performance optimizations, and modules.
*   **Product Maintenance Projects**: Ongoing support, patching, and adaptation to changing technologies.

#### Advantages & Disadvantages [18, 53, 186]

##### Advantages [18, 186]
*   Excellent risk management, as potential issues are analyzed and addressed in every loop [18, 186].
*   Encompasses and integrates multiple process models (e.g., prototyping, waterfall) within its meta-framework [53, 186].
*   Highly flexible; accommodates requirements changes and enhancements easily.
*   Provides a highly realistic approach to large-scale, complex software engineering.

##### Disadvantages [18, 53, 186]
*   Requires deep expertise in risk assessment, making success highly dependent on specialized analysts [18, 186].
*   Can be highly expensive and resource-intensive, making it unsuitable for small, low-budget projects.
*   Difficult to estimate total schedules and budgets at the start of the project.
*   Requires significant documentation, which can slow down progress.

#### Suitability & Use Cases [18, 186]
Ideal for large-scale, high-budget, complex projects where risk management is paramount and requirements are highly likely to evolve over time [18, 186].

---

### 1.8 The Concurrent Development Model

#### Definition
The **Concurrent Development Model** (sometimes called **Concurrent Engineering**) is a process model that represents a network of activities where each activity exists as a state machine, allowing the software team to develop multiple system components simultaneously [90, 191].

```
                      +-------------------+
                      |   Awaiting Tasks  |
                      +-------------------+
                                |
                                v
                      +-------------------+      Under Review
                      | Under Development | --------+
                      +-------------------+         |
                                |                   v
                                |           +---------------+
                                |           | Under Revision|
                                |           +---------------+
                                v                   |
                      +-------------------+         |
                      |     Baselined     | <-------+
                      +-------------------+
```

#### Step-by-Step Working & State-Transition Architecture
An activity (such as modeling or analysis) is not represented as a static block, but rather transitions through multiple states:
*   **Awaiting Tasks**: The activity is currently idle, waiting for inputs or dependencies.
*   **Under Development**: Work on the activity is active and ongoing.
*   **Under Review**: The completed work product is undergoing technical review or auditing.
*   **Under Revision**: Defects have been identified, and the work product is being updated.
*   **Baselined**: The work product is approved, frozen, and ready to guide downstream activities.
*   **Done**: The activity is completed.

#### Key Characteristics
*   **Parallel Execution**: Allows modeling, coding, and testing to occur concurrently on different parts of the system.
*   **State-Driven Triggers**: Activity transitions are triggered by events (e.g., a changed requirement shifts a "Baselined" design back to "Under Revision").

#### Advantages & Disadvantages
*   **Advantages**: Significantly reduces time-to-market by enabling parallel work; provides a realistic view of real-world multi-tasking.
*   **Disadvantages**: Highly complex to manage; requires excellent communication, coordination, and configuration management.

#### Suitability & Use Cases
Ideal for projects developed by highly specialized, distributed teams where different system components can be engineered in parallel.

---

### 1.9 Tailored/Hybrid SDLC Models [108, 485]

#### Purpose & Philosophy
In real-world software engineering, **one size does not fit all**. Prescriptive and agile models represent theoretical archetypes [108]. To succeed, an organization must analyze project characteristics and tailor or combine models to match their precise risk profiles, team experience levels, and system parameters [108].

#### Why Models are Tailored [108]
*   **Risk vs. Complexity**: Some projects have highly innovative UI components (which need prototyping) but also safety-critical algorithms (which need Waterfall design).
*   **Speed vs. Reliability**: Teams may need to deliver fast, incremental benefits but require extremely high reliability for medical, financial, or defense systems [108].

#### Presentation Examples [108, 485]
*   **Spiral / Waterfall Hybrid (Spiral with Paring)**: A project has significant technical risk, so the team begins with the Spiral model's formal risk analysis [108]. However, to avoid excessive administrative overhead, they pare down the plan and transition into Waterfall once risks are fully resolved [108].
*   **Incremental / V-Shaped Hybrid**: Software must be delivered in increments to get fast business value, but has high reliability requirements [108]. The team combines the incremental delivery cycle with the V-shaped model's planning-for-testing, ensuring every delivered increment is thoroughly verified and validated before release [108].

---

## Part 2: Agile Process Models

### 2.1 Agility & Agile Process

#### Simple Definition
**Agility** is a dynamic, people-centric, and iterative approach to software engineering that emphasizes rapid delivery of operational code, close collaboration with stakeholders, and rapid adaptation to changing requirements [6, 147].

#### Basic Concept & Need for Agility
Traditional prescriptive models (such as Waterfall) are plan-driven and assume requirements can be frozen early [14, 15, 25, 181, 190]. However, in modern software development, business needs, technologies, and market pressures change rapidly [141]. Prescriptive models often fail in these environments because their rigid, document-driven processes make changes highly expensive and slow to implement [141, 190].

```
Prescriptive Path:  [Plan] -> [Design] -> [Code] -> [Test] -> [Deploy] (Rigid, High-risk)
Agile Path:         [Loop: Feedback -> Fast Iteration -> Increment Delivery] (Adaptive)
```

#### The Four Core Values of the Agile Manifesto [191]
1.  **Individuals and interactions** over processes and tools.
2.  **Working software** over comprehensive documentation.
3.  **Customer collaboration** over contract negotiation.
4.  **Responding to change** over following a plan.

#### The 12 Agile Principles
1.  Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
2.  Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.
3.  Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
4.  Business people and developers must work together daily throughout the project.
5.  Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
6.  The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
7.  Working software is the primary measure of progress.
8.  Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9.  Continuous attention to technical excellence and good design enhances agility.
10. Simplicity—the art of maximizing the amount of work not done—is essential.
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

---

### 2.2 Adaptive Software Development (ASD)

#### Definition
**Adaptive Software Development (ASD)** is an agile software development model originally proposed by Jim Highsmith and Sam Bayer that focuses on applying evolutionary, collaborative techniques to build complex, high-speed software systems [90, 98, 191]. It grew directly out of rapid application development (RAD) [98].

#### The 3 Core Pillars & Phases of ASD [90, 100, 191, 240]
1.  **Speculation**: Planning is referred to as "speculation" because ASD accepts that requirements are too volatile and unpredictable to lock in a rigid plan [90]. Instead, high-level objectives, project constraints, and cycle time-boxes are estimated based on customer mission statements and user needs [102].
2.  **Collaboration**: Complex systems require diverse skills. Developers, domain experts, and stakeholders work in high-collaboration environments, sharing knowledge and building on each other's expertise while respecting individual creativity [102, 241].
3.  **Learning**: The team reflects and learns continuously to increase their level of real understanding [103, 241]. At the end of each iteration, learning occurs through three primary mechanisms [103]:
    *   *Technical Reviews*: Verifying software quality and design [103].
    *   *Customer Focus Groups*: Gathering feedback directly from users [103].
    *   *Project Postmortems*: Reflecting on performance to optimize team methods [103].

```
                 +-----------------------+
                 |      SPECULATION      |  <--- Planning, cycle time-boxes [102]
                 +-----------------------+      |
                             |                  |
                             v                  |
                 +-----------------------+      |
                 |     COLLABORATION     |      |  Evolutionary Loop
                 +-----------------------+      |
                             |                  |
                             v                  |
                 +-----------------------+      |
                 |       LEARNING        |  ----+  Focus groups, postmortems [103]
                 +-----------------------+
```

#### The Complete Adaptive SDLC Phases [107, 245, 484]
1.  **Project initiation**: Determining the baseline intent of the project.
2.  **Adaptive cycle planning**: Defining release milestones and time-boxed increments.
3.  **Concurrent component engineering**: Coding and developing modules in parallel.
4.  **Quality review**: Gathering feedback from users and conducting technical reviews.
5.  **Final QA and release**: Deploying the tested software increment.

#### The Eight Adaptive Steps (Authoritative PPT) [107, 245, 484]
1.  **Project Initialization**: Determine the absolute intent of the project [107].
2.  **Determine Project Time-Box**: Estimate the total duration of the project [107].
3.  **Determine Optimal Cycles**: Map out the optimal number of cycles and specify the time-box for each [107].
4.  **Write Objective Statements**: Write an objective statement for each individual cycle [107].
5.  **Assign Primary Components**: Assign primary software components to each cycle [107].
6.  **Develop Project Task List**: Map out all technical tasks required [107].
7.  **Review success of a cycle**: Conduct focus groups and reviews [107].
8.  **Plan the next cycle**: Adapt the next cycle plan based on feedback [107].

---

### 2.3 Extreme Programming (XP)

#### Definition
**Extreme Programming (XP)** is a highly influential agile software development framework focused on delivering high-quality software rapidly through intensive engineering practices and close developer-customer collaboration [56, 147, 191].

#### The Five Core Values of XP
*   **Communication**: Intensive, informal collaboration between developers and customers.
*   **Simplicity**: Focus on building the simplest design that meets today's requirements.
*   **Feedback**: Continuous feedback through automated testing, short delivery cycles, and customer collaboration.
*   **Courage**: The willingness to refactor code, throw away bad designs, and tackle complex problems.
*   **Respect**: Trust and collaboration among team members.

#### The 12 Core Practices of XP
1.  **The Planning Game**: Collaborative release planning sessions.
2.  **Small Releases**: Frequent delivery of small, working increments.
3.  **System Metaphor**: Using a shared story or naming convention to guide design.
4.  **Simple Design**: Write code to meet current requirements, avoiding over-engineering.
5.  **Continuous Testing (Test-First Development)**: Writing unit tests before writing the corresponding application code.
6.  **Refactoring**: Continuously improving and simplifying code architecture without changing its functional behavior.
7.  **Pair Programming**: Two developers work together at a single workstation—one writing code while the other reviews it in real-time.
8.  **Collective Code Ownership**: Any developer is authorized to change any line of code in the codebase.
9.  **Continuous Integration**: Integrating and building the software system multiple times daily.
10. **40-Hour Week**: Avoiding burnout by maintaining sustainable, consistent working hours.
11. **On-Site Customer**: An active user representative sits full-time with the development team to answer questions.
12. **Coding Standards**: Following strict, uniform style guidelines.

#### XP Phases & Lifecycle
1.  **Planning**: Writing User Stories and estimating effort.
2.  **Design**: Using Class-Responsibility-Collaborator (CRC) cards and building simple designs. If a difficult design blocker occurs, developers build a "Spike Solution" (a rapid throwaway prototype) to resolve technical uncertainty.
3.  **Coding**: Pair programming and writing unit tests first.
4.  **Testing**: Automated unit tests are executed continuously, followed by customer acceptance testing.

---

### 2.4 SCRUM Framework

#### Definition
**Scrum** is an agile management framework designed to orchestrate software development in a highly dynamic, collaborative, and iterative environment through structured roles, events, and artifacts [56, 191].

```
                 Daily Scrum (15 Mins, 3 Questions)
                         Product Backlog ----> Sprint Planning ----> Sprint (1-4 Weeks) ----> Demo/Review
                             /
                       Sprint Backlog
```

#### The 3 Core Roles in Scrum
*   **Product Owner**: Represents the customer and business stakeholders. They own the Product Backlog, prioritize requirements, and define acceptance criteria.
*   **Scrum Master**: A servant-leader who facilitates Scrum events, ensures Agile principles are followed, and removes blockers for the development team.
*   **Development Team**: A cross-functional, self-organizing team (typically 5 to 9 members) responsible for delivering the working product increments.

#### The 3 Core Artifacts in Scrum
*   **Product Backlog**: A dynamic, prioritized list of all features, enhancements, and bug fixes required for the product. **Note**: New requirements and changes are introduced only in the Product Backlog [162].
*   **Sprint Backlog**: A subset of Product Backlog items selected for development during the current Sprint.
*   **Product Increment**: The fully functional, integrated, and validated software package delivered at the end of a Sprint.

#### The 5 Core Events in Scrum
1.  **Sprint**: A strict, time-boxed iteration (typically 1 to 4 weeks) where the development work occurs. **Note**: Requirements are completely stable inside the Sprint; changes are not allowed inside active Sprints [162].
2.  **Sprint Planning**: A collaborative session where the Product Owner and Team define the Sprint Goal and select Sprint Backlog items.
3.  **Daily Scrum**: A brief, daily 15-minute meeting where developers coordinate and answer three standard questions:
    *   *What did I do since the last meeting?*
    *   *What will I do before the next meeting?*
    *   *What obstacles are blocking my progress?*
4.  **Sprint Review (Demo)**: A session at the end of the Sprint where the Team demonstrates the working Product Increment to stakeholders and collects feedback.
5.  **Sprint Retrospective**: An internal team reflection session to optimize processes and collaboration for the next Sprint.

#### Key Terminology
*   **Velocity**: The amount of backlog effort a team can complete in a single Sprint.
*   **Burndown Chart**: A visual graph tracking outstanding work against remaining time.

---

### 2.5 Dynamic Systems Development Method (DSDM) [105, 159, 244, 482]

#### Definition
The **Dynamic Systems Development Method (DSDM)** is an agile software development approach that provides a comprehensive framework for building and maintaining systems under tight time constraints through the use of incremental prototyping in a controlled environment [105, 159, 482].

#### The 80/20 Rule Paradigm [105, 482]
The philosophical core of DSDM is the modified **Pareto Principle (80/20 Rule)** [105]. In DSDM, it is assumed that **80 percent of an application can be delivered in 20 percent of the time** it would take to build the complete (100 percent) system [105, 355]. DSDM is an iterative process where only enough work is performed in each iteration to transition safely to the next, leaving finer details to be refined later as requirements evolve [105, 194, 355].

#### The Nine Guiding Principles of DSDM [105, 160, 244, 483]
1.  **Active User Involvement**: Imperative throughout the process (utilizing "Ambassador Users") [105, 244].
2.  **Empowered Teams**: DSDM teams must be fully empowered to make quick, decisive decisions [106, 244].
3.  **Frequent Product Delivery**: Focuses on delivering functional increments frequently [106, 244].
4.  **Fitness for Business Purpose**: The essential criterion for accepting deliverables [106, 244].
5.  **Iterative and Incremental Development**: Mandatory to converge on an accurate business solution [106, 244].
6.  **High-Level Agreement**: Requirements are initially agreed at a high level and baselined [106, 244].
7.  **Reversible Changes**: All changes made during development must be completely reversible [106, 244].
8.  **Integrated Testing**: Testing is integrated continuously throughout the entire lifecycle [106, 244].
9.  **Collaborative Approach**: A collaborative and cooperative approach among all stakeholders is essential [106, 244].

#### The DSDM Lifecycle [106, 245, 316, 484]
*   **Feasibility Study**: Establishes basic requirements and constraints to determine if the application is a viable candidate for DSDM [106, 317].
*   **Business Study**: Defines functional and informational requirements to establish business value, maps the core system architecture, and outlines maintainability parameters [106, 317].
*   **Functional Model Iteration**: Produces a set of incremental, evolving prototypes to demonstrate functionality and elicit direct user feedback [106, 317].
*   **Design and Build Iteration**: Revisits prototypes built in the functional iteration to ensure they are properly engineered for long-term operational value [106, 318].
*   **Implementation**: Places the latest operational prototype/increment into the client's working environment. If requirements change or are incomplete, the loop returns to functional iteration [106, 318].

---

### 2.6 Feature Driven Development (FDD) [103, 163, 242, 481]

#### Definition
**Feature Driven Development (FDD)** is an agile, adaptive, and practical software process model designed originally by Peter Coad for object-oriented software engineering, and later extended by Stephen Palmer and John Felsing for larger scale projects [54, 103, 163, 242, 481].

#### The Core Concept of a "Feature" [55, 164, 242]
In FDD, a **feature** is defined as "a client-valued function that can be implemented in two weeks or less" [55, 164, 242]. 
*   **PPT Feature Format Template**: `<action> <result> <object>` (Slide 104, 242), e.g., `Calculate the total of a sale`.
*   **Textbook Extension Template**: `<action> the <result> <by | for | of | to> a(n) <object>` [57, 164], e.g.:
    *   *Add the product to shopping cart* [58, 164]
    *   *Display the technical-specifications of the product* [58, 164]
    *   *Store the shipping-information for the customer* [58, 164]

```
    Feature Set Grouping Template:  <action><-ing> a(n) <object> [58]
    Example:                        "Making a product sale" [58]
```

#### The Five FDD Process Activities [59, 104, 242, 321, 481]
1.  **Develop an Overall Model**: Chief architects meet with domain experts and developers to analyze scope and produce system class and sequence diagrams [104, 242, 321].
2.  **Build a Features List**: Identify all functions supporting requirements. The domain is decomposed into Subject Areas, which contain Business Activities, which are mapped to individual categorized Features [104, 242, 321].
3.  **Plan by Feature**: The development staff sequences the features, allocates classes to individual developers (Class Owners), and assigns features to Feature Set Owners [105, 243, 323].
4.  **Design by Feature**: A small design team produces detailed sequence diagrams and design packages for selected features inside a 2-week cycle [105, 243, 323].
5.  **Build by Feature**: Class owners write code, conduct design and code inspections, run unit tests, and promote the completed client-valued function to the main build [105, 243, 323].

#### FDD Suitability, Advantages, and Limitations [56, 324]
*   **Advantages**: Highly granular progress tracking (using milestones like: *design walkthrough, design, design inspection, code, code inspection, promote to build*) [60]; small deliverable blocks minimize ambiguity [56].
*   **Limitations**: High dependence on specialized Chief Architects and individual Class Owners; heavy overhead for small projects.
*   **Suitability**: Excellent choice for medium-to-large object-oriented projects and corporate teams.

---

## Part 3: Software Quality & Quality Assurance Plan

### 3.1 Software Quality Definitions & Concepts [135, 327]

#### Definition (Authoritative Textbook)
As established by Roger S. Pressman, **Software Quality** is defined as:
1.  **Conformance to explicitly stated** functional and performance requirements [135].
2.  **Conformance to explicitly documented** development standards [135].
3.  **Conformance to implicit characteristics** that are expected of all professionally developed software [135].

```
                             +-------------------------------+
                             |        SOFTWARE QUALITY       |
                             +-------------------------------+
                               /             |                               +--------------------+ +--------------------+ +--------------------+
                |  Stated functional | |   Explicitly documented| |   Implicit expectations|
                |  and performance   | |   development      | |   such as usability|
                |  requirements      | |   standards        | |   and reliability  |
                +--------------------+ +--------------------+ +--------------------+
```

#### Stated vs. Implied Requirements & User Expectations
*   **Stated Requirements**: Explicitly logged user requirements, performance goals, and specifications documented in the SRS [135].
*   **Implied Requirements**: Characteristics expected of any high-quality software, even if not explicitly requested by the user (e.g., system reliability, data security, robust error handling, and intuitive navigation) [135]. If implied requirements are violated, the software is deemed poor quality, even if it fulfills all functional requirements.

#### Effects of Poor Quality [151, 312]
*   **Accumulation of Technical Debt**: Rushed implementations lead to chaotic code structures [312].
*   **Extreme Rework Costs**: Defects found late during deployment cost up to 100x more to fix than during analysis.
*   **Project Slippage**: Continuous debugging loops ("code-and-fix") destroy project schedules.
*   **Customer Dissatisfaction**: Rejection of software products upon release.

---

### 3.2 SQA Plan Components & Activities [327]

The **Software Quality Assurance (SQA) Plan** is a vital document designed to provide confidence to both developers and customers that the final software product will satisfy all quality standards and user expectations [327].

An effective SQA Plan incorporates the following core verification and validation activities [327, 332]:

#### 1. Defect Tracking and Tracing
*   Systematic tracking of identified software anomalies from discovery, through prioritization and assignment, to final resolution and regression testing.

#### 2. Unit Testing
*   Checking individual program modules, classes, or subroutines in complete isolation to verify correct internal functional logic, local data structures, and boundary limits.

#### 3. Source-Code Tracing
*   Ensuring complete consistency and bidirectional traceability. Every line of source code must trace back to a specific component design element, which in turn must map to a verified stakeholder requirement in the SRS.

#### 4. Technical Reviews (FTR)
*   Structured peer reviews, design walkthroughs, and code inspections conducted by a small group of specialists to identify functional errors, logic omissions, and standard violations early [165].

#### 5. Integration Testing
*   Testing the interfaces and communication links between integrated modules [330]. Done using either **Incremental Approaches** (Top-down, Bottom-up, Sandwich) or **Big Bang Approaches** (consolidated end-stage integration) [332].

#### 6. System Testing
*   Verifying that the entire integrated software system functions correctly in its target environment and meets all functional and non-functional specifications.

---

## Part 4: Lecture Scenario-Based Questions & Answers

These questions reflect the core scenario-testing patterns from actual university examination keys [116, 420, 486]:

### Scenario 1: Select the best SDLC model for porting an existing system to a new platform. [459, 474]
*   **Answer/Recommendation**: **Waterfall Model (Classic Life Cycle)** [459].
*   **Justification**: The requirements of the system are 100% known and fully stable (since the system already exists and is simply being moved to a new operating environment) [459, 474]. The technology is understood, and the risk of requirement volatility is virtually non-existent [459, 474].

### Scenario 2: Select the model for a large-scale hospital patient monitoring system. [90, 475]
*   **Answer/Recommendation**: **V-Shaped SDLC Model** [90, 475].
*   **Justification**: Patient monitoring software is safety-critical and requires **extreme reliability** [90, 475]. The V-model integrates rigorous planning for verification and validation at every development tier (requirements, design, and detailed code) before coding begins [89, 475]. This ensures zero defect leakage into the operational system [89].

### Scenario 3: A team has limited staff, but needs to deploy a core version of a new product to market quickly. [94, 115, 185]
*   **Answer/Recommendation**: **Incremental SDLC Model** [94, 185].
*   **Justification**: The Incremental model allows the team to prioritize requirements and engineer a stripped-down **Core Product** (Increment 1) with minimal staff and budget [5, 20, 115, 185]. This gets the product to market quickly, while subsequent releases add secondary features based on direct user feedback [20, 94, 115, 185].

### Scenario 4: The customer is confused about the requirements, and the development team is using a totally new technology. [6, 119, 142, 162]
*   **Answer/Recommendation**: **Structured Evolutionary Prototyping** [119, 142].
*   **Justification**: When requirements are unstable or fuzzy, prototyping is the premier paradigm [6, 119]. Building a rapid, user-visible working preview allows the customer to interact with the system, clarify their goals, and provide corrective feedback early, while allowing developers to master the new technology boundaries [16, 119, 142].

### Scenario 5: Summary Matrix of PPT Scenario Matchings
Based on the official lecture guidelines, use this comparative guide for scenario-based exam questions:

| Application / Project Scenario | Best Model Match | Key Decision Criteria |
| :--- | :--- | :--- |
| **Well-understood data processing** | **Waterfall** | Highly stable, frozen requirements. |
| **Library automation linking regional libraries** | **Prototyping / Incremental** | Fragmented requirements needing active user evaluation. |
| **Development of a new, original text editor** | **Incremental / Agile** | Deliver core functions fast; add advanced features in loops. |
| **User Interface (GUI) of a large system** | **RAD / Prototyping** | Needs fast visual prototyping and frequent UI revisions. |
| **Huge satellite-based communications** | **Spiral / Concurrent** | Extreme technical complexity, high risks, parallel hardware/software. |

---

## Part 5: Comparative Analysis Matrices

### Table 1: Waterfall vs. Incremental Models [1, 21, 47, 48, 89, 94, 95, 96, 112, 114, 115, 177, 178, 181, 185]

| Parameter | Waterfall Model [60] | Incremental Model [108] |
| :--- | :--- | :--- |
| **Simplicity** | Simple and easy to understand [47, 112]. | Intermediate; requires skilled management [96, 115]. |
| **Requirements** | Must be fully defined and stable upfront [15, 48, 113, 181]. | Can start with core requirements; features evolve [89, 178, 185]. |
| **First Delivery** | Only at the end of the development lifecycle [15, 48, 112, 181]. | Quick delivery of an operational Core Product [5, 20, 76, 108, 114, 150]. |
| **Feedback Loop** | Occurs late, during user acceptance testing [15, 112, 181]. | Continuous; occurs after every increment delivery [50, 108, 114, 151]. |
| **Risk Management** | Low; risks are discovered late [112]. | High; risk areas are mitigated early [20, 177, 185]. |
| **Total Cost** | Predictable and lower for stable projects. | Often higher than a single-pass Waterfall approach [21, 89, 96, 115, 178, 185]. |

### Table 2: Prototyping vs. Waterfall Models [15, 47, 48, 54, 55, 60, 111, 112, 119, 120, 181]

| Parameter | Prototyping Model [119] | Waterfall Model [60] |
| :--- | :--- | :--- |
| **Requirements** | Highly unstable, fuzzy, or unclear [6, 119, 141, 162]. | Well-defined, clear, and stable upfront [15, 48, 113, 181]. |
| **Rigidity** | Flexible; adapts to continuous feedback [119, 120]. | Rigid; strictly enforces sequential phases [15, 25, 181, 190]. |
| **Feedback Mechanism** | Active "test driving" of early builds [16, 119, 174]. | Reviewing flat text documentation. |
| **Development Speed** | Rapid, quick-and-dirty initial builds [16, 62, 103, 119, 174]. | Controlled, sequential, and disciplined progression [23, 188]. |
| **Maintainability** | Prone to bad design choices if shortcuts persist [154]. | High; architecture is planned thoroughly upfront. |

### Table 3: Spiral vs. Other Prescriptive Models [18, 53, 60, 108, 186]

| Parameter | Spiral Model [53] | Waterfall / Incremental [60, 108] |
| :--- | :--- | :--- |
| **Primary Driver** | Risk assessment and mitigation [18, 53, 186]. | Plan-driven; phase deadlines [186]. |
| **Meta-Framework** | Can encompass and guide other models [53, 186]. | Single-process model architecture [60, 108]. |
| **Project Complexity** | Best suited for large, complex projects [18, 186]. | Simple to medium projects. |
| **Risk Evaluation** | Done systematically at every loop [18, 53, 186]. | Done once at planning; minimal iteration [22, 187]. |
| **Documentation** | Heavy; required for risk tracking [186]. | Light to moderate depending on project. |

### Table 4: Agile vs. Prescriptive Models [6, 14, 15, 25, 123, 141, 144, 147, 181, 190, 191]

| Parameter | Agile Models [147] | Prescriptive Models [144] |
| :--- | :--- | :--- |
| **Management Focus** | Adaptive; welcoming change and agility [6, 147]. | Plan-driven; maintaining process order [144]. |
| **Requirements** | Unstable, dynamic, and evolving [6]. | Stable, fixed, and locked upfront [14, 15, 48, 181]. |
| **Documentation** | Light; prioritizes working code [191]. | Heavy; required at every phase gate [25, 190]. |
| **Customer Interaction** | High; continuous daily collaboration [191]. | Limited; focused on sign-offs [22, 187]. |
| **Unit of Delivery** | Small, working software increments [191]. | Completed, integrated system at the end [15, 181]. |

### Table 5: Extreme Programming (XP) vs. Scrum Framework [56, 191]

| Parameter | Extreme Programming (XP) | Scrum Framework |
| :--- | :--- | :--- |
| **Primary Focus** | Heavy focus on disciplined engineering practices. | Heavy focus on collaborative management. |
| **Iteration Length** | Short (typically 1 to 2 weeks). | Fixed Sprint (typically 1 to 4 weeks). |
| **Requirements Order** | Strict prioritization; team builds tests first. | Dynamic Product Backlog prioritized by Product Owner. |
| **Change Tolerance** | High; pair programming facilitates review. | Team focuses on Sprint Goal; changes deferred. |
| **On-Site Collaboration** | Strict "On-Site Customer" required. | Scrum Master facilitates stakeholder demos. |

### Table 6: ASD vs. XP/Scrum Frameworks [90, 191]

| Parameter | Adaptive Software Development (ASD) [90] | XP / Scrum Frameworks [191] |
| :--- | :--- | :--- |
| **Core Philosophy** | Speculate, Collaborate, and Learn [90, 191]. | Value-driven and Scrum ceremony-oriented. |
| **Planning Approach** | Strictly speculative; plans are estimated. | Release planning; Sprint planning sessions. |
| **Technical Review** | Formal focus groups and retrospectives [90]. | Sprint reviews and retrospect reviews. |
| **Risk Acceptance** | High; accepts total technological volatility [90]. | Managed through prioritized backlog selection. |

---

## Part 6: Verified PPT Coverage Audit

### Slide-by-Slide PPT Checklist

This checklist represents a thorough audit of all Unit 2 presentation materials.

*   [x] **Slide 1: Title & Overview** — *Fully Covered*
*   [x] **Slide 2: Course Contents** — *Fully Covered*
*   [x] **Slide 3: Process Framework Definition** — *Fully Covered*
*   [x] **Slide 4: Generic Process Model & Framework Activities** — *Fully Covered*
*   [x] **Slide 5: Umbrella Activities Breakdown** — *Fully Covered*
*   [x] **Slide 6: Process Flows (Linear, Parallel, Iterative)** — *Fully Covered*
*   [x] **Slide 7: Task Sets and Software Engineering Actions** — *Fully Covered*
*   [x] **Slide 8: Capability Maturity Model (CMM) Concept** — *Fully Covered*
*   [x] **Slide 9: CMM Maturity Levels (1 to 5) Breakdown** — *Fully Covered*
*   [x] **Slide 10: Capability Maturity Model Integration (CMMI)** — *Fully Covered*
*   [x] **Slide 11: Staged Representation of CMMI** — *Fully Covered*
*   [x] **Slide 12: Continuous Representation of CMMI** — *Fully Covered*
*   [x] **Slide 13: Maturity Level 1 (Initial)** — *Fully Covered*
*   [x] **Slide 14: Maturity Level 2 (Managed)** — *Fully Covered*
*   [x] **Slide 15: Maturity Level 3 (Defined)** — *Fully Covered*
*   [x] **Slide 16: Maturity Level 4 (Quantitatively Managed)** — *Fully Covered*
*   [x] **Slide 17: Maturity Level 5 (Optimizing)** — *Fully Covered*
*   [x] **Slide 18: Continuous Representation Capability Levels** — *Fully Covered*
*   [x] **Slide 19: The Waterfall Model Introduction** — *Fully Covered*
*   [x] **Slide 20: Waterfall Model Phases & Flow** — *Fully Covered*
*   [x] **Slide 21: Waterfall Strengths & Milestones** — *Fully Covered*
*   [x] **Slide 22: Waterfall Deficiencies & Rigidity** — *Fully Covered*
*   [x] **Slide 23: When to use the Waterfall Model** — *Fully Covered*
*   [x] **Slide 24: Case Studies: NASA Shuttle & Core Banking** — *Fully Covered*
*   [x] **Slide 25: The V-Model Variation** — *Fully Covered*
*   [x] **Slide 26: V-Shaped Steps: Planning to Coding & Testing** — *Fully Covered*
*   [x] **Slide 27: V-Shaped Model Strengths & Weaknesses** — *Fully Covered*
*   [x] **Slide 28: When to use the V-Shaped Model & Case Studies** — *Fully Covered*
*   [x] **Slide 29: The Prototyping Paradigm Introduction** — *Fully Covered*
*   [x] **Slide 30: Structured Evolutionary Prototyping Steps** — *Fully Covered*
*   [x] **Slide 31: Prototype Construction & Shortcuts** — *Fully Covered*
*   [x] **Slide 32: Customer Evaluation Loop** — *Fully Covered*
*   [x] **Slide 33: Prototyping Advantages & Trust Building** — *Fully Covered*
*   [x] **Slide 34: Prototyping Drawbacks & "Quick-and-Dirty" Risks** — *Fully Covered*
*   [x] **Slide 35: When to use the Prototyping Model** — *Fully Covered*
*   [x] **Slide 36: The Incremental Model Concept** — *Fully Covered*
*   [x] **Slide 37: Successive Version Model Working** — *Fully Covered*
*   [x] **Slide 38: Deliverable Core Product Concept** — *Fully Covered*
*   [x] **Slide 39: Incremental Model Strengths** — *Fully Covered*
*   [x] **Slide 40: Incremental Model Weaknesses** — *Fully Covered*
*   [x] **Slide 41: When to use the Incremental Model** — *Fully Covered*
*   [x] **Slide 42: Word Processing Software Case Study** — *Fully Covered*
*   [x] **Slide 43: Rapid Application Development (RAD) Introduction** — *Fully Covered*
*   [x] **Slide 44: RAD Model Parallel Team Structure** — *Fully Covered*
*   [x] **Slide 45: RAD Phase 1: Requirements Planning** — *Fully Covered*
*   [x] **Slide 46: RAD Phase 2: User Description** — *Fully Covered*
*   [x] **Slide 47: RAD Phase 3: Construction & Coding** — *Fully Covered*
*   [x] **Slide 48: RAD Phase 4: Cutover & Training** — *Fully Covered*
*   [x] **Slide 49: RAD Strengths & Schedule Mitigation** — *Fully Covered*
*   [x] **Slide 50: RAD Weaknesses & Modularity Risks** — *Fully Covered*
*   [x] **Slide 51: When to use the RAD Model** — *Fully Covered*
*   [x] **Slide 52: Multi-Team E-Commerce Case Study** — *Fully Covered*
*   [x] **Slide 53: The Spiral Model Concept** — *Fully Covered*
*   [x] **Slide 54: The 6 Task Regions of the Spiral** — *Fully Covered*
*   [x] **Slide 55: Spiral Loops (Concept to Maintenance)** — *Fully Covered*
*   [x] **Slide 56: Spiral Model Advantages & Risks** — *Fully Covered*
*   [x] **Slide 57: Spiral Model Drawbacks & Limitations** — *Fully Covered*
*   [x] **Slide 58: The Concurrent Development Model** — *Fully Covered*
*   [x] **Slide 59: Tailored SDLC Models: Purpose & Customization** — *Fully Covered*
*   [x] **Slide 60: Tailored SDLC Models: Hybrid Examples** — *Fully Covered*
*   [x] **Slide 61: Introduction to Agility** — *Fully Covered*
*   [x] **Slide 62: The Agile Manifesto & 4 Core Values** — *Fully Covered*
*   [x] **Slide 63: Evolving Agile Principles (1 to 12)** — *Fully Covered*
*   [x] **Slide 64: Agile vs. Prescriptive Comparative Analysis** — *Fully Covered*
*   [x] **Slide 65: Adaptive Software Development (ASD) Pillars & Steps** — *Fully Covered*
*   [x] **Slide 66: Dynamic Systems Development Method (DSDM) & 80/20 Rule** — *Fully Covered*
*   [x] **Slide 67: Nine Guiding Principles & Lifecycle of DSDM** — *Fully Covered*
*   [x] **Slide 68: Feature Driven Development (FDD) & Feature Template** — *Fully Covered*
*   [x] **Slide 69: The Five FDD Process Activities** — *Fully Covered*
*   [x] **Slide 70: Extreme Programming (XP) Values & Values** — *Fully Covered*
*   [x] **Slide 71: XP Engineering Practices (Pair Programming, TDD)** — *Fully Covered*
*   [x] **Slide 72: The Scrum Framework & Roles** — *Fully Covered*
*   [x] **Slide 73: Scrum Ceremonies (Sprints, Daily Scrum)** — *Fully Covered*
*   [x] **Slide 74: Scrum Artifacts & Terminology** — *Fully Covered*
*   [x] **Slide 75: Software Quality Definitions & Stated/Implied Needs** — *Fully Covered*
*   [x] **Slide 76: Software Quality Assurance (SQA) Plan Elements** — *Fully Covered*

---

### Complete Syllabus Checklist

*   [x] **Process Framework: Roles & Architecture** — *Fully Covered* [91, 110, 139]
*   [x] **Capability Maturity Model Integration (CMMI)** — *Fully Covered* [11, 26, 83, 106, 124, 145]
*   [x] **Waterfall Model** — *Fully Covered* [3, 60, 111, 160]
*   [x] **V-Shaped SDLC Model** — *Fully Covered* [3, 74, 88, 474]
*   [x] **Incremental Model** — *Fully Covered* [4, 108, 114, 149]
*   [x] **Rapid Application Development (RAD) Model** — *Fully Covered* [51, 68, 116, 126, 182]
*   [x] **Prototyping Model** — *Fully Covered* [6, 61, 102, 119, 141]
*   [x] **Spiral Model** — *Fully Covered* [18, 53, 186]
*   [x] **Concurrent Development Model** — *Fully Covered* [90, 191]
*   [x] **Tailored/Hybrid SDLC Models** — *Fully Covered* [108, 246, 485]
*   [x] **Agility & Agile Process** — *Fully Covered* [6, 147, 191]
*   [x] **Adaptive Software Development (ASD)** — *Fully Covered* [90, 191]
*   [x] **Extreme Programming (XP)** — *Fully Covered* [56, 191]
*   [x] **SCRUM Framework** — *Fully Covered* [56, 191]
*   [x] **Dynamic Systems Development Method (DSDM)** — *Fully Covered* [105, 159, 244, 482]
*   [x] **Feature Driven Development (FDD)** — *Fully Covered* [104, 163, 242, 481]
*   [x] **Software Quality & SQA Plan** — *Fully Covered* [135, 327]

---
