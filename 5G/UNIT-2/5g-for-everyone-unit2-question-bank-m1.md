# 5G for Everyone - Unit 2 Expected Question Bank (v2)
## Introduction to 5G and Service Ecosystem (Syllabus-Bounded)

This document contains a comprehensive **Expected and Probable Exam Question Bank** for the B.Tech / MBA Tech / BTI B.Div program course **"5G for Everyone"** at SVKM’s NMIMS, Mukesh Patel School of Technology Management and Engineering (MPSTME) [10, 148].

Since this is a newly introduced, cross-disciplinary course, **there are no previous-year question papers (PYQs)**. The questions and model answers compiled below have been engineered by performing a rigorous analysis of the primary lecture material (**Unit 2.pptx**), the official course syllabus (**5G for Everyone.pdf**), and authoritative textbooks [5, 10, 63].

### ⚠️ STRICT SYLLABUS BOUNDARY COMPLIANCE
To comply with the revised exam guidelines, this question bank covers **ONLY the first three sections of Unit 2** and **STOPS immediately after the 5G NR Overview** [61]:
1. **Evolution of Mobile Communications (2G → 3G → 4G → 5G)** [61]
2. **The Need for 5G (Technical Gaps & the Digital Economy Perspective)** [61]
3. **5G New Radio (NR) Overview (High-Level, Non-Mathematical)** [61]

*All subsequent topics from Unit 2—including the eMBB/mMTC/URLLC service classes, Digital India policies, Department of Telecommunications (DoT) R&D initiatives, and socioeconomic startup pilot projects—are **strictly out of scope** for this document and have been completely omitted to ensure focused, high-yield preparation.*

---

## 📋 UNIT 2 SYLLABUS & SLIDE COVERAGE CHECKLIST

This audit table maps the exact slide-by-slide examinable coverage of this question bank relative to the primary source material (**Unit 2.pptx**) [61]:

| Syllabus Subsection / Topic | Slides in `Unit 2.pptx` | Status in this Question Bank |
| :--- | :--- | :---: |
| **1. Evolution: 2G → 3G → 4G → 5G** | Slide 2 (Generations Timeline), Slides 3-5 (Generational Breakdown) | ✅ **Fully Covered** |
| **2. Technical Gaps in 4G Networks** | Slide 6 (Gaps in 4G Networks), Slide 7 (ITU-R Radar KPI Comparison) | ✅ **Fully Covered** |
| **3. Need for 5G: Beyond Connectivity** | Slide 7 (A Unified, Scalable Platform), Slide 21 (Flexible Carrier Architecture) | ✅ **Fully Covered** |
| **4. The Digital Economy Perspective** | Slides 17-20 (Digital Transformation, Macroeconomics, Industry 4.0) | ✅ **Fully Covered** |
| **5. 5G New Radio (NR) High-Level Overview** | Slide 21 (5G NR Air Interface Definition, OFDM, FR1 vs. FR2 Bands) | ✅ **Fully Covered** |
| **6. 5G Service Classes (eMBB, mMTC, URLLC)** | Slides 8-16 (Service Class Deep-Dives, Requirements, Use Cases) | ❌ **Strictly Excluded (Out of Scope)** |
| **7. Policy & Indian Governance (DoT, Digital India)** | Slides 22-25 (BharatNet, USOF/DBN, Paulraj 5G Forum, Testbed Consortium) | ❌ **Strictly Excluded (Out of Scope)** |
| **8. Socio-economic Impact & Pilots** | Slides 26-28 (Indian Startup Field Projects - Easiofy, Perkant, Nayan) | ❌ **Strictly Excluded (Out of Scope)** |

---

## SECTION 1: TOPIC-WISE EXPECTED QUESTION BANK

### TOPIC 1: MOBILE EVOLUTION (2G → 3G → 4G → 5G)

#### Q1. Define the term "Generation" in mobile cellular communications and describe the typical timeline and drivers associated with generational shifts.
*   **Marks:** 2 Marks (Short Answer)
*   **Priority:** ⭐ **High Probability**
*   **Why Expected:** Sourced directly from Slide 2 of `Unit 2.pptx`, which establishes that cellular technology evolves in discrete waves [84, 218]. Understanding what defines a "generation" is fundamental to the entire syllabus.

##### Model Answer:
1.  **Definition:** In mobile communications, a **"Generation" (represented as "G")** refers to a major technological shift in wireless standards, protocols, and hardware architectures that occurs roughly **once every decade** (approx. 10 years) [43, 84, 218]. 
2.  **Timeline & Drivers:** Each new generation introduces a completely redesigned physical layer and air interface that provides an order-of-magnitude leap in throughput, latency, capacity, and supported services [42, 84, 211]. These transitions are driven by growing user data demands, scientific advancements in electronics, and global standardization efforts by bodies like the **3GPP** and the **ITU** [9, 86, 319, 373].

