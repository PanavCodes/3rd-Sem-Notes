# Unit 2: Image Enhancement (Spatial Domain) - Solved Numerical Workbook
**Course:** Image and Video Processing (IVP)  
**Level:** SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC)  
**Primary References:** `IVP UNIT 2.pptx`, `IVP_M2_NOTES.pdf`, and official university PYQs  
**Focus:** Comprehensive, step-by-step mathematical solutions to prepare you to solve any exam numerical independently.

---

## 📅 Part 1: Point Processing Operations Numericals

### 📍 Problem 1.1: Digital Negative / Image Negation
⭐ **Formula / Rule:**
$$s = (L - 1) - r$$
where:
* $r$ is the input pixel intensity.
* $s$ is the output transformed pixel intensity.
* $L$ is the total number of gray levels in the image ($L = 2^k$ for a $k$-bit image).
* $L - 1$ is the maximum intensity value (e.g., $255$ for an 8-bit image, $7$ for a 3-bit image).

---

#### **Question (NMIMS Term Exam / Student Lab Manual Reference)**
Obtain the digital negative of the following 3-bit ($L = 8$) and 8-bit ($L = 256$) image matrices:

**Matrix A (3-bit):**
$$A = \begin{bmatrix} 1 & 2 & 2 \\ 6 & 7 & 3 \\ 3 & 7 & 3 \end{bmatrix}$$

**Matrix B (8-bit):**
$$B = \begin{bmatrix} 139 & 205 & 105 \\ 141 & 252 & 99 \\ 201 & 15 & 76 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Determine the maximum intensity level ($L - 1$) based on the specified bit depth ($k$).
   * For 3-bit image: $L = 2^3 = 8 \implies L - 1 = 7$.
   * For 8-bit image: $L = 2^8 = 256 \implies L - 1 = 255$.
2. Subtract each pixel value of the input matrix from the maximum intensity level ($L - 1$).

#### **1. Solving for Matrix A (3-bit, $L-1 = 7$):**
Apply $s = 7 - r$ for each coordinate:
* $s(0,0) = 7 - 1 = 6$
* $s(0,1) = 7 - 2 = 5$
* $s(0,2) = 7 - 2 = 5$
* $s(1,0) = 7 - 6 = 1$
* $s(1,1) = 7 - 7 = 0$
* $s(1,2) = 7 - 3 = 4$
* $s(2,0) = 7 - 3 = 4$
* $s(2,1) = 7 - 7 = 0$
* $s(2,2) = 7 - 3 = 4$

$$\text{Output Matrix } A_{\text{neg}} = \begin{bmatrix} 6 & 5 & 5 \\ 1 & 0 & 4 \\ 4 & 0 & 4 \end{bmatrix}$$

#### **2. Solving for Matrix B (8-bit, $L-1 = 255$):**
Apply $s = 255 - r$ for each coordinate:
* $s(0,0) = 255 - 139 = 116$
* $s(0,1) = 255 - 205 = 50$
* $s(0,2) = 255 - 105 = 150$
* $s(1,0) = 255 - 141 = 114$
* $s(1,1) = 255 - 252 = 3$
* $s(1,2) = 255 - 99 = 156$
* $s(2,0) = 255 - 201 = 54$
* $s(2,1) = 255 - 15 = 240$
* $s(2,2) = 255 - 76 = 179$

$$\text{Output Matrix } B_{\text{neg}} = \begin{bmatrix} 116 & 50 & 150 \\ 114 & 3 & 156 \\ 54 & 240 & 179 \end{bmatrix}$$

⚡ **Exam Shortcut:**
When subtracting from $255$, split the math into: $(250 - r) + 5$ or write down intermediate steps. It is a simple subtraction, but under exam pressure, simple arithmetic errors are the most common cause of lost marks!

⚠️ **Common Mistakes:**
Using $L$ instead of $L - 1$ (e.g., subtracting from $256$ or $8$ instead of $255$ or $7$). This will result in pixel values exceeding the valid range ($256$ is invalid for an 8-bit image) and is a critical error!

---

### 📍 Problem 1.2: Piecewise-Linear Contrast Stretching
⭐ **Formula / Rule:**
The contrast stretching transformation function is defined in three distinct linear regions:

$$s = \begin{cases}
\alpha \cdot r & 0 \le r < r_1 \\
\beta \cdot (r - r_1) + s_1 & r_1 \le r < r_2 \\
\gamma \cdot (r - r_2) + s_2 & r_2 \le r \le L - 1
\end{cases}$$

