# NMIMS Unit 1: Image Fundamentals - PYQ Solved Question Bank
**Course:** Image and Video Processing (IVP)  
**Target Exam:** SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC)  
**Primary Reference:** `IVP UNIT 1.pptx` (Authoritative Source)  
**Syllabus Covered:**
*   Digital Image Representation — image as a 2-D matrix and mathematical function
*   Basics of Color Images — monochromatic vs. true color (RGB) planes and calculations
*   Resolution — spatial and gray-level resolution, sampling, and quantization
*   Distance Measures — Euclidean, City-Block ($D_4$), Chessboard ($D_8$), and m-distance ($D_m$)
*   Pixel Relationships — neighborhoods ($N_4(p), N_D(p), N_8(p)$), adjacency, connectivity, and paths
*   Image File Formats — Tagged Image File Format (TIFF), Portable Network Graphics (PNG), and Joint Photographic Experts Group (JPEG)

---

## 📊 PART A: TOPIC-WISE PYQ FREQUENCY & HIGH-PRIORITY ANALYSIS

To help you optimize your study time, this directory maps the frequency and recurring patterns of Unit 1 topics across all available SVKM's NMIMS Term Exams and Re-Exams (2022–2026):

### 1. Topic-Wise PYQ Frequency Map

| Topic Section | Sub-Topic / Concept | Frequency | Key Papers / Years |
| :--- | :--- | :---: | :--- |
| **Pixel Relationships & Distance Measures** | Distance measures ($D_e, D_4, D_8, D_m$) with numerical matrices | **High** (6x) | NMIMS Term Exam Dec 2025 (Q6a), NMIMS Re-Exam 2024-25 (Q1a), NMIMS Term Exam Nov 2023 (Q2b), NMIMS Test-I Set 1 (Q1a), NMIMS Test-I Set 2 (Q1b), NMIMS Re-Exam 2022-23 (Q1b) |
| **Pixel Relationships & Adjacency** | 4/8/m-adjacency drawing and paths in binary images | **Medium** (3x) | NMIMS Term Exam Dec 2025 (Q1d), NMIMS Term Exam Nov 2024 (Q2a), NMIMS Test-I Set 1 (Q1a) |
| **Image Sampling & Quantization** | A/D conversion processes, Down-sampling / Up-sampling matrices | **High** (4x) | NMIMS Re-Exam 2024-25 (Q1a), NMIMS Term Exam Nov 2023 (Q2b), NMIMS Re-Exam 2022-23 (Q2b), NMIMS Special Re-Exam 2022-23 (Q6a) |
| **Digital Image Representation** | Storage size, planes, bit depth, and dynamic range calculations | **High** (5x) | NMIMS Test-I Set 1 (Q1b), NMIMS Test-I Set 2 (Q1a), NMIMS Re-Exam 2024-25 (Q2a), NMIMS Re-Exam 2022-23 (Q1a), NMIMS Final Exam Dec 2022 (Q1g) |
| **Image File Formats** | Comparing features (JPEG vs. PNG vs. TIFF) & compression impact | **Medium** (3x) | NMIMS Term Exam Dec 2025 (Q1a), NMIMS Term Exam Nov 2024 (Q1a), NMIMS Re-Exam 2024-25 (Q1a) |

### 2. Repeated & Grouped Exam Concepts
1.  **The Sampling & Quantization Matrix Down/Up-Sampling Pattern:**
    *   NMIMS Re-Exam Jan 2023 (Q2b) asks for down-sampling by a factor of 2, followed by up-sampling by **averaging**.
    *   NMIMS Special Re-Exam June 2023 (Q6a) asks for down-sampling by a factor of 2, followed by up-sampling by **replication**.
    *   *Syllabus Concept:* Spatial resolution and gray-level resolution reduction.
2.  **Distance Measure on Arbitrary Matrices Pattern:**
    *   NMIMS Test-I Set 1 (Q1a) and Set 2 (Q1b) ask for city-block ($D_4$) and chessboard ($D_8$) distance on the exact same 3x3 matrices with different parameters.
    *   NMIMS Term Exam Nov 2023 (Q2b) asks for $D_4$ and $D_8$ distances on a 5x5 matrix.
    *   NMIMS Term Exam Dec 2025 (Q6a) asks for $D_e, D_4, D_8,$ and $D_m$ distances on a 3x3 matrix segment for $V = \{1, 2\}$.

---

## 📂 PART B: COMPLETE SOLUTIONS TO NMIMS TEST-I PAPERS (AUGUST 2025)

### ✍️ NMIMS TEST-I (SET 1) - August 22, 2025

#### **Question 1(a)(i)** [0.5 Marks]
**Question:** The \_\_\_\_\_ distance metric calculates the sum of the absolute differences between the coordinates of two pixels, assuming movement is restricted to horizontal and vertical directions.
*   **Answer:** **City-Block** (also denoted as $D_4$) [225].
*   **Concept:** The City-block distance restricts path traversal to only horizontal and vertical steps (4-connectivity neighborhood), analogous to navigating gridded streets in a city [420].

#### **Question 1(a)(ii)** [1.5 Marks]
**Question:** Apply the same distance measure on the given image from pixel at $(0,0)$ to pixel at $(1,2)$. Index starts from 0. Show the path.
| 20 | 40 | 60 |
|----|----|----|
| 80 | 100 | 120 |
| 140 | 160 | 180 |

*Image $I$, size $3 \times 3$ (0-based index)*
*   **Step 1: Identify Coordinates and Formula:**
    *   Start pixel $p$ is at $(0, 0)$ with intensity value `20`.
    *   End pixel $q$ is at $(1, 2)$ with intensity value `120`.
    *   City-block distance formula: 
        $$D_4(p, q) = |x - s| + |y - t|$$
        where $p = (x, y) = (0, 0)$ and $q = (s, t) = (1, 2)$ [225].
