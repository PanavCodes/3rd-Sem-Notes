# Software Engineering Unit 2 Study Guide: Prescriptive & Agile Process Models

---

## Unit 2 At a Glance

*   **Prescriptive vs. Agile Paradigms**: This unit contrasts structured, plan-driven **prescriptive process models** (built for predictability, stability, and disciplined phases) with lightweight, customer-centric **agile process models** (engineered for adaptability, rapid iteration, and active customer feedback).
*   **Process Assessment & Quality Assurance**: Processes can be measured and matured using the **Capability Maturity Model Integration (CMMI)** framework. A systematic **Software Quality Assurance (SQA) Plan** ensures that both explicit requirements (stated in documents) and implicit user expectations are completely met.
*   **Model Selection & Tailoring**: No single model is a silver bullet; success lies in assessing project constraints (risks, team skills, requirements stability) and selecting the right model, or designing a **tailored hybrid model** (such as a Spiral-Waterfall or Incremental-V hybrid) to mitigate risks.

---

## Core Concepts

### Process Framework: Roles & Architecture

A **Process Framework** is the foundational structure of a software engineering process that establishes a small number of core activities applicable to all software projects, regardless of their size or complexity. It establishes the organizational architecture defining **who** does **what**, **when**, and **how** to achieve project success.

#### The Four-Layer Process Hierarchy
The structural layers of a process framework are nested as follows:
1.  **Framework Activities**: High-level development milestones (e.g., Communication, Planning) that form the overall software process flow.
2.  **Software Engineering Actions**: A collection of cohesive tasks that produce a major software work product (e.g., Requirements Elicitation, Architectural Design).
3.  **Task Sets**: The actual granular work steps, work products, quality assurance points, and project milestones that populate each engineering action.
4.  **Umbrella Activities**: High-level management and quality control processes that run concurrently across all framework activities.

#### The Five Framework Activities
*   **Communication**: Early stakeholder collaboration, meetings, and initial requirement gathering.
*   **Planning**: Estimating costs, allocating resources, scheduling milestones, and assessing project risks.
*   **Modeling**: Designing blueprints of the software (e.g., architectures, algorithms, data structures).
*   **Construction**: Code generation and intensive verification testing (unit and integration testing).
*   **Deployment**: Delivering the operating software to the client, collecting feedback, and supporting installation.

💡 **Mnemonic to Memorize Framework Activities**: **C**oding **P**lans **M**ake **C**omputers **D**eliver
*   **C**ommunication
*   **P**lanning
*   **M**odeling
*   **C**onstruction
*   **D**eployment

#### The Eight Umbrella Activities
*   **Software Project Tracking and Control**: Monitoring development milestones against the project schedule and adjusting plans for deviations.
*   **Risk Management**: Identifying, assessing, and mitigating risks that threaten project success.
*   **Software Quality Assurance (SQA)**: Performing audits to ensure compliance with standard engineering practices.
*   **Software Configuration Management (SCM)**: Controlling, tracking, and managing changes made to source code, documentation, and data structures.
*   **Technical Reviews**: Conducting structured peer assessments to catch and resolve design/code defects early.
*   **Measurement**: Collecting process, project, and product metrics to evaluate efficiency and quality.
*   **Reusability Management**: Defining guidelines for constructing and utilizing reusable software components.
*   **Work Product Preparation**: Designing documents, developer logs, and installation guides.

---

### Capability Maturity Model Integration (CMMI)

**CMMI** is a comprehensive process meta-model developed by the Software Engineering Institute (SEI) that provides a quantitative framework to evaluate and improve an organization's software development capabilities. It integrated previously fragmented models (Systems Engineering, Software CMM, and People CMM) into a single unified roadmap.

#### The Dual Representations of CMMI
CMMI allows organizations to improve their processes through two distinct architectural representations:

1.  **Staged Representation**:
    *   **Focus**: Evaluates the maturity of the *entire organization*.
    *   **Structure**: Uses **5 pre-defined maturity levels**.
    *   **Path**: Requires achieving all Process Areas (PAs) of a level before moving to the next.
    *   **Usage**: Ideal for global organization-to-organization benchmarking and marketing.
2.  **Continuous Representation**:
    *   **Focus**: Evaluates individual *Process Areas (PAs)* in isolation.
    *   **Structure**: Uses **6 capability levels** (Level 0 to Level 5).
    *   **Path**: Allows complete flexibility to target and raise the capability of specific process areas depending on business goals.
    *   **Usage**: Ideal for targeted risk reduction and custom process tuning.

