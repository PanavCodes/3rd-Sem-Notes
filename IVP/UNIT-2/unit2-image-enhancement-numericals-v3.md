# Unit 2: Image Enhancement (Spatial Domain) - Solved Numerical Workbook (v3)

**Course:** Image and Video Processing (IVP)  
**Level:** SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC)  
**Primary References:** `IVP UNIT 2.pptx`, `IVP_M2_NOTES.pdf`, and official university PYQs [7, 8, 9, 10, 31, 32, 33, 34, 35, 38, 39, 43, 44, 45, 46, 47, 48, 53, 55, 56, 59, 68, 80, 86, 124, 125, 143, 147, 149, 150, 151, 211, 212, 213]  
**Focus:** Comprehensive, step-by-step mathematical solutions to prepare you to solve any exam numerical independently.

---

## 📅 PART 1: POINT PROCESSING OPERATIONS NUMERICALS

---

### 📍 Problem 1.1: Digital Negative / Image Negation
⭐ **Formula / Rule:**
   $$s = (L - 1) - r$$
where:
*   $r$ is the input pixel intensity.
*   $s$ is the output transformed pixel intensity.
*   $L$ is the total number of gray levels in the image ($L = 2^k$ for a $k$-bit image).
*   $L - 1$ is the maximum intensity value (e.g., $255$ for an 8-bit image, $7$ for a 3-bit image).

---

#### **Question (NMIMS Term Exam / Student Lab Manual Reference)**
🟢 **Verified PYQ (Re-Exam, Batch 2023-24 - Q2a) [4 Marks]**  
Describe the process to obtain an image negative. Apply this process to the $5 \times 5$ image matrix below assuming 3 BPP (bits per pixel) depth:
   $$A = \begin{bmatrix} 1 & 2 & 2 & 2 & 2 \\ 3 & 2 & 4 & 5 & 2 \\ 7 & 7 & 7 & 7 & 6 \\ 2 & 2 & 2 & 3 & 3 \\ 4 & 4 & 4 & 4 & 4 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Determine the maximum intensity level ($L - 1$) based on the specified bit depth ($k = 3 \implies L = 2^3 = 8 \implies L - 1 = 7$).
2. Subtract each pixel value of the input matrix from the maximum intensity level ($L - 1$).

#### **Calculation cell-by-cell ($s = 7 - r$):**
*   **Row 1:** 
    *   $s(0,0) = 7 - 1 = 6$
    *   $s(0,1) = 7 - 2 = 5$
    *   $s(0,2) = 7 - 2 = 5$
    *   $s(0,3) = 7 - 2 = 5$
    *   $s(0,4) = 7 - 2 = 5$
*   **Row 2:** 
    *   $s(1,0) = 7 - 3 = 4$
    *   $s(1,1) = 7 - 2 = 5$
    *   $s(1,2) = 7 - 4 = 3$
    *   $s(1,3) = 7 - 5 = 2$
    *   $s(1,4) = 7 - 2 = 5$
*   **Row 3:** 
    *   $s(2,0) = 7 - 7 = 0$
    *   $s(2,1) = 7 - 7 = 0$
    *   $s(2,2) = 7 - 7 = 0$
    *   $s(2,3) = 7 - 7 = 0$
    *   $s(2,4) = 7 - 6 = 1$
*   **Row 4:** 
    *   $s(3,0) = 7 - 2 = 5$
    *   $s(3,1) = 7 - 2 = 5$
    *   $s(3,2) = 7 - 2 = 5$
    *   $s(3,3) = 7 - 3 = 4$
    *   $s(3,4) = 7 - 3 = 4$
*   **Row 5:** 
    *   $s(4,0) = 7 - 4 = 3$
    *   $s(4,1) = 7 - 4 = 3$
    *   $s(4,2) = 7 - 4 = 3$
    *   $s(4,3) = 7 - 4 = 3$
    *   $s(4,4) = 7 - 4 = 3$

✍️ **Final Exam Output Matrix:**
   $$A_{\text{neg}} = \begin{bmatrix} 6 & 5 & 5 & 5 & 5 \\ 4 & 5 & 3 & 2 & 5 \\ 0 & 0 & 0 & 0 & 1 \\ 5 & 5 & 5 & 4 & 4 \\ 3 & 3 & 3 & 3 & 3 \end{bmatrix}$$

⚡ **Exam Shortcut:**
When subtracting from $255$ (for 8-bit negatives), split the math into: $(250 - r) + 5$ or write down intermediate steps. It is a simple subtraction, but under exam pressure, simple arithmetic errors are the most common cause of lost marks!

⚠️ **Common Mistakes:**
Using $L$ instead of $L - 1$ (e.g., subtracting from $256$ or $8$ instead of $255$ or $7$). This will result in pixel values exceeding the valid range ($256$ is invalid for an 8-bit image) and is a critical error!

---

### 📍 Problem 1.2: Piecewise-Linear Contrast Stretching (Matrix Example)
⭐ **Formula / Rule:**
The contrast stretching transformation function is defined in three distinct linear regions [203]:

   $$s = \begin{cases} 
\alpha \cdot r & 0 \le r < r_1 \\ 
\beta \cdot (r - r_1) + s_1 & r_1 \le r < r_2 \\ 
\gamma \cdot (r - r_2) + s_2 & r_2 \le r \le L - 1 
\end{cases}$$

Where the slopes of each linear segment ($\alpha$, $\beta$, $\gamma$) are computed as:
   $$\alpha = \frac{s_1}{r_1}, \quad \beta = \frac{s_2 - s_1}{r_2 - r_1}, \quad \gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2}$$

---

#### **Question (University Exam / Class notes)**
🔵 **Classroom / Homework Practice Question**  
Given the following $4 \times 4$ image segment of a 3-bit image ($L = 8$):
   $$I = \begin{bmatrix} 4 & 3 & 5 & 2 \\ 3 & 6 & 4 & 6 \\ 2 & 2 & 6 & 5 \\ 7 & 6 & 4 & 1 \end{bmatrix}$$

Apply contrast stretching with the control parameters:
*   $r_1 = 3, \quad s_1 = 2$
*   $r_2 = 5, \quad s_2 = 6$

Construct the final output image matrix (round values to the nearest integer).

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Calculate the three segment slopes ($\alpha$, $\beta$, $\gamma$).
2. Map each original intensity level $r \in \{0, 1, 2, \dots, 7\}$ to its stretched intensity $s$ using the piecewise formula.
3. Replace the original values in matrix $I$ with the mapped stretched values.

#### **Step 1: Compute Slopes**
*   **Segment 1:** $\alpha = \frac{s_1}{r_1} = \frac{2}{3} \approx 0.6667$
*   **Segment 2:** $\beta = \frac{s_2 - s_1}{r_2 - r_1} = \frac{6 - 2}{5 - 3} = \frac{4}{2} = 2.0000$
*   **Segment 3:** $\gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2} = \frac{7 - 6}{7 - 5} = \frac{1}{2} = 0.5000$

#### **Step 2: Generate Intensity Mapping Table**
Let's compute $s$ for each level of $r$ from $0$ to $7$:

*   **For $r = 0$** (Region 1): $s = 0.6667 \times 0 = 0 \implies \mathbf{0}$
*   **For $r = 1$** (Region 1): $s = 0.6667 \times 1 = 0.6667 \implies \mathbf{1}$ (rounded)
*   **For $r = 2$** (Region 1): $s = 0.6667 \times 2 = 1.3333 \implies \mathbf{1}$ (rounded)
*   **For $r = 3$** (Region 2): $s = 2 \times (3 - 3) + 2 = 2 \implies \mathbf{2}$
*   **For $r = 4$** (Region 2): $s = 2 \times (4 - 3) + 2 = 4 \implies \mathbf{4}$
*   **For $r = 5$** (Region 3): $s = 0.5 \times (5 - 5) + 6 = 6 \implies \mathbf{6}$
*   **For $r = 6$** (Region 3): $s = 0.5 \times (6 - 5) + 6 = 6.5 \implies \mathbf{7}$ (rounded up)
*   **For $r = 7$** (Region 3): $s = 0.5 \times (7 - 5) + 6 = 7 \implies \mathbf{7}$