*   **Step 2: Calculate Distance:**
    $$D_4(p, q) = |0 - 1| + |0 - 2| = 1 + 2 = \mathbf{3} \text{ units}$$
*   **Step 3: Define Path options and Corresponding Values:**
    Since city-block restricts movement to horizontal/vertical steps, any path of minimum length 3 must take 1 vertical step and 2 horizontal steps. There are three possible shortest paths:
    1.  **Path 1 (Right-Right-Down):** $(0,0) \rightarrow (0,1) \rightarrow (0,2) \rightarrow (1,2)$
        *   *Intensity Path:* $20 \rightarrow 40 \rightarrow 60 \rightarrow 120$
    2.  **Path 2 (Right-Down-Right):** $(0,0) \rightarrow (0,1) \rightarrow (1,1) \rightarrow (1,2)$
        *   *Intensity Path:* $20 \rightarrow 40 \rightarrow 100 \rightarrow 120$
    3.  **Path 3 (Down-Right-Right):** $(0,0) \rightarrow (1,0) \rightarrow (1,1) \rightarrow (1,2)$
        *   *Intensity Path:* $20 \rightarrow 80 \rightarrow 100 \rightarrow 120$
*   *Note for Exam:* Presenting any of these paths with the correct formula guarantees full marks.

---

#### **Question 1(b)(i)** [0.5 Marks]
**Question:** If an image has $L$ intensity levels, the pixel values range from \_\_\_\_\_ to \_\_\_\_\_.
*   **Answer:** **$0$** to **$L-1$** [292].
*   **Concept:** Standard computer representation indexes discrete intensity levels starting at 0 (representing pure black) up to the maximum level $L-1$ (representing pure white) [292].

#### **Question 1(b)(ii)** [0.5 Marks]
**Question:** To represent 1024 intensity levels, a minimum of \_\_\_\_\_ bits per pixel are needed.
*   **Answer:** **10 bits**
*   **Calculation:** 
    $$L = 2^k \implies 1024 = 2^k \implies k = \log_2(1024) = 10 \text{ bits}$$

#### **Question 1(b)(iii)** [1 Mark]
**Question:** A color image has a resolution of $512 \times 512$ pixels with 24-bit depth. Define no. of planes in the given image and compute the size of the image.
*   **Step 1: Define Number of Planes:**
    *   A 24-bit true color RGB image consists of **3 planes**: one for Red, one for Green, and one for Blue [293].
*   **Step 2: Calculate Image Size:**
    $$\text{Size in bits} = \text{Height} \times \text{Width} \times \text{Bit Depth}$$
    $$\text{Size in bits} = 512 \times 512 \times 24 = \mathbf{6,291,456 \text{ bits}}$$
*   **Step 3: Convert to Bytes and Kilobytes (Highly Recommended for Exam):**
    $$\text{Size in Bytes} = \frac{6,291,456}{8} = \mathbf{786,432 \text{ Bytes}}$$
    $$\text{Size in KB} = \frac{786,432}{1024} = \mathbf{768 \text{ KB}}$$

---

### ✍️ NMIMS TEST-I (SET 2) - August 22, 2025

#### **Question 1(a)(i)** [2 Marks]
**Question:** A gray scale image has a resolution of $512 \times 512$ pixels with 8 bits depth. Define no. of planes in the image and compute the size of the image.
*   **Step 1: Define Number of Planes:**
    *   A grayscale (monochromatic) image has **1 plane** [293].
*   **Step 2: Calculate Image Size:**
    $$\text{Size in bits} = 512 \times 512 \times 8 \times 1 = \mathbf{2,097,152 \text{ bits}}$$
*   **Step 3: Convert to Bytes and Kilobytes:**
    $$\text{Size in Bytes} = \frac{2,097,152}{8} = \mathbf{262,144 \text{ Bytes}}$$
    $$\text{Size in KB} = \frac{262,144}{1024} = \mathbf{256 \text{ KB}}$$

#### **Question 1(a)(ii)** [1 Mark]
**Question:** The process of converting a continuous-tone image into a digital image involves two steps: \_\_\_\_\_ and \_\_\_\_\_.
*   **Answer:** **Sampling** and **Quantization** [236].
*   **Concept:** Sampling converts spatial continuous coordinates to discrete grid points; Quantization maps continuous amplitudes to discrete levels [236].

---

#### **Question 1(b)(i)** [0.5 Marks]
**Question:** The \_\_\_\_\_ distance metric is defined as the maximum of the absolute differences between the coordinates of two pixels, allowing horizontal and diagonal movement.
*   **Answer:** **Chessboard** (also denoted as $D_8$) [225, 299].
*   **Concept:** The Chessboard distance measures the shortest path assuming an 8-way adjacent movement (kings on a chessboard), meaning horizontal, vertical, and diagonal steps are all weighted as exactly 1 unit [299].

#### **Question 1(b)(ii)** [1.5 Marks]
**Question:** Write the formula and apply the same distance measure on the given image from pixel at $(0,0)$ to pixel at $(2,2)$. Index starts from 0. Show the path.
| 16 | 64 | 144 |
|----|----|----|
| 25 | 81 | 169 |
| 36 | 100 | 196 |

*Image $I$, size $3 \times 3$ (0-based index)*
*   **Step 1: Write Formula:**
    The Chessboard distance between pixels $p(x, y)$ and $q(s, t)$ is defined as:
    $D_8(p, q) = \max(|x - s|, |y - t|)$ [299]
*   **Step 2: Apply Coordinates:**
    Let $p = (0, 0)$ and $q = (2, 2)$:
    $$D_8(p, q) = \max(|0 - 2|, |0 - 2|) = \max(2, 2) = \mathbf{2} \text{ units}$$