#### The 5 Staged Maturity Levels
1.  **Level 1: Initial**: Processes are chaotic, ad-hoc, and poorly controlled. Project success relies on the heroics of individuals. No Process Areas (PAs) are defined.
2.  **Level 2: Managed (Repeatable)**: Basic project management disciplines (requirements, cost, schedule, and tracking) are established so past successes can be repeated.
    *   *Key Process Areas (PAs)*: Requirements Management (REQM), Project Planning (PP), Project Monitoring & Control (PMC), Supplier Agreement Management (SAM), Process and Product Quality Assurance (PPQA), Measurement and Analysis (MA), Configuration Management (CM).
3.  **Level 3: Defined**: Software engineering and management processes are standard, documented, and integrated into a standard organization-wide process.
    *   *Key Process Areas (PAs)*: Peer Reviews, Intergroup Coordination, Software Product Engineering, Integrated Software Management, Training Program, Organization Process Definition, Organization Process Focus.
4.  **Level 4: Quantitatively Managed**: Software processes and products are quantitatively measured, understood, and controlled using statistical techniques.
    *   *Key Process Areas (PAs)*: Organizational Process Performance (OPP), Quantitative Project Management (QPM).
5.  **Level 5: Optimizing**: Quantitative feedback mechanisms are used to drive continuous process improvement and pilot innovative technologies.
    *   *Key Process Areas (PAs)*: Causal Analysis and Resolution (CAR), Organizational Innovation and Deployment (OID).

🧠 **Mnemonic for Staged Maturity Levels**: **I** **M**ake **D**evices **Q**uite **O**ptimal
*   **I**nitial (Level 1)
*   **M**anaged (Level 2)
*   **D**efined (Level 3)
*   **Q**uantitatively Managed (Level 4)
*   **O**ptimizng (Level 5)

#### The 6 Continuous Capability Levels
*   **Level 0: Incomplete**: The process is not performed or fails to achieve its core goals.
*   **Level 1: Performed**: The process is executed, and work tasks are completed, but goals are unstable.
*   **Level 2: Managed**: The process is planned, monitored, controlled, and audited for conformance.
*   **Level 3: Defined**: The process is customized using standard organizational tailoring guidelines.
*   **Level 4: Quantitatively Managed**: The process is controlled using precise statistical and quantitative metrics.
*   **Level 5: Optimizing**: The process is continuously refined to meet changing business goals.

---

### The Waterfall Model (Linear Sequential Model)

The **Waterfall Model** (also known as the **Classic Life Cycle**) is a plan-driven software process model that proposes a systematic, linear approach to software development, progressing strictly through a sequence of non-overlapping phases.

#### Step-by-Step Execution Process
1.  **Requirements Analysis (Communication)**: Gather all software goals and user requirements through collaborative sessions, document them in the **Software Requirements Specification (SRS)**, and freeze them.
2.  **System Design (Modeling)**: Translate the SRS into high-level and detailed blueprints (software architectures, database schemas, and algorithms).
3.  **Implementation (Construction - Coding)**: Write the actual source code according to the design models.
4.  **Testing**: Integrate the code components and test them (unit, integration, and system testing) to identify defects.
5.  **Deployment**: Deliver the fully verified, integrated, and complete software package to the customer.
6.  **Maintenance**: Perform post-delivery bug fixes, adaptations, and optimizations to keep the system operational.

#### Deficiencies & Risk Statements
*   **Inflexible upfront requirements**: Assumes all user needs are stable and can be finalized at the start.
*   **No working previews**: The customer does not see a functional system until deployment, making late changes extremely expensive.
*   **False sense of progress**: Project tracking is based on document completion rather than operating code.
*   **Late-stage integration ("Big Bang")**: Component integration happens late, exposing critical interface flaws near the deadline.

🧱 **Analogy to Memorize**: **Building a Concrete Bridge**
You must design the bridge fully, construct the foundation, pour the concrete pillars, and then lay the asphalt. You cannot lay asphalt until the pillars are dry. Once built, changing the bridge's design is astronomically expensive.

---

### The V-Shaped SDLC Model (Verification & Validation Variant)

The **V-Shaped Model** is a prominent variation of the Waterfall model that highlights the direct relationship between development phases (Verification) and corresponding testing phases (Validation), planning testing activities in parallel with early design.

#### Step-by-Step Execution Process
```
Project Planning (V1) -----------------------------> Production & Maintenance (V9)
  └─ Requirements Analysis (V2) --------------> System/Acceptance Testing (V8)
       └─ Architectural Design (V3) --------> Integration Testing (V7)
            └─ Detailed Design (V4) ------> Unit Testing (V6)
                 └─ Coding & Production (V5 - Vertex of the V)
```
1.  **Project Planning**: Estimate resources and schedule the timeline.
2.  **Requirements Analysis**: Define the complete and unambiguous specifications of the software.
3.  **Architectural Design**: Map the high-level software structures and interfaces.
4.  **Detailed Design**: Create specific algorithms for each component.
5.  **Coding (Vertex of the V)**: Translate detailed algorithms into executable code.
6.  **Unit Testing**: Verify that individual modules exhibit correct behavior.
7.  **Integration Testing**: Verify that interconnected modules communicate correctly.
8.  **System & Acceptance Testing**: Verify the entire integrated system operates within the target environment.
9.  **Production & Maintenance**: Perform post-delivery optimizations and bug fixes.

