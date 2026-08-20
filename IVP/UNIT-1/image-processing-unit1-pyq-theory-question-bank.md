# NMIMS Unit 1: Image Fundamentals - Solved Theoretical PYQ & Expected Question Bank

**Course:** Image and Video Processing (IVP)  
**Target Exam:** Mid-Sem Prep (SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC))  
**Primary References:** `IVP UNIT 1.pptx` (Class Slides) & Official Past University Question Papers (2022–2026)  
**Syllabus Focus:** Digital Image Representation, Basics of Color Images, Spatial and Gray-Level Resolution, Distance Measures, Pixel Relationships, and Image File Formats (TIFF, PNG, JPEG).  
**Strict Exclusion:** No Point Processing, Histogram Equalization, or Spatial/Frequency-Domain Filters.

---

## 📊 PART A: TOPIC-WISE PYQ FREQUENCY & PRIORITY ANALYSIS

This analysis maps the frequency and recurrence patterns of theoretical Unit 1 topics across all available SVKM's NMIMS Term Exams and Re-Exams (2022–2026) to guide your study priorities:

### 1. Topic-Wise PYQ Frequency Map

| Syllabus Section | Core Topic / Concept Tested | Frequency | Priority Level | Key Papers / Years |
| :--- | :--- | :---: | :---: | :--- |
| **Image Sampling & Quantization** | Digitization processes (A/D block diagram, Sampling, Quantization definitions, and relationships) | **High** (4x) | 🔥 **Very High** | NMIMS Re-Exam Dec 2024 (Q2b), NMIMS Re-Exam Jan 2023 (Q2b), NMIMS Special Re-Exam June 2023 (Q6a), NMIMS Test-I Aug 2025 (Set 2 - Q1a.ii) |
| **Image File Formats** | Comparing features and compression modes (JPEG vs. PNG and JPEG vs. TIFF) | **High** (3x) | 🔥 **Very High** | NMIMS Term Exam Dec 2025 (Q1a), NMIMS Term Exam Nov 2024 (Q1a), NMIMS Re-Exam Dec 2024 (Q1a) |
| **Spatial & Gray-Level Resolution** | Definitions, visual impact of decimation (checkerboard & false contouring), and trade-offs | **Medium** (2x) | ⭐ **High** | NMIMS Re-Exam Dec 2024 (Q2a), NMIMS Re-Exam 2022-23 (Q2a) |
| **Pixel Relationships & Adjacency** | 4-connectivity vs. 8-connectivity, m-adjacency definitions, and path drawing | **Medium** (2x) | ⭐ **High** | NMIMS Term Exam Dec 2025 (Q1d), NMIMS Term Exam Nov 2023 (Q1a.1) |
| **Distance Measures** | Definitions and comparisons of Euclidean ($D_e$), City-block ($D_4$), and Chessboard ($D_8$) | **Medium** (2x) | ⭐ **High** | NMIMS Test-I Aug 2025 (Set 1 - Q1a.i, Set 2 - Q1b.i), NMIMS Re-Exam Dec 2024 (Q1a) |
| **Digital Image Representation** | Defining image as 2D function / matrix, RGB color planes, and pixels | **Low** (1x) | 🟡 **Moderate** | NMIMS Test-I Aug 2025 (Set 1 - Q1b.i) |

### 2. Repeated & Grouped Exam Concepts
1.  **The Sampling & Quantization Digitization Pattern:**
    *   *NMIMS Re-Exam Jan 2023 (Q2b)* and *Special Re-Exam June 2023 (Q6a)* both ask for the block diagram and detailed explanation of sampling and quantization to digitize an analog image.
2.  **The Image File Formats Comparison Pattern:**
    *   *NMIMS Term Exam Dec 2025 (Q1a)* compares JPEG vs. PNG features and usage.
    *   *NMIMS Term Exam Nov 2024 (Q1a)* compares JPEG vs. TIFF compression methods and quality impact.