| Original Level $r$ | Stretched Formula Applied | Computed Value | Rounded Output $s$ |
| :---: | :--- | :---: | :---: |
| **0** | $0.6667 \times 0$ | 0.00 | **0** |
| **1** | $0.6667 \times 1$ | 0.67 | **1** |
| **2** | $0.6667 \times 2$ | 1.33 | **1** |
| **3** | $2 \times (3 - 3) + 2$ | 2.00 | **2** |
| **4** | $2 \times (4 - 3) + 2$ | 4.00 | **4** |
| **5** | $0.5 \times (5 - 5) + 6$ | 6.00 | **6** |
| **6** | $0.5 \times (6 - 5) + 6$ | 6.50 | **7** |
| **7** | $0.5 \times (7 - 5) + 6$ | 7.00 | **7** |

#### **Step 3: Map the Input Matrix**
Replace values of the input matrix $I$ using the lookup table:
*   $I(0,0) = 4 \to 4$
*   $I(0,1) = 3 \to 2$
*   $I(0,2) = 5 \to 6$
*   $I(0,3) = 2 \to 1$
*   $I(1,0) = 3 \to 2$
*   $I(1,1) = 6 \to 7$
*   $I(1,2) = 4 \to 4$
*   $I(1,3) = 6 \to 7$
*   $I(2,0) = 2 \to 1$
*   $I(2,1) = 2 \to 1$
*   $I(2,2) = 6 \to 7$
*   $I(2,3) = 5 \to 6$
*   $I(3,0) = 7 \to 7$
*   $I(3,1) = 6 \to 7$
*   $I(3,2) = 4 \to 4$
*   $I(3,3) = 1 \to 1$

✍️ **Final Exam Output Matrix:**
   $$I_{\text{stretched}} = \begin{bmatrix} 4 & 2 & 6 & 1 \\ 2 & 7 & 4 & 7 \\ 1 & 1 & 7 & 6 \\ 7 & 7 & 4 & 1 \end{bmatrix}$$

⚠️ **Common Mistakes:**
*   Applying the incorrect slope equation based on boundary overlaps. For instance, at $r = r_1$ (which is $3$), make sure you use Region 2's formula, not Region 1's.
*   Failing to round the final mapped levels to integers. Pixels must be discrete integers.

---

### 📍 Problem 1.3: Piecewise-Linear Contrast Stretching (Chronological PYQ)
⭐ **Formula / Rule:**
Same as Problem 1.2, but applied to a $4 \times 8$ grayscale matrix.

---

#### **Question (NMIMS Re-Exam, Batch 2024-25 - Q7b)**
🟢 **Verified PYQ [10 Marks]**  
On the given image, perform contrast stretching using two location points $(r_1, s_1) = (5, 2)$ and $(r_2, s_2) = (10, 13)$:
   $$I = \begin{bmatrix} 1 & 3 & 5 & 7 & 9 & 11 & 13 & 15 \\ 1 & 3 & 5 & 7 & 9 & 11 & 13 & 15 \\ 1 & 3 & 5 & 7 & 9 & 11 & 13 & 15 \\ 1 & 3 & 5 & 7 & 9 & 11 & 13 & 15 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Determine bit scale from maximum value. The matrix values go up to 15, representing a 4-bit scale ($L-1 = 15$).
2. Compute regional slopes $\alpha, \beta, \gamma$.
3. Substitute input pixel values column-by-column into correct piecewise segment equations and round output values.

#### **Step 1: Calculate slopes**
*   **Segment 1:** $\alpha = \frac{s_1}{r_1} = \frac{2}{5} = \mathbf{0.4}$
*   **Segment 2:** $\beta = \frac{s_2 - s_1}{r_2 - r_1} = \frac{13 - 2}{10 - 5} = \frac{11}{5} = \mathbf{2.2}$
*   **Segment 3:** $\gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2} = \frac{15 - 13}{15 - 10} = \frac{2}{5} = \mathbf{0.4}$

#### **Step 2: Generate Mapping Lookup Table**
*   **For $r = 1$:** (Region 1, $0 \le r < 5$):
   $$s = 0.4 \times 1 = 0.4 \implies \mathbf{0}$$
*   **For $r = 3$:** (Region 1, $0 \le r < 5$):
   $$s = 0.4 \times 3 = 1.2 \implies \mathbf{1}$$
*   **For $r = 5$:** (Region 2, $5 \le r < 10$):
   $$s = 2.2 \times (5 - 5) + 2 = \mathbf{2}$$
*   **For $r = 7$:** (Region 2, $5 \le r < 10$):
   $$s = 2.2 \times (7 - 5) + 2 = 2.2(2) + 2 = 6.4 \implies \mathbf{6}$$
*   **For $r = 9$:** (Region 2, $5 \le r < 10$):
   $$s = 2.2 \times (9 - 5) + 2 = 2.2(4) + 2 = 8.8 + 2 = 10.8 \implies \mathbf{11}$$
*   **For $r = 11$:** (Region 3, $10 \le r \le 15$):
   $$s = 0.4 \times (11 - 10) + 13 = 0.4(1) + 13 = 13.4 \implies \mathbf{13}$$
*   **For $r = 13$:** (Region 3, $10 \le r \le 15$):
   $$s = 0.4 \times (13 - 10) + 13 = 0.4(3) + 13 = 1.2 + 13 = 14.2 \implies \mathbf{14}$$
*   **For $r = 15$:** (Region 3, $10 \le r \le 15$):
   $$s = 0.4 \times (15 - 10) + 13 = 0.4(5) + 13 = 2.0 + 13 = \mathbf{15}$$

#### **Step 3: Construct Output Matrix**
Since the matrix consists of identical columns, we can directly map each column to the calculated values:
*   Col 1: $1 \to 0$
*   Col 2: $3 \to 1$
*   Col 3: $5 \to 2$
*   Col 4: $7 \to 6$
*   Col 5: $9 \to 11$
*   Col 6: $11 \to 13$
*   Col 7: $13 \to 14$
*   Col 8: $15 \to 15$

✍️ **Final Exam Output Matrix:**
   $$I_{\text{stretched}} = \begin{bmatrix} 0 & 1 & 2 & 6 & 11 & 13 & 14 & 15 \\ 0 & 1 & 2 & 6 & 11 & 13 & 14 & 15 \\ 0 & 1 & 2 & 6 & 11 & 13 & 14 & 15 \\ 0 & 1 & 2 & 6 & 11 & 13 & 14 & 15 \end{bmatrix}$$

---

### 📍 Problem 1.4: Power-Law / Gamma Transformation
⭐ **Formula / Rule:**
   $$s = c \cdot r^{\gamma}$$

**Gamma Impact Analysis on Image Tones:**
*   **$\gamma < 1$ (Fractional Gamma):** Transformation curve arches upward. It maps a narrow band of dark input values into a wider, brighter band of output values. **This brightens the overall image**, revealing hidden details in dark shadow regions [142].
*   **$\gamma = 1$ (Identity):** Linear/Identity transformation. No change in intensity contrast occurs [119].
*   **$\gamma > 1$ (Integer Gamma):** Transformation curve arches downward. It compresses dark regions and stretches bright regions into a wider output range. **This darkens the overall image**, enhancing the contrast in extremely bright, overexposed or washed-out images (e.g., aerial views) [142].

---

#### **Question (NMIMS TEE Dec 2025 - Q7(b))**
🟢 **Verified PYQ [10 Marks]**  
Apply the Power-Law (Gamma) Transformation on the following image with $c = 1.2$ and $\gamma = 0.6$ and obtain the final output image matrix (round to nearest integer).
   $$f(x, y) = \begin{bmatrix} 0 & 20 & 40 \\ 60 & 80 & 100 \\ 110 & 120 & 127 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Because the inputs range up to 127, direct power evaluation of $r^{\gamma}$ is expected based on the synoptic answers provided in the exam key ($s = 1.2 \times r^{0.6}$) [11].

Calculate $s$ for each unique pixel value in the matrix:
1.  **For $r = 0$:**
   $$s = 1.2 \times (0)^{0.6} = 0 \implies \mathbf{0}$$
2.  **For $r = 20$:**
   $$s = 1.2 \times (20)^{0.6} = 1.2 \times 6.037 = 7.24 \implies \mathbf{7}$$
3.  **For $r = 40$:**
   $$s = 1.2 \times (40)^{0.6} = 1.2 \times 9.155 = 10.99 \implies \mathbf{11}$$
4.  **For $r = 60$:**
   $$s = 1.2 \times (60)^{0.6} = 1.2 \times 11.664 = 13.99 \implies \mathbf{14}$$