#### Key Principles, Advantages & Disadvantages
*   **Key Principles**: Integrated Verification and Validation (V&V), Early Test Planning, and testable deliverables.
*   **Advantages**: Highly structured and easy to use; early test planning reduces bug leakage; clear milestone tracking.
*   **Disadvantages**: Rigid; lacks phase-overlapping or cyclical iterations; poor risk management; cannot handle shifting requirements.
*   **When to Use**: Best for highly reliable and safety-critical systems (e.g., medical devices, flight control) with completely stable, well-understood technology and requirements.

---

### The Incremental Model (Successive Version Model)

The **Incremental Model** is an evolutionary SDLC process where requirements are broken down into independent functional modules, each developed through a linear process flow to deliver working software in successive releases.

#### Step-by-Step Execution Process
```
[Increment 1] Communication -> Planning -> Modeling -> Coding -> Testing -> CORE PRODUCT
[Increment 2] Communication -> Planning -> Modeling -> Coding -> Testing -> VERSION 2
[Increment 3] Communication -> Planning -> Modeling -> Coding -> Testing -> VERSION 3
```
1.  **System-Level Requirements Definition**: Gather global software goals and baseline architecture.
2.  **Prioritization of Requirements**: Prioritize functional requirements, assigning critical or high-risk features to early increments.
3.  **Core Product Development (Increment 1)**: Develop, verify, and release a stripped-down yet operational "Core Product" containing essential features.
4.  **Feedback and Planning**: The customer test-drives the core build and provides corrective feedback.
5.  **Subsequent Increments**: Design, code, and test additional features, integrating them into the existing core.
6.  **Final Release**: Repeat the cycle until the complete, integrated system is delivered.

#### Key Principles, Advantages & Disadvantages
*   **Key Principles**: Delivery of operational builds, prioritised development, and iterative feedback loops.
*   **Advantages**: Delivers an operational product to market very early; reduces the risk of overall project failure; accommodates evolving requirements easily.
*   **Disadvantages**: Requires expert global architecture planning upfront to support future integrations; total project cost is often higher than a single-pass Waterfall approach.
*   **When to Use**: Best when a product must go to market quickly, staffing is limited, or core requirements are stable but auxiliary features are expected to evolve.

---

### Rapid Application Development (RAD) Model

The **RAD Model** is a high-speed incremental process model that aims to construct a complete operational software system within an extremely tight "time-box" of 60 to 90 days.

#### Step-by-Step Execution Process
1.  **Requirements Planning**: Conduct highly collaborative workshop sessions (Joint Application Design - JAD) to establish business goals and high-level requirements.
2.  **User Description**: Utilize automated modeling tools to capture detailed functional layouts, database models, and user interface designs directly from active user reviews.
3.  **Construction**: Deploy parallel teams to build modular components concurrently using code generators, screen builders, and component reuse libraries.
4.  **Cutover**: Integrate parallel modules, perform final user acceptance testing, run database migrations, train users, and launch.

#### Key Principles, Advantages & Disadvantages
*   **Key Principles**: Parallel engineering teams, component reuse, and strict time-boxing.
*   **Advantages**: Drastically reduces development time-to-market; lower overall cost due to shortened schedules; active customer participation ensuring satisfaction.
*   **Disadvantages**: Requires a massive pool of highly skilled developers; depends heavily on developer-customer commitment; fails if the software cannot be cleanly modularized.
*   **When to Use**: Best for business-oriented systems with well-understood requirements, high modularity, and high availability of automated modeling tools.

🏗️ **Analogy to Memorize**: **Modular House Construction**
Instead of building a house sequentially, different factory crews build the kitchen, bathrooms, and bedrooms concurrently in 60-90 days, then transport and assemble them on-site.

---

### The Prototyping Model (Structured Evolutionary Prototyping)

The **Prototyping Model** is an evolutionary SDLC model designed to quickly construct a physical working mockup (prototype) of a system to help clarify and define stable user requirements.