Where the slopes of each linear segment ($\alpha$, $\beta$, $\gamma$) are computed as:
$$\alpha = \frac{s_1}{r_1}, \quad \beta = \frac{s_2 - s_1}{r_2 - r_1}, \quad \gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2}$$

---

#### **Question (University Exam / Class notes)**
Given the following $4 \times 4$ image segment of a 3-bit image ($L = 8$):
$$I = \begin{bmatrix} 4 & 3 & 5 & 2 \\ 3 & 6 & 4 & 6 \\ 2 & 2 & 6 & 5 \\ 7 & 6 & 4 & 1 \end{bmatrix}$$

Apply contrast stretching with the control parameters:
* $r_1 = 3, \quad s_1 = 2$
* $r_2 = 5, \quad s_2 = 6$

Construct the final output image matrix (round values to the nearest integer).

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Calculate the three segment slopes ($\alpha$, $\beta$, $\gamma$).
2. Map each original intensity level $r \in \{0, 1, 2, \dots, 7\}$ to its stretched intensity $s$ using the piecewise formula.
3. Replace the original values in matrix $I$ with the mapped stretched values.

#### **Step 1: Compute Slopes**
* **Segment 1:** $\alpha = \frac{s_1}{r_1} = \frac{2}{3} \approx 0.6667$
* **Segment 2:** $\beta = \frac{s_2 - s_1}{r_2 - r_1} = \frac{6 - 2}{5 - 3} = \frac{4}{2} = 2.0000$
* **Segment 3:** $\gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2} = \frac{7 - 6}{7 - 5} = \frac{1}{2} = 0.5000$

#### **Step 2: Generate Intensity Mapping Table**
Let's compute $s$ for each level of $r$ from $0$ to $7$:

* **For $r = 0$** (Region 1): $s = 0.6667 \times 0 = 0 \implies \mathbf{0}$
* **For $r = 1$** (Region 1): $s = 0.6667 \times 1 = 0.6667 \implies \mathbf{1}$ (rounded)
* **For $r = 2$** (Region 1): $s = 0.6667 \times 2 = 1.3333 \implies \mathbf{1}$ (rounded)
* **For $r = 3$** (Region 2): $s = 2 \times (3 - 3) + 2 = 2 \implies \mathbf{2}$
* **For $r = 4$** (Region 2): $s = 2 \times (4 - 3) + 2 = 4 \implies \mathbf{4}$
* **For $r = 5$** (Region 3): $s = 0.5 \times (5 - 5) + 6 = 6 \implies \mathbf{6}$
* **For $r = 6$** (Region 3): $s = 0.5 \times (6 - 5) + 6 = 6.5 \implies \mathbf{7}$ (rounded up)
* **For $r = 7$** (Region 3): $s = 0.5 \times (7 - 5) + 6 = 7 \implies \mathbf{7}$

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
* $I(0,0) = 4 \to 4$
* $I(0,1) = 3 \to 2$
* $I(0,2) = 5 \to 6$
* $I(0,3) = 2 \to 1$
* $I(1,0) = 3 \to 2$
* $I(1,1) = 6 \to 7$
* $I(1,2) = 4 \to 4$
* $I(1,3) = 6 \to 7$
* $I(2,0) = 2 \to 1$
* $I(2,1) = 2 \to 1$
* $I(2,2) = 6 \to 7$
* $I(2,3) = 5 \to 6$
* $I(3,0) = 7 \to 7$
* $I(3,1) = 6 \to 7$
* $I(3,2) = 4 \to 4$
* $I(3,3) = 1 \to 1$

✍️ **Final Exam Output Matrix:**
$$I_{\text{stretched}} = \begin{bmatrix} 4 & 2 & 6 & 1 \\ 2 & 7 & 4 & 7 \\ 1 & 1 & 7 & 6 \\ 7 & 7 & 4 & 1 \end{bmatrix}$$

⚠️ **Common Mistakes:**
* Applying the incorrect slope equation based on boundary overlaps. For instance, at $r = r_1$ (which is $3$), make sure you use Region 2's formula, not Region 1's.
* Failing to round the final mapped levels to integers. Pixels must be discrete integers.

---

### 📍 Problem 1.3: Power-Law / Gamma Transformation
⭐ **Formula / Rule:**
$$s = c \cdot r^{\gamma}$$
where:
* $c$ is a scaling constant (often set to $1$, or calculated to map output to the maximum display range).
* $\gamma$ is the power exponent (gamma).
* $r$ is the input pixel intensity, usually normalized to $[0, 1]$ before applying the power to prevent large number overflows, then scaled back to $[0, L-1]$.
* **Exception:** For simple math matrices in class exams, values can be mapped directly if explicitly specified.