*   **Step 3: Show Path:**
    Since diagonal movement is allowed, the shortest 8-adjacent path from $(0,0)$ to $(2,2)$ contains a single diagonal hop via the center pixel $(1,1)$:
    $$\text{Path:} \quad (0, 0) \rightarrow (1, 1) \rightarrow (2, 2)$$
    *   *Intensity Path:* $16 \rightarrow 81 \rightarrow 196$
*   ⭐ **Must Remember (Theoretical Trap):** Distance metrics ($D_4$ and $D_8$) depend *exclusively* on coordinates, not the intensity values stored in the matrix. The values along the path are simply evaluated to trace the visual path.

---

## 📂 PART C: COMPLETE SOLUTIONS TO NMIMS TERM EXAMS (2022–2026)

### ✍️ NMIMS TERM EXAM - December 8, 2025

#### **Question 1(a)** [4 Marks]
**Question:** Compare JPEG and PNG image file formats with respect to features and usage.
*   **Answer:**
    Here is the standard, 4-mark comparison table mapped from the synoptic answers [21, 22]:

| Feature Parameter | JPEG (Joint Photographic Experts Group) | PNG (Portable Network Graphics) |
| :--- | :--- | :--- |
| **Compression Type** | **Lossy** compression (removes visual redundant details) [21, 305]. | **Lossless** compression (perfect bit-by-bit recovery) [21, 424]. |
| **Color Support** | Optimized for **24-bit true color** (natural photographs) [304, 305]. | Supports **48-bit true color**, grayscale, and indexed [76]. |
| **Transparency (Alpha)**| Does **NOT** support transparency [21, 304]. | Fully supports **alpha channel transparency** [21, 76]. |
| **Interlacing** | Standard JPEGs are **not interlaced** (progressive variants exist) [21]. | Supports **interlacing** (progressive loading on web) [21, 300]. |
| **Ideal Usage** | Final distribution of **photographic scenes** to save space [22, 305]. | Web graphics, **diagrams, text logos, and image editing** [22, 305]. |

---

#### **Question 1(d)** [4 Marks]
**Question:** What is adjacency in image processing? Consider the following $5 \times 5$ binary image. The origin is at top-left and coordinates are written as (row,column) with 1-based indexing. Foreground pixels have value 1, (set $V = \{1\}$).
| 1 | 1 | 0 | 0 | 1 |
|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |

*Binary Image $I$, size $5 \times 5$, $V = \{1\}$ (1-based index)*
Draw dashed lines showing connections between pixels of the same label under:
1. 8-adjacency
2. m-adjacency
*   **Answer:**
    *   **Definition of Adjacency:** Two pixels are adjacent if they are spatial neighbors (e.g., sharing an edge or corner) and their intensity values satisfy a common criterion of similarity defined by a set $V$ [294].
    *   **Grid Coordinates (1-based indexing):**
        *   Row 1: $(1,1)=1$, $(1,2)=1$, $(1,5)=1$
        *   Row 2: $(2,1)=1$, $(2,2)=1$, $(2,4)=1$
        *   Row 4: $(4,2)=1$
        *   Row 5: $(5,3)=1$
    
    *   **Connections analysis (Set V = {1}):**
        *   **For 8-adjacency (diagonal allowed unconditionally):**
            *   Group A: Block $(1,1), (1,2), (2,1), (2,2)$ are all adjacent.
            *   Group B: $(1,5)$ is diagonally connected to $(2,4)$. (No other connections for Group B).
            *   Group C: $(4,2)$ is diagonally connected to $(5,3)$.
        *   **For m-adjacency (mixed adjacency to eliminate 8-way paths ambiguities):**
            *   Recall m-adjacency condition: $p$ and $q$ are m-adjacent if:
                1.  $q$ is in $N_4(p)$ [295], or
                2.  $q$ is in $N_D(p)$ and the intersection $N_4(p) \cap N_4(q)$ has **no pixels** whose values are from $V$ [295].
            *   *Let's analyze $(1,1), (1,2), (2,1), (2,2)$ block:*
                *   $(1,1)$ to $(1,2)$ is 4-adjacent $\rightarrow$ **Connected**.
                *   $(1,1)$ to $(2,1)$ is 4-adjacent $\rightarrow$ **Connected**.
                *   $(1,2)$ to $(2,2)$ is 4-adjacent $\rightarrow$ **Connected**.
                *   $(2,1)$ to $(2,2)$ is 4-adjacent $\rightarrow$ **Connected**.
                *   *What about diagonal $(1,1)$ to $(2,2)$?*
                    *   $N_4(1,1) \cap N_4(2,2) = \{(1,2), (2,1)\}$.
                    *   Since both $(1,2)$ and $(2,1)$ contain values from $V = \{1\}$, **the diagonal $(1,1)-(2,2)$ connection is DISALLOWED under m-adjacency** [295, 296].
                *   *What about diagonal $(1,2)$ to $(2,1)$?*
                    *   $N_4(1,2) \cap N_4(2,1) = \{(1,1), (2,2)\}$.
                    *   Since both $(1,1)$ and $(2,2)$ contain values from $V$, **the diagonal $(1,2)-(2,1)$ connection is DISALLOWED under m-adjacency** [295, 296].
            *   *Let's analyze $(1,5)$ and $(2,4)$:*
                *   They are diagonally related.
                *   $N_4(1,5) \cap N_4(2,4) = \{(1,4), (2,5)\}$.
                *   The values at $(1,4)$ and $(2,5)$ are both `0` (not in $V = \{1\}$).
                *   Thus, $(1,5)$ and $(2,4)$ **ARE connected under m-adjacency** [295].
            *   *Let's analyze $(4,2)$ and $(5,3)$:*
                *   They are diagonally related.
                *   $N_4(4,2) \cap N_4(5,3) = \{(4,3), (5,2)\}$.
                *   The values at $(4,3)$ and $(5,2)$ are both `0` (not in $V = \{1\}$).
                *   Thus, $(4,2)$ and $(5,3)$ **ARE connected under m-adjacency** [295].

