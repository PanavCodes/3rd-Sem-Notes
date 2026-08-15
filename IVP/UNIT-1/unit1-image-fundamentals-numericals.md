# Unit 1: Image Fundamentals - Solved Numerical Workbook
**Course:** Image and Video Processing (IVP)  
**Target Audience:** NMIMS MPSTME B.Tech COMP/EXTC Semester V students  
**Primary Source:** `IVP UNIT 1.pptx` (and official past year university papers 2022-2026)  
**Tone:** Clear, rigorous, mathematical, and exam-focused.

---

## 📖 Introduction & Syllabus Mapping

This workbook is a comprehensive collection of **every single numerical and problem-solving question** related to **Unit 1: Image Fundamentals** that has appeared in NMIMS Term Exams, Re-Exams, and Class Tests. 

Every problem features an analytical breakdown: its coordinate indexing convention, the underlying physical and mathematical concepts, a detailed step-by-step solution, and an explanation of common traps used by examiners.

---

## 📊 Section 1: Digital Image Representation & Size Calculations

### 🧠 Core Concepts & Formulas

1. **Digital Image Function:** An image is represented as a 2D continuous intensity function $f(x, y)$, where $x$ and $y$ are spatial coordinates. When $x$, $y$, and the amplitude values of $f$ are discrete and finite, it is a **digital image** [74, 179].
2. **Matrix Representation:** A digital image of size $M 	imes N$ is represented as a matrix with $M$ rows (vertical coordinate $x = 0 \text{ to } M-1$) and $N$ columns (horizontal coordinate $y = 0 \text{ to } N-1$) [3, 80].
3. **Bit Depth ($k$):** The number of bits used to represent the intensity level of each pixel [3, 64].
4. **Grayscale Levels ($L$):** The number of distinct shades of gray an image can display [3, 41]:
   $$L = 2^k \implies k = \log_2(L)$$
5. **Number of Planes ($P$):**
   * Grayscale (monochrome) images consist of **1 spatial plane** [293].
   * True color (RGB) images consist of **3 spatial planes** (Red, Green, Blue channels) [13, 14].
6. **Total Storage Size Equation:**
   $$\text{Size (bits)} = M \times N \times k \times P$$
   To convert bits to Bytes:
   $$\text{Size (Bytes)} = \frac{\text{Size (bits)}}{8}$$
   To convert Bytes to Kilobytes (KB):
   $$\text{Size (KB)} = \frac{\text{Size (Bytes)}}{1024}$$

---

### 📝 Problem 1.1: Grayscale Image Size Calculation
* **Exact Original Question:** A gray scale image has a resolution of $512 \times 512$ pixels with 8 bits depth. Define no. of planes in the image and compute the size of the image.
* **Exam Source:** NMIMS Test-I (Set 2), August 22, 2025, Q1(a)(i) [1+1 Marks]
* **Topic:** Digital Image Representation / Storage Resolution
* **Given Information:**
  * Spatial resolution: $M = 512$ rows, $N = 512$ columns
  * Bit depth: $k = 8$ bits per pixel
* **What is Asked:**
  1. Define the number of spatial planes in the image.
  2. Compute the total storage size of the image.

#### 🧠 How to Approach
1. Recall the physical definition of a grayscale image: it has no color components, meaning only a single channel/plane is required to represent the light intensity [164, 182].
2. Apply the Storage Size Equation using the dimensions, bit depth, and planes.
3. Perform the arithmetic and convert the final result into standard bytes and kilobytes to show complete work.

#### ⭐ Relevant Formulas & Why They Are Used
* **Number of planes for grayscale:** $P = 1$
* **Storage Size Equation:** $\text{Size (bits)} = M \times N \times k$
  * *Reason:* Each of the $M \times N$ pixels requires exactly $k$ bits to store its gray-level value [290].

#### ⚡ Step-by-Step Solution
1. **Identify the Number of Planes:**
   A grayscale image is monochromatic and does not contain separate color bands. Therefore, it consists of **1 spatial plane** [293].
   
2. **Compute the Storage Size in Bits:**
   $$\text{Size (bits)} = 512 \times 512 \times 8 \times 1$$
   $$\text{Size (bits)} = 262,144 \times 8 = \mathbf{2,097,152 \text{ bits}}$$

3. **Convert to Bytes (Divide by 8):**
   $$\text{Size (Bytes)} = \frac{2,097,152}{8} = \mathbf{262,144 \text{ Bytes}}$$

4. **Convert to Kilobytes (Divide by 1024):**
   $$\text{Size (KB)} = \frac{262,144}{1024} = \mathbf{256 \text{ KB}}$$

#### ⚠️ Common Mistake & Exam Trick
* **The KB division error:** Many students divide by $1000$ instead of $1024$ when converting bytes to KB, which results in $262.14$ KB. Always divide by $1024$ for binary-based computer storage units.
* **✍️ Final Exam Answer:** The image has **1 plane**, and its size is **262,144 Bytes** (or **256 KB**).

---

### 📝 Problem 1.2: True Color (RGB) Image Size Calculation
* **Exact Original Question:** A color image has a resolution of $512 \times 512$ pixels with 24-bit depth. Define no. of planes in the given image and compute the size of the image.
* **Exam Source:** NMIMS Test-I (Set 1), August 22, 2025, Q1(b)(iii) [1 Mark]
* **Topic:** Digital Image Representation / Storage Resolution
* **Given Information:**
  * Spatial resolution: $M = 512$ rows, $N = 512$ columns
  * Color depth: 24 bits total per pixel (8 bits each for R, G, B) [4, 56]
* **What is Asked:**
  1. Define the number of spatial planes.
  2. Compute the total storage size in bytes.

#### 🧠 How to Approach
1. Recall that a true-color RGB image is represented by combining three separate primary color channels (Red, Green, Blue) [13, 14].
2. Identify that the total bit depth is $24$ bits (which is equivalent to $P=3$ planes $\times$ $8$ bits/plane).
3. Apply the Storage Size Equation and perform conversions.

#### ⭐ Relevant Formulas & Why They Are Used
* **Number of planes for RGB:** $P = 3$ [293]
* **Storage Size Equation:** $\text{Size (bits)} = M \times N \times \text{Bit Depth}$
  * *Reason:* A true color pixel is represented as a triplet $(R, G, B)$ where each element requires 8 bits of memory [19, 56].

#### ⚡ Step-by-Step Solution
1. **Identify the Number of Planes:**
   An RGB true color image is composed of **3 distinct spatial planes** (one Red plane, one Green plane, and one Blue plane) [13, 14].
   
2. **Compute the Storage Size in Bits:**
   $$\text{Size (bits)} = 512 \times 512 \times 24 = \mathbf{6,291,456 \text{ bits}}$$

3. **Convert to Bytes (Divide by 8):**
   $$\text{Size (Bytes)} = \frac{6,291,456}{8} = \mathbf{786,432 \text{ Bytes}}$$

4. **Convert to Kilobytes (Divide by 1024):**
   $$\text{Size (KB)} = \frac{786,432}{1024} = \mathbf{768 \text{ KB}}$$