3.  **Adjacency and Connectivity Path Patterns:**
    *   *NMIMS Term Exam Dec 2025 (Q1d)* tests 8-adjacency vs. m-adjacency drawing and connectivity conditions in binary images.
    *   *NMIMS Term Exam Nov 2023 (Q1a.1)* compares 4-connectivity and 8-connectivity.

---

## 📂 PART B: SOLVED THEORETICAL PYQ BANK

---

### 📥 MODULE 1.1: DIGITAL IMAGE REPRESENTATION & FUNDAMENTALS

#### **PYQ 1: Digital Image Representation and Coordinate Range** (Test-I Aug 2025, Set 1 - Q1b.i) [0.5 Marks]
**Question:** If an image has $L$ intensity levels, the pixel values range from _____ to _____.
*   **Topic:** Digital Image Representation (Grayscale range)
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    The pixel values range from **$0$** to **$L-1$**.
*   **Concept Explanation:** In digital systems, computer indexing begins at 0. Therefore, a discrete intensity spectrum containing $L$ unique gray levels maps to the range $[0, L-1]$, where $0$ represents pure black (minimum brightness) and $L-1$ represents pure white (maximum brightness).

---

#### **PYQ 2: Storage Bit Depth Requirements** (Test-I Aug 2025, Set 1 - Q1b.ii) [0.5 Marks]
**Question:** To represent 1024 intensity levels, a minimum of _____ bits per pixel are needed.
*   **Topic:** Digital Image Representation (Bit Depth)
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    A minimum of **10 bits** per pixel are needed.
*   **Mathematical Calculation:**
    $$L = 2^k \implies 1024 = 2^k \implies k = \log_2(1024) = 10 	ext{ bits}$$
    where $L$ is the number of intensity levels and $k$ is the bit depth (bits per pixel).

---

#### **PYQ 3: RGB True Color Image Storage and Planes** (Test-I Aug 2025, Set 1 - Q1b.iii) [1 Mark]
**Question:** A color image has a resolution of $512 	imes 512$ pixels with 24-bit depth. Define no. of planes in the given image and compute the size of the image.
*   **Topic:** Basics of Color Images
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    *   **Number of Planes:** A 24-bit true color RGB image consists of **3 planes** (Red, Green, Blue).
    *   **Image Size Calculation:**
        $$	ext{Size in bits} = 	ext{Height} 	imes 	ext{Width} 	imes 	ext{Bit Depth} = 512 	imes 512 	imes 24 = \mathbf{6,291,456 	ext{ bits}}$$
        $$	ext{Size in Bytes} = rac{6,291,456}{8} = \mathbf{786,432 	ext{ Bytes}}$$
        $$	ext{Size in Kilobytes (KB)} = rac{786,432}{1024} = \mathbf{768 	ext{ KB}}$$
*   **Concept Explanation:** True color systems represent color pixels as triplets $(R, G, B)$ mapped across three distinct spatial planes in memory. Each channel is quantized to 8 bits ($2^8 = 256$ levels per plane), yielding a total bit depth of $24$ bits per pixel ($2^{24} pprox 16.7$ million possible colors).

---

### 📥 MODULE 1.2: SPATIAL & GRAY-LEVEL RESOLUTION