---

#### Q2. Identify the dominant global wireless standard of the second generation (2G) digital networks and state its maximum throughput.
*   **Marks:** 2 Marks (Short Answer)
*   **Priority:** ⭐ **High Probability**
*   **Why Expected:** Handled on Slide 3 of the PPT and in standard textbook history [421, 472]. GSM is the single most important standard of the 1990s digital revolution.

##### Model Answer:
*   **Dominant Standard:** The dominant global standard of the 2G digital era was the **GSM (Global System for Mobile Communications)** [406, 423].
*   **Throughput/Speed:** Traditional GSM networks delivered a data transmission speed of **up to 64 kbps** [222, 263, 423]. *(Note: Later transitional extensions, such as 2.5G GPRS and 2.75G EDGE, eventually boosted these speeds up to 384 kbps [218, 421]).*

---

#### Q3. Explain the technical differences between 3G and 4G networks regarding their multiple access technologies, carrier multiplexing, and core network packet-switching architectures.
*   **Marks:** 3–4 Marks (Medium Analytical)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Comparing the foundational access schemes of LTE (4G) and WCDMA (3G) is a classic academic exam question. Highlighted on Slide 3 and Slide 4 of the lecture slides [29, 301].

##### Model Answer:
The transition from 3G to 4G LTE represents a structural shift from circuit-switched voice channels to a pure, flat IP-packet-based data pipe [29, 149]:

| Technical Dimension | Third Generation (3G) | Fourth Generation (4G LTE) |
| :--- | :--- | :--- |
| **Multiple Access Scheme** | **CDMA (Code Division Multiple Access)** or **WCDMA (Wideband CDMA)** [149, 210, 424]. | **OFDMA (Orthogonal Frequency Division Multiple Access)** [228, 317, 422]. |
| **Carrier Multiplexing** | Codes are assigned to separate users over a single, wide 5 MHz channel [210]. | Signals are divided orthogonally into hundreds of parallel, narrow subcarriers to prevent self-interference [216, 269]. |
| **Core Architecture** | **Mixed core network:** Circuit-switched lines handle voice calls; packet-switched routing handles data [149, 157]. | **Flat, All-IP Core (EPC - Evolved Packet Core):** Voice and data are completely packetized (VoLTE) [29, 96, 422]. |
| **Peak Throughput** | Typical speeds range from **384 kbps up to 2 Mbps** [149, 421]. | Typical speeds range from **100 Mbps up to 1 Gbps** [100, 422]. |

---

#### Q4. Explain why the digital revolution of 2G was a major leap forward compared to the analog 1G networks.
*   **Marks:** 3–4 Marks (Medium Conceptual)
*   **Priority:** ⭐ **High Probability**
*   **Why Expected:** Touched upon on Slide 3 of the PPT. The core concepts of security, efficiency, and SMS capabilities are highly examinable [192, 406].

##### Model Answer:
The transition from 1G to 2G in the early 1990s shifted cellular technology from analog frequency modulation (FM) to digital processing, introducing four major leaps [43, 84, 192, 230]:
1.  **Digital Encryption (Security):** 1G networks transmitted unencrypted voice over the air, allowing simple RF scanners to eavesdrop on calls [84, 267]. 2G GSM introduced digital encryption, securing the air interface [192, 423].
2.  **Introduction of SMS (Text Messaging):** 2G digitized the carrier wave, allowing the transmission of control plane signaling packets that enabled Short Message Service (SMS) text messages [192, 248].
3.  **Spectral Capacity (FDMA vs. TDMA/CDMA):** Instead of dedicating a whole analog frequency channel to a single user (FDMA in 1G) [230, 263], 2G compressed voice digitally and multiplexed multiple users onto the same channel via Time Division (TDMA) or Code Division (CDMA), drastically multiplying network capacity [192, 234].
4.  **Mobility & Roaming:** 2G digital networks enabled carriers to seamlessly track user locations, facilitating automatic network handovers and international roaming [192, 423].

---

#### Q5. Write a comprehensive, comparative analysis of cellular mobile communication generations from 1G to 5G. Outline their deployment decades, typical data speeds, access schemes, core services, and disadvantages.
*   **Marks:** 10 Marks / Comprehensive Essay (High-Weightage)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** This is the ultimate "evolution" question summarizing the entire historical portion of the syllabus. It spans slides 2 to 5 and represents a major chunk of the Unit 2 curriculum [43, 218].

##### Model Answer:
The generational timeline of cellular systems is characterized by an exponential expansion of bandwidth, shifting from human-centric analog telephony to machine-centric digital ecosystems [15, 28, 420]:

```
[1G: Analog Voice (1980s)] ──> [2G: Digital Voice & SMS (1990s)] ──> [3G: Mobile Broadband (2000s)] 
                                                                                   │
[5G: Cyber-Physical Ecosystem (2020s)] <── [4G: All-IP High-Speed Internet (2010s)] <┘
```

##### Master Generational Comparison Table:

| Generation | Timeline | Primary Access Technology | Standard Speed Range | Key Services Enabled | Major Technical Disadvantages |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1G** | **1980s** [43, 412] | **FDMA** (Analog Frequency Division) [230, 263] | **2.4 kbps** [230, 421] | Analog Voice Telephony only ("Brick Phones") [43, 222, 230]. | Zero security (no encryption), high interference, poor call quality, no data support [84, 267]. |
| **2G** | **1990s** [192, 412] | **TDMA / CDMA** (Time & Code Division GSM) [192, 317] | **9.6 kbps to 64 kbps** [149, 192] | Digital Voice calls, text messaging (SMS), basic email, caller ID [113, 192, 263]. | Very slow data speeds, limited web browsing capability, high handoff latency [267]. |
| **3G** | **2000s** [412, 421] | **WCDMA / CDMA2000** (Wideband CDMA) [149, 301] | **384 kbps to 2 Mbps** [149, 421] | Mobile internet access, video calls, MMS, GPS tracking, photo sharing [113, 219, 227]. | Low spectral efficiency, expensive infrastructure, poor indoor penetration [213, 280]. |
| **4G LTE** | **2010s** [413, 422] | **OFDMA** (Orthogonal Frequency Division) [228, 317, 422] | **100 Mbps to 1 Gbps** [100, 422] | High-Definition video streaming, VoLTE, online gaming, mobile cloud services [29, 100]. | Latency is too high for real-time controls (>50ms); struggles with high user density [206, 216]. |
| **5G** | **2020s** [420, 422] | **OFDM with Scalable Numerology & 5G NR** [151, 284] | **1 Gbps to 20 Gbps** [299, 300] | Connected IoT sensors, autonomous driving, immersive AR/VR, ultra-HD streaming [248, 282]. | High initial deployment costs, short coverage range at high mmWave frequencies [34, 40]. |

---

### TOPIC 2: NEED FOR 5G (TECHNICAL GAPS & DIGITAL ECONOMY PERSPECTIVE)

#### Q6. What are the key technical limitations and Gaps of 4G LTE networks that make them insufficient for emerging haptic, autonomous, and massive device requirements?
*   **Marks:** 3–4 Marks (Medium Conceptual)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Handled on Slide 6 of the PPT, this lists the technical "Why" behind the development of 5G [216, 264]. 

##### Model Answer:
While 4G LTE is highly optimized for smartphone-centric mobile broadband, it exhibits critical technical gaps when confronted with next-generation requirements [29, 206]:
1.  **Latency Constraints:** 4G LTE latency ranges from **60 to 98 milliseconds** [216]. This is far too slow for time-critical, haptic feedback applications like autonomous driving collision-avoidance or remote robotic surgery, which demand sub-millisecond reaction times [206, 216].
2.  **Connection Density Limitations:** 4G cells are physically limited to supporting approximately **200 to 400 active users per cell**, or roughly 100,000 devices per square kilometer [216, 306]. This capacity crumbles in dense urban centers or stadiums crowded with billions of smart sensors and IoT nodes [184, 208].
3.  **Rigid Spectrum Channels:** 4G is restricted to narrow channel bandwidths of **up to 20 MHz** [216]. This spectrum bottleneck cannot deliver the multi-gigabit throughput needed for ultra-high-definition haptic streams [216, 222].
4.  **Wasted Transmit Power:** 4G base stations broadcast signaling patterns in all directions simultaneously, causing substantial power wastage and limiting network efficiency [330].

---

#### Q7. Explain the concept of "Forward Compatibility" in 5G NR design. Why is it considered a major architectural advantage compared to legacy 4G LTE?
*   **Marks:** 3–4 Marks (Medium Conceptual)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Highlighted as a "cornerstone" principle of 5G NR on Slide 21 and discussed extensively in Dahlman's textbook [303]. It is a high-level architectural concept suitable for university exams.

##### Model Answer:
1.  **Definition:** **Forward Compatibility** is the architectural design principle built into 5G NR that ensures the network can flexibly support future, currently unknown use cases, services, and technologies without requiring a complete redesign of the physical air interface [16, 303].
2.  **How it works (The Ultra-Lean Concept):** Legacy networks like 4G LTE constantly broadcast a massive amount of "always-on" reference signals (such as synchronization and cell-search sequences) even when there is zero active user traffic [19, 102]. This creates "signal clutter" that locks the frame structure in place. 5G NR is designed as an **"ultra-lean" network** where transmission occurs **only when there is data to be sent**, leaving empty space in the time-frequency grid to cleanly inject future services without interfering with legacy devices [16, 102].
3.  **Why it is a Major Advantage:** Forward compatibility protects long-term infrastructure investments [303]. Instead of deploying a brand-new generation of physical equipment every ten years, network operators can dynamically deploy new vertical services on the fly via software upgrades [153, 177, 303].