---

#### **Question Variant A (NMIMS TEE Dec 2025 - Q7(b))** [10 Marks]
Apply the Power-Law (Gamma) Transformation on the following image with $c = 1.2$ and $\gamma = 0.6$ and obtain the final output image matrix (round to nearest integer).
$$f(x, y) = \begin{bmatrix} 0 & 20 & 40 \\ 60 & 80 & 100 \\ 110 & 120 & 127 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Because the inputs range up to 127, direct power evaluation of $r^{\gamma}$ is expected based on the synoptic answers provided in the exam key ($s = 1.2 \times r^{0.6}$).

Calculate $s$ for each unique pixel value in the matrix:
1. **For $r = 0$:**
    $$s = 1.2 \times (0)^{0.6} = 0 \implies \mathbf{0}$$
2. **For $r = 20$:**
    $$s = 1.2 \times (20)^{0.6} = 1.2 \times 6.037 = 7.24 \implies \mathbf{7}$$
3. **For $r = 40$:**
    $$s = 1.2 \times (40)^{0.6} = 1.2 \times 9.155 = 10.99 \implies \mathbf{11}$$
4. **For $r = 60$:**
    $$s = 1.2 \times (60)^{0.6} = 1.2 \times 11.664 = 13.99 \implies \mathbf{14}$$
5. **For $r = 80$:**
    $$s = 1.2 \times (80)^{0.6} = 1.2 \times 13.764 = 16.52 \implies \mathbf{17}$$
6. **For $r = 100$:**
    $$s = 1.2 \times (100)^{0.6} = 1.2 \times 15.860 = 19.03 \implies \mathbf{19}$$
7. **For $r = 110$:**
    $$s = 1.2 \times (110)^{0.6} = 1.2 \times 16.844 = 20.21 \implies \mathbf{20}$$
8. **For $r = 120$:**
    $$s = 1.2 \times (120)^{0.6} = 1.2 \times 17.777 = 21.33 \implies \mathbf{21}$$
9. **For $r = 127$:**
    $$s = 1.2 \times (127)^{0.6} = 1.2 \times 18.415 = 22.10 \implies \mathbf{22}$$

✍️ **Final Exam Output Matrix:**
$$g(x, y) = \begin{bmatrix} 0 & 7 & 11 \\ 14 & 17 & 19 \\ 20 & 21 & 22 \end{bmatrix}$$

---

#### **Question Variant B (DIP Slides / Classroom Notebook Reference)**
Perform power-law transformation on the given input 3-bit image matrix $A$ below with $c = 3$ and 2nd root ($\gamma = 0.5$).
$$A = \begin{bmatrix} 2 & 3 & 0 & 6 & 7 \\ 0 & 3 & 7 & 5 & 2 \\ 5 & 3 & 2 & 4 & 0 \\ 4 & 2 & 2 & 1 & 0 \\ 1 & 7 & 6 & 4 & 5 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Apply the transformation formula:
$$s = 3 \cdot A^{0.5} = 3 \cdot \sqrt{A}$$
Round the final answers to discrete integers in the range $[0, 7]$.

Calculate $s$ for each unique intensity level:
* $r = 0 \implies s = 3 \cdot \sqrt{0} = 0 \implies \mathbf{0}$
* $r = 1 \implies s = 3 \cdot \sqrt{1} = 3 \implies \mathbf{3}$
* $r = 2 \implies s = 3 \cdot \sqrt{2} = 3 \times 1.414 = 4.24 \implies \mathbf{4}$
* $r = 3 \implies s = 3 \cdot \sqrt{3} = 3 \times 1.732 = 5.19 \implies \mathbf{5}$
* $r = 4 \implies s = 3 \cdot \sqrt{4} = 3 \times 2 = 6 \implies \mathbf{6}$
* $r = 5 \implies s = 3 \cdot \sqrt{5} = 3 \times 2.236 = 6.70 \implies \mathbf{7}$
* $r = 6 \implies s = 3 \cdot \sqrt{6} = 3 \times 2.449 = 7.34 \implies \mathbf{7}$ (Clipped to max level 7)
* $r = 7 \implies s = 3 \cdot \sqrt{7} = 3 \times 2.646 = 7.93 \implies \mathbf{7}$ (Clipped to max level 7)