5.  **For $r = 80$:**
   $$s = 1.2 \times (80)^{0.6} = 1.2 \times 13.764 = 16.52 \implies \mathbf{17}$$
6.  **For $r = 100$:**
   $$s = 1.2 \times (100)^{0.6} = 1.2 \times 15.860 = 19.03 \implies \mathbf{19}$$
7.  **For $r = 110$:**
   $$s = 1.2 \times (110)^{0.6} = 1.2 \times 16.844 = 20.21 \implies \mathbf{20}$$
8.  **For $r = 120$:**
   $$s = 1.2 \times (120)^{0.6} = 1.2 \times 17.777 = 21.33 \implies \mathbf{21}$$
9.  **For $r = 127$:**
   $$s = 1.2 \times (127)^{0.6} = 1.2 \times 18.415 = 22.10 \implies \mathbf{22}$$

✍️ **Final Exam Output Matrix:**
   $$g(x, y) = \begin{bmatrix} 0 & 7 & 11 \\ 14 & 17 & 19 \\ 20 & 21 & 22 \end{bmatrix}$$

---

### 📍 Problem 1.5: Logarithmic Transformations
⭐ **Formula / Rule:**
   $$s = c \cdot \log_{10}(1 + r)$$

---

#### **Question (Syllabus Concept / University Exam PYQ - Q1h)**
🟢 **Verified PYQ (Final Exam 2024-25 / 2023-24 - Q1h) [2 Marks]**  
Two pixel values of an image are given as 0 and 1000. What is the resultant value after applying log transformation to the two pixels? Assume constant c=1. Comment on the results obtained.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Apply the transformation formula directly using base-10 logarithms:
   $$s = 1 \cdot \log_{10}(1 + r)$$

1.  **For the minimum intensity $r_1 = 0$:**
   $$s_1 = \log_{10}(1 + 0) = \log_{10}(1) = \mathbf{0}$$
2.  **For the maximum intensity $r_2 = 1000$:**
   $$s_2 = \log_{10}(1 + 1000) = \log_{10}(1001) \approx \mathbf{3.0004}$$

#### **Conclusion & Exam Comments:**
*   **Output levels:** $r = 0 \to \mathbf{0}$; $r = 1000 \to \mathbf{3.00}$ (or $\mathbf{6.91}$ if natural logarithm is explicitly used by the evaluator).
*   **Visual Comment:** The log transform maps a massive range of dynamic input intensities $[0, 1000]$ into a highly compressed, narrow display range $[0, 3]$. It stretches the contrast of dark shadow values while compressing light values. This is ideal for visualizing the vast dynamic spectrum of Fourier transforms where high-energy peaks dominate, allowing lower-intensity structural details to be visualized simultaneously [49, 50].

---

### 📍 Problem 1.6: Intensity-Level / Gray-Level Slicing (Syllabus-Matched PYQ)
⭐ **Formula / Rule:**
Highlighting a range of intensities $[T_1, T_2]$:

**Approach A: Gray-level Slicing With Background Preservation**
   $$s = \begin{cases} L - 1 & \text{if } T_1 \le r \le T_2 \\ r & \text{otherwise} \end{cases}$$

**Approach B: Gray-level Slicing Without Background Preservation**
   $$s = \begin{cases} L - 1 & \text{if } T_1 \le r \le T_2 \\ 0 & \text{otherwise} \end{cases}$$

---

#### **Question (NMIMS Test-I August 2025, Set 2 - Q2)**
🟢 **Verified PYQ [3 Marks]**  
Apply Grey level slicing on the given $3 \times 3$ grayscale image for the range $[T_1=5, T_2=10]$ and compute the new pixel values of the image:
   $$I = \begin{bmatrix} 3 & 6 & 12 \\ 7 & 9 & 15 \\ 4 & 8 & 10 \end{bmatrix}$$

1.  Apply Grey level slicing with background on the first row of the image and generate the updated matrix.
2.  Apply Grey level slicing without background on the second row of the generated matrix in step (i) and update the matrix.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Identify parameters: target range $[5, 10]$. Assume standard maximum intensity scale of 8-bit digital representation ($L - 1 = 255$) representing pure white highlight [136].

#### **Step 1: Slicing with background on the first row:**
The first row elements are $[3, 6, 12]$:
*   $r = 3$: $3 \notin [5, 10] \implies$ preserved as **`3`**.
*   $r = 6$: $6 \in [5, 10] \implies$ highlighted to **`255`**.
*   $r = 12$: $12 \notin [5, 10] \implies$ preserved as **`12`**.

This generates the intermediate matrix:
   $$I_{\text{step1}} = \begin{bmatrix} 3 & 255 & 12 \\ 7 & 9 & 15 \\ 4 & 8 & 10 \end{bmatrix}$$

#### **Step 2: Slicing without background on the second row of $I_{\text{step1}}$:**
The second row elements of the intermediate matrix are $[7, 9, 15]$. Slicing without background maps values outside $[5, 10]$ to `0`, and values inside to `255`:
*   $r = 7$: $7 \in [5, 10] \implies$ highlighted to **`255`**.
*   $r = 9$: $9 \in [5, 10] \implies$ highlighted to **`255`**.
*   $r = 15$: $15 \notin [5, 10] \implies$ mapped to **`0`**.

Row 3 remains unchanged: $[4, 8, 10]$.

✍️ **Final Exam Output Matrix:**
   $$I_{\text{final}} = \begin{bmatrix} 3 & 255 & 12 \\ 255 & 255 & 0 \\ 4 & 8 & 10 \end{bmatrix}$$

---

### 📍 Problem 1.7: Intensity-Level / Gray-Level Slicing (Chronological PYQ)
⭐ **Formula / Rule:**
Slicing without background preservation on 3 BPP ($L-1 = 7$) [223].

---

#### **Question (NMIMS Re-Exam, Batch 2023-24 - Q2a)**
🟢 **Verified PYQ [4 Marks]**  
Apply gray level slicing without preserving background on the following 3 Bits Per Pixel image given below. Assume $r_1=2$ and $r_2=5$. Size of image is $5 \times 5$:
   $$A = \begin{bmatrix} 1 & 1 & 1 & 1 & 2 \\ 6 & 6 & 6 & 6 & 1 \\ 4 & 4 & 4 & 1 & 1 \\ 3 & 3 & 3 & 3 & 3 \\ 1 & 1 & 1 & 1 & 1 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Given 3 Bits Per Pixel $\implies L = 2^3 = 8$ gray levels. Maximum gray scale level $L-1 = 7$.
2. Segment condition: range $[r_1, r_2] = [2, 5]$.
3. Apply formula:
   $$s = \begin{cases} 7 & \text{if } 2 \le r \le 5 \\ 0 & \text{otherwise} \end{cases}$$

#### **Calculation cell-by-cell:**
*   **Row 1:** $[1, 1, 1, 1, 2] \implies [0, 0, 0, 0, 7]$
*   **Row 2:** $[6, 6, 6, 6, 1] \implies [0, 0, 0, 0, 0]$
*   **Row 3:** $[4, 4, 4, 1, 1] \implies [7, 7, 7, 0, 0]$
*   **Row 4:** $[3, 3, 3, 3, 3] \implies [7, 7, 7, 7, 7]$
*   **Row 5:** $[1, 1, 1, 1, 1] \implies [0, 0, 0, 0, 0]$

✍️ **Final Exam Output Matrix:**
   $$A_{\text{sliced}} = \begin{bmatrix} 0 & 0 & 0 & 0 & 7 \\ 0 & 0 & 0 & 0 & 0 \\ 7 & 7 & 7 & 0 & 0 \\ 7 & 7 & 7 & 7 & 7 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix}$$

---

### 📍 Problem 1.8: Basic Iterative Global Thresholding (Matrix Example)
⭐ **Formula / Rule:**
The threshold converges iteratively midway between the means of two segmented groups:
   $$T_{i+1} = \frac{\mu_1 + \mu_2}{2}$$

---

#### **Question (DIP Course Lecture Slides Reference)**
🔵 **Classroom / Homework Practice Question**  
Consider the following $3 \times 3$ image segment of an 8-bit image:
   $$I = \begin{bmatrix} 5 & 3 & 9 \\ 2 & 1 & 7 \\ 8 & 4 & 2 \end{bmatrix}$$

Calculate the optimal global threshold $T$ using the Basic Iterative Global Thresholding algorithm. Show every iteration to convergence. Round intermediate values to the nearest integer.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Initialize the threshold with the overall mean of the matrix, then iteratively partition and update until stable.