---

#### Q8. Why is 5G described as a "Unified, More Capable Platform" rather than a mere speed upgrade of 4G LTE?
*   **Marks:** 3–4 Marks (Medium Conceptual)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Addressed directly on Slide 7 of `Unit 2.pptx` [428]. It tests the student's conceptual understanding of 5G's broader multi-purpose platform design.

##### Model Answer:
5G is not just about faster download speeds; it is a unified platform engineered from the ground up to support highly diverse and often contradictory requirements [15, 206, 301]:
*   **Supports Contradictory Use Cases:** Legacy 4G was single-purpose, optimized solely to deliver faster mobile broadband to human cellphones [29, 301]. 5G is a multi-dimensional platform capable of simultaneously serving a massive density of low-power, sparse-data IoT sensors (machine-type communication) and safety-critical, ultra-low latency haptic controls [13, 17].
*   **Native Spectrum Flexibility:** Unlike 4G, 5G natively operates across **all spectrum bands** (low, mid, and millimeter-wave high bands) and accommodates all licensing models (licensed, unlicensed, and shared spectrum access) [23, 25, 430].
*   **Service-Based Architecture:** Running on software-defined networks (SDN) and network function virtualization (NFV), it allows carriers to slice a single physical network into isolated, virtual networks tailored to the exact Quality of Service (QoS) required by different industries [13, 153, 177].

---

#### Q9. Analyze the "Need for 5G" from a digital-economy perspective. Detail how the transition to 5G is expected to catalyze Industry 4.0 and benefit major sectors like manufacturing.
*   **Marks:** 5 Marks (Detailed Long Answer)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Directly matches the syllabus topic "Need for 5G: beyond connectivity (digital economy perspective)" covered on Slides 17 to 20 of `Unit 2.pptx` [61]. High economic relevance.

##### Model Answer:
##### 1. The Paradigm Shift (Beyond Cellular Phones)
From a digital-economy perspective, 5G is not a consumer technology but the foundational backbone of the **fourth industrial revolution (Industry 4.0)** [152, 226]. It bridges the historical gap between information technology (IT) and operational technology (OT) [226].

```
┌────────────────────────────────────────────────────────┐
│               5G DIGITAL ECONOMY VALUE CHAIN           │
├───────────────┬────────────────────────┬───────────────┤
│ SMART FACTORY │ FINANCIAL TRANSFORMATION│ CLOUD EDGES   │
│ Autonomous V2X│ UPI, Micro-payments    │ Real-time AI  │
│ Actuators & ot│ Haptic Stock-Trading   │ Low latency   │
└───────────────┴────────────────────────┴───────────────┘
```

##### 2. Key Economic & Industrial Pillars
*   **Catalyzing Industry 4.0 (Smart Manufacturing):** Traditional factories rely on heavy, rigid wired communication cables that are highly expensive to reconfigure when shifting production lines [278]. 5G replaces these cables with ultra-reliable, wireless links. It allows millions of high-precision sensors, robotic arms, and actuators to communicate in near-real-time, enabling self-managing, modular smart factories [179, 278, 285].
*   **Macroeconomic Impact:** According to global projections, the 5G value chain is poised to generate up to **$13.2 trillion in global sales activity by 2035** and support **22 million jobs** [278, 313]. In India, 5G is estimated to benefit the economy by **₹36.4 trillion ($455 billion) by 2040**, with **20% of this benefit realized directly in the manufacturing sector** [135, 201].
*   **On-Device Processing and the Smart Edge:** To avoid sending vast amounts of raw data to distant cloud centers (which adds latency), 5G brings computation to the network edge (MEC). This allows devices to perform complex real-time data mining, predictive maintenance, and local AI processing [138, 221, 309].
*   **Financial & Retail Ecosystems:** 5G's capability to process near-instantaneous transactions securely enables high-frequency stock trading, secure UPI micro-payments, and automated inventory logistics without packet timeouts or drops [149, 279, 280].

---

#### Q10. Compare the performance requirements and Key Performance Indicators (KPIs) of 4G (IMT-Advanced) and 5G (IMT-2020) networks. Draft a comparative matrix detailing at least six performance metrics and explain the visual diagram used by the ITU to represent these targets.
*   **Marks:** 5 Marks (Detailed Long Answer)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** This compares the technical benchmarks of the two generations. Slide 7 of the PPT features the classic ITU Radar KPI diagram [216].

##### Model Answer:

**📊 Diagram Required: YES**
*   **What to Draw:** Draw an octagonal, spider-web radar chart representing the **IMT-2020 Key Performance Indicators** (Slide 7 of `Unit 2.pptx`) [59]. 
*   **Visual Structure:** 
    *   Plot an inner octagonal loop representing 4G (IMT-Advanced) metrics [216].
    *   Plot a much larger outer octagonal loop representing 5G (IMT-2020) targets [216].
    *   Label the eight radiating axes with the exact values shown below [219, 250]:

```
                     Peak Data Rate (20 Gbps) [250]
                            ^
                            │  / [5G Outer Loop]
                            │ /
   Latency (1 ms) <─────────┼─────────> Connection Density (10^6 devices/km2) [19, 250]
                            │ \ [4G Inner Loop]
                            │                              v
               Spectrum Efficiency (3x improvement) [219, 250]
```

##### 4G vs. 5G Performance Benchmarks (KPI) Matrix:

| Key Performance Indicator | 4G Benchmark (IMT-Advanced) | 5G Target (IMT-2020) | Leap / Fold Improvement |
| :--- | :--- | :--- | :--- |
| **Peak Data Rate** | **1 Gbps** (1,000 Mbps) [306] | **20 Gbps** (20,000 Mbps) [216, 250] | **20x Increase** [216] |
| **User Plane Latency** | **10 milliseconds** [219] | **1 millisecond** (Air interface) [2, 19, 250] | **10x Reduction** [216] |
| **Connection Density** | **10⁵ devices per km²** [216, 219] | **10⁶ (1 Million) devices per km²** [19, 250] | **10x Increase** [216, 219] |
| **Spectral Efficiency** | **1x** (Base level) [219] | **3x** (Bits per second per Hz) [19, 250] | **3x Improvement** [216, 219] |
| **Network Energy Efficiency** | **1x** (Base level) [216] | **100x** (Efficient sleep states) [216] | **100x Improvement** [216] |
| **Area Traffic Capacity** | **0.1 Mbps per m²** [216] | **10 Mbps per m²** [216] | **100x Increase** [216] |
| **User Experienced Speed** | **10 Mbps** average [216] | **100 Mbps** average [216] | **10x Increase** [216] |
| **Mobility Support** | **350 km/h** (High-speed trains) [216] | **500 km/h** (Autonomous V2X/Aviation) [216, 219] | **~1.5x Increase** [216] |

---

### TOPIC 3: 5G NR OVERVIEW (HIGH-LEVEL, NON-MATHEMATICAL)

#### Q11. Define 5G NR (New Radio) and specify which international standardization release introduced its first set of commercial standards.
*   **Marks:** 2 Marks (Short Answer)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Basic terminological definition covered on Slide 21. Highly expected for short-definition questions [319, 321].

##### Model Answer:
1.  **Definition:** **5G NR (New Radio)** is the next-generation global standard for the physical wireless air interface of 5G mobile networks [319, 321]. It defines the physical algorithms, frame structures, and spectrum rules that allow 5G devices to transmit and receive radio signals [242, 321].
2.  **Standardization Release:** The first version of the 5G NR specifications was officially finalized in **3GPP Release 15** in mid-2018 [2, 9, 319].

---

#### Q12. Distinguish between Frequency Range 1 (FR1) and Frequency Range 2 (FR2) as defined by the 3GPP for 5G NR deployments.
*   **Marks:** 2 Marks (Short Answer)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** A fundamental technical categorization in 5G spectrum planning [196]. Always featured in 5G papers.

##### Model Answer:
3GPP has divided the 5G NR operational spectrum into two distinct Frequency Ranges (FR) [196, 322]:
1.  **Frequency Range 1 (FR1 - Sub-7 GHz):** Spans frequencies from **410 MHz to 7125 MHz** [196]. It includes low and mid-bands for wide-area coverage and standard urban deployments [322].
2.  **Frequency Range 2 (FR2 - Millimeter Wave / mmWave):** Spans ultra-high frequencies from **24.25 GHz up to 52.6 GHz** (and extended to 71 GHz in Rel-17) [196, 322]. It provides extreme multi-gigabit throughput over short distances [323, 324].

---

#### Q13. Detail the technical trade-offs between Frequency Range 1 (FR1) and Frequency Range 2 (FR2) bands regarding signal propagation, antenna physical size, and channel bandwidths.
*   **Marks:** 3–4 Marks (Medium Conceptual)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Handled on Slide 21 of the PPT and in textbooks [11, 216]. Tests understanding of high-frequency vs. low-frequency propagation physics.

##### Model Answer:
The deployment of 5G NR requires balancing the propagation coverage of lower bands with the extreme capacity of high bands [11, 322]:

| Parameter | Frequency Range 1 (FR1: < 7.125 GHz) | Frequency Range 2 (FR2: > 24 GHz) |
| :--- | :--- | :--- |
| **Operational Bandwidth** | Uses narrow channel bandwidths: **5 MHz up to 100 MHz** [115, 274]. | Uses massive, continuous channel bandwidths: **50 MHz up to 800 MHz** [115, 126, 216]. |
| **Propagation & Path Loss** | **Low path loss:** Low frequencies travel tens of kilometers, easily penetrate walls and trees, and provide deep indoor coverage [322, 342]. | **Severe path loss (atmospheric attenuation):** High frequencies travel less than 1 km and are heavily blocked by concrete, rain, and foliage [103, 311, 333]. |
| **Optimal Antenna Size** | Long wavelengths ($\lambda$) require larger physical antenna elements (centimeters) [336]. | Millimeter wavelengths permit tiny antenna elements, allowing hundreds to fit in a small array [14, 321]. |
| **Primary Use Cases** | Baseline wide-area rural, suburban, and urban coverage [322]. | Localized high-density hotspots, Fixed Wireless Access (FWA), and factory-floor private networks [34, 148, 323]. |

---

#### Q14. Why do high-frequency mmWave (FR2) networks require Massive MIMO and directional Beamforming to achieve stable wireless links? Explain the technical mechanism.
*   **Marks:** 3–4 Marks (Medium Analytical)
*   **Priority:** ⭐ **High Probability**
*   **Why Expected:** Highlighted as a key enabling feature on Slide 21. Explains how 5G overcomes high-frequency physics [18, 321].

##### Model Answer:
1.  **The Physical Problem (Path Loss):** Millimeter-wave frequencies (FR2 >24 GHz) suffer from extreme path loss, atmospheric attenuation, and signal absorption by physical obstacles [103, 311, 333]. Traditional omnidirectional broadcasting, which spreads power in all directions, causes the signal to decay within a few meters [330].
2.  **The Massive MIMO Solution:** Because high-frequency wavelengths are so small (millimeters), engineers can fit hundreds of tiny antenna elements into a compact array at the base station (Massive MIMO) [14, 142, 321]. This massive scaling multiplies the signal capture capability [321, 460].
3.  **The Beamforming Mechanism:** Instead of broadcasting the signal everywhere, 5G base stations use advanced signal processing to coordinate these antennas. They construct highly focused, narrow **directional beams** directed specifically toward individual active users [459]. This direct pointing concentrates the radio energy, overcomes path loss, minimizes signal interference, and ensures stable, high-speed links [74].

---

#### Q15. Detail the physical working of Frequency Division Duplexing (FDD) and Time Division Duplexing (TDD) schemes. Explain why TDD is the preferred configuration for 5G NR spectrum allocations.
*   **Marks:** 5 Marks (Detailed Long Answer)
*   **Priority:** 🔥 **Very High Probability**
*   **Why Expected:** Syllabus topic "Spectrum sharing (FDD & TDD)" and Slides 15-17 of `Unit 1.pptx` combined with `Unit 2.pptx` [60]. Standard exam essay question.

##### Model Answer:

**📊 Diagram Required: YES**
*   **What to Draw:** Draw two time-frequency spectrum grids [404, 411]:
    *   *FDD Grid:* Show two separate, parallel frequency bands ($F_1$ for Uplink, $F_2$ for Downlink) running continuously over time, separated by a blank **Guard Band** [404].
    *   *TDD Grid:* Show a single, continuous frequency band sharing the same channel, but divided into alternating blocks of Time ($T_1$ for Downlink, $T_2$ for Uplink), separated by a blank **Guard Period** [411].

```
 FDD: Frequency Division (Two Bands)      TDD: Time Division (Single Band)
 ──────────────────────────────────       ──────────────────────────────────
 Downlink (F2) ▓▓▓▓▓▓▓▓ (Continuous)      DL (T1)  ▓▓▓▓    DL (T3)  ▓▓▓▓
 ──────────────────────────────────       ──────────────────────────────────
  [ Guard Band ]                          GP ──> ▒          GP ──> ▒
 ──────────────────────────────────       ──────────────────────────────────
 Uplink (F1)   ░░░░░░░░ (Continuous)      UL (T2)   ░░░░   UL (T4)   ░░░░
 ──────────────────────────────────       ──────────────────────────────────
```

##### 1. Conceptual Breakdown of Duplexing Schemes
*   **Frequency Division Duplex (FDD):** Transmit and receive signals operate simultaneously but are separated in the **frequency domain** [404]. The downlink (base-station to mobile) and uplink (mobile to base-station) utilize two separate, paired frequency bands separated by a safety frequency gap called a **guard band** to prevent self-collision [404].
*   **Time Division Duplex (TDD):** Transmit and receive signals operate on the **exact same frequency band** but are separated in the **time domain** [411]. Downlink and uplink communications take turns transmitting in alternating, non-overlapping time slots, separated by a short safety time buffer called a **guard period** [411].