#### ⚠️ Common Mistake & Exam Trick
* **Plane vs. Bit Depth Multiplication:** Do not multiply the size by $3$ again if you have already used the total bit depth of $24$ bits. The total size is $512 \times 512 \times 24$ bits, which is exactly equal to $512 \times 512 \times 8 \text{ bits} \times 3 \text{ planes}$.
* **✍️ Final Exam Answer:** The image has **3 planes**, and its size is **786,432 Bytes** (or **768 KB**).

---

### 📝 Problem 1.3: Grayscale Bit Depth & Storage Size Analysis
* **Exact Original Question:** For the given image, $S(x,y)$:
  a) Identify the type of image (binary/ gray/ color).
  b) How many bits are required to represent this image by considering the range of pixel values?
  c) Compute the number of bits required to store this image.

| 65 | 25 | 95 | 65 | 40 |
|----|----|----|----|----|
| 10 | 95 | 40 | 65 | 25 |
| 95 | 25 | 65 | 40 | 65 |
| 65 | 40 | 40 | 10 | 25 |
| 25 | 65 | 10 | 65 | 10 |

*Matrix $S(x,y)$, size $5 \times 5$*
* **Exam Source:** NMIMS Re-Exam (Batch 2023-24), February 15, 2025, Q2(a) [Parts a, b, d - 4 Marks]
* **Topic:** Digital Image Representation / Quantization
* **Given Information:**
  * Image Matrix: $5 \times 5$ dimension
  * Dynamic range of intensities: Minimum value = $10$, Maximum value = $95$
* **What is Asked:**
  1. Identify the image type.
  2. Compute the minimum bit depth ($k$) required based on the intensity range.
  3. Compute the total storage space in bits.

#### 🧠 How to Approach
1. Look at the pixel values. Since they contain numbers other than $0$ and $1$ (e.g., $65, 25, 95$), and there are no three distinct spatial planes mentioned, it is a grayscale image.
2. Find the maximum pixel intensity in the matrix ($95$). Find the smallest power of 2 ($2^k$) that is strictly greater than or equal to this maximum value to satisfy the quantization range.
3. Multiply the total pixels ($M \times N$) by this calculated minimum bit depth ($k$) to find the total storage bits.

#### ⭐ Relevant Formulas & Why They Are Used
* **Maximum Grayscale Level Condition:** $2^k \ge \text{Maximum intensity value} + 1$
  * *Reason:* If the maximum value in the image is $95$, we must be able to represent at least $0$ to $95$ (which is $96$ distinct gray levels). The minimum bit depth $k$ must satisfy $2^k \ge 96$.
* **Storage Space:** $\text{Bits} = M \times N \times k$

#### ⚡ Step-by-Step Solution
1. **Identify the Type of Image (Part a):**
   The pixel intensities are integers spanning from $10$ to $95$ (multiple levels of gray, no color triplet structures). Therefore, it is a **grayscale (monochromatic) image**.
   
2. **Compute the Minimum Bit Depth Required (Part b):**
   * Scan the matrix to find the maximum intensity value: $\text{Max Value} = 95$.
   * To prevent truncation, the quantization levels $L$ must be able to represent intensities up to $95$.
   * Let's test powers of 2:
     * For $k = 6 \implies L = 2^6 = 64$ levels (can only represent values $0$ to $63$, which is too small for $95$).
     * For $k = 7 \implies L = 2^7 = 128$ levels (can represent values $0$ to $127$, which safely covers $95$).
   * Therefore, a minimum of **7 bits** are required to represent each pixel.

3. **Compute the Storage Space Needed (Part d / c):**
   * Dimensions: $M = 5$, $N = 5$
   * Total pixels: $5 \times 5 = 25$ pixels
   * Bit depth: $k = 7$ bits per pixel
   * Total storage bits:
     $$\text{Total Storage} = 25 \text{ pixels} \times 7 \text{ bits/pixel} = \mathbf{175 \text{ bits}}$$

#### ⚠️ Common Mistake & Exam Trick
* **The "95 is less than 256" trap:** Many students automatically assume any grayscale image is default 8-bit. However, the question says *"by considering the range of pixel values"*. Since the maximum value is $95$, a 7-bit encoder ($128$ levels) is mathematically sufficient and saves storage. Do not default to 8 bits unless specified!
* **✍️ Final Exam Answer:**
  * a) Image Type: **Grayscale**
  * b) Minimum Bit Depth: **7 bits**
  * c) Total Storage Space: **175 bits**

---

### 📝 Problem 1.4: Gray Levels to Bit Depth Storage Conversion
* **Exact Original Question:** Find the number of bits required to store a $256 \times 256$ image with 32 gray levels.
* **Exam Source:** NMIMS Solved University Papers / PYQ [2 Marks]
* **Topic:** Digital Image Representation
* **Given Information:**
  * Spatial resolution: $256 \times 256$ pixels
  * Allowed intensity levels: $L = 32$
* **What is Asked:** Compute the total number of bits required to store the image.

#### ⚡ Step-by-Step Solution
1. **Find Bit Depth ($k$):**
   $$L = 2^k \implies 32 = 2^k \implies k = \log_2(32) = \mathbf{5 \text{ bits}}$$
2. **Apply Storage Formula:**
   $$\text{Size (bits)} = 256 \times 256 \times 5 \times 1 = 65,536 \times 5 = \mathbf{327,680 \text{ bits}}$$
3. **Convert to Bytes (for completeness):**
   $$\text{Size (Bytes)} = \frac{327,680}{8} = \mathbf{40,960 \text{ Bytes}} \quad (40 \text{ KB})$$
* **✍️ Final Exam Answer:** **327,680 bits** (or **40,960 Bytes**).

---

## 🔗 Section 2: Pixel Adjacency, Neighborhoods, and Connectivity

### 🧠 Core Concepts & Formulas

1. **Neighborhoods of a Pixel $p(x, y)$:**
   * **4-Neighbors ($N_4(p)$):** The set of horizontal and vertical immediate neighbors:
     $$N_4(p) = \{(x-1, y), (x+1, y), (x, y-1), (x, y+1)\}$$
   * **Diagonal Neighbors ($N_D(p)$):** The set of four diagonal neighbors:
     $$N_D(p) = \{(x-1, y-1), (x-1, y+1), (x+1, y-1), (x+1, y+1)\}$$
   * **8-Neighbors ($N_8(p)$):** The union of orthogonal and diagonal neighbors:
     $$N_8(p) = N_4(p) \cup N_D(p)$$
2. **Adjacency Conditions (using set $V$ of similar intensities):**
   * **4-Adjacency:** Two pixels $p$ and $q$ with values in $V$ are 4-adjacent if $q \in N_4(p)$.
   * **8-Adjacency:** Two pixels $p$ and $q$ with values in $V$ are 8-adjacent if $q \in N_8(p)$.
   * **m-Adjacency (Mixed Adjacency):** Two pixels $p$ and $q$ with values in $V$ are m-adjacent if:
     1. $q \in N_4(p)$, **OR**
     2. $q \in N_D(p)$ **AND** the intersection of their 4-neighborhoods $N_4(p) \cap N_4(q)$ contains **no pixels** with values from set $V$.

---

### 📝 Problem 2.1: 8-Adjacency and m-Adjacency Drawing and Connections
* **Exact Original Question:** What is adjacency in image processing? Consider the following $5 \times 5$ binary image. The origin is at top-left and coordinates are written as (row,column) with 1-based indexing. Foreground pixels have value 1 (set V = {1}).