*   **📊 Diagram Required: YES** (This question requires you to copy the matrix and draw these connections directly).
    *   *How to draw in exam:*
        ```
        1. 8-adjacency:
        [1] ─── [1]      [1]
         │ ╲   ╱ │      ╱
         │   ╳   │    ╱ 
         │ ╱   ╲ │  ╱
        [1] ─── [1] [1]

        [1]
          ╲
            ╲
             [1]
        
        2. m-adjacency:
        [1] ─── [1]      [1]
         │       │      ╱
         │       │    ╱
         │       │  ╱
        [1] ─── [1] [1]

        [1]
          ╲
            ╲
             [1]
        ```

---

#### **Question 6(a)** [4 Marks]
**Question:** An image segment is shown below. Let, $V$ be the set of Gray-level values used to define connectivity in the image. Compute: $D_e$, $D_4$, $D_8$ and $D_m$ distances between pixels ‘p’ and ‘q’ for: $V = \{1,2\}$.
| 0 | 1 | **2 (q)** |
|---|---|---------|
| 2 | 3 | 2 |
| **1 (p)** | 1 | 3 |

*Image $I$, size $3 \times 3$, $V = \{1,2\}$ (0-based index)*
*   **Step 1: Set coordinate system and parameters:**
    *   Let's use 0-based indexing:
        *   $p = (2, 0)$ with intensity value `1`. (Since $1 \in V$, $p$ is valid) [23].
        *   $q = (0, 2)$ with intensity value `2`. (Since $2 \in V$, $q$ is valid) [23].
    *   Let $p = (x, y) = (2, 0)$ and $q = (s, t) = (0, 2)$.

*   **Step 2: Calculate Euclidean Distance ($D_e$):**
    $D_e(p, q) = \sqrt{(x - s)^2 + (y - t)^2}$ [298]
    $D_e(p, q) = \sqrt{(2 - 0)^2 + (0 - 2)^2} = \sqrt{4 + 4} = \sqrt{8} \approx \mathbf{2.828 \text{ units}}$ [23]

*   **Step 3: Calculate City-Block Distance ($D_4$):**
    $D_4(p, q) = |x - s| + |y - t|$ [299]
    $D_4(p, q) = |2 - 0| + |0 - 2| = 2 + 2 = \mathbf{4} \text{ units}$ [23]

*   **Step 4: Calculate Chessboard Distance ($D_8$):**
    $D_8(p, q) = \max(|x - s|, |y - t|)$ [299]
    $D_8(p, q) = \max(|2 - 0|, |0 - 2|) = \max(2, 2) = \mathbf{2} \text{ units}$ [23]

*   **Step 5: Calculate Mixed Distance ($D_m$):**
    The mixed distance is defined as the length of the shortest path between $p$ and $q$ consisting strictly of m-adjacent pixels whose values are in $V = \{1, 2\}$ [214].
    *   *Let's trace pixels belonging to $V$:*
        *   $(2,0)=1 \in V$ ($p$)
        *   $(2,1)=1 \in V$
        *   $(1,0)=2 \in V$
        *   $(0,1)=1 \in V$
        *   $(0,2)=2 \in V$ ($q$)
        *   $(1,2)=2 \in V$
    *   *Analyze connectivity hops starting at $p(2,0)$:*
        *   Hop 1: From $(2,0)$ to $(1,0)$ $\rightarrow$ 4-adjacent (m-adjacent) $\rightarrow$ **Valid**.
        *   Hop 2: From $(1,0)$ to $(0,1)$ (diagonal) $\rightarrow$ check $N_4(1,0) \cap N_4(0,1) = \{(0,0), (1,1)\}$.
            *   Values: $(0,0)=0 
otin V$, $(1,1)=3 
otin V$.
            *   Since the intersection has no values from $V$, $(1,0)$ and $(0,1)$ are **m-adjacent**.
        *   Hop 3: From $(0,1)$ to $q(0,2)$ $\rightarrow$ 4-adjacent (m-adjacent) $\rightarrow$ **Valid**.
        *   *Resulting Path:* $(2,0) \rightarrow (1,0) \rightarrow (0,1) \rightarrow (0,2)$ has length = **3 hops** [214].
    *   *Alternate Path check:* $(2,0) \rightarrow (2,1) \rightarrow (1,2) \rightarrow (0,2)$
        *   Hop 1: $(2,0)$ to $(2,1)$ is 4-adjacent $\rightarrow$ **Valid**.
        *   Hop 2: $(2,1)$ to $(1,2)$ (diagonal) $\rightarrow$ check $N_4(2,1) \cap N_4(1,2) = \{(2,2), (1,1)\}$.
            *   Values: $(2,2)=3 
otin V$, $(1,1)=3 
otin V$.
            *   Since intersection has no values from $V$, they are **m-adjacent**.
        *   Hop 3: $(1,2)$ to $(0,2)$ is 4-adjacent $\rightarrow$ **Valid**.
        *   *Resulting Path:* $(2,0) \rightarrow (2,1) \rightarrow (1,2) \rightarrow (0,2)$ has length = **3 hops**.
    *   Therefore, the shortest m-path has length **3**.
    $$D_m(p, q) = \mathbf{3} \text{ units}$$

---

### ✍️ NMIMS TERM EXAM - November 2024