##### 2. Why TDD is Highly Preferred for 5G NR
Although FDD was widely used in 3G/4G, TDD is the dominant configuration for 5G NR due to four key factors [411, 418]:
1.  **Spectrum Efficiency:** 5G high-frequency bands (especially mmWave) are highly scarce and expensive [41]. Finding "paired" symmetric bands for FDD is extremely difficult [411]. TDD operates on a **single, unpaired band**, utilizing every sliver of available spectrum [411, 430].
2.  **Asymmetric Traffic Handling:** Internet traffic is highly asymmetric, with users downloading roughly 9x more data than they upload (e.g., video streaming) [206]. FDD locks equal bandwidth to both uplink and downlink, wasting half the capacity [411]. TDD can **dynamically adjust time slot allocations** to devote more time to the downlink, optimizing throughput [411, 461].
3.  **Support for Massive MIMO & Beamforming:** For beamforming to work, the base station must calculate the exact state of the wireless path (channel state information) [345]. In TDD, because both directions share the exact same frequency, the channels are **reciprocal** [21]. The uplink channel measurements can be directly used to form perfect downlink beams, reducing calculation complexity [21].
4.  **Hardware Cost Savings:** TDD eliminates the need for expensive RF duplex filters at the receiver to separate paired bands, allowing for lighter and cheaper antenna arrays [30].

---

## SECTION 2: SEPARATE CLASSIFIED QUESTION SUMMARY

### 1. MOST PROBABLE EXAM QUESTIONS (TOP-PRIORITY)
1.  **Comparative table of mobile communication generations (2G to 5G).** (10 Marks) [🔥 Very High Probability] [222]
2.  **IMT-2020 8-KPI Spider Web Radar Chart comparison between 4G and 5G.** (5 Marks) [🔥 Very High Probability] [216]
3.  **Detailed economic analysis of 5G's impact on Industry 4.0 and manufacturing.** (5 Marks) [🔥 Very High Probability] [135, 278]
4.  **FDD vs. TDD working, advantages, and why TDD is preferred for 5G NR.** (5 Marks) [🔥 Very High Probability] [411, 418]
5.  **Technical trade-offs between Sub-7 GHz (FR1) and mmWave (FR2) spectrum bands.** (4 Marks) [🔥 Very High Probability] [196, 322]

---

### 2. IMPORTANT 2-MARK QUESTIONS (DEFINITIONS & TERM-BASED)
*   **Q: Define "Generation" in wireless communications.** [84]
    *   *Answer:* A generational shift occurring once every decade, introducing a leap in physical-layer speeds, capacities, and standards [43, 84, 218].
*   **Q: Identify the dominant global standard of 2G digital networks.** [406]
    *   *Answer:* GSM (Global System for Mobile Communications) with speeds up to 64 kbps [222, 406, 423].
*   **Q: State two key performance limitations of 4G LTE.** [216]
    *   *Answer:* High latency (60-98 ms) and limited connection density (100,000 devices/km²) [216].
*   **Q: What is "Forward Compatibility" in 5G NR?** [16]
    *   *Answer:* An architectural design concept ensuring the 5G air interface can flexibly support future, unknown services without redesigning the physical layer [16, 303].
*   **Q: Define Frequency Range 1 (FR1) and Frequency Range 2 (FR2).** [196]
    *   *Answer:* FR1 covers Sub-7 GHz bands (410 MHz - 7125 MHz); FR2 covers mmWave bands (24.25 GHz - 52.6 GHz) [196, 322].
*   **Q: What does "5G NR" stand for, and which standardizing body created it?** [319]
    *   *Answer:* Stands for "5G New Radio," developed as the global 5G physical air interface standard by the 3GPP in Release 15 [2, 319, 321].

---

### 3. IMPORTANT 3–4-MARK QUESTIONS (CONCEPTUAL & EXPLANATORY)
*   **Q: Distinguish between the multiple access schemes and packet-switching cores of 3G and 4G.** [29, 317]
*   **Q: Why was the digital transition from 1G to 2G GSM considered revolutionary?** [43, 192]
*   **Q: Why is 5G referred to as a "unified platform" rather than just a high-speed 4G upgrade?** [428, 430]
*   **Q: Detail the coverage and capacity trade-offs between FR1 (<7 GHz) and FR2 (>24 GHz) bands.** [11, 322]
*   **Q: Why do millimeter-wave (FR2) networks require directional beamforming? Explain the path loss mechanism.** [103, 311, 459]

---