✍️ **Final Exam Output Matrix:**
$$A_{\text{transformed}} = \begin{bmatrix} 4 & 5 & 0 & 7 & 7 \\ 0 & 5 & 7 & 7 & 4 \\ 7 & 5 & 4 & 6 & 0 \\ 6 & 4 & 4 & 3 & 0 \\ 3 & 7 & 7 & 6 & 7 \end{bmatrix}$$

---

### 📍 Problem 1.4: Logarithmic Transformations
⭐ **Formula / Rule:**
$$s = c \cdot \log_{10}(1 + r)$$
For 8-bit images, $c$ is calculated dynamically to scale the maximum output value to 255:
$$c = \frac{255}{\log_{10}(1 + 255)} = \frac{255}{\log_{10}(256)} \approx 105.88 \approx 106$$

---

#### **Question (Syllabus Concept / Lab manual Notes)**
An input medical MRI image has gray levels containing values from a massive dynamic range of $0$ to $10^6$. Explain how applying a log transformation with $c = 1$ compresses this dynamic range.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Apply the transformation formula:
$$s = 1 \cdot \log_{10}(1 + r)$$

1. **For the minimum intensity $r = 0$:**
    $$s = \log_{10}(1 + 0) = \log_{10}(1) = \mathbf{0}$$
2. **For the maximum intensity $r = 10^6$:**
    $$s = \log_{10}(1 + 10^6) \approx \log_{10}(10^6) = \mathbf{6}$$

#### **Conclusion:**
The dynamic range is compressed from $[0, 10^6]$ down to a highly manageable scale of $[0, 6]$. This allows low-intensity dark regions to be visibly stretched and displayed on standard monitors without being overpowered by highlight details.

---

### 📍 Problem 1.5: Intensity-Level / Gray-Level Slicing
⭐ **Formula / Rule:**
Highlighting a range of intensities $[r_1, r_2]$:

**Case 1: Without Background Preservation (Binary Slicing)**
$$s = \begin{cases} L - 1 & r_1 \le r \le r_2 \\ 0 & \text{otherwise} \end{cases}$$

**Case 2: With Background Preservation**
$$s = \begin{cases} L - 1 & r_1 \le r \le r_2 \\ r & \text{otherwise} \end{cases}$$

---

#### **Question (DIP Lab Manual 3 Reference)**
Given a 3-bit image matrix:
$$I = \begin{bmatrix} 2 & 5 & 1 \\ 3 & 4 & 6 \\ 0 & 7 & 5 \end{bmatrix}$$

Apply gray-level slicing to highlight the band $[3, 5]$:
1. Without background preservation.
2. With background preservation.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Identify the active range: $r_1 = 3$, $r_2 = 5$, and maximum level $L-1 = 7$.

#### **1. Without Background Preservation (Replace other levels with 0):**
* $2 \notin [3,5] \implies 0$
* $5 \in [3,5] \implies 7$
* $1 \notin [3,5] \implies 0$
* $3 \in [3,5] \implies 7$
* $4 \in [3,5] \implies 7$
* $6 \notin [3,5] \implies 0$
* $0 \notin [3,5] \implies 0$
* $7 \notin [3,5] \implies 0$

$$I_{\text{slice\_no\_bg}} = \begin{bmatrix} 0 & 7 & 0 \\ 7 & 7 & 0 \\ 0 & 0 & 7 \end{bmatrix}$$

#### **2. With Background Preservation (Keep other levels as $r$):**
* $2 \notin [3,5] \implies 2$ (Kept as is)
* $5 \in [3,5] \implies 7$ (Sliced)
* $1 \notin [3,5] \implies 1$ (Kept as is)
* $3 \in [3,5] \implies 7$ (Sliced)
* $4 \in [3,5] \implies 7$ (Sliced)
* $6 \notin [3,5] \implies 6$ (Kept as is)
* $0 \notin [3,5] \implies 0$ (Kept as is)
* $7 \notin [3,5] \implies 7$ (Sliced/Kept)


$$I_{\text{slice\_with\_bg}} = \begin{bmatrix} 2 & 7 & 1 \\ 7 & 7 & 6 \\ 0 & 7 & 7 \end{bmatrix}$$

---

### 📍 Problem 1.6: Basic Iterative Global Thresholding (Matrix Example)
⭐ **Formula / Rule:**
The Basic Iterative Global Thresholding algorithm segment pixels based on successive threshold updates:
1. Select an initial estimate for the global threshold, $T_0$ (typically the average intensity of the entire image).
2. Segment the image using $T_0$ into two groups:
   * $G_1$: Pixels with intensity values $> T_0$.
   * $G_2$: Pixels with intensity values $\le T_0$.