#### Step-by-Step Execution Process
1.  **Initial Communication**: Gather basic objectives and define fuzzy customer expectations.
2.  **Quick Design**: Focus strictly on user-visible layouts, navigation paths, and input screens while bypassing deep backend architecture.
3.  **Prototype Construction**: Rapidly assemble a functional preview using development "shortcuts" (e.g., dummy functions, hardcoded tables).
4.  **Customer Evaluation**: The client test-drives the mockup and identifies omissions, corrections, or errors.
5.  **Iteration and Refinement**: The team refines the prototype iteratively based on feedback.
6.  **Final Conversion**: Once requirements are clear, the prototype is either thrown away (throwaway prototyping) to engineer production code, or heavily refactored (evolutionary prototyping) to meet architectural standards.

#### Key Principles, Advantages & Disadvantages
*   **Key Principles**: User-visible feedback, active experimentation, and iterative requirement clarification.
*   **Advantages**: Drastically reduces requirement misunderstandings; builds high stakeholder trust; catches defects extremely early.
*   **Disadvantages**: Leads to long-term maintainability risks if the "quick-and-dirty" prototype is pushed prematurely to production; feedback loops can repeat endlessly without closure.
*   **When to Use**: Excellent for systems with highly interactive user interfaces (e.g., web portals, mobile layouts) or when requirements are completely unstable or unknown.

---

### The Spiral Model (Risk-Driven Evolutionary Model)

The **Spiral Model** is an evolutionary, risk-driven process model that combines the iterative feedback of prototyping with the controlled, systematic steps of the Waterfall model. It acts as a **meta-model** because it can encompass other models.

#### Step-by-Step Execution Process (Quadrants)
Each loop of the spiral progresses through four critical quadrants:
1.  **Determine Objectives, Alternatives, and Constraints**: Define the specific goals of the current loop, alternative solutions, and operational boundaries.
2.  **Evaluate Alternatives and Identify/Resolve Risks**: Perform intense risk assessment and build rapid prototypes to eliminate technical and business uncertainties.
3.  **Develop and Verify Next-Level Product**: Engineer, code, and thoroughly test the software increment designed for this loop.
4.  **Plan Next Phases**: Review the current progress, gain customer sign-off, and plan the objectives for the next loop.

#### The Four Loops of Development
*   **Concept Development Loop**: Scoping and exploring initial product viability.
*   **New Product Development Loop**: Designing and engineering the first official version.
*   **Product Enhancement Loop**: Designing and integrating advanced features.
*   **Product Maintenance Loop**: Long-term patching and technological adaptation.

🌪️ **Analogy to Memorize**: **Hurricane Tracking**
A meteorologist starts with a broad, wide forecasting ring (concept development loop) and spirals tighter and tighter toward the target eye (final production release) as atmospheric data (risk assessment) becomes clear.

---

### The Concurrent Development Model (Concurrent Engineering)

The **Concurrent Development Model** represents a project as a network of framework activities, actions, and task sets that exist simultaneously. Each activity is treated as a state machine that transitions through multiple states based on event triggers.

#### Step-by-Step State Transitions
Each engineering activity (e.g., Modeling) progresses through these states:
1.  **Awaiting Tasks**: The activity is idle, waiting for upstream dependencies.
2.  **Under Development**: Work is active and ongoing.
3.  **Under Review**: The work product is undergoing technical evaluation or testing.
4.  **Under Revision**: Defects have been found, and the team is correcting the work product.
5.  **Baselined**: The work product is approved, frozen, and ready to guide downstream tasks.
6.  **Done**: The activity is successfully finalized.

#### Key Principles, Advantages & Disadvantages
*   **Key Principles**: Parallel component engineering, event-driven transitions, and state-machine tracking.
*   **Advantages**: Drastically cuts time-to-market by enabling parallel development across different teams; provides a highly realistic, fluid view of software projects.
*   **Disadvantages**: Extremely complex to manage; requires impeccable coordination, communication, and software configuration management (SCM).

---

### Tailored/Hybrid SDLC Models

In real-world software engineering, **one size does not fit all**. Pure models represent theoretical ideals. Teams often combine elements of different models to balance risks, speed, and reliability.

#### Tailoring Drivers
*   **UI Risk vs. Algorithmic Rigour**: Highly interactive frontends require fast prototyping, while backend processing requires waterfall-like rigor.
*   **Time-to-Market vs. High Reliability**: Products must be delivered in fast increments but require extensive validation.

#### Hybrid Model Examples
*   **Spiral / Waterfall Hybrid**: A project begins with the Spiral model's intensive risk assessment. Once core architectural risks are resolved, the team transitions to a stable, low-overhead Waterfall process.
*   **Incremental / V-Shaped Hybrid**: Software features are delivered in successive increments. However, each increment is engineered using the V-shaped model's planning-for-testing discipline to guarantee extreme reliability.

---

### Agility & Agile Process

**Agility** is a dynamic, people-centric, and iterative approach to software engineering that prioritizes rapid delivery of operational software, close collaboration with stakeholders, and immediate adaptation to changing requirements.