#### **PYQ 4: Spatial and Gray-Level Resolution and Dynamic Range Limits** (Re-Exam Dec 2024 - Q2a) [10 Marks]
**Question:** Describe spatial resolution and gray level resolution. Discuss the effects of decreased spatial and gray level resolution on the appearance of the image. Deliberate on the disadvantage of having increased resolution.
*   **Topic:** Spatial and Gray-Level Resolution
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    ##### **1. Spatial Resolution**
    *   **Definition:** Spatial resolution is the smallest discernible detail in an image.
    *   **Metric:** In physical print media, it is measured in dots per inch (DPI) or lines per inch. In digital computer systems, it is defined by the image grid dimensions: rows ($M$) $	imes$ columns ($N$), representing the total pixel density ($M 	imes N$).
    
    ##### **2. Gray-Level (Intensity) Resolution**
    *   **Definition:** Gray-level resolution refers to the smallest discernible change in intensity level.
    *   **Metric:** It is measured by the number of bits ($k$) used to quantize the intensity range, allowing $L = 2^k$ distinct shades of gray. For example, an 8-bit image has a gray-level resolution of 256 levels.
    
    ##### **3. Visual Effects of Decreased Spatial Resolution**
    *   Decreasing the spatial resolution (down-sampling/decimation) reduces the pixel density.
    *   **Visual Artifact — The Checkerboard Effect:** As pixel size increases, the image becomes progressively blurred and loses fine structural details. At very low resolutions, individual pixels become visible to the naked eye as large square blocks (pixelation), creating a "checkerboard" appearance.
    
    ##### **4. Visual Effects of Decreased Gray-Level Resolution**
    *   Decreasing the gray-level resolution (reducing bit depth $k$) limits the number of shades of gray available to represent smooth shading.
    *   **Visual Artifact — False Contouring:** Instead of smooth gray transitions, the image exhibits harsh, stepped boundaries between different intensity regions. This artificial banding is called "false contouring" and is highly noticeable in areas of smooth gradients, such as human skin or sky backdrops.
    
    ##### **5. Disadvantages of Having Increased Resolution (The Design Bottlenecks)**
    While high-resolution images provide outstanding visual fidelity, they introduce three critical hardware and computational bottlenecks:
    1.  **Massive Storage Costs:** Storage space scales quadratically with resolution. Doubling the spatial resolution of an 8-bit image from $512 	imes 512$ (256 KB) to $1024 	imes 1024$ (1 MB) quadruples the required hard drive space.
    2.  **Transmission Bandwidth Constraints:** High-resolution files require significant network bandwidth to transmit. This leads to slow loading speeds on web interfaces and lag in real-time streaming applications.
    3.  **High Processing Latency:** Mathematical operations (such as 2D convolutions, spatial filtering, or image transforms) require significantly more CPU/GPU cycles on larger matrices, slowing down processing speeds.

---

### 📥 MODULE 1.3: IMAGE SAMPLING & QUANTIZATION

#### **PYQ 5: Analog-to-Digital Conversion (Sampling & Quantization)** (Re-Exam Jan 2023 - Q2b & Special Re-Exam June 2023 - Q6a) [5 Marks]
**Question:** Draw the block diagram and explain the process of spatial sampling and quantization to digitize an analog image.
*   **Topic:** Image Sampling and Quantization
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    ##### **1. The Block Diagram of Image Digitization**
    
    ```
      Continuous Scene f(x,y)
                 │
                 ▼
       ┌───────────────────┐
       │  SPATIAL SAMPLING │  ◄── Discretizes coordinates (x, y) into a grid
       └─────────┬─────────┘
                 │
                 ▼
       ┌───────────────────┐
       │    QUANTIZATION   │  ◄── Maps continuous amplitude f to discrete integers
       └─────────┬─────────┘
                 │
                 ▼
       ┌───────────────────┐
       │ DIGITAL 2D MATRIX │  ◄── Discrete grid of pixels stored in memory
       └───────────────────┘
    ```
    
    ##### **2. Spatial Sampling (Discretizing Coordinates)**
    *   **Definition:** Sampling is the discretization of continuous spatial coordinates $(x, y)$ of a continuous scene onto a structured grid of physical sensor elements.
    *   **Mechanism:** When light passes through a camera lens, it is projected onto a 2-D sensor array (such as a CCD or CMOS chip). The physical spacing of the individual photodiodes in the array divides the continuous analog scene into a discrete grid of square or rectangular pixels.
    *   **Result:** Sampling directly determines the **spatial resolution** (number of pixels, $M 	imes N$) of the digital image.
    
    ##### **3. Amplitude Quantization (Discretizing Intensity)**
    *   **Definition:** Quantization is the transformation of a continuous intensity (amplitude) value $f(x, y)$ at a sampled coordinate into a finite, discrete integer representing a specific gray level or color.
    *   **Mechanism:** Each sensor element outputs a continuous analog voltage proportional to the amount of light it receives. An Analog-to-Digital Converter (ADC) rounds this continuous voltage value to the nearest discrete integer level in our digital scale.
    *   **Result:** Quantization directly determines the **intensity/gray-level resolution** (number of gray levels, $L = 2^k$).