#### **Iteration 1:**
*   **Step 1: Calculate Initial Threshold ($T_0$):**
   $$T_0 = \text{round}\left( \frac{5 + 3 + 9 + 2 + 1 + 7 + 8 + 4 + 2}{9} \right) = \text{round}\left( \frac{41}{9} \right) = \text{round}(4.5556) \implies \mathbf{5}$$
*   **Step 2: Partition the image into $G_1$ and $G_2$ using $T_0 = 5$:**
    *   $G_1$ (values $> 5$): $\{7, 8, 9\}$
    *   $G_2$ (values $\le 5$): $\{1, 2, 2, 3, 4, 5\}$
*   **Step 3: Compute Means $\mu_1$ and $\mu_2$:**
   $$\mu_1 = \frac{7 + 8 + 9}{3} = \frac{24}{3} = \mathbf{8}$$
   $$\mu_2 = \text{round}\left( \frac{1 + 2 + 2 + 3 + 4 + 5}{6} \right) = \text{round}\left( \frac{17}{6} \right) = \text{round}(2.8333) \implies \mathbf{3}$$
*   **Step 4: Calculate New Threshold ($T_1$):**
   $$T_1 = \text{round}\left( \frac{\mu_1 + \mu_2}{2} \right) = \text{round}\left( \frac{8 + 3}{2} \right) = \text{round}(5.5) \implies \mathbf{6}$$
*   Since $T_1 \neq T_0$ ($6 \neq 5$), we proceed to Iteration 2.

#### **Iteration 2:**
*   **Step 2: Partition the image using $T_1 = 6$:**
    *   $G_1$ (values $> 6$): $\{7, 8, 9\}$
    *   $G_2$ (values $\le 6$): $\{1, 2, 2, 3, 4, 5\}$
*   **Step 3: Compute Means $\mu_1$ and $\mu_2$:**
   $$\mu_1 = \frac{7 + 8 + 9}{3} = \mathbf{8}$$
   $$\mu_2 = \text{round}\left( \frac{1 + 2 + 2 + 3 + 4 + 5}{6} \right) = \mathbf{3}$$
*   **Step 4: Calculate New Threshold ($T_2$):**
   $$T_2 = \text{round}\left( \frac{\mu_1 + \mu_2}{2} \right) = \text{round}\left( \frac{8 + 3}{2} \right) \implies \mathbf{6}$$
*   Since $T_2 = T_1$ ($6 = 6$), the threshold has successfully converged!

✍️ **Final Exam Answer:**
The optimal global threshold for the given image segment is **`6`**.

---

### 📍 Problem 1.9: Basic Iterative Global Thresholding (Histogram Distribution)
---

#### **Question (DIP Course Lecture Slides Reference)**
🔵 **Classroom / Homework Practice Question**  
A 3-bit image has the following gray-level frequency distribution:

| Gray level $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Pixel Count $n_k$** | 5 | 6 | 4 | 3 | 1 | 4 | 3 | 4 |

Using an initial threshold estimate of $T_0 = 3$, calculate the optimal global threshold. Show how the algorithm converges under both:
1.  **Method A:** The simple unweighted arithmetic mean of gray level indices.
2.  **Method B:** The mathematically rigorous histogram-weighted mean.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Start with $T_0 = 3$. Partition the histogram into two classes: levels $\le 3$ and levels $> 3$.

#### **1. Solving by Method A (Unweighted/Arithmetic Mean of Level Indices):**
This is the simplified method shown in standard lecture summaries [261]:
*   **Group 1 (levels $> 3$):** $\{4, 5, 6, 7\}$
   $$\mu_1 = \text{round}\left( \frac{4 + 5 + 6 + 7}{4} \right) = \text{round}(5.5) \implies \mathbf{6}$$
*   **Group 2 (levels $\le 3$):** $\{0, 1, 2, 3\}$
   $$\mu_2 = \text{round}\left( \frac{0 + 1 + 2 + 3}{4} \right) = \text{round}(1.5) \implies \mathbf{2}$$
*   **Update Threshold ($T_1$):**
   $$T_1 = \frac{\mu_1 + \mu_2}{2} = \frac{6 + 2}{2} = \mathbf{4}$$
*   Since $T_1 \neq T_0$ ($4 \neq 3$), we repeat the process with $T_1 = 4$:
    *   **Group 1 (levels $> 4$):** $\{5, 6, 7\}$
   $$\mu_1 = \text{round}\left( \frac{5 + 6 + 7}{3} \right) = \mathbf{6}$$
    *   **Group 2 (levels $\le 4$):** $\{0, 1, 2, 3, 4\}$
   $$\mu_2 = \text{round}\left( \frac{0 + 1 + 2 + 3 + 4}{5} \right) = \mathbf{2}$$
    *   **Update Threshold ($T_2$):**
   $$T_2 = \frac{6 + 2}{2} = \mathbf{4}$$
*   Since $T_2 = T_1 = 4$, the algorithm converged. Final threshold = **`4`**.

#### **2. Solving by Method B (Histogram-Weighted Mean):**
This is the mathematically correct implementation used in Gonzalez & Woods [109, 261]:
*   **Iteration 1 with $T_0 = 3$:**
    *   $G_1$ (levels $> 3$, i.e., $4, 5, 6, 7$): Total pixels $N_1 = 1 + 4 + 3 + 4 = 12$
   $$\mu_1 = \frac{(4 \times 1) + (5 \times 4) + (6 \times 3) + (7 \times 4)}{12} = \frac{70}{12} \approx 5.8333$$
    *   $G_2$ (levels $\le 3$, i.e., $0, 1, 2, 3$): Total pixels $N_2 = 5 + 6 + 4 + 3 = 18$
   $$\mu_2 = \frac{(0 \times 5) + (1 \times 6) + (2 \times 4) + (3 \times 3)}{18} = \frac{23}{18} \approx 1.2778$$
    *   **Update Threshold ($T_1$):**
   $$T_1 = \text{round}\left( \frac{5.8333 + 1.2778}{2} \right) = \text{round}(3.5556) \implies \mathbf{4}$$
    *   Since $T_1 \neq T_0$ ($4 \neq 3$), proceed to Iteration 2.

*   **Iteration 2 with $T_1 = 4$:**
    *   $G_1$ (levels $> 4$, i.e., $5, 6, 7$): Total pixels $N_1 = 4 + 3 + 4 = 11$
   $$\mu_1 = \frac{(5 \times 4) + (6 \times 3) + (7 \times 4)}{11} = \frac{66}{11} = \mathbf{6.0000}$$
    *   $G_2$ (levels $\le 4$, i.e., $0, 1, 2, 3, 4$): Total pixels $N_2 = 5 + 6 + 4 + 3 + 1 = 19$
   $$\mu_2 = \frac{(0 \times 5) + (1 \times 6) + (2 \times 4) + (3 \times 3) + (4 \times 1)}{19} = \frac{27}{19} \approx 1.4211$$
    *   **Update Threshold ($T_2$):**
   $$T_2 = \text{round}\left( \frac{6.0000 + 1.4211}{2} \right) = \text{round}(3.7106) \implies \mathbf{4}$$
    *   Since $T_2 = T_1 = 4$, the algorithm has successfully converged!

✍️ **Final Exam Answer:**
Under both simple unweighted and rigorous weighted methods, the optimal global threshold is **`4`**.

---

### 📍 Problem 1.10: Power-Law / Gamma Transformation (Slide Typo Alert)
⭐ **Formula / Rule:**
   $$s = c \cdot r^{\gamma}$$

---

#### **Question (DIP Class Slides / Practical Homework Homework)**
🔵 **Classroom / Homework Practice Question**  
Perform power-law transformation on the given input 3-bit image matrix $A$ below with $c = 3$ and 2nd root ($\gamma = 0.5$):
   $$A = \begin{bmatrix} 2 & 3 & 0 & 6 & 7 \\ 0 & 3 & 7 & 5 & 2 \\ 5 & 3 & 2 & 4 & 0 \\ 4 & 2 & 2 & 1 & 0 \\ 1 & 7 & 6 & 4 & 5 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Apply the transformation formula:
   $$s = 3 \cdot A^{0.5} = 3 \cdot \sqrt{A}$$