#### The 4 Core Values of the Agile Manifesto
1.  **Individuals and interactions** over processes and tools.
2.  **Working software** over comprehensive documentation.
3.  **Customer collaboration** over contract negotiation.
4.  **Responding to change** over following a plan.

#### The 12 Agile Principles
1.  Satisfy the customer through early and continuous delivery of valuable software.
2.  Welcome changing requirements, even late in development, for competitive advantage.
3.  Deliver working software frequently (weeks to months, preferring shorter timescales).
4.  Business people and developers must work together daily throughout the project.
5.  Build projects around motivated individuals; give support and trust them.
6.  Convey information via face-to-face conversation.
7.  Working software is the primary measure of progress.
8.  Promote sustainable development; maintain a constant, indefinte pace.
9.  Continuous attention to technical excellence and good design enhances agility.
10. Simplicity—the art of maximizing the amount of work not done—is essential.
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, reflect and tune team behavior to increase effectiveness.

---

### Adaptive Software Development (ASD)

**Adaptive Software Development (ASD)** is an agile process model that applies evolutionary, collaborative techniques to build complex, high-speed software systems. It directly evolved from Rapid Application Development (RAD).

#### The 3 Core Pillars of ASD
*   **Speculation**: Traditional planning is replaced by speculative forecasting, accepting that requirements are too volatile to lock in. It outlines release dates, cycle time-boxes, and high-level objectives.
*   **Collaboration**: Emphasizes cooperative teamwork among developers, customers, and domain experts, balancing strict engineering rules with human creativity.
*   **Learning**: The team reflects and adapts continuously. Learning occurs via **Technical Reviews**, **Customer Focus Groups**, and **Project Postmortems**.

#### The 8 Step execution Process
1.  **Project Initialization**: Define the baseline mission and intent of the project.
2.  **Determine Project Time-Box**: Estimate the overall calendar duration.
3.  **Determine Optimal Cycles**: Map out the total number of iterations and set the time-box for each.
4.  **Write Objective Statements**: Write explicit, measurable goal statements for each individual cycle.
5.  **Assign Primary Components**: Allocate functional software components to specific cycles.
6.  **Develop Project Task List**: Detail all required coding, design, and testing tasks.
7.  **Review Cycle Success**: Gather customer feedback via focus groups and conduct technical reviews.
8.  **Plan the Next Cycle**: Adapt and refine the next speculative cycle plan based on actual feedback.

🔄 **Mnemonic to Memorize ASD Pillars**: **S**oftware **C**reates **L**earning
*   **S**peculation
*   **C**ollaboration
*   **L**earning

---

### Extreme Programming (XP)

**Extreme Programming (XP)** is a highly influential agile framework focusing on delivering high-quality code rapidly through intensive engineering practices and continuous collaboration.

#### The 5 Core Values of XP
*   **Communication**: Informal, active collaboration between developers and customers.
*   **Simplicity**: Building the simplest design that fulfills today's requirements, avoiding over-engineering.
*   **Feedback**: Continuous feedback through automated testing, short releases, and daily meetings.
*   **Courage**: Willingness to refactor bad code, discard failing designs, and tackle hard problems.
*   **Respect**: Mutual trust and collaboration across the development team.

#### The 12 Core Practices of XP
1.  **The Planning Game**: Collaborative release planning using user story estimates.
2.  **Small Releases**: Frequent, low-risk deployment of functional increments.
3.  **System Metaphor**: Utilizing a shared naming convention or story to guide consistent design.
4.  **Simple Design**: Writing clean, straightforward code only to fulfill active requirements.
5.  **Continuous Testing**: Writing automated unit tests *before* writing application code (**Test-First Development**).
6.  **Refactoring**: Continuously cleaning, simplifying, and optimizing code architecture without changing its functional behavior.
7.  **Pair Programming**: Two developers work together at one workstation (one "driver" writing code; one "navigator" reviewing in real-time).
8.  **Collective Code Ownership**: Empowering any developer to edit and improve any line of code in the repository.
9.  **Continuous Integration**: Integrating and building the complete software system multiple times daily.
10. **40-Hour Week**: Preventing developer burnout to maintain a sustainable, highly productive pace.
11. **On-Site Customer**: An active user representative sits full-time with the team to resolve requirements.
12. **Coding Standards**: Adhering to strict, uniform formatting and style guidelines.

#### Step-by-Step Lifecycle
1.  **Planning**: Customers write **User Stories**; developers estimate effort and plan release boundaries.
2.  **Design**: Design is kept simple. Teams use **Class-Responsibility-Collaborator (CRC) Cards** to map objects. If technical blockers occur, teams code a **Spike Solution** (a rapid, throwaway technical prototype).
3.  **Coding**: Pair programming is utilized. Automated unit tests are written first.
4.  **Testing**: All unit tests are executed continuously; customers write and execute **Acceptance Tests** to sign off.