| 1 | 1 | 0 | 0 | 1 |
|---|---|---|---|---|
| 1 | 1 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |

*Binary Image $I$, size $5 \times 5$, V = {1}*

  Draw dashed lines showing connections between pixels of the same label under:
  1. 8-adjacency
  2. m-adjacency
* **Exam Source:** NMIMS Final Examination, December 8, 2025, Q1(d) [4 Marks]
* **Topic:** Pixel Adjacency / Spatial Connectivity
* **Given Information:**
  * Binary Matrix ($5 \times 5$)
  * Adjacency set $V = \{1\}$ (we only care about connecting pixels carrying the value `1`)
  * 1-based indexing with top-left origin
* **What is Asked:**
  1. Define Adjacency.
  2. Map and draw all valid links between adjacent 1s under 8-adjacency.
  3. Map and draw all valid links between adjacent 1s under m-adjacency.

#### 🧠 How to Approach
1. **Identify the coordinates of all pixels containing 1:**
   * $A(1,1)=1$, $B(1,2)=1$, $C(2,1)=1$, $D(2,2)=1$ (The top-left block)
   * $E(1,5)=1$, $F(2,4)=1$ (Top-right diagonal relationship)
   * $G(4,2)=1$, $H(5,3)=1$ (Bottom-left diagonal relationship)
2. **For 8-adjacency:** Connect any two 1s that are horizontal, vertical, or diagonal neighbors.
3. **For m-adjacency:** 
   * Connect all vertical and horizontal neighbors first (4-adjacency is automatically m-adjacent).
   * For diagonal neighbors, compute the intersection of their 4-neighbors. If there is a `1` in the intersection, **do not connect** diagonally. If the intersection contains only `0`s, **connect** diagonally.

#### ⭐ Relevant Formulas & Rules
* **Intersection test for diagonal $p$ and $q$:** $N_4(p) \cap N_4(q)$.
  * If $\text{values in intersection} \cap V = \emptyset$, the connection is m-adjacent [295].

#### ⚡ Step-by-Step Solution

##### Step 1: Map Out All Potential Connections
Let's analyze each group of 1s in the image:

* **Group 1: Top-Left $2 \times 2$ block of 1s**
  * Orthogonal connections (Row 1 Col 1 to Row 1 Col 2, etc.):
    * $(1,1) \text{ to } (1,2)$ is horizontal $\implies$ **Connected in 8-adj and m-adj**
    * $(1,1) \text{ to } (2,1)$ is vertical $\implies$ **Connected in 8-adj and m-adj**
    * $(1,2) \text{ to } (2,2)$ is vertical $\implies$ **Connected in 8-adj and m-adj**
    * $(2,1) \text{ to } (2,2)$ is horizontal $\implies$ **Connected in 8-adj and m-adj**
  * Diagonal connections within the $2 \times 2$ block:
    * **Diagonal 1: $(1,1)$ to $(2,2)$**
      * Under 8-adjacency: They are diagonal neighbors $\implies$ **Connected**.
      * Under m-adjacency: Let's find $N_4(1,1) \cap N_4(2,2)$.
        $$N_4(1,1) = \{(1,2), (2,1)\} \quad \text{and} \quad N_4(2,2) = \{(1,2), (2,1), (2,3), (3,2)\}$$
        $$Intersection = \{(1,2), (2,1)\}$$
        * Values at these intersection coordinates are $(1,2) = 1$ and $(2,1) = 1$. Since these are $\in V = \{1\}$, the m-adjacency condition is violated.
        * Therefore, **$(1,1)$ and $(2,2)$ are NOT m-adjacent** [295].
    * **Diagonal 2: $(1,2)$ to $(2,1)$**
      * Under 8-adjacency: They are diagonal neighbors $\implies$ **Connected**.
      * Under m-adjacency: $N_4(1,2) \cap N_4(2,1) = \{(1,1), (2,2)\}$.
        * Values at the intersection coordinates are $(1,1) = 1$ and $(2,2) = 1$. Both are $\in V$.
        * Therefore, **$(1,2)$ and $(2,1)$ are NOT m-adjacent** [295].

* **Group 2: Top-Right diagonal 1s: $(1,5)$ and $(2,4)$**
  * Under 8-adjacency: They are diagonal neighbors $\implies$ **Connected**.
  * Under m-adjacency: Find $N_4(1,5) \cap N_4(2,4) = \{(1,4), (2,5)\}$.
    * Intensity values at coordinates $(1,4) = 0$ and $(2,5) = 0$. Since neither is $\in V = \{1\}$, the diagonal link is valid.
    * Therefore, **$(1,5)$ and $(2,4)$ ARE m-adjacent** [295].

* **Group 3: Bottom-Left diagonal 1s: $(4,2)$ and $(5,3)$**
  * Under 8-adjacency: They are diagonal neighbors $\implies$ **Connected**.
  * Under m-adjacency: Find $N_4(4,2) \cap N_4(5,3) = \{(4,3), (5,2)\}$.
    * Intensity values at coordinates $(4,3) = 0$ and $(5,2) = 0$. Since neither is $\in V = \{1\}$, the diagonal link is valid.
    * Therefore, **$(4,2)$ and $(5,3)$ ARE m-adjacent** [295].

##### Step 2: Draw the Connectivity Diagrams
This visual representation is mandatory to receive the full 4 marks in the exam:

```
=== (1) 8-Adjacency Connections ===

(1,1) [1] ──────── [1] (1,2)                       (1,5) [1]
       │  ╲        ╱  │                                   ╱
       │    ╲    ╱    │                                 ╱
       │      ╳       │                               ╱
       │    ╱    ╲    │                             ╱
(2,1) [1] ──────── [1] (2,2)                 (2,4) [1]




(4,2) [1]
        ╲
          ╲
            ╲
             [1] (5,3)


=== (2) m-Adjacency Connections ===

(1,1) [1] ──────── [1] (1,2)                       (1,5) [1]
       │              │                                   ╱
       │  NO DIAGONAL │                                 ╱
       │  CONNECTIONS │                               ╱
       │  ALLOWED     │                             ╱
(2,1) [1] ──────── [1] (2,2)                 (2,4) [1]




(4,2) [1]
        ╲
          ╲
            ╲
             [1] (5,3)
```

#### ⚠️ Common Mistake & Exam Trick
* **The diagonal "X" crossing loop:** 8-adjacency creates crossing lines (closed diagonal loop) in the top-left block of four 1s. This is called "multiple path ambiguity" [296, 297]. m-adjacency was invented specifically to prevent this. If you see crossing lines in your m-adjacency sketch, you have made an error!
* **✍️ Final Exam Answer:** Under m-adjacency, diagonal connections within the $2 \times 2$ top-left block are disallowed because their intersecting orthogonal neighbors are 1. The separate diagonal groups connect under both 8- and m-adjacency because their intersecting orthogonal neighbors are 0.

---

### 📝 Problem 2.2: Adjacency and Neighborhood Mapping on a $5 	imes 5$ Grid
* **Exact Original Question:** Explain the neighborhood and adjacency. According to the following intensity values of a $5 \times 5$ image, show the paths by drawing dashed lines for 4-adjacency, 8-adjacency and m-adjacency. Let V = {1,2,3}.