3. Compute the average (mean) intensity values $\mu_1$ and $\mu_2$ for the pixels in $G_1$ and $G_2$ respectively.
4. Compute a new threshold value midway between $\mu_1$ and $\mu_2$:
   $$T_{\text{new}} = \frac{\mu_1 + \mu_2}{2}$$
5. Repeat Steps 2 through 4 until the threshold value converges (i.e., $T_{i+1} = T_i$).

---

#### **Question (IVP UNIT 2 PPT / Classroom Example Reference)**
Consider the following $3 \times 3$ image segment of an 8-bit image:
$$I = \begin{bmatrix} 5 & 3 & 9 \\ 2 & 1 & 7 \\ 8 & 4 & 2 \end{bmatrix}$$

Calculate the optimal global threshold $T$ using the Basic Iterative Global Thresholding algorithm. Show every iteration to convergence. Round intermediate values to the nearest integer.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Initialize the threshold with the overall mean of the matrix, then iteratively partition and update until stable.

#### **Iteration 1:**
* **Step 1: Calculate Initial Threshold ($T_0$):**
    $$T_0 = \text{round}\left( \frac{5 + 3 + 9 + 2 + 1 + 7 + 8 + 4 + 2}{9} \right) = \text{round}\left( \frac{41}{9} \right) = \text{round}(4.5556) \implies \mathbf{5}$$
* **Step 2: Partition the image into $G_1$ and $G_2$ using $T_0 = 5$:**
    * $G_1$ (values $> 5$): $\{7, 8, 9\}$
    * $G_2$ (values $\le 5$): $\{1, 2, 2, 3, 4, 5\}$
* **Step 3: Compute Means $\mu_1$ and $\mu_2$:**
    $$\mu_1 = \frac{7 + 8 + 9}{3} = \frac{24}{3} = \mathbf{8}$$
    $$\mu_2 = \text{round}\left( \frac{1 + 2 + 2 + 3 + 4 + 5}{6} \right) = \text{round}\left( \frac{17}{6} \right) = \text{round}(2.8333) \implies \mathbf{3}$$
* **Step 4: Calculate New Threshold ($T_1$):**
    $$T_1 = \text{round}\left( \frac{\mu_1 + \mu_2}{2} \right) = \text{round}\left( \frac{8 + 3}{2} \right) = \text{round}(5.5) \implies \mathbf{6}$$
* Since $T_1 \neq T_0$ ($6 \neq 5$), we proceed to Iteration 2.

#### **Iteration 2:**
* **Step 2: Partition the image using $T_1 = 6$:**
    * $G_1$ (values $> 6$): $\{7, 8, 9\}$
    * $G_2$ (values $\le 6$): $\{1, 2, 2, 3, 4, 5\}$
* **Step 3: Compute Means $\mu_1$ and $\mu_2$:**
    $$\mu_1 = \frac{7 + 8 + 9}{3} = \mathbf{8}$$
    $$\mu_2 = \text{round}\left( \frac{1 + 2 + 2 + 3 + 4 + 5}{6} \right) = \mathbf{3}$$
* **Step 4: Calculate New Threshold ($T_2$):**
    $$T_2 = \text{round}\left( \frac{\mu_1 + \mu_2}{2} \right) = \text{round}\left( \frac{8 + 3}{2} \right) \implies \mathbf{6}$$
* Since $T_2 = T_1$ ($6 = 6$), the threshold has successfully converged!

✍️ **Final Exam Answer:**
The optimal global threshold for the given image segment is **`6`**.

---

### 📍 Problem 1.7: Basic Iterative Global Thresholding (Histogram Distribution)
---

#### **Question (DIP Course Lecture Slides Reference)**
A 3-bit image has the following gray-level frequency distribution:

| Gray level $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Pixel Count $n_k$** | 5 | 6 | 4 | 3 | 1 | 4 | 3 | 4 |

Using an initial threshold estimate of $T_0 = 3$, calculate the optimal global threshold. Show how the algorithm converges under both:
1. **Method A:** The simple unweighted arithmetic mean of gray level indices.
2. **Method B:** The mathematically rigorous histogram-weighted mean.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Start with $T_0 = 3$. Partition the histogram into two classes: levels $\le 3$ and levels $> 3$.