---

### SCRUM Framework

**Scrum** is an agile management framework designed to organize and manage software development in highly volatile environments through structured roles, time-boxed events, and artifacts.

#### The 3 Scrum Roles
*   **Product Owner**: Represents customer interests. Owns, refines, and prioritizes the **Product Backlog** and defines acceptance criteria.
*   **Scrum Master**: A servant-leader who facilitates events, ensures Agile principles are followed, and removes blockers.
*   **Development Team**: A cross-functional, self-organizing team (typically 5 to 9 members) that builds and tests the product.

#### The 3 Scrum Artifacts
*   **Product Backlog**: A dynamic, master list of all features, enhancements, and bugs. New requirements or changes can only enter the project here.
*   **Sprint Backlog**: A subset of high-priority backlog items selected by the team to be completed during the active sprint.
*   **Product Increment**: The fully functional, integrated, and validated software package delivered at sprint end.

#### The 5 Scrum Events
1.  **Sprint**: A strict, time-boxed iteration (typically 1 to 4 weeks) where development occurs. Requirements are completely frozen inside the Sprint; changes are strictly forbidden.
2.  **Sprint Planning**: A collaborative session where the Product Owner and Team select items for the Sprint Backlog and define the Sprint Goal.
3.  **Daily Scrum**: A brief, daily 15-minute meeting where developers coordinate and answer three questions:
    *   *What did I do since the last meeting?*
    *   *What will I do before the next meeting?*
    *   *What obstacles are blocking my progress?*
4.  **Sprint Review (Demo)**: A demo session at sprint end where the team presents the operating increment to stakeholders.
5.  **Sprint Retrospective**: An internal reflection session to optimize team processes and collaboration for future Sprints.

---

### Dynamic Systems Development Method (DSDM)

**DSDM** is an agile software development framework that provides comprehensive guidelines for building systems under tight time constraints through incremental prototyping in a controlled environment.

#### The 80/20 Rule Paradigm (Pareto Principle)
DSDM operates on the paradigm that **80 percent of an application can be delivered in 20 percent of the time** it would take to build the complete (100 percent) system. It is an iterative process where only enough work is performed in each loop to safely transition to the next, deferring finer details to future iterations.

#### The Nine Guiding Principles of DSDM
1.  **Active User Involvement**: Imperative throughout the process (utilizing full-time **Ambassador Users**).
2.  **Empowered Teams**: DSDM teams must be authorized to make rapid, decisive project decisions.
3.  **Frequent Product Delivery**: Focus on deploying operating increments frequently.
4.  **Fitness for Business Purpose**: The essential criterion for accepting any deliverable.
5.  **Iterative and Incremental Development**: Mandatory to converge on the correct business solution.
6.  **High-Level Agreement**: Requirements are agreed upon at a high level and baselined early.
7.  **Reversible Changes**: All development changes must be completely reversible to manage risk.
8.  **Integrated Testing**: Testing is integrated continuously throughout the entire SDLC.
9.  **Collaborative Approach**: High cooperation among all stakeholders is essential.

#### Step-by-Step Lifecycle
1.  **Feasibility Study**: Assess basic constraints and requirements to determine if the project is viable for DSDM.
2.  **Business Study**: Define informational and functional requirements to establish business value, map core architectures, and outline maintenance criteria.
3.  **Functional Model Iteration**: Produce a series of rapid, incremental prototypes to demonstrate functionality and collect user feedback.
4.  **Design and Build Iteration**: Re-engineer and refactor the prototypes to meet strict operational quality and architectural standards.
5.  **Implementation**: Place the fully tested increment into the client's production environment. If changes are needed, loop back to Functional Model Iteration.

---

### Feature Driven Development (FDD)

**Feature Driven Development (FDD)** is an agile, practical process model designed for larger-scale projects, focusing on object-oriented software engineering.

#### The Core Concept of a "Feature"
In FDD, a **Feature** is defined as "a client-valued function that can be implemented in two weeks or less."
*   **Standard Feature Template**: `<action> <result> <object>` (e.g., `Calculate the total of a sale`).
*   **Extended Feature Template**: `<action> the <result> <by | for | of | to> a(n) <object>` (e.g., `Add the product to shopping cart`, `Store the shipping-information for the customer`).
*   **Feature Set Grouping Template**: `<action><-ing> a(n) <object>` (e.g., `Making a product sale`).