---

### 📥 MODULE 1.4: NEIGHBORHOODS, ADJACENCY & CONNECTIVITY

#### **PYQ 6: Differences Between 4-Connectivity and 8-Connectivity** (Term Exam Nov 2023 - Q1a.1) [2 Marks]
**Question:** In a digital image, how does the 4-connectivity differ from the 8-connectivity? Give any 2 differences.
*   **Topic:** Pixel Spatial Relationships
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    Below is a comparison table outlining the key structural and traversal differences between 4-connectivity and 8-connectivity:

| Feature Parameter | 4-Connectivity | 8-Connectivity |
| :--- | :--- | :--- |
| **Neighbor Definition** | Two pixels $p$ and $q$ are connected only if $q$ is in the set of 4 orthogonal neighbors $N_4(p)$ (horizontal and vertical only). | Two pixels $p$ and $q$ are connected if $q$ is in the set of 8 orthogonal/diagonal neighbors $N_8(p)$. |
| **Shared Boundaries** | Pixels must share a **physical edge**. | Pixels can share either a **physical edge** or a **corner**. |
| **Path Traversal** | Restricts digital paths to horizontal and vertical moves, resulting in longer path distances. | Allows diagonal path hops, yielding shorter path lengths. |

---

#### **PYQ 7: Adjacency and mixed (m-) Connectivity** (Term Exam Dec 2025 - Q1d) [4 Marks]
**Question:** What is adjacency in image processing? Explain m-adjacency and why it is preferred over 8-adjacency with a brief graphical example.
*   **Topic:** Adjacency and Connectivity
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    ##### **1. Definition of Adjacency**
    Two pixels $p$ and $q$ are adjacent if they are spatial neighbors (e.g., sharing an edge or corner) and their intensity values satisfy a common criterion of similarity defined by a set $V$ (for binary images, $V = \{1\}$).
    
    ##### **2. Definition of m-Adjacency (Mixed Adjacency)**
    Two pixels $p$ and $q$ with values from set $V$ are m-adjacent if:
    1.  $q$ is in the 4-neighborhood of $p$ ($q \in N_4(p)$), **OR**
    2.  $q$ is in the diagonal neighborhood of $p$ ($q \in N_D(p)$) **AND** the intersection of their 4-neighborhoods ($N_4(p) \cap N_4(q)$) contains **no pixels** whose values are from set $V$.
    
    ##### **3. Why m-Adjacency is Preferred Over 8-Adjacency (Path Ambiguity)**
    8-adjacency permits horizontal, vertical, and diagonal connections unconditionally. When multiple foreground pixels are grouped together, 8-adjacency often forms multiple redundant paths and closed crossing loops (resembling an "X" intersection). This creates path ambiguity. 
    **m-adjacency was designed to eliminate this path ambiguity** by prioritizing 4-adjacency connections and only allowing diagonal links when no vertical or horizontal alternative path exists.

*   **📊 Diagram Required: YES**
    *   *What to draw:* Sketch the comparison of 8-adjacency vs. m-adjacency on a $2 	imes 2$ block of $1$s.
    ```
    Input Grid:     8-Adjacency (Ambiguous "X" Paths)    m-Adjacency (Unique Path)
    ┌───┬───┐          [1] ─────── [1]                    [1] ─────── [1]
    │ 1 │ 1 │           │  ╲     ╱  │                      │           │
    ├───┼───┤           │    ╳   │                      │           │
    │ 1 │ 1 │           │  ╱     ╲  │                      │           │
    └───┴───┘          [1] ─────── [1]                    [1] ─────────┘
    ```
    *   *Source slide:* `IVP UNIT 1.pptx` (Slide 9).

---