#### **Question 1(a)** [5 Marks]
**Question:** How do TIFF and JPEG differ in terms of compression methods, what impact does this have on image quality?
*   **Answer:**
    Here is a structured comparison table outlining the compression methods and their explicit impact on quality [3, 64, 428, 429]:

| Property Area | Tagged Image File Format (TIFF) | Joint Photographic Experts Group (JPEG) |
| :--- | :--- | :--- |
| **Compression Algorithm** | Supports **Lossless** compression algorithms (e.g., LZW, ZIP) as well as uncompressed storage [3, 429]. | Uses **Lossy** compression based on Discrete Cosine Transform (DCT) and coefficient quantization [428]. |
| **Compression Mode** | **Reversible** (No data discarded) [428]. | **Irreversible** (High-frequency details discarded) [428]. |
| **Impact on Quality** | **Zero quality degradation**. Ensures 100% fidelity, making it perfect for archives [63, 429]. | **Degrades on every save**. Introduces blocking artifacts (8x8 blocks) and blurring around sharp edges [305, 428]. |
| **Re-edit Suitability** | Excellent. Ideal for professional graphic design and raw photo capturing [62, 64]. | Poor. Continual decoding and re-saving worsens compression artifacts [64]. |
| **File Size Constraint** | Very large. Requires significant local storage [62, 63]. | Very small. Perfect for efficient internet bandwidth and web display [64, 305]. |

---

### ✍️ NMIMS RE-EXAM (Batch 2023-24) - December 2024

#### **Question 1(a)** [4 Marks]
**Question:** Calculate the Euclidean distance, city block distance and chessboard distance between two pixels located at $(0, 4)$ and $(6, 1)$.
*   **Step 1: Set coordinates:**
    *   $p = (x, y) = (0, 4)$
    *   $q = (s, t) = (6, 1)$
*   **Step 2: Calculate Euclidean Distance ($D_e$):**
    $D_e(p, q) = \sqrt{(0 - 6)^2 + (4 - 1)^2} = \sqrt{(-6)^2 + (3)^2}$ [298]
    $$D_e(p, q) = \sqrt{36 + 9} = \sqrt{45} \approx \mathbf{6.708 \text{ units}}$$
*   **Step 3: Calculate City-Block Distance ($D_4$):**
    $D_4(p, q) = |0 - 6| + |4 - 1| = 6 + 3 = \mathbf{9 \text{ units}}$ [299]
*   **Step 4: Calculate Chessboard Distance ($D_8$):**
    $D_8(p, q) = \max(|0 - 6|, |4 - 1|) = \max(6, 3) = \mathbf{6 \text{ units}}$ [299]

---

#### **Question 2(a)** [10 Marks]
**Question:** Describe spatial resolution and gray level resolution. Discuss the effects of decreased spatial and gray level resolution on the appearance of the image. Deliberate on the disadvantage of having increased resolution.
*   **Answer:**
    *   **1. Spatial Resolution:**
        *   **Definition:** Spatial resolution is the smallest discernible detail in an image [15].
        *   **Metric:** In print media, it is measured in dots per inch (DPI) or lines per inch; in digital systems, it is defined by the image dimensions (number of rows $M$ and columns $N$, i.e., $M \times N$ pixels) [15, 70].
    *   **2. Gray-Level (Intensity) Resolution:**
        *   **Definition:** Gray-level resolution refers to the smallest discernible change in intensity level [15].
        *   **Metric:** Measured by the number of bits $k$ used to quantize the intensity range, allowing $L = 2^k$ shades of gray [3].
    *   **3. Effect of Decreasing Spatial Resolution:**
        *   Decreasing spatial resolution reduces the total pixel density [70].
        *   **Visual Artifact:** The image becomes progressively blurred, leading to the **"checkerboard effect"** (pixelation error), where individual square pixels become visible to the naked eye.
    *   **4. Effect of Decreasing Gray-Level Resolution:**
        *   Decreasing the number of quantization bits reduces the number of available shades of gray [16].
        *   **Visual Artifact:** The transition between shades becomes harsh and stepped instead of smooth. This phenomenon is called **"false contouring"**, creating artificial banding in areas that should have smooth gradients (e.g., human skin or blue skies).
    *   **5. Disadvantages of Having Increased Resolution:**
        *   While increased resolution improves image fidelity, it has distinct design and hardware bottlenecks:
            1.  **Storage Costs:** Doubling the resolution quadruples the pixel count ($512 \times 512 = 256$ KB vs. $1024 \times 1024 = 1$ MB), requiring larger hard drives and memory [15].
            2.  **Transmission Bandwidth:** Higher resolution files demand greater transmission bandwidth, leading to slow loading speeds on web interfaces and lag in real-time streaming systems [64, 305].
            3.  **Processing Latency:** Complex mathematical transformations (such as 2D convolutions or transforms) scale quadratically with image size, drastically slowing down processing speeds.

---

### ✍️ NMIMS TERM EXAM - November 28, 2023

#### **Question 1(a.1)** [2 Marks]
**Question:** In a digital image, how does the 4-connectivity differ from the 8-connectivity? Give any 2 differences.
*   **Answer:**
    Here is a clear 2-mark comparison table outlining the structural differences:

| Parameter | 4-Connectivity | 8-Connectivity |
| :--- | :--- | :--- |
| **Neighbor Definition** | Two pixels $p$ and $q$ are connected only if $q$ is in the set of 4 orthogonal neighbors $N_4(p)$ [293, 294]. | Two pixels $p$ and $q$ are connected if $q$ is in the set of 8 orthogonal/diagonal neighbors $N_8(p)$ [294]. |
| **Shared Boundaries** | Pixels must share a **physical edge** [165]. | Pixels can share either a **physical edge** or a **corner** [165]. |
| **Path Traversal** | Restricts digital paths to only horizontal and vertical moves [420]. | Allows diagonal path hops, yielding shorter path lengths [299]. |