#### Step-by-Step Execution Process (5 Activities)
1.  **Develop an Overall Model**: Chief architects meet with domain experts to analyze scope, producing system class and sequence diagrams.
2.  **Build a Features List**: Decompose the domain into Subject Areas, which contain Business Activities, and map them to categorized Features.
3.  **Plan by Feature**: Sequence the features, allocate specific classes to individual developers (**Class Owners**), and assign features to **Feature Set Owners**.
4.  **Design by Feature**: A small design team produces detailed sequence diagrams and design packages for selected features inside a strict 2-week cycle.
5.  **Build by Feature**: Class owners write code, conduct design and code inspections, run unit tests, and merge the feature into the master build.

---

### Software Quality & Quality Assurance Plan

As established in software engineering principles, **Software Quality** is defined as:
1.  **Conformance to explicitly stated** functional and performance requirements.
2.  **Conformance to explicitly documented** development standards.
3.  **Conformance to implicit characteristics** expected of all professionally developed software.

#### Stated vs. Implied Requirements
*   **Stated Requirements**: Explicit user needs, performance metrics, and features formally documented in the **Software Requirements Specification (SRS)**.
*   **Implied Requirements**: Characteristics expected of any professional software, even if not requested by the user (e.g., data security, system reliability, intuitive navigation, and error handling). Violating implied requirements results in a poor-quality system, even if all stated requirements are met.

#### Core SQA Plan Components
The **Software Quality Assurance (SQA) Plan** defines the programmatic quality verification and validation activities:
1.  **Defect Tracking**: Systematically logging, prioritizing, and tracking anomalies from discovery to resolution.
2.  **Unit Testing**: Verifying individual modules, classes, or subroutines in isolation to check local logic and boundary limits.
3.  **Source-Code Tracing**: Ensuring complete bidirectional traceability (every line of code traces back to a design element, which maps to an SRS requirement).
4.  **Technical Reviews**: Conducting structured peer reviews and code inspections to catch logical defects early.
5.  **Integration Testing**: Testing communication interfaces between modules using **Incremental** (Top-down, Bottom-up, Sandwich) or **Big Bang** approaches.
6.  **System Testing**: Verifying the entire integrated system complies with all functional and non-functional requirements in its target environment.

---

## Critical Comparisons

### CMM vs. CMMI Terminology

| Concept / Parameter | Capability Maturity Model (CMM) | Capability Maturity Model Integration (CMMI) |
| :--- | :--- | :--- |
| **Organization of Areas** | Organizes processes into **Key Process Areas (KPAs)**. | Organizes processes into **Process Areas (PAs)**. |
| **Level 2 Nomenclature** | Formally defined as **Repeatable**. | Formally defined as **Managed**. |
| **Level 4 Nomenclature** | Formally defined as **Managed**. | Formally defined as **Quantitatively Managed**. |

### CMMI Staged vs. Continuous Representations

| Parameter | Staged Representation | Continuous Representation |
| :--- | :--- | :--- |
| **Improvement Focus** | Measures maturity of the **entire organization**. | Measures capability of **individual process areas**. |
| **Structure** | Uses **5 pre-defined maturity levels** (1 to 5). | Uses **6 capability levels** (0 to 5). |
| **Improvement Path** | Rigid, step-by-step path (must complete all level PAs). | Highly flexible; customize specific process areas in isolation. |
| **Primary Usage** | Standardizing organization-wide benchmarking. | Targeted risk mitigation and specific process tuning. |

### Waterfall vs. Incremental Models

| Parameter | Waterfall Model | Incremental Model |
| :--- | :--- | :--- |
| **Simplicity** | Extremely simple; easy to understand and manage. | Moderate complexity; requires experienced management. |
| **Requirements** | Must be completely defined and stable upfront. | Evolving requirements; baseline core defined upfront. |
| **First Delivery** | Delivered only at the end of the entire SDLC. | Quick delivery of an operational **Core Product** (Increment 1). |
| **Feedback Loop** | Occurs late during user acceptance testing. | Continuous; occurs after every increment delivery. |
| **Risk Management** | Low; high risk of late-stage defect discovery. | High; risks are resolved early in core releases. |
| **Total Cost** | Predictable and lower for highly stable projects. | Often higher than Waterfall due to integration overhead. |

### Prototyping vs. Waterfall Models

| Parameter | Prototyping Model | Waterfall Model |
| :--- | :--- | :--- |
| **Initial Requirements** | Unstable, fuzzy, or completely unknown. | Highly stable, well-defined, and frozen. |
| **Process Flexibility** | Highly flexible; adapts dynamically to reviews. | Rigid; strictly enforces sequential phase gates. |
| **Feedback Mechanism** | Active "test driving" of physical mockups. | Static review of flat documentation. |
| **Development Speed** | Rapid, quick-and-dirty initial builds. | Disciplined, thorough, and paced development. |
| **Maintainability** | Prone to bad design choices if shortcuts persist. | High; software architecture is planned thoroughly upfront. |