#### **1. Solving by Method A (Unweighted/Arithmetic Mean of Level Indices):**
This is the simplified method shown in standard lecture summaries:
* **Group 1 (levels $> 3$):** $\{4, 5, 6, 7\}$
    $$\mu_1 = \text{round}\left( \frac{4 + 5 + 6 + 7}{4} \right) = \text{round}(5.5) \implies \mathbf{6}$$
* **Group 2 (levels $\le 3$):** $\{0, 1, 2, 3\}$
    $$\mu_2 = \text{round}\left( \frac{0 + 1 + 2 + 3}{4} \right) = \text{round}(1.5) \implies \mathbf{2}$$
* **Update Threshold ($T_1$):**
    $$T_1 = \frac{\mu_1 + \mu_2}{2} = \frac{6 + 2}{2} = \mathbf{4}$$
* Since $T_1 \neq T_0$ ($4 \neq 3$), we repeat the process with $T_1 = 4$:
    * **Group 1 (levels $> 4$):** $\{5, 6, 7\}$
        $$\mu_1 = \text{round}\left( \frac{5 + 6 + 7}{3} \right) = \mathbf{6}$$
    * **Group 2 (levels $\le 4$):** $\{0, 1, 2, 3, 4\}$
        $$\mu_2 = \text{round}\left( \frac{0 + 1 + 2 + 3 + 4}{5} \right) = \mathbf{2}$$
    * **Update Threshold ($T_2$):**
        $$T_2 = \frac{6 + 2}{2} = \mathbf{4}$$
* Since $T_2 = T_1 = 4$, the algorithm converged. Final threshold = **`4`**.

#### **2. Solving by Method B (Histogram-Weighted Mean):**
This is the mathematically correct implementation used in Gonzalez & Woods:
* **Iteration 1 with $T_0 = 3$:**
    * $G_1$ (levels $> 3$, i.e., $4, 5, 6, 7$): Total pixels $N_1 = 1 + 4 + 3 + 4 = 12$
        $$\mu_1 = \frac{(4 \times 1) + (5 \times 4) + (6 \times 3) + (7 \times 4)}{12} = \frac{70}{12} \approx 5.8333$$
    * $G_2$ (levels $\le 3$, i.e., $0, 1, 2, 3$): Total pixels $N_2 = 5 + 6 + 4 + 3 = 18$
        $$\mu_2 = \frac{(0 \times 5) + (1 \times 6) + (2 \times 4) + (3 \times 3)}{18} = \frac{23}{18} \approx 1.2778$$
    * **Update Threshold ($T_1$):**
        $$T_1 = \text{round}\left( \frac{5.8333 + 1.2778}{2} \right) = \text{round}(3.5556) \implies \mathbf{4}$$
    * Since $T_1 \neq T_0$ ($4 \neq 3$), proceed to Iteration 2.

* **Iteration 2 with $T_1 = 4$:**
    * $G_1$ (levels $> 4$, i.e., $5, 6, 7$): Total pixels $N_1 = 4 + 3 + 4 = 11$
        $$\mu_1 = \frac{(5 \times 4) + (6 \times 3) + (7 \times 4)}{11} = \frac{66}{11} = \mathbf{6.0000}$$
    * $G_2$ (levels $\le 4$, i.e., $0, 1, 2, 3, 4$): Total pixels $N_2 = 5 + 6 + 4 + 3 + 1 = 19$
        $$\mu_2 = \frac{(0 \times 5) + (1 \times 6) + (2 \times 4) + (3 \times 3) + (4 \times 1)}{19} = \frac{27}{19} \approx 1.4211$$
    * **Update Threshold ($T_2$):**
        $$T_2 = \text{round}\left( \frac{6.0000 + 1.4211}{2} \right) = \text{round}(3.7106) \implies \mathbf{4}$$
    * Since $T_2 = T_1 = 4$, the algorithm has successfully converged!

✍️ **Final Exam Answer:**
Under both simple unweighted and rigorous weighted methods, the optimal global threshold is **`4`**.

---


## 📊 Part 2: Histogram Equalization (HE) Numericals

### 📍 Problem 2.1: Hand-Calculated Equalization on a $3 \times 3$ Matrix
⭐ **Formula / Rule:**
$$s_k = \text{round}\left( (L - 1) \cdot \sum_{j=0}^{k} p_r(r_j) \right) = \text{round}\left( (L - 1) \cdot \text{CDF}(r_k) \right)$$

---

#### **Question (Experiment 4, Task 1 - Master Student Lab Book)** [5 Marks]
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
* $5 \to 5$
* $2 \to 2$
* $6 \to 5$
* $7 \to 7$
* $3 \to 4$