---

#### **Question 2(b)** [8 Marks]
**Question:** Imagine you are working on a task to digitize old photographs for a historical archive. Explain, in detail, the processes of sampling and quantization in the context of converting analog photographs into digital images. Discuss the relationship of quantization with gray level resolution. Also, analyze how the number of bits in an image define the size and quality of the image.
*   **Answer:**
    *   **1. Sampling Process for Digitization:**
        *   To preserve an old physical photograph, its continuous 2-D coordinates must be digitized [236].
        *   This is achieved by a scanning device or camera containing a sensor array (e.g., CCD) [17]. The photographic surface is partitioned into a 2-D grid of $M \times N$ discrete points [39, 144].
        *   The sampling density determines the **spatial resolution** [9, 245]. Higher sampling (e.g., 600 DPI vs 300 DPI) captures finer physical details from the photograph.
    *   **2. Quantization Process for Digitization:**
        *   Once sampled, each grid point has a continuous light intensity value [40, 245].
        *   Quantization maps this continuous analog value into a discrete level using an Analog-to-Digital converter [16]. It divides the continuous range into a limited, discrete set of $L$ values [236, 245].
    *   **3. Relationship of Quantization with Gray-Level Resolution:**
        *   Quantization defines the intensity steps [245]. If $k$ bits are used per pixel, the image possesses $L = 2^k$ gray levels [3].
        *   **Gray-level resolution** is directly proportional to $k$ [15]. An 8-bit quantization ($L=256$) is sufficient for smooth human visual perception; reducing it to 4-bit or 3-bit causes severe **false contouring** [16].
    *   **4. Impact of Bit Depth on Size and Quality:**
        *   **Storage Size Equation:** 
            $\text{Total Bits} = \text{Rows} \times \text{Columns} \times \text{Bit Depth } (k)$ [290]
        *   **Visual Quality relationship:** Higher $k$ allows smoother gradients, richer details, and wider dynamic range [3]. However, increasing $k$ increases storage and computational bandwidth requirements proportionally.

---

### ✍️ NMIMS RE-EXAM - January 27, 2023

#### **Question 2(b)** [10 Marks]
**Question:** Draw the block diagram and explain the process of spatial sampling and quantization to digitize an analog image. What is the resultant output image if the gray scale image given below is down sampled by a factor of 2? Further at the receiver, the down sampled image is up-sampled by factor of 2 by averaging. Write the resultant up-sampled image.
| 5 | 2 | 3 | 1 |
|---|---|---|---|
| 4 | 1 | 6 | 4 |
| 3 | 0 | 9 | 5 |
| 2 | 7 | 8 | 2 |

*Grayscale Image $I$, size $4 \times 4$*
*   **Answer Part 1: Spatial Sampling & Quantization Block Diagram and Explanation**
    *   *Block Diagram concept to study:*
        ```
         Continuous Scene [f(x,y)] 
                   │
                   ▼
         [ Spatial Sampling Grid ]   ──► Discretizes Coordinates
                   │
                   ▼
         [ Photo-Diode A/D Conv ]    ──► Quantizes Intensity Amplitudes
                   │
                   ▼
         [ 2-D Digital Matrix ]      ──► Discrete Integer Grid Output
        ```
    *   *Explanation:* Mapped in Topic 2, sampling digitizes coordinates, quantization digitizes intensity [236].

*   **Answer Part 2: Down-Sampling by a factor of 2**
    Down-sampling an image by a factor of 2 involves keeping every alternate row and column [48]. Let us use standard 0-based indexing and select even rows (Row 0, Row 2) and even columns (Col 0, Col 2):
    *   Selected coordinate entries:
        *   $(0,0) = 5$
        *   $(0,2) = 3$
        *   $(2,0) = 3$
        *   $(2,2) = 9$
    *   **Resultant Down-sampled Image ($I_{down}$):**

        | 5 | 3 |
        |---|---|
        | 3 | 9 |

*   **Answer Part 3: Up-sampling by a factor of 2 by Averaging (At Receiver)**
    At the receiver, the $2 \times 2$ matrix $I_{down}$ is expanded back to a $4 \times 4$ matrix by placing the down-sampled pixels at even row and column coordinates, then filling in intermediate pixels by taking the arithmetic mean of neighbors:
    *   *Step 1: Placement grid (blank cells = to be interpolated):*

        | 5 | _ | 3 | _ |
        |---|---|---|---|
        | _ | _ | _ | _ |
        | 3 | _ | 9 | _ |
        | _ | _ | _ | _ |
    *   *Step 2: Interpolate Horizontal intermediate values:*
        *   $I_{up}(0,1) = \frac{I_{up}(0,0) + I_{up}(0,2)}{2} = \frac{5 + 3}{2} = 4$
        *   $I_{up}(2,1) = \frac{I_{up}(2,0) + I_{up}(2,2)}{2} = \frac{3 + 9}{2} = 6$
    *   *Step 3: Interpolate Vertical intermediate values:*
        *   $I_{up}(1,0) = \frac{I_{up}(0,0) + I_{up}(2,0)}{2} = \frac{5 + 3}{2} = 4$
        *   $I_{up}(1,2) = \frac{I_{up}(0,2) + I_{up}(2,2)}{2} = \frac{3 + 9}{2} = 6$
    *   *Step 4: Interpolate Center value:*
        *   $I_{up}(1,1) = \frac{I_{up}(0,1) + I_{up}(2,1) + I_{up}(1,0) + I_{up}(1,2)}{4} = \frac{4 + 6 + 4 + 6}{4} = 5$
    *   *Step 5: Handle boundary extrapolation (replicate row 2 and column 2 to row 3 and column 3):*
        *   *Column 3:* $I_{up}(0,3) = I_{up}(0,2) = 3$, $I_{up}(1,3) = I_{up}(1,2) = 6$, $I_{up}(2,3) = I_{up}(2,2) = 9$
        *   *Row 3:* Replicate row 2 to row 3:
            *   $I_{up}(3,0) = 3$
            *   $I_{up}(3,1) = 6$
            *   $I_{up}(3,2) = 9$
            *   $I_{up}(3,3) = 9$
    *   **Resultant Up-sampled Image Matrix ($I_{up}$):**

        | 5 | 4 | 3 | 3 |
        |---|---|---|---|
        | 4 | 5 | 6 | 6 |
        | 3 | 6 | 9 | 9 |
        | 3 | 6 | 9 | 9 |