### Spiral vs. Waterfall/Incremental Models

| Parameter | Spiral Model | Waterfall / Incremental Models |
| :--- | :--- | :--- |
| **Primary Driver** | **Risk assessment and mitigation**. | Schedule milestones and plan-driven phase gates. |
| **Meta-Framework** | Acts as a meta-model (can guide/encompass others). | Follows a single, standalone process flow. |
| **Project Complexity** | Engineered for massive, complex, high-risk projects. | Best for simple to medium, standard projects. |
| **Risk Evaluation** | Performed systematically at every loop. | Performed once during initial planning phases. |
| **Documentation** | Heavy; detailed risk tracking logs are required. | Light to moderate depending on project standards. |

### Agile vs. Prescriptive Models

| Parameter | Agile Process Models | Prescriptive Process Models |
| :--- | :--- | :--- |
| **Management Focus** | **Adaptive**; welcomes changing requirements. | **Plan-driven**; maintains structured process order. |
| **Initial Requirements** | Unstable, highly dynamic, and evolving. | Stable, fixed, and locked upfront. |
| **Documentation** | Minimal; prioritizes functional, operating code. | Heavy; detailed documents required at every phase gate. |
| **Customer Interaction** | High; continuous daily collaboration. | Limited; focused on contractual sign-offs. |
| **Unit of Delivery** | Frequent, small, working software increments. | A single, fully completed system at the end. |

### Extreme Programming (XP) vs. Scrum Framework

| Parameter | Extreme Programming (XP) | Scrum Framework |
| :--- | :--- | :--- |
| **Primary Focus** | Heavy focus on disciplined **engineering practices**. | Heavy focus on collaborative **project management**. |
| **Iteration Length** | Short, rapid cycles (typically 1 to 2 weeks). | Fixed, time-boxed **Sprints** (typically 1 to 4 weeks). |
| **Requirements Order** | Strict prioritization; team builds tests first. | Dynamic Product Backlog prioritized by the Product Owner. |
| **Change Tolerance** | High; pair programming facilitates real-time review. | Team focuses on Sprint Goal; changes deferred to backlog. |
| **Collaboration** | Requires a strict, full-time **On-Site Customer**. | Scrum Master facilitates stakeholder demo sessions. |

### ASD vs. DSDM vs. FDD Agile Models

| Parameter | Adaptive Software Development (ASD) | Dynamic Systems Dev Method (DSDM) | Feature Driven Development (FDD) |
| :--- | :--- | :--- | :--- |
| **Primary Philosophy** | Speculate, Collaborate, and Learn. | Pareto Principle (80/20 Rule) & MOSCOW. | High-speed, object-oriented development. |
| **Iteration Cycle** | Variable time-boxed speculation loops. | Strict time-boxing with prototyping. | Rigid, fast 2-week feature cycles. |
| **Developer Role** | Highly collaborative, cross-functional. | Empowered, cooperative teams. | Divided into **Class Owners** & Chief Architects. |
| **Feature Definition** | Outlined as high-level system components. | Part of high-level baselined agreements. | Strictly defined client-valued functions (< 2 weeks). |

---

## Last-Minute Cheat Sheet

*   **Process Framework**: The underlying structure of software engineering defining generic activities (Communication, Planning, Modeling, Construction, Deployment).
*   **Umbrella Activities**: Concurrently running management processes (Risk Management, SQA, SCM, Tracking).
*   **CMMI**: Process meta-model with 5 staged maturity levels (**I**nitial, **M**anaged, **D**efined, **Q**uantitatively Managed, **O**ptimizing).
*   **Waterfall Model**: A rigid, sequential life cycle best for fully stable, well-understood systems.
*   **V-Model**: A Waterfall variant mapping Verification (design) directly to Validation (testing).
*   **Prototyping Model**: Rapid, "quick-and-dirty" mockup development used to clarify unstable requirements.
*   **Spiral Model**: Risk-driven meta-model utilizing quadrants (Objective, Risk Analysis, Engineering, Planning).
*   **Agility**: Evolving, people-centric, adaptive approach prioritizing working software over comprehensive documentation.
*   **Scrum**: Facilitative agile framework characterized by Sprints, Product Owners, Scrum Masters, and Backlogs.
*   **Extreme Programming (XP)**: Engineering-focused agile framework utilizing Pair Programming and Test-First Development.
*   **DSDM Pareto Principle**: Agile concept assuming **80% of an application is delivered in 20% of the time**.
*   **FDD Feature**: Client-valued function taking less than 2 weeks to code: `<action> <result> <object>`.
*   **Software Quality**: Conformance to explicitly stated, documented, and implicit software characteristics.
*   **SQA Plan**: Programmatic assurance activities verifying code, testing (unit/integration/system), and standards.