✍ *Resulting Output Matrix:*
$$I_{\text{equalized}} = \begin{bmatrix} 5 & 2 & 2 \\ 5 & 7 & 4 \\ 4 & 7 & 4 \end{bmatrix}$$

---

### 📍 Problem 2.2: Equalization on a Gray-Level Distribution ($N = 60$)
---

#### **Question (NMIMS Term Exam Dec 2025 - Q2(a))** [10 Marks]
An image has the following gray levels and corresponding number of pixels:

| Gray level $r_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **No. of pixels $n_k$** | 2 | 3 | 5 | 8 | 10 | 20 | 8 | 4 |

Compute the gray level distribution using histogram equalization. Also plot the histogram of the input and output (equalized) images.

---

#### **Step-by-Step Solution**

🧠 **Approach:**
1. Sum all pixel counts to find $N$:
   $$N = 2 + 3 + 5 + 8 + 10 + 20 + 8 + 4 = 60 \text{ pixels}$$
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
* Output **`0`**: matches input $r_0 \implies n'_0 = 2$ pixels
* Output **`1`**: matches input $r_1, r_2 \implies n'_1 = 3 + 5 = 8$ pixels
* Output **`2`**: matches input $r_3 \implies n'_2 = 8$ pixels
* Output **`3`**: matches input $r_4 \implies n'_3 = 10$ pixels
* Output **`4`**: no inputs mapped here $\implies n'_4 = 0$ pixels
* Output **`5`**: no inputs mapped here $\implies n'_5 = 0$ pixels
* Output **`6`**: matches input $r_5 \implies n'_6 = 20$ pixels
* Output **`7`**: matches input $r_6, r_7 \implies n'_7 = 8 + 4 = 12$ pixels

✍️ **Final Equalized Gray Level Distribution Table:**

| Equalized level $s_k$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **New Pixel Count $n'_k$**| 2 | 8 | 8 | 10 | 0 | 0 | 20 | 12 |

*(Ensure total pixels check: $2 + 8 + 8 + 10 + 20 + 12 = 60$. Correct!)*

---

## 🎨 Part 3: Neighborhood Operations & Spatial Filter Numericals

### 📍 Problem 3.1: Laplacian Edge Sharpening (Positive Center Mask)
⭐ **Formula / Rule:**
The Laplacian filter mask having a **positive center without diagonal elements** is represented by:
$$H = \begin{bmatrix} 0 & -1 & 0 \\ -1 & 4 & -1 \\ 0 & -1 & 0 \end{bmatrix}$$

*If using a negative center mask, replace it with:*
$$H = \begin{bmatrix} 0 & 1 & 0 \\ 1 & -4 & 1 \\ 0 & 1 & 0 \end{bmatrix}$$

---

#### **Question (NMIMS TEE Dec 2025 - Q1(b))** [4 Marks]
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

### 📍 Problem 3.2: 3x3 Average (Box) Filter
⭐ **Formula / Rule:**
The standard $3 \times 3$ average box filter is defined as:
$$H = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$$

---

#### **Question (DIP Textbook / Slide Example Reference)**
Apply a $3 \times 3$ average box filter on the central pixel (value marked as 15) in the following image segment:
$$I = \begin{bmatrix} 3 & 9 & 11 & 12 \\ 7 & 15 & 8 & 8 \\ 10 & 12 & 9 & 10 \\ 1 & 0 & 11 & 2 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
The center pixel coordinate of the first $3 \times 3$ block is at location $(1, 1)$ (value 15).

#### **Calculation:**
1. Extract the $3 \times 3$ neighborhood around pixel 15:
   $$\text{Sub-matrix} = \begin{bmatrix} 3 & 9 & 11 \\ 7 & 15 & 8 \\ 10 & 12 & 9 \end{bmatrix}$$
2. Compute the average of these 9 elements:
   $$\text{Sum} = 3 + 9 + 11 + 7 + 15 + 8 + 10 + 12 + 9 = 84$$
   $$\text{Average} = \frac{84}{9} = \mathbf{9.33}$$

✍️ **Final Output Sub-Matrix:**
$$I_{\text{average}} = \begin{bmatrix} 3 & 9 & 11 & 12 \\ 7 & 9.33 & 8 & 8 \\ 10 & 12 & 9 & 10 \\ 1 & 0 & 11 & 2 \end{bmatrix}$$

---

### 📍 Problem 3.3: Weighted Average Filter
⭐ **Formula / Rule:**
A weighted average filter gives more importance to the center pixel to prevent excessive blurring of edges:
$$H = \frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$$