### 4. IMPORTANT 5-MARK QUESTIONS (TECHNICAL & REGULATORY ESSAYS)
*   **Q: Explain the IMT-2020 Key Performance Indicators (KPIs) comparing 4G and 5G. Draw the radar spider chart.** [59, 216]
*   **Q: Analyze the "Need for 5G" from a digital-economy perspective, highlighting Industry 4.0 and macroeconomics.** [61, 135]
*   **Q: Describe the physical differences between FDD and TDD duplexing schemes. Detail why TDD is preferred for 5G NR.** [411, 418]

---

### 5. HIGHER-MARK / COMPREHENSIVE QUESTIONS
*   **Q: Provide a comprehensive timeline analysis of mobile network evolution from 1G to 5G. Draft a complete comparative matrix outlining primary access technologies, speed ranges, services, and disadvantages.** (10 Marks) [43, 218]
*   **Q: Explain how 5G NR resolves the physical size, coverage, and scalability limits of legacy cellular networks. Detail the roles of ultra-lean design, scalable numerology, and the division of frequency ranges (FR1 and FR2).** (8 Marks) [16, 102, 321, 324]

---

### 6. IMPORTANT COMPARISON QUESTIONS
1.  **1G vs. 2G vs. 3G vs. 4G vs. 5G (Master Evolution Matrix).** [222]
2.  **3G vs. 4G LTE (Access schemes, duplex, data speeds, packet core).** [29, 149]
3.  **Frequency Range 1 (FR1) vs. Frequency Range 2 (FR2) Bands.** [322, 323, 324]
4.  **Frequency Division Duplexing (FDD) vs. Time Division Duplexing (TDD).** [404, 411]

---

### 7. DIAGRAM-BASED QUESTIONS
*   **IMT-2020 KPI Radar Spider-Web Diagram:** Comparing 4G and 5G target metrics [216]. (Slide 7 of `Unit 2.pptx`) [59].
*   **Duplexing Spectrum Division Grid (FDD vs. TDD):** Showing time, frequency, guard bands, and guard periods [404, 411]. (Slide 15 of `Unit 1.pptx`) [60].
*   **5G NR Frequency Range Split Spectrum:** Mapping FR1 (Sub-7 GHz) and FR2 (mmWave) ranges on a logarithmic scale [196, 322]. (Slide 21 of `Unit 2.pptx`).

---

### 8. MOST IMPORTANT DEFINITIONS
*   **Generation ("G"):** Approx. 10-year step change in mobile cellular architecture and standards [43, 84].
*   **GSM:** Second-generation digital mobile standard introducing digital security and SMS [192, 423].
*   **All-IP Core (EPC):** 4G flat packet core converting all voice and data streams to IP packets [29, 96].
*   **Forward Compatibility:** Lean frame design allowing network upgrades to support future, unknown services [16, 303].
*   **5G NR (New Radio):** The unified physical air interface standard defined in 3GPP Release 15 [319, 321].
*   **FR1 (Sub-7 GHz):** 5G frequency range from 410 MHz to 7.125 GHz for wide area coverage [196, 322].
*   **FR2 (mmWave):** 5G frequency range from 24.25 GHz to 52.6 GHz for high-capacity hotspots [196, 322].
*   **TDD:** A duplex configuration separating uplink and downlink via time slots on a single frequency band [411].

---

### 9. LAST-MINUTE PRIORITY REVISION LIST
- [ ] Learn the **radar spider web axes values** for 4G vs. 5G (Latency, Speed, Efficiency, Connection Density) [216, 250].
- [ ] Understand **why FDD is disadvantageous** for asymmetric data downloads compared to TDD [411].
- [ ] Memorize the exact speed targets: **20 Gbps Peak Downlink** [250] and **100 Mbps Experienced Downlink** [216, 250].
- [ ] Know the frequency boundaries: **FR1 (410 MHz - 7125 MHz)** and **FR2 (24.25 GHz - 52.6 GHz)** [196].
- [ ] Understand why **shorter wavelengths ($\lambda$) at mmWave frequencies** require highly directional beamforming [103, 311, 459].

---

### 10. COMPLETE SYLLABUS QUESTION CHECKLIST
- [x] Evolution: 2G → 3G → 4G → 5G (Timeline, Speeds, Standards, Disadvantages) ── **✅ Fully Covered**
- [x] Gaps in 4G Networks (Latency, Capacity, Bandwidth bottlenecks) ───────────── **✅ Fully Covered**
- [x] Need for 5G: Beyond Connectivity (Forward Compatibility, Unified Platform) ── **✅ Fully Covered**
- [x] Need for 5G: Digital Economy (Industry 4.0, Smart Factories, Edge MEC) ───────── **✅ Fully Covered**
- [x] 5G NR Overview (Definition, 3GPP standard releases, Duplex schemes) ────────── **✅ Fully Covered**
- [x] Frequency Bands (FR1 and FR2 boundaries, characteristics, and propagation) ──── **✅ Fully Covered**