#### **Calculation for unique values:**
*   $r = 0 \implies s = 3 \times \sqrt{0} = \mathbf{0}$
*   $r = 1 \implies s = 3 \times \sqrt{1} = \mathbf{3}$
*   $r = 2 \implies s = 3 \times \sqrt{2} \approx 4.24 \implies \mathbf{4}$
*   $r = 3 \implies s = 3 \times \sqrt{3} \approx 5.19 \implies \mathbf{5}$
*   $r = 4 \implies s = 3 \times \sqrt{4} = \mathbf{6}$
*   $r = 5 \implies s = 3 \times \sqrt{5} \approx 6.70 \implies \mathbf{7}$
*   $r = 6 \implies s = 3 \times \sqrt{6} \approx 7.34 \implies \mathbf{7}$ (Clipped to max level 7)
*   $r = 7 \implies s = 3 \times \sqrt{7} \approx 7.93 \implies \mathbf{7}$ (Clipped to max level 7)

⚠️ **Exam Slide Typo Alert (Crucial for MPSTME Students):**
In the teacher-provided class presentation slide, the value $r = 7$ is mapped as $3 \times \sqrt{7} \approx 7.93$ and rounded to **`8`** [181]. However, a 3-bit image has a maximum gray level of $2^3 - 1 = 7$. Thus, mathematically, the value `8` is **completely invalid** and must be clipped/saturated to `7` [181]. 
In your exam, write the mathematically correct matrix (with values capped at 7) but add a small note explaining that if following the slide's literal typo, the value is rounded to 8 to secure maximum marks.

*   **Mathematically Correct Matrix (Clipped to 7):**
   $$A_{\text{correct}} = \begin{bmatrix} 4 & 5 & 0 & 7 & 7 \\ 0 & 5 & 7 & 7 & 4 \\ 7 & 5 & 4 & 6 & 0 \\ 6 & 4 & 4 & 3 & 0 \\ 3 & 7 & 7 & 6 & 7 \end{bmatrix}$$
*   **Slide Literal Typo Matrix (With 8s):**
   $$A_{\text{slide}} = \begin{bmatrix} 4 & 5 & 0 & 7 & 8 \\ 0 & 5 & 8 & 7 & 4 \\ 7 & 5 & 4 & 6 & 0 \\ 6 & 4 & 4 & 3 & 0 \\ 3 & 8 & 7 & 6 & 7 \end{bmatrix}$$

---
---

## 📊 PART 2: HISTOGRAM PROCESSING NUMERICALS

---

### 📍 Problem 2.1: Hand-Calculated Equalization on a $3 \times 3$ Matrix
⭐ **Formula / Rule:**
   $$s_k = \text{round}\left( (L - 1) \cdot \sum_{j=0}^{k} p_r(r_j) \right) = \text{round}\left( (L - 1) \cdot \text{CDF}(r_k) \right)$$

---

#### **Question (Experiment 4, Task 1 - Master Student Lab Book)**
🔵 **Classroom / Homework Practice Question**  
Apply the histogram equalization process on the given $3 \times 3$, 3-bit image matrix:
   $$I = \begin{bmatrix} 5 & 2 & 2 \\ 6 & 7 & 3 \\ 3 & 7 & 3 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Compute the frequency $n_k$ of each intensity level $r_k$ from $0$ to $7$.
2. Compute the total number of pixels $N$ ($N = 3 \times 3 = 9$ pixels).
3. Compute the PDF: $p_r(r_k) = \frac{n_k}{N}$.
4. Compute the running CDF: $\text{CDF}(r_k) = \sum p_r(r_j)$.
5. Calculate the transformed rounded scale level: $s_k = \text{round}(7 \times \text{CDF}(r_k))$.
6. Replace the original pixels in the input matrix with the mapped values $s_k$.

#### **Step 1: Construct the Frequency and CDF Table**

| Gray Level ($r_k$) | Pixel Count ($n_k$) | PDF ($p_r(r_k)$) | CDF ($S_k$) | $7 \times S_k$ | Rounded Level ($s_k$) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **0** | 0 | 0.0000 | 0.0000 | 0.0000 | **0** |
| **1** | 0 | 0.0000 | 0.0000 | 0.0000 | **0** |
| **2** | 2 | $2/9 \approx 0.2222$ | 0.2222 | 1.5556 | **2** |
| **3** | 3 | $3/9 \approx 0.3333$ | 0.5556 | 3.8889 | **4** |
| **4** | 0 | 0.0000 | 0.5556 | 3.8889 | **4** |
| **5** | 1 | $1/9 \approx 0.1111$ | 0.6667 | 4.6667 | **5** |
| **6** | 1 | $1/9 \approx 0.1111$ | 0.7778 | 5.4444 | **5** |
| **7** | 2 | $2/9 \approx 0.2222$ | 1.0000 | 7.0000 | **7** |

#### **Step 2: Map the Input Matrix**
Map each original level to its new equalized value:
*   $5 \to 5$
*   $2 \to 2$
*   $6 \to 5$
*   $7 \to 7$
*   $3 \to 4$

✍ *Resulting Output Matrix:*
   $$I_{\text{equalized}} = \begin{bmatrix} 5 & 2 & 2 \\ 5 & 7 & 4 \\ 4 & 7 & 4 \end{bmatrix}$$

---

### 📍 Problem 2.2: Equalization on a Gray-Level Distribution ($N = 60$)
---

#### **Question (NMIMS Final Exam December 2025 - Q2a)**
🟢 **Verified PYQ [10 Marks]**  
An image has the following gray levels and corresponding number of pixels:

| Gray level $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **No. of pixels $n_k$** | 2 | 3 | 5 | 8 | 10 | 20 | 8 | 4 |

Compute the gray level distribution using histogram equalization. Also plot the histogram of the input and output (equalized) images.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Sum all pixel counts to find $N$:
   $$N = 2 + 3 + 5 + 8 + 10 + 20 + 8 + 4 = 60 \text{ pixels}$$ [8]
2. Calculate the PDF and CDF, then apply $s_k = \text{round}(7 \times \text{CDF}(r_k))$.

#### **Step 1: Complete Calculation Table**

| $k$ | $r_k$ | $n_k$ | PDF ($p_r(r_k)$) | CDF ($S_k$) | $7 \times S_k$ | Rounded $s_k$ |
| :-: | :---: | :---: | :--- | :--- | :--- | :---: |
| 0 | **0** | 2 | $2/60 = 0.0333$ | $0.0333$ | $0.2333$ | **0** |
| 1 | **1** | 3 | $3/60 = 0.0500$ | $0.0833$ | $0.5833$ | **1** |
| 2 | **2** | 5 | $5/60 = 0.0833$ | $0.1667$ | $1.1667$ | **1** |
| 3 | **3** | 8 | $8/60 = 0.1333$ | $0.3000$ | $2.1000$ | **2** |
| 4 | **4** | 10 | $10/60 = 0.1667$ | $0.4667$ | $3.2667$ | **3** |
| 5 | **5** | 20 | $20/60 = 0.3333$ | $0.8000$ | $5.6000$ | **6** |
| 6 | **6** | 8 | $8/60 = 0.1333$ | $0.9333$ | $6.5333$ | **7** |
| 7 | **7** | 4 | $4/60 = 0.0667$ | $1.0000$ | $7.0000$ | **7** |

#### **Step 2: Grouping / Redistribution of Output Pixels**
Now combine the frequency counts of input levels that mapped to the same output level:
*   Output **`0`**: matches input $r_0 \implies n'_0 = 2$ pixels
*   Output **`1`**: matches input $r_1, r_2 \implies n'_1 = 3 + 5 = 8$ pixels
*   Output **`2`**: matches input $r_3 \implies n'_2 = 8$ pixels
*   Output **`3`**: matches input $r_4 \implies n'_3 = 10$ pixels
*   Output **`4`**: no inputs mapped here $\implies n'_4 = 0$ pixels
*   Output **`5`**: no inputs mapped here $\implies n'_5 = 0$ pixels
*   Output **`6`**: matches input $r_5 \implies n'_6 = 20$ pixels
*   Output **`7`**: matches input $r_6, r_7 \implies n'_7 = 8 + 4 = 12$ pixels

✍️ **Final Equalized Gray Level Distribution Table:**

| Equalized level $s_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **New Pixel Count $n'_k$**| 2 | 8 | 8 | 10 | 0 | 0 | 20 | 12 |

*(Ensure total pixels check: $2 + 8 + 8 + 10 + 20 + 12 = 60$. Correct!)*

---

### 📍 Problem 2.3: Equalization on an 8x8 Grayscale Matrix
---