### 📥 MODULE 1.5: COORDINATE DISTANCE METRICS

#### **PYQ 8: Distance Metrics Definition** (Test-I Aug 2025, Set 1 - Q1a.i) [0.5 Marks]
**Question:** The _____ distance metric calculates the sum of the absolute differences between the coordinates of two pixels, assuming movement is restricted to horizontal and vertical directions.
*   **Topic:** Distance Measures
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    The **City-Block** (also denoted as $D_4$) distance metric.
*   **Concept Explanation:** City-block distance calculates the shortest path between two points on a grid where diagonal movement is disallowed. It is modeled as:
    $$D_4(P, Q) = |x - u| + |y - v|$$

---

#### **PYQ 9: Chessboard Distance Definition** (Test-I Aug 2025, Set 2 - Q1b.i) [0.5 Marks]
**Question:** The _____ distance metric is defined as the maximum of the absolute differences between the coordinates of two pixels, allowing horizontal and diagonal movement.
*   **Topic:** Distance Measures
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    The **Chessboard** (also denoted as $D_8$) distance metric.
*   **Concept Explanation:** Chessboard distance calculates the shortest path assuming an 8-way adjacent movement (similar to a king on a chessboard), meaning horizontal, vertical, and diagonal steps are all weighted as exactly 1 unit. It is modeled as:
    $$D_8(P, Q) = \max(|x - u|, |y - v|)$$

---

### 📥 MODULE 1.6: IMAGE FILE FORMATS

#### **PYQ 10: Comparison Between JPEG and PNG File Formats** (Term Exam Dec 2025 - Q1a) [4 Marks]
**Question:** Compare JPEG and PNG image file formats with respect to features and usage.
*   **Topic:** Image File Formats
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    Below is a comparison table outlining the distinct characteristics and primary use cases of JPEG and PNG file formats:

| Feature Parameter | JPEG (Joint Photographic Experts Group) | PNG (Portable Network Graphics) |
| :--- | :--- | :--- |
| **Compression Type** | **Lossy** compression (irreversibly discards high-frequency visual details to save space). | **Lossless** compression (perfect, bit-by-bit recovery of original image data). |
| **Color Support** | Optimized for **24-bit true color** (16.7 million colors), making it perfect for natural scenes. | Supports **48-bit true color**, grayscale, and indexed color palettes. |
| **Transparency (Alpha)**| Does **NOT** support transparency (transparent areas default to solid white or black). | Fully supports **alpha channel transparency** with varying opacity levels. |
| **Interlacing Support**| Standard JPEGs are **not interlaced** (progressive variants exist but are less common). | Supports **interlacing** (progressive loading on web browsers, rendering a low-res preview first). |
| **Primary Use Cases** | Final distribution of natural photographs, scenic images, and digital web photos. | Web graphics, logos, diagrams, text overlays, and images undergoing editing. |

---

#### **PYQ 11: Comparison Between TIFF and JPEG File Formats** (Term Exam Nov 2024 - Q1a) [5 Marks]
**Question:** How do TIFF and JPEG differ in terms of compression methods, what impact does this have on image quality?
*   **Topic:** Image File Formats
*   **Verification Status:** 🟢 **Verified PYQ**
*   **Answer:**
    Below is a comparison table detailing how TIFF and JPEG differ in compression methods and image quality:

| Property Area | Tagged Image File Format (TIFF) | Joint Photographic Experts Group (JPEG) |
| :--- | :--- | :--- |
| **Compression Method** | Supports **Lossless** compression algorithms (e.g., LZW, Lempel-Ziv-Welch) or uncompressed storage. | Uses **Lossy** compression based on Discrete Cosine Transform (DCT) and coefficient quantization. |
| **Reversibility** | **Reversible**: No image data is discarded during compression. | **Irreversible**: High-frequency color details are permanently discarded. |
| **Impact on Quality** | **Zero quality degradation**. Ensures 100% pixel fidelity, maintaining professional standards. | **Degrades on every save**. Introduces blocking artifacts (8x8 pixel blocks) and blurring around sharp edges. |
| **File Size Constraints**| Very large file sizes, requiring significant local storage capacity. | Highly compact file sizes, making it exceptionally bandwidth-efficient. |
| **Editing Suitability** | Ideal for professional graphic design, medical imaging, and raw photo archiving. | Poor suitability for repeated editing and saving due to cumulative compression loss. |