---

### ✍️ NMIMS TERM EXAM - December 15, 2022

#### **Question 1(g)** [5 Marks]
**Question:** The least significant bit of each pixel of the 3-bit image given below is replaced with 0. Draw the resultant image. Also, draw the histogram of the original and the resultant image.
| 0 | 1 | 2 | 3 |
|---|---|---|---|
| 4 | 5 | 6 | 7 |

*3-bit Image $I$, size $2 \times 4$*
*   **Step 1: Translate decimal values to 3-bit binary representation:**
    *   $0 \implies 000_2$
    *   $1 \implies 001_2$
    *   $2 \implies 010_2$
    *   $3 \implies 011_2$
    *   $4 \implies 100_2$
    *   $5 \implies 101_2$
    *   $6 \implies 110_2$
    *   $7 \implies 111_2$
*   **Step 2: Replace Least Significant Bit (LSB) with 0:**
    *   $000_2 \rightarrow 000_2 \implies 0$
    *   $001_2 \rightarrow 000_2 \implies 0$
    *   $010_2 \rightarrow 010_2 \implies 2$
    *   $011_2 \rightarrow 010_2 \implies 2$
    *   $100_2 \rightarrow 100_2 \implies 4$
    *   $101_2 \rightarrow 100_2 \implies 4$
    *   $110_2 \rightarrow 110_2 \implies 6$
    *   $111_2 \rightarrow 110_2 \implies 6$
*   **Step 3: Construct Resultant Image Matrix:**
    **Resultant Matrix $I_{result}$:**

    | 0 | 0 | 2 | 2 |
    |---|---|---|---|
    | 4 | 4 | 6 | 6 |
*   **Step 4: Draw Histograms (Original vs. Resultant):**
    *   *Original Histogram:* An even, flat distribution where each of the 8 levels has exactly 1 pixel.
    *   *Resultant Histogram:* All odd levels map to the even level directly below them.
        *   Level 0: **2 pixels**
        *   Level 1: **0 pixels**
        *   Level 2: **2 pixels**
        *   Level 3: **0 pixels**
        *   Level 4: **2 pixels**
        *   Level 5: **0 pixels**
        *   Level 6: **2 pixels**
        *   Level 7: **0 pixels**
*   **📊 Diagram Required: YES** (In the exam, sketch the bar charts matching these counts).

---

### ✍️ NMIMS SPECIAL RE-EXAM - June 12, 2023

#### **Question 6(a)** [10 Marks]
**Question:** Explain the process of Sampling and Quantization with neat sketch. Apply the process of down sampling by factor of 2 on the image given below. Also at receiver, the down sampled image is up sampled by factor of 2 by replication.
| 7 | 8 | 9 | 10 |
|---|---|---|---|
| 5 | 4 | 3 | 2 |
| 6 | 8 | 10 | 12 |
| 2 | 7 | 8 | 2 |

*Grayscale Image $I$, size $4 \times 4$*
*   **Answer Part 1: Sampling & Quantization Sketch and Explanation**
    *   *Refer to Topic 2 for full theoretical details [236].*
*   **Answer Part 2: Down-Sampling by a factor of 2**
    Using 0-based indexing, select alternate even rows (Row 0, Row 2) and even columns (Col 0, Col 2):
    *   $I_{down}(0,0) = I(0,0) = 7$
    *   $I_{down}(0,1) = I(0,2) = 9$
    *   $I_{down}(1,0) = I(2,0) = 6$
    *   $I_{down}(1,1) = I(2,2) = 10$
    *   **Resultant Down-sampled Matrix ($I_{down}$):**

        | 7 | 9 |
        |---|---|
        | 6 | 10 |
*   **Answer Part 3: Up-sampling by a factor of 2 by Replication (Nearest Neighbor)**
    Up-sampling by replication involves repeating each pixel entry to form a $2 \times 2$ homogeneous block [48]:
    *   For $I_{down}(0,0) = 7$: Replicated to positions $(0,0), (0,1), (1,0), (1,1)$
    *   For $I_{down}(0,1) = 9$: Replicated to positions $(0,2), (0,3), (1,2), (1,3)$
    *   For $I_{down}(1,0) = 6$: Replicated to positions $(2,0), (2,1), (3,0), (3,1)$
    *   For $I_{down}(1,1) = 10$: Replicated to positions $(2,2), (2,3), (3,2), (3,3)$
    *   **Resultant Up-sampled Matrix ($I_{up\_replicated}$):**

        | 7 | 7 | 9 | 9 |
        |---|---|---|---|
        | 7 | 7 | 9 | 9 |
        | 6 | 6 | 10 | 10 |
        | 6 | 6 | 10 | 10 |

---

## 📁 PART D: CORE UNIT 1 STUDY CONCEPTS & SUMMARY REFERENCE

### 1. The Core Formulas Sheet