#### **Question (NMIMS Re-Exam, Batch 2023-24 - Q3a)**
🟢 **Verified PYQ [10 Marks]**  
Perform histogram equalization on the given $8 \times 8$ image. The gray level distribution of the image is given below:

| Gray levels $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **No. of pixels $n_k$** | 18 | 10 | 3 | 2 | 2 | 3 | 14 | 12 |

Draw the original histogram and the equalized histogram.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Verify spatial dimensions: $8 \times 8 \implies N = 64$ total pixels.
2. Sum given pixel counts: $N = 18 + 10 + 3 + 2 + 2 + 3 + 14 + 12 = 64$.
3. Compute PDF, CDF, and target levels scaled to $L-1 = 7$.

#### **Step 1: Construct Mappings**

| $k$ | $r_k$ | $n_k$ | PDF ($p_r(r_k) = n_k/64$) | CDF ($S_k$) | $7 \times S_k$ | Rounded Output ($s_k$) |
| :-: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | **0** | 18 | $18/64 \approx 0.2813$ | $0.2813$ | $1.9688$ | **2** |
| 1 | **1** | 10 | $10/64 \approx 0.1563$ | $0.4375$ | $3.0625$ | **3** |
| 2 | **2** | 3 | $3/64 \approx 0.0469$ | $0.4844$ | $3.3906$ | **3** |
| 3 | **3** | 2 | $2/64 \approx 0.0313$ | $0.5156$ | $3.6094$ | **4** |
| 4 | **4** | 2 | $2/64 \approx 0.0313$ | $0.5469$ | $3.8281$ | **4** |
| 5 | **5** | 3 | $3/64 \approx 0.0469$ | $0.5938$ | $4.1563$ | **4** |
| 6 | **6** | 14 | $14/64 \approx 0.2188$ | $0.8125$ | $5.6875$ | **6** |
| 7 | **7** | 12 | $12/64 \approx 0.1875$ | $1.0000$ | $7.0000$ | **7** |

#### **Step 2: Redistribute pixel counts to equalized levels**
*   **s = 0**: $0$ pixels
*   **s = 1**: $0$ pixels
*   **s = 2**: maps from $r_0 \implies \mathbf{18}$ pixels
*   **s = 3**: maps from $r_1, r_2 \implies 10 + 3 = \mathbf{13}$ pixels
*   **s = 4**: maps from $r_3, r_4, r_5 \implies 2 + 2 + 3 = \mathbf{7}$ pixels
*   **s = 5**: $0$ pixels
*   **s = 6**: maps from $r_6 \implies \mathbf{14}$ pixels
*   **s = 7**: maps from $r_7 \implies \mathbf{12}$ pixels

✍️ **Final Equalized Gray Level Table:**

| Equalized level $s_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **New Pixel Count $n'_k$**| 0 | 0 | 18 | 13 | 7 | 0 | 14 | 12 |

*(Total pixels check: $18 + 13 + 7 + 14 + 12 = 64$. Correct!)*

---

### 📍 Problem 2.4: Point Processing Contrast Stretching and Equalization
---

#### **Question (NMIMS Final Exam December 2024 - Q2a)**
🟢 **Verified PYQ [10 Marks]**  
Perform the following operations on the 4-bit image shown below:
1. Contrast stretching using the transformation characteristics shown in the graph below. Comment on the effect.
2. Histogram equalization of the image. Comment on the effect.
   $$A = \begin{bmatrix} 10 & 2 & 13 & 7 \\ 11 & 14 & 6 & 9 \\ 4 & 7 & 3 & 2 \\ 0 & 7 & 10 & 7 \end{bmatrix}$$

*(Note: The graph accompanying Part 1 has three linear segments starting at $(0,0)$, passing through $(5,2)$ and $(10,12)$, and ending at $(15,15)$).*

---

#### **Step-by-Step Solution**

🧠 **Approach:**
*   Input matrix dimensions: $4 \times 4 \implies N = 16$ total pixels.
*   4-bit depth implies $L = 2^4 = 16$ gray scale levels ($0$ to $15$).

##### **Part 1: Contrast Stretching Calculation**
*   **Step A: Compute Slopes and Equations:**
   $$\alpha = \frac{2}{5} = \mathbf{0.4}, \quad \beta = \frac{12 - 2}{10 - 5} = \frac{10}{5} = \mathbf{2.0}, \quad \gamma = \frac{15 - 12}{15 - 10} = \frac{3}{5} = \mathbf{0.6}$$
    *   **Region 1 ($0 \le r < 5$):** $s = \text{round}(0.4 \cdot r)$
    *   **Region 2 ($5 \le r < 10$):** $s = \text{round}(2(r - 5) + 2)$
    *   **Region 3 ($10 \le r \le 15$):** $s = \text{round}(0.6(r - 10) + 12)$

*   **Step B: Construct lookup table for original values present in matrix:**
    *   $r=0 \implies s = 0.4 \times 0 = \mathbf{0}$
    *   $r=2 \implies s = \text{round}(0.4 \times 2) = \text{round}(0.8) \implies \mathbf{1}$
    *   $r=3 \implies s = \text{round}(0.4 \times 3) = \text{round}(1.2) \implies \mathbf{1}$
    *   $r=4 \implies s = \text{round}(0.4 \times 4) = \text{round}(1.6) \implies \mathbf{2}$
    *   $r=6 \implies s = \text{round}(2 \times (6 - 5) + 2) = \mathbf{4}$
    *   $r=7 \implies s = \text{round}(2 \times (7 - 5) + 2) = \mathbf{6}$
    *   $r=9 \implies s = \text{round}(2 \times (9 - 5) + 2) = \mathbf{10}$
    *   $r=10 \implies s = \text{round}(0.6 \times (10 - 10) + 12) = \mathbf{12}$
    *   $r=11 \implies s = \text{round}(0.6 \times (11 - 10) + 12) = \text{round}(12.6) \implies \mathbf{13}$
    *   $r=13 \implies s = \text{round}(0.6 \times (13 - 10) + 12) = \text{round}(13.8) \implies \mathbf{14}$
    *   $r=14 \implies s = \text{round}(0.6 \times (14 - 10) + 12) = \text{round}(14.4) \implies \mathbf{14}$

*   **Step C: Replace values to generate Stretched Matrix:**
   $$A_{\text{stretched}} = \begin{bmatrix} 12 & 1 & 14 & 6 \\ 13 & 14 & 4 & 10 \\ 2 & 6 & 1 & 1 \\ 0 & 6 & 12 & 6 \end{bmatrix}$$

*   **Comment on Effect:** Contrast stretching mapped the low values to a highly compressed dark range and high values to compressed bright highlights, whilst steeply stretching the mid-tones (slope of $\beta = 2.0$). This significantly expands visual contrast and separates the mid-gray details.

##### **Part 2: Histogram Equalization Calculation**
*   **Step A: Count unique levels, compute PDF and CDF ($N=16$, $L-1=15$):**

| $r_k$ | Count $n_k$ | PDF ($p_r = n_k/16$) | CDF ($S_k$) | $15 \times S_k$ | Rounded Level ($s_k$) |
| :-: | :---: | :---: | :---: | :---: | :---: |
| **0** | 1 | $1/16 = 0.0625$ | $0.0625$ | $0.9375$ | **1** |
| **2** | 2 | $2/16 = 0.1250$ | $0.1875$ | $2.8125$ | **3** |
| **3** | 1 | $1/16 = 0.0625$ | $0.2500$ | $3.7500$ | **4** |
| **4** | 1 | $1/16 = 0.0625$ | $0.3125$ | $4.6875$ | **5** |
| **6** | 1 | $1/16 = 0.0625$ | $0.3750$ | $5.6250$ | **6** |
| **7** | 4 | $4/16 = 0.2500$ | $0.6250$ | $9.3750$ | **9** |
| **9** | 1 | $1/16 = 0.0625$ | $0.6875$ | $10.3125$ | **10** |
| **10** | 2 | $2/16 = 0.1250$ | $0.8125$ | $12.1875$ | **12** |
| **11** | 1 | $1/16 = 0.0625$ | $0.8750$ | $13.1250$ | **13** |
| **13** | 1 | $1/16 = 0.0625$ | $0.9375$ | $14.0625$ | **14** |
| **14** | 1 | $1/16 = 0.0625$ | $1.0000$ | $15.0000$ | **15** |