---

## 📂 PART C: EXPECTED / PROBABLE THEORY QUESTIONS

This section contains highly expected theoretical questions based on the Unit 1 syllabus and lecture slides to help ensure complete coverage of the material:

---

#### **⭐ Expected Q1: Image Representation as a Mathematical Function** [3 Marks]
**Question:** Why is a digital image represented mathematically as a two-dimensional continuous function $f(x, y)$? Explain what each variable represents.
*   **Topic:** Digital Image Representation
*   **Answer:**
    *   **The 2D Function:** A digital image is represented as $f(x, y)$ because identifying any physical point on a flat visual surface requires specifying its relative location along two orthogonal coordinate axes (horizontal and vertical directional axes).
    *   **Spatial Coordinates $(x, y)$:** The variables $x$ and $y$ represent the spatial coordinates in a 2-D plane. By convention, $x$ denotes the row (vertical axis, increasing downward) and $y$ denotes the column (horizontal axis, increasing to the right).
    *   **Amplitude $f$:** The value of the function $f$ at any coordinate pair $(x, y)$ is a scalar quantity that represents the **intensity** or **gray level** of the image at that specific point. For color images, $f(x, y)$ is a vector containing the intensities of the red, green, and blue primary color channels:
        $$f(x, y) = egin{bmatrix} r(x, y) \ g(x, y) \ b(x, y) \end{bmatrix}$$

---

#### **⭐ Expected Q2: Continuous vs. Digital Images** [2 Marks]
**Question:** Differentiate between a continuous (analog) image and a digital image.
*   **Topic:** Digital Image Fundamentals
*   **Answer:**
    Below is a comparison table outlining the differences between continuous and digital images:

| Parameter | Continuous (Analog) Image | Digital Image |
| :--- | :--- | :--- |
| **Coordinate Resolution** | Spatial coordinates $(x, y)$ are continuous with infinite resolution. | Spatial coordinates $(x, y)$ are discrete and mapped onto a finite grid. |
| **Amplitude Value** | The intensity amplitude $f(x, y)$ can take any real value across an infinite range. | The intensity is quantized into a finite set of discrete integer values (e.g., $0$ to $255$). |
| **Computer Readability** | Cannot be processed directly by computers. | Natively processed and stored by computers as a 2D matrix of numbers. |

---

#### **⭐ Expected Q3: Bits Per Pixel (BPP) and Dynamic Range** [3 Marks]
**Question:** Explain the concept of bits per pixel (BPP) and how it defines the dynamic range of a digital image.
*   **Topic:** Digital Image Representation
*   **Answer:**
    *   **Bits Per Pixel (BPP):** BPP represents the bit depth of an image, which is the number of bits used to represent the intensity value of a single pixel in memory.
    *   **Dynamic Range Definition:** The dynamic range refers to the ratio of the maximum measurable intensity level to the minimum detectable intensity level in an image. In digital systems, it is represented by the total number of gray levels $L$ available.
    *   **Relationship:** The relationship is exponential:
        $$L = 2^k$$
        where $k$ is the BPP. A higher BPP exponentially increases the dynamic range of an image:
        *   **1 BPP:** $2^1 = 2$ levels (Binary image, containing only black and white).
        *   **8 BPP:** $2^8 = 256$ levels (Grayscale image, containing shades of gray from 0 to 255).
        *   **24 BPP:** $2^{24} pprox 16.7$ million colors (True color RGB image, with 8 bits per channel).

---