*   **Digital Image Representation:**
    $$f(x, y) = \text{Intensity of pixel at row } x \text{ and column } y$$
*   **Image Storage Size Equation:**
    $$\text{Total Bits} = M \times N \times k$$
    where $M = \text{Rows}$, $N = \text{Columns}$, and $k = \text{Bit Depth}$.
*   **Number of Grayscale Levels:**
    $$L = 2^k$$
*   **Distance Formulas:**
    *   **Euclidean Distance ($D_e$):**
        $$D_e(p, q) = \sqrt{(x - s)^2 + (y - t)^2}$$
    *   **City-Block Distance ($D_4$):**
        $$D_4(p, q) = |x - s| + |y - t|$$
    *   **Chessboard Distance ($D_8$):**
        $$D_8(p, q) = \max(|x - s|, |y - t|)$$
    *   **m-Distance ($D_m$):**
        $$D_m(p, q) = \text{Shortest m-path length between } p \text{ and } q \text{ using set } V$$

---

### 2. Comprehensive Comparison Tables

#### **Sampling vs. Quantization**

| Parameter | Sampling | Quantization |
| :--- | :--- | :--- |
| **Primary Definition** | Discretization of continuous **spatial coordinates $(x, y)$** [236, 264]. | Discretization of continuous **intensity amplitude $f(x, y)$** [236, 264]. |
| **Domain** | **Spatial** Domain [252]. | **Intensity / Amplitude** Domain [252]. |
| **Determines** | Image **Dimensions** (height, width, spatial resolution) [15]. | Image **Depth / Tonal range** (gray-levels, colors) [15]. |
| **Primary Hardware** | CCD/CMOS sensor array dimension layout [87]. | Analog-to-Digital Converter (ADC) logic [16]. |
| **Low-Resolution Limit** | **Checkerboard Effect** (Pixelation / blurring) [290]. | **False Contouring** (Harsh step banding) [290]. |

---

### 3. Study Checklist & Exam Revision Points

*   [ ] **Origin Position Check:** Remember that by standard matrix convention, the origin $(0, 0)$ is at the **top-left corner** of the image [146, 211].
*   [ ] **Bit Depth Calculation Trap:** Read carefully if a question says "8-bit color image" (often means 8 bits total color depth) or "8 bits per channel color image" (means 24 bits color depth) [70].
*   [ ] **Distance Metrics Dependency:** Remember that $D_4$ and $D_8$ distances are *entirely independent of pixel path values*—they are calculated purely from coordinates [150, 214].
*   [ ] **m-Adjacency Conditions:** Diagonal pixels are m-connected *only* if their horizontal/vertical intersection contains no pixel with values from the set $V$ [295]. This is highly tested to eliminate paths ambiguities [296].

---

## 📝 PRACTICE QUESTIONS FOR REVISION

1.  **Practice Q1:** Calculate the Euclidean, City-Block, and Chessboard distances between $p(1, 2)$ and $q(5, 6)$ on a standard coordinate grid.
    *   *Hint:* $x-s = -4$, $y-t = -4 \implies D_e = \sqrt{32} \approx 5.66$, $D_4 = 8$, $D_8 = 4$.
2.  **Practice Q2:** Draw all m-path connections for a binary image segment where $V = \{1\}$:
    | 1 | 0 | 1 |
    |---|---|---|
    | 0 | 1 | 0 |
    | 1 | 0 | 1 |
    *   *Hint:* Analyze intersections.
3.  **Practice Q3:** If a continuous-tone color photograph is scanned at 300 DPI and has a physical dimension of 4 x 6 inches with 24-bit color, compute its spatial resolution and storage size in Megabytes (MB).
    *   *Hint:* Spatial resolution = $(4 \times 300) \times (6 \times 300) = 1200 \times 1800$ pixels. Total bits = $1200 \times 1800 \times 24$. Convert to Bytes, then MB.

---

## 🏁 SLIDE-BY-SLIDE COVERAGE CHECKLIST (`IVP UNIT 1.pptx`)

Every slide in the authoritative Unit 1 slide presentation has been meticulously covered in the notes and this question bank:

*   [x] **Slide 1: Title & Course Introduction** — Covered in study note introductions [232, 245].
*   [x] **Slide 2: Grayscale and Color images 2D concept** — Covered in Question 1.1–1.4 solutions [233, 247].
*   [x] **Slide 3: Definitions of digital image processing** — Covered in Section 1 study guide [233, 247].
*   [x] **Slide 4: Understanding the digital image matrix** — Covered in Topic 1 matrices [234, 245].
*   [x] **Slide 5: Sampling Definition and Mechanism** — Covered in Question 2.1–2.4 solutions [236, 252].
*   [x] **Slide 6: Quantization Definition and Mechanism** — Covered in Question 2.1–2.4 solutions [236, 252].
*   [x] **Slide 7: Pixel neighborhoods ($N_4(p), N_D(p), N_8(p)$)** — Covered in Section 3 study guide [293].
*   [x] **Slide 8: Adjacency (4-, 8-, and m-adjacency)** — Covered in Question 3.1–3.4 solutions [295].
*   [x] **Slide 9: Ambiguities of 8-adjacency & m-connectivity** — Covered in Question 3.2 solutions [296, 297].
*   [x] **Slide 10: Distance measures ($D_e, D_4, D_8$)** — Covered in Question 3.4–3.8 solutions [298, 299].
*   [x] **Slide 11: Tagged Image File Format (TIFF) properties** — Covered in Question 4.1–4.3 solutions [301].
*   [x] **Slide 12: Portable Network Graphics (PNG) properties** — Covered in Question 4.1–4.3 solutions [300].
*   [x] **Slide 13: Joint Photographic Experts Group (JPEG) properties** — Covered in Question 4.1–4.3 solutions [300].