---

#### **Question (DIP Slides / Classroom Notebook Reference)**
Apply the $3 \times 3$ weighted average filter on the same pixel (value 15) of the previous image matrix:
$$I = \begin{bmatrix} 3 & 9 & 11 & 12 \\ 7 & 15 & 8 & 8 \\ 10 & 12 & 9 & 10 \\ 1 & 0 & 11 & 2 \end{bmatrix}$$

---

#### **Step-by-Step Solution**

🧠 **Approach:**
Multiply each element in the neighborhood sub-matrix by its corresponding kernel weight, sum them, and divide by 16.

#### **Calculation:**
$$\text{Sum} = (1 \times 3) + (2 \times 9) + (1 \times 11) + (2 \times 7) + (4 \times 15) + (2 \times 8) + (1 \times 10) + (2 \times 12) + (1 \times 9)$$
$$\text{Sum} = 3 + 18 + 11 + 14 + 60 + 16 + 10 + 24 + 9 = 165$$
$$\text{Weighted Average} = \frac{165}{16} = 10.3125 \approx \mathbf{10}$$

✍️ **Final Exam Answer:**
The convolved weighted average output at the center pixel location is **`10`**.

---

### 📍 Problem 3.4: Median Filter (Salt & Pepper Noise Removal)
⭐ **Formula / Rule:**
The Median filter is a **nonlinear order-statistics filter**. It replaces the central pixel value with the **median value** of the sorted intensity values within the neighborhood window.

---

#### **Question (NMIMS Final Exam Dec 2024 - Q1(a))** [5 Marks]
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

## 📝 Part 4: Quick Reference Formula Sheet

### **1. Gray Level Point Transformations**
* **Image Negation:** $s = (L - 1) - r$
* **Binarization / Thresholding:**
    $$s = \begin{cases} L - 1 & r \ge T \\ 0 & \text{otherwise} \end{cases}$$
* **Logarithmic Transform:** $s = c \cdot \log(1 + r)$
* **Power-Law / Gamma Transform:** $s = c \cdot r^{\gamma}$

### **2. Piecewise Linear Contrast Stretching Slopes**
* **Slope 1 (Shadows):** $\alpha = \frac{s_1}{r_1}$
* **Slope 2 (Mid-tones):** $\beta = \frac{s_2 - s_1}{r_2 - r_1}$
* **Slope 3 (Highlights):** $\gamma = \frac{(L - 1) - s_2}{(L - 1) - r_2}$

### **3. Discrete Histogram Equalization**
* **Probability Density Function (PDF):**
    $$p_r(r_k) = \frac{n_k}{N}$$
* **Cumulative Distribution Function (CDF):**
    $$\text{CDF}(r_k) = \sum_{j=0}^{k} p_r(r_j)$$
* **HE Mapping equation:**
    $$s_k = \text{round}\left( (L - 1) \cdot \text{CDF}(r_k) \right)$$

### **4. Neighborhood Operators & Filters**
* **3x3 Average Mask:** $\frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$
* **3x3 Weighted Average Mask:** $\frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$
* **Isotropic Sharpening Laplacian Mask:** $\begin{bmatrix} 0 & -1 & 0 \\ -1 & 4 & -1 \\ 0 & -1 & 0 \end{bmatrix}$

---

## 🏁 Final Numerical Coverage Checklist

Below is the verification checklist mapping every syllabus concept to its solved problem in this workbook:

* [x] **Digital Negatives** — Solved in **Problem 1.1**.
* [x] **Piecewise Contrast Stretching** — Solved in **Problem 1.2**.
* [x] **Power-Law Gamma Transforms** — Solved in **Problem 1.3**.
* [x] **Log Transformations** — Solved in **Problem 1.4**.
* [x] **Intensity-Level Slicing** — Solved in **Problem 1.5**.
* [x] **Histogram Equalization Matrix Problems** — Solved in **Problem 2.1**.
* [x] **Grayscale Count Vector Equalizations** — Solved in **Problem 2.2**.
* [x] **Laplacian Filtering** — Solved in **Problem 3.1**.
* [x] **Averaging Smoothing Filtering** — Solved in **Problem 3.2**.
* [x] **Weighted Average Filtering** — Solved in **Problem 3.3**.
* [x] **Basic Iterative Global Thresholding** — Solved in **Problem 1.6 & 1.7**.
* [x] **Nonlinear Median Filtering** — Solved in **Problem 3.4**.