#### **⭐ Expected Q4: Pixel Neighborhoods ($N_4(p), N_D(p), N_8(p)$)** [4 Marks]
**Question:** Define and mathematically represent the three types of pixel neighborhoods for a pixel $p$ at coordinate $(x, y)$.
*   **Topic:** Pixel Spatial Relationships
*   **Answer:**
    ##### **1. 4-Neighborhood ($N_4(p)$)**
    The 4-neighborhood of pixel $p(x, y)$ consists of its four horizontal and vertical neighbors that share a physical edge:
    $$N_4(p) = \{(x+1, y), (x-1, y), (x, y+1), (x, y-1)\}$$
    
    ##### **2. Diagonal Neighborhood ($N_D(p)$)**
    The diagonal neighborhood of pixel $p(x, y)$ consists of its four diagonal neighbors that share only a physical corner:
    $$N_D(p) = \{(x+1, y+1), (x+1, y-1), (x-1, y+1), (x-1, y-1)\}$$
    
    ##### **3. 8-Neighborhood ($N_8(p)$)**
    The 8-neighborhood of pixel $p(x, y)$ is the union of its 4-neighborhood and diagonal neighborhood, representing all eight immediate neighbors:
    $$N_8(p) = N_4(p) \cup N_D(p)$$

*   **📊 Diagram Required: YES**
    *   *What to draw:* Sketch the three neighborhood layouts on a $3 	imes 3$ coordinate grid centered at $p(x, y)$.
    ```
       4-Neighbors (N4)         Diagonal Neighbors (ND)         8-Neighbors (N8)
        ┌───┬───┬───┐               ┌───┬───┬───┐               ┌───┬───┬───┐
        │   │ 1 │   │               │ 1 │   │ 1 │               │ 1 │ 1 │ 1 │
        ├───┼───┼───┤               ├───┼───┼───┤               ├───┼───┼───┤
        │ 1 │ p │ 1 │               │   │ p │   │               │ 1 │ p │ 1 │
        ├───┼───┼───┤               ├───┼───┼───┤               ├───┼───┼───┤
        │   │ 1 │   │               │ 1 │   │ 1 │               │ 1 │ 1 │ 1 │
        └───┴───┴───┘               └───┴───┴───┘               └───┴───┴───┘
    ```
    *   *Source slide:* `IVP UNIT 1.pptx` (Slide 7).

---

#### **⭐ Expected Q5: Metric Properties of Distance Functions** [5 Marks]
**Question:** For a function $D$ to be classified as a valid metric distance between two pixels $p(x,y)$ and $q(s,t)$, what mathematical properties must it satisfy?
*   **Topic:** Distance Measures
*   **Answer:**
    For a function $D$ to be a valid distance metric, it must satisfy the following four fundamental properties for all pixels $p$, $q$, and $z$:
    
    1.  **Non-Negativity:** The distance between any two pixels must be non-negative:
        $$D(p, q) \ge 0$$
    2.  **Identity of Indiscernibles:** The distance is zero if and only if the pixels are at the exact same coordinate location:
        $$D(p, q) = 0 \iff p = q$$
    3.  **Symmetry:** The distance from $p$ to $q$ is identical to the distance from $q$ to $p$:
        $$D(p, q) = D(q, p)$$
    4.  **Triangle Inequality:** The direct distance between $p$ and $q$ is always less than or equal to the path distance through a third intermediate pixel $z$:
        $$D(p, q) \le D(p, z) + D(z, q)$$

---

## 📂 PART D: COMPILATION ANALYSIS

To help optimize your study time, this section analyzes the Unit 1 theoretical topics, key comparisons, and diagram-based questions:

---

### 1. Most Frequently Asked Theoretical Concepts
1.  **Digitization (Sampling & Quantization):** This is the most highly tested concept in Unit 1. Exams often ask for the block diagram and definitions of sampling and quantization, as well as the effects of decreasing resolution (checkerboard effect and false contouring).
2.  **Connectivity & Adjacency:** Understating the differences between 4-connectivity, 8-connectivity, and m-connectivity is highly tested, particularly why m-connectivity is preferred to resolve path ambiguities.
3.  **Image File Formats:** High-weightage comparison questions regularly contrast JPEG vs. PNG and JPEG vs. TIFF.