*   **Step B: Replace input matrix values using the mapping lookup table:**
   $$A_{\text{equalized}} = \begin{bmatrix} 12 & 3 & 14 & 9 \\ 13 & 15 & 6 & 10 \\ 5 & 9 & 4 & 3 \\ 1 & 9 & 12 & 9 \end{bmatrix}$$

*   **Comment on Effect:** Histogram equalization expands the dynamic range over the entire possible spectrum $[0, 15]$. By linearizing the Cumulative Distribution Function, it ensures that all intensity bins are populated more uniformly, dramatically increasing contrast and making dark and light structures more visible simultaneously.

---
---

## 🎨 PART 3: SMOOTHING SPATIAL FILTER OPERATIONS

---

### 📍 Problem 3.1: 3x3 Average (Box) Filter
⭐ **Formula / Rule:**
   $$g(x,y) = \frac{1}{9} \sum_{s=-1}^{1} \sum_{t=-1}^{1} f(x+s, y+t)$$

---

#### **Question (NMIMS Final Exam December 2022 - Q10)**
🟢 **Verified PYQ [10 Marks]**  
What are the linear and non-linear smoothing filters in spatial domain? Compute the new pixel values after applying the $3 \times 3$ box filter on the following $5 \times 5$ matrix of an 8-bit image (ignore rows and columns at extreme edges):
   $$I = \begin{bmatrix} 139 & 128 & 237 & 126 & 129 \\ 145 & 129 & 123 & 89 & 132 \\ 146 & 122 & 128 & 87 & 135 \\ 141 & 125 & 134 & 131 & 139 \\ 112 & 127 & 138 & 133 & 142 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. State definitions: Box filter is a linear operator computing local arithmetic means [64]; Median filter is order-statistics sorting [63].
2. Grid coordinate extraction: ignore edge boundaries. Compute the mean of the $3 \times 3$ local grid for each of the 9 inner pixels:

#### **Inner Grid Convolved Calculations:**
*   **Pixel (1,1) [Value: 129]:**
    - Subgrid: $\begin{bmatrix} 139 & 128 & 237 \\ 145 & 129 & 123 \\ 146 & 122 & 128 \end{bmatrix}$
    - Sum $= 139+128+237+145+129+123+146+122+128 = 1197$
    - Output $= \text{round}(1197 / 9) = \mathbf{133}$
*   **Pixel (1,2) [Value: 123]:**
    - Subgrid: $\begin{bmatrix} 128 & 237 & 126 \\ 129 & 123 & 89 \\ 122 & 128 & 87 \end{bmatrix}$
    - Sum $= 128+237+126+129+123+89+122+128+87 = 1169$
    - Output $= \text{round}(1169 / 9) \approx \mathbf{130}$
*   **Pixel (1,3) [Value: 89]:**
    - Subgrid: $\begin{bmatrix} 237 & 126 & 129 \\ 123 & 89 & 132 \\ 128 & 87 & 135 \end{bmatrix}$
    - Sum $= 237+126+129+123+89+132+128+87+135 = 1186$
    - Output $= \text{round}(1186 / 9) \approx \mathbf{132}$
*   **Pixel (2,1) [Value: 122]:**
    - Subgrid: $\begin{bmatrix} 145 & 129 & 123 \\ 146 & 122 & 128 \\ 141 & 125 & 134 \end{bmatrix}$
    - Sum $= 145+129+123+146+122+128+141+125+134 = 1193$
    - Output $= \text{round}(1193 / 9) \approx \mathbf{133}$
*   **Pixel (2,2) [Value: 128]:**
    - Subgrid: $\begin{bmatrix} 129 & 123 & 89 \\ 122 & 128 & 87 \\ 125 & 134 & 131 \end{bmatrix}$
    - Sum $= 129+123+89+122+128+87+125+134+131 = 1068$
    - Output $= \text{round}(1068 / 9) = \mathbf{119}$
*   **Pixel (2,3) [Value: 87]:**
    - Subgrid: $\begin{bmatrix} 123 & 89 & 132 \\ 128 & 87 & 135 \\ 134 & 131 & 139 \end{bmatrix}$
    - Sum $= 123+89+132+128+87+135+134+131+139 = 1098$
    - Output $= \text{round}(1098 / 9) = \mathbf{122}$
*   **Pixel (3,1) [Value: 125]:**
    - Subgrid: $\begin{bmatrix} 146 & 122 & 128 \\ 141 & 125 & 134 \\ 112 & 127 & 138 \end{bmatrix}$
    - Sum $= 146+122+128+141+125+134+112+127+138 = 1173$
    - Output $= \text{round}(1173 / 9) = \mathbf{130}$
*   **Pixel (3,2) [Value: 134]:**
    - Subgrid: $\begin{bmatrix} 122 & 128 & 87 \\ 125 & 134 & 131 \\ 127 & 138 & 133 \end{bmatrix}$
    - Sum $= 122+128+87+125+134+131+127+138+133 = 1125$
    - Output $= \text{round}(1125 / 9) = \mathbf{125}$
*   **Pixel (3,3) [Value: 131]:**
    - Subgrid: $\begin{bmatrix} 128 & 87 & 135 \\ 134 & 131 & 139 \\ 138 & 133 & 142 \end{bmatrix}$
    - Sum $= 128+87+135+134+131+139+138+133+142 = 1177$
    - Output $= \text{round}(1177 / 9) \approx \mathbf{131}$

✍️ **Final Grayscale Output Matrix:**
   $$I_{\text{box}} = \begin{bmatrix} 139 & 128 & 237 & 126 & 129 \\ 145 & \mathbf{133} & \mathbf{130} & \mathbf{132} & 132 \\ 146 & \mathbf{133} & \mathbf{119} & \mathbf{122} & 135 \\ 141 & \mathbf{130} & \mathbf{125} & \mathbf{131} & 139 \\ 112 & 127 & 138 & 133 & 142 \end{bmatrix}$$

---

### 📍 Problem 3.2: Weighted Average Filter
⭐ **Formula / Rule:**
   $$g(x,y) = \frac{1}{16} \sum \sum w_i \cdot z_i \implies H_{\text{weighted}} = \frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$$

---

#### **Question (DIP Slides / Classroom Notebook Reference)**
🔵 **Classroom / Homework Practice Question**  
Using the standard $3 \times 3$ Weighted Average Filter, calculate the convolved output value at center pixel coordinate $(1,1)$ (value 15) in the following image matrix:
   $$I = \begin{bmatrix} 3 & 9 & 11 & 12 \\ 7 & \mathbf{\underline{15}} & 8 & 8 \\ 10 & 12 & 9 & 10 \\ 1 & 0 & 11 & 2 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Extract local $3 \times 3$ neighborhood around center pixel $15$:
   $$\text{Sub-grid} = \begin{bmatrix} 3 & 9 & 11 \\ 7 & 15 & 8 \\ 10 & 12 & 9 \end{bmatrix}$$
2. Multiply corresponding indices by the weighted average mask:

#### **Calculation:**
   $$\text{Weighted Sum} = 1(3) + 2(9) + 1(11) + 2(7) + 4(15) + 2(8) + 1(10) + 2(12) + 1(9)$$
   $$\text{Weighted Sum} = 3 + 18 + 11 + 14 + 60 + 16 + 10 + 24 + 9 = 165$$
   $$\text{Weighted Output} = \text{round}\left( \frac{165}{16} \right) = \text{round}(10.3125) \implies \mathbf{10}$$

✍️ **Final Exam Answer:**
The convolved weighted average output at the center pixel location is **`10`**.

---

### 📍 Problem 3.3: 3x3 Median Filter (Salt & Pepper Noise Removal)
⭐ **Formula / Rule:**
The Median filter is a **nonlinear order-statistics filter** [20]. It replaces the central pixel value with the **median value** of the sorted intensity values within the neighborhood window [161].

---

#### **Question (NMIMS Final Exam December 2024 - Q1(a))**
🟢 **Verified PYQ [5 Marks]**  
Apply a $3 \times 3$ median filter on the pixel underlined in the below image. **Use zero padding.**
   $$I = \begin{bmatrix} 8 & 17 & 4 & 10 & 15 \\ 3 & \mathbf{\underline{30}} & 6 & 32 & 3 \\ 15 & 10 & 7 & 5 & 2 \\ 4 & 29 & 3 & 31 & 1 \\ 16 & 7 & 4 & 3 & 0 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. The target pixel is at index row 1, column 1 (value **`30`**).