| 5 | 8 | 3 | 4 | 2 |
|---|---|---|---|---|
| 4 | 8 | 7 | 1 | 3 |
| 8 | 2 | 3 | 6 | 1 |
| 8 | 2 | 1 | 0 | 1 |
| 2 | 4 | 6 | 9 | 3 |

*Grayscale Image $I$, size $5 \times 5$, V = {1,2,3}*

* **Exam Source:** NMIMS Final Examination, December 7, 2024, Q2(a) [10 Marks]
* **Topic:** Pixel Adjacency / Connectivity Graph
* **Given Information:**
  * Grayscale Matrix ($5 \times 5$)
  * Allowed connectivity intensity values: $V = \{1, 2, 3\}$
* **What is Asked:**
  1. Define neighborhood and adjacency.
  2. Trace and draw the connectivity pathways using set $V$ under 4-adjacency, 8-adjacency, and m-adjacency.

#### 🧠 How to Approach
1. **Highlight and list all coordinates (using 1-based indexing) that have values inside $V = \{1, 2, 3\}$:**
   * $(1,3) = 3$
   * $(1,5) = 2$
   * $(2,4) = 1$
   * $(2,5) = 3$
   * $(3,2) = 2$
   * $(3,3) = 3$
   * $(3,5) = 1$
   * $(4,2) = 2$
   * $(4,3) = 1$
   * $(4,5) = 1$
   * $(5,1) = 2$
   * $(5,5) = 3$
2. **Analyze step-by-step connectivity transitions:**
   * *orthogonal steps:* check for any direct vertical/horizontal steps among these selected coordinates.
   * *diagonal steps:* check for diagonal relations and apply m-adjacency intersection exclusions.

#### ⚡ Step-by-Step Solution

##### Step 1: Theoretical Definitions
* **Neighborhood:** A subset of pixels surrounding a central pixel $p(x, y)$ that are physically close [20].
* **Adjacency:** A combination of a neighborhood relationship (closeness in space) and an intensity relationship (closeness in grayscale value defined by set $V$) [294].

##### Step 2: Establish Connectivity Paths
Let's analyze the spatial clusters of pixels with values in $V$:

* **Cluster A: Top-Right Corner Block**
  * Pixels in this cluster: $(1,3)=3$, $(2,4)=1$, $(1,5)=2$, $(2,5)=3$, $(3,5)=1$
  * **4-Adjacency Links:**
    * $(1,5)=2$ and $(2,5)=3$ are vertical neighbors $\implies$ **Connected**.
    * $(2,5)=3$ and $(3,5)=1$ are vertical neighbors $\implies$ **Connected**.
  * **8-Adjacency Links:**
    * Includes the 4-adjacency links.
    * Diagonal $(1,3)=3$ and $(2,4)=1$ are diagonal neighbors $\implies$ **Connected**.
    * Diagonal $(2,4)=1$ and $(1,5)=2$ are diagonal neighbors $\implies$ **Connected**.
    * Diagonal $(2,4)=1$ and $(2,5)=3$ are horizontal neighbors (not adjacent since $N_4$ doesn't connect $(2,4)$ and $(2,5)$? Wait, $(2,4)$ and $(2,5)$ are horizontal neighbors $\implies$ **Connected** in 4-adjacency!).
      * Ah! $(2,4)$ and $(2,5)$ are horizontal neighbors, so they are directly 4-adjacent! Let's update that.
    * Diagonal $(2,4)=1$ and $(3,5)=1$ are diagonal neighbors $\implies$ **Connected**.
  * **m-Adjacency Links:**
    * Includes all 4-adjacency links: $(2,4)-(2,5)$, $(1,5)-(2,5)$, $(2,5)-(3,5)$.
    * *Let's test diagonal $(1,3)$ to $(2,4)$:*      $N_4(1,3) \cap N_4(2,4) = \{(1,4), (2,3)\}$.
      * Intensity values: $(1,4) = 4 \notin V$, $(2,3) = 7 \notin V$.
      * Both are outside $V$, so the intersection contains no values from $V$.
      * Therefore, **$(1,3)$ and $(2,4)$ are m-adjacent**.
    * *Let's test diagonal $(2,4)$ to $(1,5)$:*      $N_4(2,4) \cap N_4(1,5) = \{(1,4), (2,5)\}$.
      * Since $(2,5) = 3 \in V$, the intersection contains a pixel from $V$.
      * Therefore, **$(2,4)$ and $(1,5)$ are NOT m-adjacent**.
    * *Let's test diagonal $(2,4)$ to $(3,5)$:*      $N_4(2,4) \cap N_4(3,5) = \{(2,5), (3,4)\}$.
      * Since $(2,5) = 3 \in V$, the intersection contains a pixel from $V$.
      * Therefore, **$(2,4)$ and $(3,5)$ are NOT m-adjacent**.

* **Cluster B: Mid-to-Bottom Left Block**
  * Pixels: $(3,2)=2$, $(3,3)=3$, $(4,2)=2$, $(4,3)=1$, $(5,1)=2$
  * **4-Adjacency Links:**
    * $(3,2)-(3,3)$ (horizontal) $\implies$ **Connected**.
    * $(3,2)-(4,2)$ (vertical) $\implies$ **Connected**.
    * $(4,2)-(4,3)$ (horizontal) $\implies$ **Connected**.
    * $(3,3)-(4,3)$ (vertical) $\implies$ **Connected**.
  * **8-Adjacency Links:**
    * Includes above orthogonal links.
    * Diagonal $(3,2)$ to $(4,3)$ $\implies$ **Connected**.
    * Diagonal $(3,3)$ to $(4,2)$ $\implies$ **Connected**.
    * Diagonal $(4,2)$ to $(5,1)$ $\implies$ **Connected**.
  * **m-Adjacency Links:**
    * Orthogonal loops remain: $(3,2)-(3,3)-(4,3)-(4,2)-(3,2)$ are connected orthogonally.
    * **Diagonal connections within the loop are disallowed** because their horizontal/vertical intersecting neighbors are part of the active path (e.g. $(3,2)$ and $(4,3)$ cannot connect diagonally because $(3,3)$ and $(4,2)$ are 1s).
    * *Let's test diagonal $(4,2)$ to $(5,1)$:*      $N_4(4,2) \cap N_4(5,1) = \{(4,1), (5,2)\}$.
      * Intensity values: $(4,1) = 8 \notin V$, $(5,2) = 4 \notin V$.
      * Since both are outside $V$, the diagonal link is valid.
      * Therefore, **$(4,2)$ and $(5,1)$ ARE m-adjacent**.

```
=== Visual Connection Graphs for Cluster A & B (V={1,2,3}) ===

1. 4-Adjacency Graph:
(1,3)[3]         (1,5)[2]       (3,2)[2] ───── (3,3)[3]
                   │             │               │
                   │             │               │
(2,4)[1] ───── (2,5)[3]          │               │
                   │            (4,2)[2] ───── (4,3)[1]
                   │
                 (3,5)[1]       (5,1)[2]


2. 8-Adjacency Graph:
(1,3)[3]         (1,5)[2]       (3,2)[2] ───── (3,3)[3]
      ╲           ╱│             │   ╲       ╱   │
        ╲       ╱  │             │     ╲   ╱     │
          ╲   ╱    │             │       ╳       │
            ╲      │             │     ╱   ╲     │
(2,4)[1] ───── (2,5)[3]         (4,2)[2] ───── (4,3)[1]
      ╲           ╱             ╱
        ╲       ╱             ╱ 
          ╲   ╱             ╱   
            ╲              ╱    
                 (3,5)[1]       (5,1)[2]


3. m-Adjacency Graph:
(1,3)[3]         (1,5)[2]       (3,2)[2] ───── (3,3)[3]
      ╲            │             │               │
        ╲  NO DIAG │             │  NO DIAG      │
          ╲  LINK  │             │  LINKS IN     │
            ╲      │             │  LOOP         │
(2,4)[1] ───── (2,5)[3]         (4,2)[2] ───── (4,3)[1]
                   │            ╱
                   │          ╱  
                 (3,5)[1]    (5,1)[2]
```

* **✍️ Final Exam Answer:** Complete the graphical connection mapping on the grid showing the removal of redundant crossing links under m-adjacency, confirming that the loop is simplified to a pure orthogonal perimeter block.

---

## 📐 Section 3: Coordinate Distance Metrics ($D_e, D_4, D_8$)

### 🧠 Core Concepts & Formulas

For any two coordinate points $p(x, y)$ and $q(s, t)$ in a 2D digital image:

1. **Euclidean Distance ($D_e$):** Measures the direct, straight-line distance (hypotenuse) between two coordinate vectors [298]:
   $$D_e(p, q) = \sqrt{(x - s)^2 + (y - t)^2}$$
2. **City-Block / Manhattan Distance ($D_4$):** Measures the path length restricted strictly to horizontal and vertical movements [225, 299]:
   $$D_4(p, q) = |x - s| + |y - t|$$
3. **Chessboard Distance ($D_8$):** Measures the path length allowing orthogonal and diagonal movements [225, 299]:
   $$D_8(p, q) = \max(|x - s|, |y - t|)$$

---

### 📝 Problem 3.1: Distance Calculations Between Far Coordinates
* **Exact Original Question:** Calculate the Euclidean distance, city block distance and chessboard distance between two pixels located at $(0, 4)$ and $(6, 1)$.
* **Exam Source:** NMIMS Re-Exam (Batch 2023-24), December 7, 2024, Q1(a) [4 Marks]
* **Topic:** Spatial Distance Metrics
* **Given Information:**
  * Coordinates of pixel $p$: $(x, y) = (0, 4)$
  * Coordinates of pixel $q$: $(s, t) = (6, 1)$
* **What is Asked:** Compute the $D_e$, $D_4$, and $D_8$ distances between these two points.

#### ⚡ Step-by-Step Solution

1. **Calculate Euclidean Distance ($D_e$):**
   * Substitute $(x, y) = (0, 4)$ and $(s, t) = (6, 1)$ into the formula:
     $$D_e(p, q) = \sqrt{(0 - 6)^2 + (4 - 1)^2}$$
     $$D_e(p, q) = \sqrt{(-6)^2 + (3)^2} = \sqrt{36 + 9}$$
     $$D_e(p, q) = \sqrt{45} \approx \mathbf{6.708 \text{ units}}$$

2. **Calculate City-Block Distance ($D_4$):**
   * Apply formula:
     $$D_4(p, q) = |0 - 6| + |4 - 1|$$
     $$D_4(p, q) = 6 + 3 = \mathbf{9 \text{ units}}$$

3. **Calculate Chessboard Distance ($D_8$):**
   * Apply formula:
     $$D_8(p, q) = \max(|0 - 6|, |4 - 1|)$$
     $$D_8(p, q) = \max(6, 3) = \mathbf{6 \text{ units}}$$

* **✍️ Final Exam Answer:**
  * Euclidean Distance ($D_e$) = **6.71 units**
  * City-Block Distance ($D_4$) = **9 units**
  * Chessboard Distance ($D_8$) = **6 units**

---

### 📝 Problem 3.2: City-Block Distance and Path Tracing
* **Exact Original Question:** Apply the same distance measure (City Block) on the given image from pixel at $(0,0)$ to pixel at $(1,2)$. Index starts from 0. Show the path.

| 20 | 40 | 60 |
|----|----|----|
| 80 | 100 | 120 |
| 140 | 160 | 180 |

*Image $I$, size $3 \times 3$ (0-based index)*

* **Exam Source:** NMIMS Test-I (Set 1), August 22, 2025, Q1(a)(ii) [1.5 Marks]
* **Topic:** City-Block Distance & Path Tracing
* **Given Information:**
  * Start Coordinate: $p = (0,0)$ (value `20`)
  * End Coordinate: $q = (1,2)$ (value `120`)
* **What is Asked:** Compute $D_4$ distance and define the shortest path.

#### ⚡ Step-by-Step Solution
1. **Compute Distance:**
   $$D_4(p, q) = |0 - 1| + |0 - 2| = 1 + 2 = \mathbf{3 \text{ units}}$$
2. **Trace the Path (restricted to horizontal and vertical movements):**
   To traverse from $(0,0)$ to $(1,2)$ in exactly 3 steps, we must take 1 vertical step and 2 horizontal steps. There are three valid equivalent paths:
   * **Path Option A:** $(0,0) \rightarrow (0,1) \rightarrow (0,2) \rightarrow (1,2)$
     * *Corresponding Intensities:* $20 \rightarrow 40 \rightarrow 60 \rightarrow 120$
   * **Path Option B:** $(0,0) \rightarrow (0,1) \rightarrow (1,1) \rightarrow (1,2)$
     * *Corresponding Intensities:* $20 \rightarrow 40 \rightarrow 100 \rightarrow 120$
   * **Path Option C:** $(0,0) \rightarrow (1,0) \rightarrow (1,1) \rightarrow (1,2)$
     * *Corresponding Intensities:* $20 \rightarrow 80 \rightarrow 100 \rightarrow 120$

* **✍️ Final Exam Answer:** Distance is **3 units**. A shortest path option is: **$(0,0) \rightarrow (0,1) \rightarrow (0,2) \rightarrow (1,2)$**.

---

### 📝 Problem 3.3: Chessboard Distance and Path Tracing
* **Exact Original Question:** Write the formula and apply the same distance measure (Chessboard) on the given image from pixel at $(0,0)$ to pixel at $(2,2)$. Index starts from 0. Show the path.

| 16 | 64 | 144 |
|----|----|----|
| 25 | 81 | 169 |
| 36 | 100 | 196 |

*Image $I$, size $3 \times 3$ (0-based index)*

* **Exam Source:** NMIMS Test-I (Set 2), August 22, 2025, Q1(b)(ii) [1.5 Marks]
* **Topic:** Chessboard Distance & Path Tracing
* **Given Information:**
  * Start Coordinate: $p = (0,0)$ (value `16`)
  * End Coordinate: $q = (2,2)$ (value `196`)
* **What is Asked:** Compute $D_8$ distance and define the shortest path.

#### ⚡ Step-by-Step Solution
1. **Compute Distance:**
   $$D_8(p, q) = \max(|0 - 2|, |0 - 2|) = \max(2, 2) = \mathbf{2 \text{ units}}$$
2. **Trace the Path (allowing diagonal movements):**
   Since Chessboard distance allows diagonal movements, we can travel diagonally from $(0,0)$ to $(2,2)$ in exactly 2 steps passing through the center pixel $(1,1)$:
   * **Shortest Path:** $(0,0) \rightarrow (1,1) \rightarrow (2,2)$
     * *Corresponding Intensities:* $16 \rightarrow 81 \rightarrow 196$

* **✍️ Final Exam Answer:** Distance is **2 units**. The path is **$(0,0) \rightarrow (1,1) \rightarrow (2,2)$**.

---

## 🧩 Section 4: Advanced Mixed Connectivity ($D_m$) on Grids

### 🧠 Core Concepts & Formulas

While $D_e, D_4,$ and $D_8$ distances are purely geometric, the **mixed path distance ($D_m$)** is defined by **both spatial constraints and intensity constraints**:

1. A path is m-compliant only if every step in the path is a valid **m-adjacent** step [295, 296].
2. $D_m$ is the length (number of pixel steps/edges) of the **shortest possible m-path** connecting $p$ and $q$ [321, 322]. If no path exists, the distance is infinite [321].

---

### 📝 Problem 4.1: Gridded Matrix Distance Analysis for $V = \{1, 2\}$
* **Exact Original Question:** An image segment is shown below. Let, $V$ be the set of Gray-level values used to define connectivity in the image. Compute: $D_e$, $D_4$, $D_8$ and $D_m$ distances between pixels ‘p’ and ‘q’ for: V = {1,2}.

| 0 | 1 | **2 (q)** |
|---|---|---------|
| 2 | 3 | 2 |
| **1 (p)** | 1 | 3 |

*Image $I$, size $3 \times 3$, V = {1,2} (0-based index)*

* **Exam Source:** NMIMS Final Examination, December 8, 2025, Q6(a) [4 Marks]
* **Topic:** Pixel Connectivity / Mixed m-Distance Calculation
* **Given Information:**
  * Index starting from $0$
  * Start pixel $p$ at $(2, 0)$ with intensity value `1` (Note: $1 \in V$)
  * End pixel $q$ at $(0, 2)$ with intensity value `2` (Note: $2 \in V$)
  * Adjacency set $V = \{1, 2\}$
* **What is Asked:** Compute the geometric distances $D_e, D_4, D_8$ and the path-based distance $D_m$ between $p$ and $q$.

#### 🧠 How to Approach
1. Define the coordinates of the endpoints: $p = (2,0)$ and $q = (0,2)$.
2. Calculate the geometric distance values directly using spatial equations (which are independent of the grid values).
3. To calculate $D_m$, trace out all potential pixel coordinate pathways connecting $p$ to $q$ using only coordinates whose values lie inside $V = \{1, 2\}$. Check m-adjacency rules for every single transition.

#### ⚡ Step-by-Step Solution

##### 1. Compute Geometric Distances ($D_e, D_4, D_8$)
Using $p = (2,0)$ and $q = (0,2)$:
* **Euclidean Distance ($D_e$):**
  $$D_e(p, q) = \sqrt{(2 - 0)^2 + (0 - 2)^2} = \sqrt{4 + 4} = \sqrt{8} \approx \mathbf{2.828 \text{ units}}$$
* **City-Block Distance ($D_4$):**
  $$D_4(p, q) = |2 - 0| + |0 - 2| = 2 + 2 = \mathbf{4 \text{ units}}$$
* **Chessboard Distance ($D_8$):**
  $$D_8(p, q) = \max(|2 - 0|, |0 - 2|) = \max(2, 2) = \mathbf{2 \text{ units}}$$

##### 2. Compute m-Path Distance ($D_m$)
* Let's list the values of all elements in our $3 \times 3$ grid:
  * $(0,0)=0 \notin V$
  * $(0,1)=1 \in V$
  * $(0,2)=2 \in V$ (Target $q$)
  * $(1,0)=2 \in V$
  * $(1,1)=3 \notin V$
  * $(1,2)=2 \in V$
  * $(2,0)=1 \in V$ (Start $p$)
  * $(2,1)=1 \in V$
  * $(2,2)=3 \notin V$

Let's test potential paths:

* **Path Option 1 (Left perimeter route):** $(2,0) \rightarrow (1,0) \rightarrow (0,1) \rightarrow (0,2)$
  * **Step 1: $(2,0) \rightarrow (1,0)$**
    * Orthogonal vertical relationship $\implies$ 4-adjacent $\implies$ **Valid m-step**.
  * **Step 2: $(1,0) \rightarrow (0,1)$**
    * Diagonal relationship. Let's run the m-adjacency intersection check:
      $$Intersection = N_4(1,0) \cap N_4(0,1) = \{(0,0), (1,1)\}$$
      * The intensity values at these intersection coordinates are $(0,0) = 0$ and $(1,1) = 3$.
      * Since neither $0$ nor $3$ is in $V = \{1, 2\}$, the diagonal transition is valid.
      * Therefore, **$(1,0)$ and $(0,1)$ are m-adjacent** $\implies$ **Valid m-step**.
  * **Step 3: $(0,1) \rightarrow (0,2)$**
    * Orthogonal horizontal relationship $\implies$ 4-adjacent $\implies$ **Valid m-step**.
  * **Total Hops:** $3$ (Length of path = 3).

* **Path Option 2 (Right perimeter route):** $(2,0) \rightarrow (2,1) \rightarrow (1,2) \rightarrow (0,2)$
  * **Step 1: $(2,0) \rightarrow (2,1)$**
    * Orthogonal horizontal relationship $\implies$ 4-adjacent $\implies$ **Valid m-step**.
  * **Step 2: $(2,1) \rightarrow (1,2)$**
    * Diagonal relationship. Let's check intersection:
      $$Intersection = N_4(2,1) \cap N_4(1,2) = \{(2,2), (1,1)\}$$
      * The intensity values at these intersection coordinates are $(2,2) = 3$ and $(1,1) = 3$.
      * Since $3 \notin V = \{1, 2\}$, the intersection is clean.
      * Therefore, **$(2,1)$ and $(1,2)$ are m-adjacent** $\implies$ **Valid m-step**.
  * **Step 3: $(1,2) \rightarrow (0,2)$**
    * Orthogonal vertical relationship $\implies$ 4-adjacent $\implies$ **Valid m-step**.
  * **Total Hops:** $3$ (Length of path = 3).

Both paths are valid and have an identical length of 3 hops.
$$D_m(p, q) = \mathbf{3 \text{ units}}$$

#### ⚠️ Common Mistake & Exam Trick
* **Confusing hops with pixels:** The distance between two nodes in a connectivity graph is defined as the number of **edges (transitions)**, not the count of pixels visited. The path $(2,0) \rightarrow (1,0) \rightarrow (0,1) \rightarrow (0,2)$ contains 4 pixels, but the distance is **3 steps**.
* **✍️ Final Exam Answer:**
  * $D_e \approx 2.83$
  * $D_4 = 4$
  * $D_8 = 2$
  * $D_m = 3$

---

## 🔄 Section 5: Spatial Sampling, Decimation, and Interpolation

### 🧠 Core Concepts & Formulas

Converting continuous signals to discrete representations or resizing matrices requires spatial conversions:

1. **Down-Sampling (Decimation) by a factor of 2:** Discard alternate columns and rows to shrink the dimensions [48]. Keep indices:
   $$I_{down}(r, c) = I(2r, 2c)$$
2. **Up-Sampling (Interpolation) by a factor of 2:**
   * **Replication (Nearest Neighbor):** Replicates each pixel into a $2 \times 2$ block [48]:

     Original $2 \times 2$:

     | A | B |
     |---|---|
     | C | D |

     Replicated to $4 \times 4$:

     | A | A | B | B |
     |---|---|---|---|
     | A | A | B | B |
     | C | C | D | D |
     | C | C | D | D |
   * **Bilinear Interpolation (Averaging):** Zero-pad the matrices first, then fill in missing values by computing the arithmetic average of neighboring active pixels.

---

### 📝 Problem 5.1: Down-Sampling and Up-Sampling by Averaging
* **Exact Original Question:** Draw the block diagram and explain the process of spatial sampling and quantization to digitize an analog image. What is the resultant output image if the gray scale image given below is down sampled by a factor of 2? Further at the receiver, the down sampled image is up-sampled by factor of 2 by **averaging**. Write the resultant up-sampled image.

| 5 | 2 | 3 | 1 |
|---|---|---|---|
| 4 | 1 | 6 | 4 |
| 3 | 0 | 9 | 5 |
| 2 | 7 | 8 | 2 |

*Input Grayscale Image $I$, size $4 \times 4$*

* **Exam Source:** NMIMS Re-Exam, January 27, 2023, Q2(b) [10 Marks]
* **Topic:** Spatial Sampling / Decimation and Interpolation
* **Given Information:**
  * Grayscale Input Image Matrix ($4 \times 4$)
  * Decimation factor = $2$
  * Interpolation technique = **Averaging** (bilinear approach)
* **What is Asked:**
  1. Draw block diagram of digitization.
  2. Compute down-sampled $2 \times 2$ matrix.
  3. Compute up-sampled $4 \times 4$ matrix using averaging.

#### ⚡ Step-by-Step Solution

##### Step 1: Spatial Down-sampling by a factor of 2
Keep every alternate even row (Row 0, Row 2) and even column (Col 0, Col 2) of the input matrix $I$:
* $I_{down}(0,0) = I(0,0) = 5$
* $I_{down}(0,1) = I(0,2) = 3$
* $I_{down}(1,0) = I(2,0) = 3$
* $I_{down}(1,1) = I(2,2) = 9$

**Down-sampled Matrix $I_{down}$:**

| 5 | 3 |
|---|---|
| 3 | 9 |

##### Step 2: Spatial Up-sampling by a factor of 2 using Averaging
Expand $I_{down}$ back to $4 \times 4$ using zero-padding:

**Zero-padded $I_{padded}$:**

| 5 | 0 | 3 | 0 |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 3 | 0 | 9 | 0 |
| 0 | 0 | 0 | 0 |

Now, compute the intermediate values:
1. **Horizontal midpoints:**
   * $I(0,1) = \frac{I(0,0) + I(0,2)}{2} = \frac{5+3}{2} = \mathbf{4}$
   * $I(2,1) = \frac{I(2,0) + I(2,2)}{2} = \frac{3+9}{2} = \mathbf{6}$
2. **Vertical midpoints:**
   * $I(1,0) = \frac{I(0,0) + I(2,0)}{2} = \frac{5+3}{2} = \mathbf{4}$
   * $I(1,2) = \frac{I(0,2) + I(2,2)}{2} = \frac{3+9}{2} = \mathbf{6}$
3. **Center midpoint:**
   * Take average of orthogonal neighbors:
     $$I(1,1) = \frac{I(0,1) + I(2,1) + I(1,0) + I(1,2)}{4} = \frac{4 + 6 + 4 + 6}{4} = \mathbf{5}$$
4. **Boundary extrapolation (handling odd rows/columns):**
   * Since we cannot calculate averages at Row 3 or Column 3 (as there are no Row 4 or Col 4 elements to average with), we replicate values from the nearest valid neighbor to prevent edge fading:
     * **Column 3 (replicate Col 2):** $I(0,3) = I(0,2) = 3$, $I(1,3) = I(1,2) = 6$, $I(2,3) = I(2,2) = 9$
     * **Row 3 (replicate Row 2):** $I(3,0) = 3$, $I(3,1) = 6$, $I(3,2) = 9$, $I(3,3) = 9$

**Resultant Up-sampled Matrix $I_{up}$:**

| 5 | 4 | 3 | 3 |
|---|---|---|---|
| 4 | 5 | 6 | 6 |
| 3 | 6 | 9 | 9 |
| 3 | 6 | 9 | 9 |

* **✍️ Final Exam Answer:**
  * Down-sampled:

    | 5 | 3 |
    |---|---|
    | 3 | 9 |

  * Up-sampled:

    | 5 | 4 | 3 | 3 |
    |---|---|---|---|
    | 4 | 5 | 6 | 6 |
    | 3 | 6 | 9 | 9 |
    | 3 | 6 | 9 | 9 |

---

### 📝 Problem 5.2: Down-Sampling and Up-Sampling by Replication
* **Exact Original Question:** Explain the process of Sampling and Quantization with neat sketch. Apply the process of down sampling by factor of 2 on the image given below. Also at receiver, the down sampled image is up sampled by factor of 2 by **replication**.

| 7 | 8 | 9 | 10 |
|---|---|---|---|
| 5 | 4 | 3 | 2 |
| 6 | 8 | 10 | 12 |
| 2 | 7 | 8 | 2 |

*Input Grayscale Image $I$, size $4 \times 4$*

* **Exam Source:** NMIMS Special Re-Examination, June 12, 2023, Q6(a) [10 Marks]
* **Topic:** Spatial Sampling / Decimation and Interpolation
* **Given Information:**
  * Input Image Matrix ($4 \times 4$)
  * Decimation factor = $2$
  * Interpolation technique = **Replication** (nearest-neighbor block replication)
* **What is Asked:**
  1. Compute down-sampled $2 \times 2$ matrix.
  2. Compute up-sampled $4 \times 4$ matrix using replication.

#### ⚡ Step-by-Step Solution

##### Step 1: Spatial Down-sampling by a factor of 2
Keep every alternate even row (Row 0, Row 2) and even column (Col 0, Col 2):
* $I_{down}(0,0) = I(0,0) = 7$
* $I_{down}(0,1) = I(0,2) = 9$
* $I_{down}(1,0) = I(2,0) = 6$
* $I_{down}(1,1) = I(2,2) = 10$

**Down-sampled Matrix $I_{down}$:**

| 7 | 9 |
|---|---|
| 6 | 10 |

##### Step 2: Spatial Up-sampling by a factor of 2 using Replication
Replicate each pixel of the $2 \times 2$ matrix $I_{down}$ to form a homogeneous $2 \times 2$ block:
* Entry $7 \implies$ copied to $(0,0), (0,1), (1,0), (1,1)$
* Entry $9 \implies$ copied to $(0,2), (0,3), (1,2), (1,3)$
* Entry $6 \implies$ copied to $(2,0), (2,1), (3,0), (3,1)$
* Entry $10 \implies$ copied to $(2,2), (2,3), (3,2), (3,3)$

**Resultant Up-sampled Matrix $I_{up}$:**

| 7 | 7 | 9 | 9 |
|---|---|---|---|
| 7 | 7 | 9 | 9 |
| 6 | 6 | 10 | 10 |
| 6 | 6 | 10 | 10 |

* **✍️ Final Exam Answer:**
  * Down-sampled:

    | 7 | 9 |
    |---|---|
    | 6 | 10 |

  * Up-sampled:

    | 7 | 7 | 9 | 9 |
    |---|---|---|---|
    | 7 | 7 | 9 | 9 |
    | 6 | 6 | 10 | 10 |
    | 6 | 6 | 10 | 10 |

---

## ⚡ Section 6: LSB (Least Significant Bit) substitutions & Histograms

### 🧠 Core Concepts & Formulas

1. **Binary Representation:** For a $b$-bit image, each pixel is represented as a binary number with $b$ bits:
   $$[b_{b-1} b_{b-2} \dots b_1 b_0]_2$$
   where $b_0$ is the **Least Significant Bit (LSB)**, carrying the smallest weight ($2^0 = 1$).
2. **LSB Replacement with 0:** Changing the LSB ($b_0$) to $0$ removes the odd part of any value, causing:
   * Even values (LSB is already 0) $\implies$ **Remain unchanged**.
   * Odd values (LSB is 1) $\implies$ **Decrease by exactly 1** to become even.
3. **Histogram ($h(r_k)$):** A plot of pixel count vs. gray level. Removing the LSB halves the unique intensity options, merging bins pairwise.

---

### 📝 Problem 6.1: LSB Substitution and Histogram Plotting
* **Exact Original Question:** The least significant bit of each pixel of the 3-bit image given below is replaced with 0. Draw the resultant image. Also, draw the histogram of the original and the resultant image.

| 0 | 1 | 2 | 3 |
|---|---|---|---|
| 4 | 5 | 6 | 7 |

*3-bit Image $I$, size $2 \times 4$*

* **Exam Source:** NMIMS Term Exam, December 15, 2022, Q1(g) [5 Marks]
* **Topic:** Quantization Depth / LSB substitution / Histogram Plotting
* **Given Information:**
  * 3-bit image segment ($2 \times 4$ dimensions, $L = 2^3 = 8$ levels)
  * Transformation rule: Replace LSB of each pixel with 0
* **What is Asked:**
  1. Write the resultant output matrix.
  2. Plot and compare the histograms before and after transformation.

#### ⚡ Step-by-Step Solution

##### Step 1: Perform LSB replacement for each value
Let's convert each decimal intensity in the input matrix into 3-bit binary, clear the last bit, and convert back:

* **Pixel $0$:** $000_2 \longrightarrow 000_2 = \mathbf{0}$
* **Pixel $1$:** $001_2 \longrightarrow 000_2 = \mathbf{0}$
* **Pixel $2$:** $010_2 \longrightarrow 010_2 = \mathbf{2}$
* **Pixel $3$:** $011_2 \longrightarrow 010_2 = \mathbf{2}$
* **Pixel $4$:** $100_2 \longrightarrow 100_2 = \mathbf{4}$
* **Pixel $5$:** $101_2 \longrightarrow 100_2 = \mathbf{4}$
* **Pixel $6$:** $110_2 \longrightarrow 110_2 = \mathbf{6}$
* **Pixel $7$:** $111_2 \longrightarrow 110_2 = \mathbf{6}$

##### Step 2: Construct the Resultant Output Matrix
Substitute the calculated values into their corresponding positions:

**Resultant Matrix $I_{result}$:**

| 0 | 0 | 2 | 2 |
|---|---|---|---|
| 4 | 4 | 6 | 6 |

##### Step 3: Draw the Histogram Tables

* **Original Histogram Table:** (Total pixels $N = 8$)

| Intensity level $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Pixel Count $n_k$** | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

* **Resultant Histogram Table:** (Total pixels $N = 8$)

| Intensity level $s_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Pixel Count $n_k$** | 2 | 0 | 2 | 0 | 2 | 0 | 2 | 0 |

##### Step 4: Draw Histograms (For Exam Sheet Submission)

```
=== (1) Original Image Histogram ===
  Pixel Count
    ▲
  2 │ 
    │ 
  1 │  █   █   █   █   █   █   █   █
    │  █   █   █   █   █   █   █   █
  0 └──┴───┴───┴───┴───┴───┴───┴───┴──► Gray Level (r_k)
       0   1   2   3   4   5   6   7


=== (2) Resultant Image Histogram ===
  Pixel Count
    ▲
  2 │  █       █       █       █
    │  █       █       █       █
  1 │  █       █       █       █
    │  █       █       █       █
  0 └──┴───┴───┴───┴───┴───┴───┴───┴──► Gray Level (s_k)
       0   1   2   3   4   5   6   7
```

* **✍️ Final Exam Answer:** Resultant matrix:

  | 0 | 0 | 2 | 2 |
  |---|---|---|---|
  | 4 | 4 | 6 | 6 |

  Its histogram shows a pairing/merging of intensity levels where all odd bins are completely emptied and their frequencies accumulated into their respective lower even neighbor bins.

---

## 📑 Section 7: Quick Revision Formula Sheet

1. **Storage Requirement:**
   $$\text{Size (bits)} = M \times N \times \text{bit depth} \times \text{planes}$$
2. **Euclidean Distance ($D_e$):**
   $$D_e = \sqrt{(x-s)^2 + (y-t)^2}$$
3. **City Block Distance ($D_4$):**
   $$D_4 = |x-s| + |y-t|$$
4. **Chessboard Distance ($D_8$):**
   $$D_8 = \max(|x-s|, |y-t|)$$
5. **m-Adjacency Diagonal Condition:**
   $$p \in N_D(q) \quad \text{and} \quad N_4(p) \cap N_4(q) \text{ contains no elements } \in V$$
6. **Decimation Rule (factor of 2):**
   $$I_{down}(x, y) = I(2x, 2y)$$

---

## 🏁 Solved Exam Numerical Checklist

* [x] Grayscale storage size (Test-I August 2025, Set 2)
* [x] Color storage size (Test-I August 2025, Set 1)
* [x] Grayscale resolution bit depth analysis (Re-Exam Feb 2025)
* [x] 8-Adjacency and m-Adjacency connections drawing (Final Exam Dec 2025)
* [x] $D_e, D_4, D_8,$ and $D_m$ connections and paths (Final Exam Dec 2025)
* [x] Coordinate distance calculation (Re-Exam Dec 2024)
* [x] City-block distance path tracing (Test-I August 2025, Set 1)
* [x] Chessboard distance path tracing (Test-I August 2025, Set 2)
* [x] Spatial Down-sampling and Interpolation by Averaging (Re-Exam Jan 2023)
* [x] Spatial Down-sampling and Interpolation by Replication (Special Re-Exam June 2023)
* [x] LSB replacements and histograms sketching (Final Exam Dec 2022)