---

### 2. High-Priority Comparison Tables

#### **Digital Grayscale Matrix vs. Continuous Mathematical Function**

| Feature | Digital Matrix Representation | Continuous Mathematical Function $f(x, y)$ |
| :--- | :--- | :--- |
| **Grid Domain** | Discrete rectangular grid of size $M 	imes N$. | Infinite continuous 2-D space. |
| **Coordinate Values** | $x \in \{0, 1, \dots, M-1\}$ and $y \in \{0, 1, \dots, N-1\}$. | $x \in \mathbb{R}$ and $y \in \mathbb{R}$. |
| **Intensity Values** | Integer gray levels (e.g., $0$ to $255$). | Continuous real-valued amplitude. |
| **Data Structure** | 2-D array of discrete numbers. | Continuous mathematical function. |

---

#### **Euclidean vs. City-Block vs. Chessboard Distance Metrics**

| Metric Parameter | Euclidean Distance ($D_e$) | City-Block Distance ($D_4$) | Chessboard Distance ($D_8$) |
| :--- | :--- | :--- | :--- |
| **Mathematical Equation** | $\sqrt{(x-u)^2 + (y-v)^2}$ | $|x-u| + |y-v|$ | $\max(|x-u|, |y-v|)$ |
| **Permitted Directions** | Any continuous direction. | Horizontal and vertical only. | Horizontal, vertical, and diagonal. |
| **Shape of Constant Distance**| Circle | Diamond | Square |
| **Shortest Path Weight** | Physical straight-line distance. | Taxicab grid-line distance. | 8-way traversal distance. |

---

### 3. High-Priority Diagram-Based Questions

*   **1. Sampling and Quantization Digitization Process:**
    *   **📊 Diagram Required: YES**
    *   *Sketch Details:* Show a continuous analog signal being spatially sampled onto a grid (discretizing coordinates), followed by amplitude rounding to discrete levels (quantization).
    *   *Source Slide:* `IVP UNIT 1.pptx` (Slides 5 & 6).
*   **2. Pixel Neighborhoods ($N_4(p), N_D(p), N_8(p)$):**
    *   **📊 Diagram Required: YES**
    *   *Sketch Details:* Draw three $3 	imes 3$ matrices centered at $p(x, y)$ highlighting the orthogonal neighbors, diagonal neighbors, and combined neighbors.
    *   *Source Slide:* `IVP UNIT 1.pptx` (Slide 7).
*   **3. Adjacency Path Ambiguity (8-connectivity vs. m-connectivity):**
    *   **📊 Diagram Required: YES**
    *   *Sketch Details:* Draw a $2 	imes 2$ matrix of $1$s. Show how 8-adjacency forms ambiguous diagonal crossing paths, and how m-adjacency eliminates this by removing the diagonal links when horizontal/vertical alternatives exist.
    *   *Source Slide:* `IVP UNIT 1.pptx` (Slide 9).

---

## 🏁 COMPLETE UNIT 1 SYLLABUS CHECKLIST

This checklist maps your exam syllabus topics to the coverage in this question bank:

*   [x] **Digital Image Representation** — Covered in **Expected Q1 & Q2** (Continuous vs. Digital).
*   [x] **Basics of Color Images** — Covered in **PYQ 3** (RGB planes and storage size).
*   [x] **Spatial and Gray-Level Resolution** — Covered in **PYQ 4** (Visual artifacts: checkerboard and false contouring).
*   [x] **Sampling and Quantization** — Covered in **PYQ 5** (Digitization block diagram).
*   [x] **Pixel Neighborhoods & Adjacency** — Covered in **PYQ 6, 7 & Expected Q4** (4-connectivity vs. 8-connectivity vs. m-connectivity).
*   [x] **Distance Measures** — Covered in **PYQ 8, 9 & Expected Q5** (Euclidean, City-block, Chessboard metrics).
*   [x] **Image File Formats** — Covered in **PYQ 10 & 11** (JPEG, PNG, TIFF comparisons).