2. Extract the $3 \times 3$ neighborhood centered at this pixel:
   $$\text{Neighborhood} = \begin{bmatrix} 8 & 17 & 4 \\ 3 & 30 & 6 \\ 15 & 10 & 7 \end{bmatrix}$$
3. List the 9 values in a 1D vector:
   $$\mathbf{V} = [8, 17, 4, 3, 30, 6, 15, 10, 7]$$
4. Sort the vector in ascending order:
   $$\mathbf{V}_{\text{sorted}} = [3, 4, 6, 7, \mathbf{8}, 10, 15, 17, 30]$$
5. The median is the 5th element (middle element):
   $$\text{Median} = \mathbf{8}$$

✍️ **Final Exam Answer:**
The sorted median value is **`8`**, which replaces the original value of **`30`**.

---

### 📍 Problem 3.4: 3x3 Gaussian Blurring Filter
⭐ **Formula / Rule:**
The Gaussian smoothing filter is an isotropic low-pass filter whose coefficients are sampled from a continuous 2-D Gaussian distribution. In your classroom materials, the standard discrete $3 \times 3$ approximation with standard deviation $\sigma = 1.0$ is equivalent to the weighted averaging filter [191]:
   $$G = \frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$$

---

#### **Question (Syllabus Textbook / Slide Numerical)**
🔵 **Classroom / Homework Practice Question**  
Given the following input matrix $I$, convolve the $3 \times 3$ Gaussian smoothing kernel using **zero-padding** and calculate the output values at the border coordinate $I_s(0,0)$ and the inner coordinate $I_s(1,1)$:
   $$I = \begin{bmatrix} 10 & 10 & 20 & 20 & 20 \\ 10 & 10 & 20 & 20 & 20 \\ 10 & 10 & 20 & 80 & 80 \\ 10 & 10 & 20 & 80 & 80 \\ 10 & 10 & 20 & 80 & 80 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. State the boundary policy: we pad the matrix with a border of zeros.
2. Convolution operation: place mask $G$ over each coordinate, multiply overlapping elements, sum, and divide by 16.

#### **1. Calculating at $I_s(0,0)$ (using zero-padding):**
With zero padding, the $3 \times 3$ neighborhood around $I(0,0)=10$ is:
   $$\text{Sub-grid} = \begin{bmatrix} 0 & 0 & 0 \\ 0 & 10 & 10 \\ 0 & 10 & 10 \end{bmatrix}$$
Multiply each element by the Gaussian mask coefficients:
   $$I_s(0,0) = \frac{1}{16} [ (1 \times 0) + (2 \times 0) + (1 \times 0) + (2 \times 0) + (4 \times 10) + (2 \times 10) + (1 \times 0) + (2 \times 10) + (1 \times 10) ]$$
   $$I_s(0,0) = \frac{1}{16} [ 40 + 20 + 20 + 10 ] = \frac{90}{16} = \mathbf{5.625}$$

#### **2. Calculating at $I_s(1,1)$ (using zero-padding):**
The $3 \times 3$ neighborhood around inner pixel $I(1,1)=10$ is:
   $$\text{Sub-grid} = \begin{bmatrix} 10 & 10 & 20 \\ 10 & 10 & 20 \\ 10 & 10 & 20 \end{bmatrix}$$
Multiply each element by the Gaussian mask coefficients:
   $$I_s(1,1) = \frac{1}{16} [ 1(10) + 2(10) + 1(20) + 2(10) + 4(10) + 2(20) + 1(10) + 2(10) + 1(20) ]$$
   $$I_s(1,1) = \frac{1}{16} [ 10 + 20 + 20 + 20 + 40 + 40 + 10 + 20 + 20 ] = \frac{200}{16} = \mathbf{12.500}$$

✍️ **Final Exam Answer:**
The calculated values are $I_s(0,0) = \mathbf{5.625}$ and $I_s(1,1) = \mathbf{12.500}$, matching the textbook scale perfectly.

---
---

## ⚠️ OUT OF MID-SEM SYLLABUS — DO NOT PREPARE

*The following point and neighborhood sharpening computations are part of the End-Sem syllabus and should be ignored during Mid-Sem preparation.*

---

### 📍 Problem 4.1: Laplacian Edge Sharpening (Isotropic Second-Order Derivative)
⭐ **Formula / Rule:**
The Laplacian filter mask having a **positive center without diagonal elements** is represented by [44]:
   $$H = \begin{bmatrix} 0 & -1 & 0 \\ -1 & 4 & -1 \\ 0 & -1 & 0 \end{bmatrix}$$

---

#### **Question (NMIMS TEE Dec 2025 - Q1(b))**
🟢 **Verified PYQ [4 Marks]**  
Consider the following $3 \times 3$ grayscale image region:
   $$I = \begin{bmatrix} 10 & 20 & 30 \\ 40 & 50 & 60 \\ 70 & 80 & 90 \end{bmatrix}$$

Using a Laplacian filter having a **positive center without diagonal elements** for sharpening, compute the output value at the center pixel ($50$).

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Place the Laplacian mask $H$ over the $3 \times 3$ sub-matrix.
2. Perform sum-of-products (correlation):
   $$R = \sum_{i=1}^{9} w_i \cdot z_i$$

#### **Calculation:**
   $$R = (0 \times 10) + (-1 \times 20) + (0 \times 30) + (-1 \times 40) + (4 \times 50) + (-1 \times 60) + (0 \times 70) + (-1 \times 80) + (0 \times 90)$$
   $$R = 0 - 20 + 0 - 40 + 200 - 60 + 0 - 80 + 0$$
   $$R = -200 + 200 = \mathbf{0}$$

✍️ **Final Exam Answer:**
The sharpened Laplacian convolved output at the center pixel location is **`0`**.

---
---

## 📝 PART 5: FORMULA SHEET & QUICK REFERENCE

### **1. Gray Level Point Transformations**
*   **Image Negation:** $s = (L - 1) - r$
*   **Binarization / Thresholding:**
   $$s = \begin{cases} L - 1 & r \ge T \\ 0 & \text{otherwise} \end{cases}$$
*   **Logarithmic Transform:** $s = c \cdot \log(1 + r)$
*   **Power-Law / Gamma Transform:** $s = c \cdot r^{\gamma}$

### **2. Piecewise Linear Contrast Stretching Slopes**
*   **Slope 1 (Shadows):** $\alpha = \frac{s_1}{r_1}$
*   **Slope 2 (Mid-tones):** $\beta = \frac{s_2 - s_1}{r_2 - r_1}$
*   **Slope 3 (Highlights):** $\gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2}$

### **3. Discrete Histogram Equalization**
*   **Probability Density Function (PDF):**
   $$p_r(r_k) = \frac{n_k}{N}$$
*   **Cumulative Distribution Function (CDF):**
   $$\text{CDF}(r_k) = \sum_{j=0}^{k} p_r(r_j)$$
*   **HE Mapping equation:**
   $$s_k = \text{round}\left( (L - 1) \cdot \text{CDF}(r_k) \right)$$

### **4. Neighborhood Operators & Filters**
*   **3x3 Average Mask:** $\frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$
*   **3x3 Weighted Average / Gaussian Mask:** $\frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$

---
---

## 🏁 FINAL SYLLABUS & NUMERICAL COVERAGE CHECKLIST

Below is the verification checklist mapping every syllabus concept to its solved problem in this workbook:

*   [x] **Digital Negatives** — Solved in **Problem 1.1**.
*   [x] **Piecewise Contrast Stretching** — Solved in **Problem 1.2 & 1.3**.
*   [x] **Power-Law Gamma Transforms** — Solved in **Problem 1.4 & 1.10**.
*   [x] **Log Transformations** — Solved in **Problem 1.5**.
*   [x] **Intensity-Level Slicing** — Solved in **Problem 1.6 & 1.7**.
*   [x] **Histogram Equalization Matrix Problems** — Solved in **Problem 2.1 & 2.4**.
*   [x] **Grayscale Count Vector Equalizations** — Solved in **Problem 2.2 & 2.3**.
*   [x] **Averaging Smoothing Filtering** — Solved in **Problem 3.1**.
*   [x] **Weighted Average Filtering** — Solved in **Problem 3.2**.
*   [x] **Basic Iterative Global Thresholding** — Solved in **Problem 1.8 & 1.9**.
*   [x] **Nonlinear Median Filtering** — Solved in **Problem 3.3**.
*   [x] **Gaussian Blurring Filter** — Solved in **Problem 3.4**.
