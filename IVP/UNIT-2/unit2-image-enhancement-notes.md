# Unit 2: Image Enhancement (Spatial Domain) - Complete Study Notes
**Course:** Image and Video Processing (IVP)  
**Level:** SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC)  

**Primary Source:** `IVP UNIT 2.pptx` (and official course policy documents)  
**Syllabus Covered:**
1. **Point Processing Operations**: Digital Negative/Complement, Contrast Stretching, Global Thresholding, Intensity-Level Slicing, Logarithmic Transformation, Power-Law (Gamma) Transformation.
2. **Histogram Processing**: Histogram Equalization (HE), HE Algorithm/Procedure, and Solved Numericals.
3. **Neighborhood Operations / Spatial Filters**: Low-Pass Filtering (Average Filter, Weighted Average Filter), Median Filter, Sharpening Filters (Laplacian/High-Pass), Gaussian Filtering.

---

## 📖 SECTION 1: Introduction to Spatial Domain Image Enhancement

### 1. What is Spatial Domain Image Enhancement?
*   **Definition:** Image enhancement refers to the process of manipulating a digital image so that the result is more suitable than the original image for a specific application [316]. The term **"Spatial Domain"** denotes the physical 2-D pixel grid of the image [315].
*   **Mathematical Model:** Spatial domain processing operates directly on the pixels of an image [37]. It is represented mathematically by the general expression:
    $g(x, y) = T[f(x, y)]$ [175]
    where:
    *   $f(x, y)$ is the input image [6].
    *   $g(x, y)$ is the processed output image [175].
    *   $T$ is an operator or transformation function defined over a specified neighborhood of coordinate $(x, y)$ [175].

### 2. Point Processing vs. Neighborhood Processing
*   **Point Processing (Pixel-by-Pixel):** The neighborhood around pixel $(x, y)$ has a size of $1 \times 1$ [83]. The output intensity $s$ at any coordinate depends *only* on the input intensity $r$ at that exact coordinate [83].
    *   *Equation:* $s = T(r)$ [83, 175]
*   **Neighborhood Processing (Filtering):** The neighborhood is larger (e.g., $3 \times 3$ or $5 \times 5$) [84]. The output intensity $g(x, y)$ is computed based on both the center pixel and its surrounding neighbors [84].

⭐ **Must Remember:** Enhancement is a **subjective process** [53]. There is no general "universal" theory of image enhancement [316]. What is "good" enhancement for a medical radiologist (highlighting bones) might be "poor" enhancement for a computer vision navigation system [294].

---

## 📐 SECTION 2: Point Processing Operations

Point operations map an input intensity level $r$ to an output intensity level $s$ [83]. For an 8-bit image, intensity levels range from $[0, L-1]$ where $L = 2^8 = 256$ [41, 79].

### 1. Digital Negative / Complement
*   **Basic Concept:** Reverses the gray-level values of an image to produce the digital equivalent of a photographic negative [117, 159].
*   **Mathematical Formula:**
    $s = (L - 1) - r$ [66]
*   **Input vs. Output Mapping Graph:**

    ```text
        Output s
          ▲
      L-1 █      │ ╲
          │   ╲
          │     ╲
          │       ╲
        0 └────────██► Input r
          0        L-1
    ```
*   **Applications:** Perfect for highlighting white or gray details embedded in dominant dark areas of an image (e.g., mammograms, medical chest X-rays) [74, 117].

✍️ **Exam Numerical Example (Q2a, Re-Exam):**
> *Question:* Describe the process to obtain an image negative. Apply this process to the $5 \times 5$ image matrix below assuming 3 BPP (bits per pixel) depth:
> $$A = \begin{bmatrix} 1 & 2 & 2 & 2 & 2 \\ 3 & 2 & 4 & 5 & 2 \\ 7 & 7 & 7 & 7 & 6 \\ 2 & 2 & 2 & 3 & 3 \\ 4 & 4 & 4 & 4 & 4 \end{bmatrix}$$
*   **Step 1: Identify Parameters:**
    *   Bit depth $b = 3 \implies$ Total levels $L = 2^3 = 8$ levels.
    *   Maximum level $L - 1 = 7$.
*   **Step 2: Apply Formula:** $s = 7 - r$.
*   **Step 3: Calculate output cell-by-cell:**
    *   Row 1: $[7-1, 7-2, 7-2, 7-2, 7-2] \rightarrow [6, 5, 5, 5, 5]$
    *   Row 2: $[7-3, 7-2, 7-4, 7-5, 7-2] \rightarrow [4, 5, 3, 2, 5]$
    *   Row 3: $[7-7, 7-7, 7-7, 7-7, 7-6] \rightarrow [0, 0, 0, 0, 1]$
    *   Row 4: $[7-2, 7-2, 7-2, 7-3, 7-3] \rightarrow [5, 5, 5, 4, 4]$
    *   Row 5: $[7-4, 7-4, 7-4, 7-4, 7-4] \rightarrow [3, 3, 3, 3, 3]$
*   **Resultant Matrix:**
    $$A_{\text{neg}} = \begin{bmatrix} 6 & 5 & 5 & 5 & 5 \\ 4 & 5 & 3 & 2 & 5 \\ 0 & 0 & 0 & 0 & 1 \\ 5 & 5 & 5 & 4 & 4 \\ 3 & 3 & 3 & 3 & 3 \end{bmatrix}$$

---

### 2. Contrast Stretching
*   **Basic Concept:** Low-contrast images result from poor illumination, lack of sensor dynamic range, or wrong lens aperture settings [48, 122]. Contrast stretching maps a narrow range of input intensities to a wider, fuller output dynamic range [122].
*   **Mathematical Formula (Piecewise Linear):**
    $$s = \begin{cases} \alpha \cdot r & 0 \le r < r_1 \\ \beta \cdot (r - r_1) + s_1 & r_1 \le r < r_2 \\ \gamma \cdot (r - r_2) + s_2 & r_2 \le r \le L-1 \end{cases} \quad \text{[281]}$$
    Where slopes in the respective regions are calculated as:
    $\alpha = \frac{s_1}{r_1}, \quad \beta = \frac{s_2 - s_1}{r_2 - r_1}, \quad \gamma = \frac{(L-1) - s_2}{(L-1) - r_2}$ [281]

🧠 **Must Understand (Slope Influence on Contrast):**
*   If **Slope $> 1$** (typically region $\beta$): The intensity range is **stretched** (contrast is increased) [49].
*   If **Slope $< 1$** (regions $\alpha$ and $\gamma$): The intensity range is **compressed** [49].
*   If **Slope $= 1$**: Represents the identity transformation; no change occurs [48, 103].

✍️ **Exam Numerical Example (Class Notes/PPT):**
> *Question:* Apply piecewise linear contrast stretching on the given 3-bit image matrix $A$ below. Consider control points $(r_1, s_1) = (3, 2)$ and $(r_2, s_2) = (5, 6)$ on a standard 3-bit scale ($L-1 = 7$):
> $$A = \begin{bmatrix} 4 & 3 & 5 & 2 \\ 3 & 6 & 4 & 6 \\ 2 & 2 & 6 & 5 \\ 7 & 6 & 4 & 1 \end{bmatrix}$$
*   **Step 1: Compute Slopes:**
    *   $\alpha = \frac{s_1}{r_1} = \frac{2}{3} \approx 0.67$
    *   $\beta = \frac{s_2 - s_1}{r_2 - r_1} = \frac{6-2}{5-3} = \frac{4}{2} = 2.0$
    *   $\gamma = \frac{(L-1) - s_2}{(L-1) - r_2} = \frac{7-6}{7-5} = \frac{1}{2} = 0.5$
*   **Step 2: Construct Piecewise Equations:**
    $$s = \begin{cases} 0.67 \cdot r & 0 \le r < 3 \\ 2 \cdot (r - 3) + 2 = 2r - 4 & 3 \le r < 5 \\ 0.5 \cdot (r - 5) + 6 = 0.5r + 3.5 & 5 \le r \le 7 \end{cases}$$
*   **Step 3: Map Input Levels to Outputs (Rounding to Integers):**
    *   $r = 0 \implies s = 0.67 \times 0 = 0$
    *   $r = 1 \implies s = 0.67 \times 1 = 0.67 \approx 1$
    *   $r = 2 \implies s = 0.67 \times 2 = 1.34 \approx 1$
    *   $r = 3 \implies s = 2(3) - 4 = 2$
    *   $r = 4 \implies s = 2(4) - 4 = 4$
    *   $r = 5 \implies s = 0.5(5) + 3.5 = 6$
    *   $r = 6 \implies s = 0.5(6) + 3.5 = 6.5 \approx 7$
    *   $r = 7 \implies s = 0.5(7) + 3.5 = 7$
*   **Step 4: Map Matrix Elements:**
    Replace input values in $A$ with equalized $s$ mapped values:
    $$A_{\text{stretched}} = \begin{bmatrix} 4 & 2 & 6 & 1 \\ 2 & 7 & 4 & 7 \\ 1 & 1 & 7 & 6 \\ 7 & 7 & 4 & 1 \end{bmatrix}$$

---

### 3. Global Thresholding
*   **Basic Concept:** Segmenting an image into distinct foreground and background classes [19].
*   **Formula:**
    $$s = \begin{cases} L-1 & \text{if } r > T \\ 0 & \text{if } r \le T \end{cases} \quad \text{[94, 290]}$$
*   **Iterative Auto-Threshold Estimation Algorithm:**
    1. Select an initial estimate for threshold $T$ (usually the average pixel intensity of the image) [95, 265].
    2. Segment the image using $T$ to produce two classes of pixels: $G_1$ (pixels $> T$) and $G_2$ (pixels $\le T$) [95, 96, 265].
    3. Compute mean intensities $\mu_1$ and $\mu_2$ for $G_1$ and $G_2$ respectively [96, 265].
    4. Compute a new threshold $T_{\text{new}} = \frac{\mu_1 + \mu_2}{2}$ [96, 270].
    5. Repeat Steps 2-4 until successive iterations yield the same threshold value [96, 271].

✍| **Exam Numerical Example (Class Notes/PPT):**
> *Question:* Estimate the final global threshold $T$ iteratively and segment the following $3 \times 3$ image matrix:
> $$f(x, y) = \begin{bmatrix} 5 & 3 & 9 \\ 2 & 1 & 7 \\ 8 & 4 & 2 \end{bmatrix}$$
*   **Iteration 1:**
    *   Compute initial $T_0$ (average):
        $$T_0 = \frac{5+3+9+2+1+7+8+4+2}{9} = \frac{41}{9} \approx 4.56 \rightarrow \mathbf{5}$$
    *   Segment using $T_0 = 5$:
        *   $G_1$ (pixels $> 5$) = $\{7, 8, 9\}$
        *   $G_2$ (pixels $\le 5$) = $\{1, 2, 2, 3, 4, 5\}$
    *   Compute class means:
        *   $\mu_1 = \frac{7+8+9}{3} = \frac{24}{3} = 8$
        *   $\mu_2 = \frac{1+2+2+3+4+5}{6} = \frac{17}{6} \approx 2.83 \rightarrow \mathbf{3}$
    *   Update threshold:
        $$T_1 = \frac{\mu_1 + \mu_2}{2} = \frac{8 + 3}{2} = 5.5 \rightarrow \mathbf{6}$$
*   **Iteration 2 (Using $T_1 = 6$):**
    *   Segment using $T = 6$:
        *   $G_1$ (pixels $> 6$) = $\{7, 8, 9\}$
        *   $G_2$ (pixels $\le 6$) = $\{1, 2, 2, 3, 4, 5\}$
    *   Since groups remain identical to Iteration 1, the means remain $\mu_1 = 8$ and $\mu_2 = 3$.
    *   Therefore, $T_2 = 6$. Since $T_2 = T_1$, the algorithm **terminates**.
*   **Final Output Segmented Image:**
    $$g(x, y) = \begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & 1 \\ 1 & 0 & 0 \end{bmatrix}$$

---

### 4. Intensity-Level Slicing / Gray-Level Slicing
*   **Basic Concept:** Highlights a specific band of intensity levels $[a, b]$ of interest while either discarding or preserving other levels [90, 123].
*   **Two Approaches:**
    1.  **Without Background Preservation:** Discards all other levels (they become 0), producing a strictly binary mask of the highlighted region [90, 123].
        $$s = \begin{cases} L-1 & \text{if } a \le r \le b \\ 0 & \text{otherwise} \end{cases} \quad \text{[64, 275]}$$
    2.  **With Background Preservation:** Preserves background grayscale details untouched while highlighting the target band as solid white [90, 123].
        $$s = \begin{cases} L-1 & \text{if } a \le r \le b \\ r & \text{otherwise} \end{cases} \quad \text{[198, 275]}$$

✍️ **Exam Numerical Example (Class Notes/PPT):**
> *Question:* Perform gray level slicing on the 3-bit image matrix $A$ such that we highlight pixels with intensity in the range 40% to 70% of maximum possible intensity:
> $$A = \begin{bmatrix} 0 & 3 & 2 & 6 & 4 \\ 6 & 3 & 4 & 5 & 2 \\ 5 & 3 & 2 & 1 & 2 \\ 4 & 2 & 3 & 6 & 5 \\ 5 & 3 & 6 & 4 & 5 \end{bmatrix}$$
*   **Step 1: Compute Highlight Range:**
    *   Max possible value for 3-bit image scale is $L-1 = 7$.
    *   Lower limit $a = 0.4 \times 7 = 2.8 \rightarrow \mathbf{3}$
    *   Upper limit $b = 0.7 \times 7 = 4.9 \rightarrow \mathbf{4}$
    *   Target band of interest: $r \in \{3, 4\}$ [255].
*   **Step 2: Slicing Without Background (all non-target become 0, targets become 7):**
    $$A_{\text{without}} = \begin{bmatrix} 0 & 7 & 0 & 0 & 7 \\ 0 & 7 & 7 & 0 & 0 \\ 0 & 7 & 0 & 0 & 0 \\ 7 & 0 & 7 & 0 & 0 \\ 0 & 7 & 0 & 7 & 0 \end{bmatrix}$$
*   **Step 3: Slicing With Background (non-targets keep original value, targets become 7):**
    $$A_{\text{with}} = \begin{bmatrix} 0 & 7 & 2 & 6 & 7 \\ 6 & 7 & 7 & 5 & 2 \\ 5 & 7 & 2 & 1 & 2 \\ 7 & 2 & 7 & 6 & 5 \\ 5 & 7 & 6 & 7 & 5 \end{bmatrix}$$

---

### 5. Logarithmic Transformation
*   **Basic Concept:** Compresses the dynamic range of an image by mapping a narrow range of low-intensity dark values into a wider range of output levels, while compressing high-intensity bright levels [85, 118, 177].
*   **Mathematical Formula:**
    $s = c \log_{10}(1 + r)$ [41, 65, 256]
*   **Dynamic Scaling Factor ($c$):**
    $c = \frac{L-1}{\log_{10}(1 + (L-1))}$ [277]

🧠 **Must Understand:** We add **$1$** to input $r$ because $\log(0)$ is mathematically undefined (approaching negative infinity) [7, 41, 176]. Adding 1 ensures that a black pixel ($r=0$) maps cleanly to $\log(1) = 0$ [7, 176].

✍️ **Exam Numerical Example (Class Notes/PPT):**
> *Question:* Perform logarithmic transformation on the 3-bit image matrix $A$ using multiplier constant $c = 8$:
> $$A = \begin{bmatrix} 2 & 3 & 0 & 6 & 7 \\ 0 & 3 & 7 & 5 & 2 \\ 5 & 3 & 2 & 4 & 0 \\ 4 & 2 & 2 & 1 & 0 \\ 1 & 7 & 6 & 4 & 5 \end{bmatrix}$$
*   **Step 1: Map Intensity Levels (rounding to nearest integers):**
    *   $r = 0 \implies s = 8 \log_{10}(1) = 0$
    *   $r = 1 \implies s = 8 \log_{10}(2) \approx 2.41 \rightarrow \mathbf{2}$
    *   $r = 2 \implies s = 8 \log_{10}(3) \approx 3.82 \rightarrow \mathbf{4}$
    *   $r = 3 \implies s = 8 \log_{10}(4) \approx 4.82 \rightarrow \mathbf{5}$
    *   $r = 4 \implies s = 8 \log_{10}(5) \approx 5.59 \rightarrow \mathbf{6}$
    *   $r = 5 \implies s = 8 \log_{10}(6) \approx 6.22 \rightarrow \mathbf{6}$
    *   $r = 6 \implies s = 8 \log_{10}(7) \approx 6.76 \rightarrow \mathbf{7}$
    *   $r = 7 \implies s = 8 \log_{10}(8) \approx 7.23 \rightarrow \mathbf{7}$
*   **Step 2: Replace values in Matrix:**
    $$A_{\text{log}} = \begin{bmatrix} 4 & 5 & 0 & 7 & 7 \\ 0 & 5 & 7 & 6 & 4 \\ 6 & 5 & 4 & 6 & 0 \\ 6 & 4 & 4 & 2 & 0 \\ 2 & 7 & 7 & 6 & 6 \end{bmatrix}$$

---

### 6. Power-Law / Gamma Transformation
*   **Basic Concept:** Also known as **Gamma Correction** [13, 201]. It is used for display calibration and image correction because most camera sensors, CRT displays, and printers have a non-linear power-law response to luminance [87, 102].
*   **Mathematical Formula:**
    $s = c \cdot r^{\gamma}$ [43, 65, 231]
*   **Fractional Gamma ($\gamma < 1$):** Behaves like a log transform—brightens the dark shadow regions and expands dynamic contrast [44, 46].
*   **Integer Gamma ($\gamma > 1$):** Maps bright highlight levels into a wider dynamic range, darkening the image [45, 46].

✍️ **Exam Numerical Example (Class Notes/PPT):**
> *Question:* Apply power law transformation with $c = 3$ and square root ($\gamma = 0.5$) on the 3-bit image matrix $A$:
> $$A = \begin{bmatrix} 2 & 3 & 0 & 6 & 7 \\ 0 & 3 & 7 & 5 & 2 \\ 5 & 3 & 2 & 4 & 0 \\ 4 & 2 & 2 & 1 & 0 \\ 1 & 7 & 6 & 4 & 5 \end{bmatrix}$$
*   **Step 1: Compute mappings ($s = 3 \cdot \sqrt{r}$, capped at max level 7):**
    *   $r = 0 \implies s = 3 \cdot \sqrt{0} = 0$
    *   $r = 1 \implies s = 3 \cdot \sqrt{1} = 3$
    *   $r = 2 \implies s = 3 \cdot \sqrt{2} \approx 4.24 \rightarrow \mathbf{4}$
    *   $r = 3 \implies s = 3 \cdot \sqrt{3} \approx 5.20 \rightarrow \mathbf{5}$
    *   $r = 4 \implies s = 3 \cdot \sqrt{4} = 6 \rightarrow \mathbf{6}$
    *   $r = 5 \implies s = 3 \cdot \sqrt{5} \approx 6.71 \rightarrow \mathbf{7}$
    *   $r = 6 \implies s = 3 \cdot \sqrt{6} \approx 7.35 \rightarrow 7$ (capped at 7)
    *   $r = 7 \implies s = 3 \cdot \sqrt{7} \approx 7.94 \rightarrow 7$ (capped at 7)
*   **Step 2: Replace values in Matrix:**
    $$A_{\text{gamma}} = \begin{bmatrix} 4 & 5 & 0 & 7 & 7 \\ 0 & 5 & 7 & 7 & 4 \\ 7 & 5 & 4 & 6 & 0 \\ 6 & 4 & 4 & 3 & 0 \\ 3 & 7 & 7 & 6 & 7 \end{bmatrix}$$

---

## 📊 SECTION 3: Histogram Processing

### 1. What is an Image Histogram?
A histogram represents the frequency of occurrence of each gray level in an image [182]. For an image with gray levels in range $[0, L-1]$, the histogram is defined as:
$$h(r_k) = n_k$$
where:
*   $r_k$ is the $k$-th gray level [182].
*   $n_k$ is the number of pixels having intensity $r_k$ [182].

### 2. Histogram Equalization (HE)
*   **Basic Concept:** A technique that spreads out the most frequent intensity levels to achieve a flatter, more uniform histogram, thereby improving global image contrast [182].
*   **Transformation Function:**
    $$s_k = T(r_k) = (L - 1) \cdot \sum_{j=0}^{k} p_r(r_j) = (L - 1) \cdot \text{CDF}(r_k)$$
    where:
    *   $p_r(r_j) = \frac{n_j}{N}$ is the Probability Density Function (PDF) [182].
    *   $N$ is the total number of pixels in the image [182].
    *   $\text{CDF}(r_k)$ is the Cumulative Distribution Function [182].

---

### 3. Solved Numerical Problem (Task 1, Lab Manual)
> *Question:* Apply histogram equalization on the given 3-bit ($L = 8$) image matrix:
> $$f(x, y) = \begin{bmatrix} 5 & 2 & 2 \\ 6 & 7 & 3 \\ 3 & 7 & 3 \end{bmatrix}$$
*   **Step A: Extract Parameters:**
    *   Total pixels $N = 3 \times 3 = 9$ pixels.
    *   Number of gray levels $L = 8$, so $L-1 = 7$.
*   **Step B: Construct PDF, CDF and Mapping Table:**

| Level ($r_k$) | Count ($n_k$) | PDF ($p_r(r_k) = n_k/9$) | CDF | $7 \times \text{CDF}$ | Rounded Level ($s_k$) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| **0** | 0 | $0.0000$ | 0.0000 | 0.0000 | **0** |
| **1** | 0 | $0.0000$ | 0.0000 | 0.0000 | **0** |
| **2** | 2 | $2/9 = 0.2222$ | 0.2222 | 1.5556 | **2** |
| **3** | 3 | $3/9 = 0.3333$ | 0.5556 | 3.8889 | **4** |
| **4** | 0 | $0.0000$ | 0.5556 | 3.8889 | **4** |
| **5** | 1 | $1/9 = 0.1111$ | 0.6667 | 4.6667 | **5** |
| **6** | 1 | $1/9 = 0.1111$ | 0.7778 | 5.4444 | **5** |
| **7** | 2 | $2/9 = 0.2222$ | 1.0000 | 7.0000 | **7** |

*   **Step C: Map the original pixels to equalized values:**
    *   $2 \rightarrow 2$
    *   $3 \rightarrow 4$
    *   $5 \rightarrow 5$
    *   $6 \rightarrow 5$
    *   $7 \rightarrow 7$
*   **Step D: Construct Equalized Output Matrix:**
    $$g(x, y) = \begin{bmatrix} 5 & 2 & 2 \\ 5 & 7 & 4 \\ 4 & 7 & 4 \end{bmatrix}$$

---

## 🛡️ SECTION 4: Neighborhood Processing & Spatial Filters

Neighborhood operations (filtering) modify the intensity of a pixel based on the intensities of surrounding pixels inside a small local sub-grid (often $3 \times 3$ or $5 \times 5$) [84].

```
       3x3 Neighborhood
      ┌───┬───┬───┐
      │w1 │w2 │w3 │
      ├───┼───┼───┤
      │w4 │w5 │w6 │   ◄─── Mask / Kernel Coefficients
      ├───┼───┼───┤
      │w7 │w8 │w9 │
      └───┴───┴───┘

```

### 1. Mechanics of Neighborhood Processing (Spatial Convolution)
The filtered value at center pixel is computed by multiplying mask coefficients with underlying pixel values, and summing them up:
$$g(x, y) = \sum_{s=-a}^{a} \sum_{t=-b}^{b} w(s, t) \cdot f(x+s, y+t)$$

---

### 2. Low-Pass Filtering (Smoothing Filters)
*   **Basic Concept:** Eliminates high-frequency noise and details, resulting in a blurred or smoothed image [174].
*   **Types of Smoothing Filters:**
    1.  **Standard Average (Box) Filter:** Replaces each pixel value with the simple average of its neighborhood [174]. It treats all neighbors with equal weight [174].
        $$\text{Box Mask (3x3)} = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$$
    2.  **Weighted Average Filter:** Replaces pixel values with a weighted average [174]. Center pixels are weighted more heavily because they are closer to the spatial origin of convolution [174].
        $$\text{Weighted Mask (3x3)} = \frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$$
    3.  **Gaussian Filtering:** The mask coefficients are sampled from a continuous 2-D Gaussian distribution:
        $$h(x, y) = e^{-\frac{x^2 + y^2}{2\sigma^2}}$$
        *Properties:* Provides mathematically optimal scale-space representation, eliminating high-frequency noise without creating jagged ring artifacts.

---

### 3. Median Filter (Non-linear Order-Statistic Filter)
*   **Basic Concept:** Replaces the center pixel value with the mathematical **median** of all pixel intensities in its neighborhood [308, 310].
*   **How it Works:**
    1. Extract all pixel intensities inside the neighborhood window [308].
    2. Sort them in ascending order [308].
    3. Choose the middle value (the median) and assign it to the center pixel [308].
*   **Applications:** Outstanding for removing **Salt and Pepper noise** (impulsive binary noise) while preserving sharp image edge boundaries [308, 310].

---

### 4. Sharpening Filters (High-Pass / Derivatives)
*   **Basic Concept:** Highlights transitions in intensity levels, enhancing edges and fine structural details [174].
*   **The Laplacian Operator:** A 2-D second-order isotropic derivative operator [116].
    $$\text{Standard Laplacian Mask} = \begin{bmatrix} 0 & 1 & 0 \\ 1 & -4 & 1 \\ 0 & 1 & 0 \end{bmatrix} \quad \text{or} \quad \begin{bmatrix} 1 & 1 & 1 \\ 1 & -8 & 1 \\ 1 & 1 & 1 \end{bmatrix}$$

---

### 5. Step-by-Step Filtering Numerical (LMS Notes)
> *Question:* Given the grayscale image segment below, apply a $3 \times 3$ mask for the following operations on the inner pixels. Ignore rows and columns at the extreme edges [256].
> $$I = \begin{bmatrix} 10 & 20 & 30 & 40 \\ 40 & 30 & 20 & 10 \\ 10 & 20 & 30 & 40 \\ 40 & 30 & 20 & 10 \end{bmatrix}$$
*   **Step A: Identify inner pixels to process:**
    Because we ignore boundary rows and columns, calculations are only done for:
    *   Pixel at $(2, 2)$ [value = $30$]
    *   Pixel at $(2, 3)$ [value = $20$]
    *   Pixel at $(3, 2)$ [value = $20$]
    *   Pixel at $(3, 3)$ [value = $30$]
*   **Step B: Compute Average Filter at Pixel $(2,2)$:**
    *   Extract $3\times 3$ Neighborhood:
        $$\begin{bmatrix} 10 & 20 & 30 \\ 40 & 30 & 20 \\ 10 & 20 & 30 \end{bmatrix}$$
    *   Calculate Average:
        $$g(2,2) = \frac{10+20+30+40+30+20+10+20+30}{9} = \frac{210}{9} \approx \mathbf{23.33}$$
*   **Step C: Compute Weighted Average Filter at Pixel $(2,2)$ (using standard $[1,2,1; 2,4,2; 1,2,1]/16$ mask):**
    $$g(2,2) = \frac{10(1) + 20(2) + 30(1) + 40(2) + 30(4) + 20(2) + 10(1) + 20(2) + 30(1)}{16}$$
    $$g(2,2) = \frac{10 + 40 + 30 + 80 + 120 + 40 + 10 + 40 + 30}{16} = \frac{400}{16} = \mathbf{25}$$
*   **Step D: Compute Median Filter at Pixel $(2,2)$:**
    *   Extract Neighborhood elements: $\{10, 20, 30, 40, 30, 20, 10, 20, 30\}$.
    *   Sort in ascending order: `[10, 10, 20, 20, 20, 30, 30, 30, 40]`.
    *   Find the 5th (middle) value: **20**.
    *   Output: **20**.
*   **Step E: Compute Laplacian Filter at Pixel $(2,2)$ (using center-negative mask $[0,1,0; 1,-4,1; 0,1,0]$):**
    $$g(2,2) = 20(1) + 40(1) + 20(1) + 20(1) + 30(-4) = 20+40+20+20-120 = \mathbf{-20}$$
    *(Note: Using standard subtraction mapping $s = f(x,y) - \nabla^2 f(x,y)$ scales contrast enhancement).*

---

## 📝 SECTION 5: QUICK REVISION SHEET

### 1. Point Processing Formula Directory
*   **Digital Negative:** $s = (L - 1) - r$ [66]
*   **Piecewise Linear Slopes:**
    $\alpha = \frac{s_1}{r_1}, \quad \beta = \frac{s_2 - s_1}{r_2 - r_1}, \quad \gamma = \frac{(L-1) - s_2}{(L-1) - r_2}$ [281]
*   **Log Transform:** $s = c \log_{10}(1 + r)$ [41, 65, 256]
*   **Power-Law Transform:** $s = c \cdot r^{\gamma}$ [43, 65, 231]
*   **Histogram Equalization:** $s_k = (L - 1) \cdot \sum_{j=0}^{k} \frac{n_j}{N}$

---

### 2. High-Priority Comparisons

#### **Logarithmic vs. Inverse Logarithmic (Exponential) Transformations**

| Feature | Logarithmic Transform | Inverse Logarithmic (Exponential) |
| :--- | :--- | :--- |
| **Mathematical Formula** | $s = c \log(1+r)$ [41] | $s = c [(1+a)^r - 1]$ [11] |
| **Expansion Region** | Expands **low gray levels (dark shadows)** [118]. | Expands **high gray levels (bright highlights)** [10]. |
| **Compression Region** | Compresses **high gray levels (bright regions)** [118]. | Compresses **low gray levels (dark regions)** [10]. |
| **Primary Application** | Compressing wide range Fourier spectrum displays [76]. | Visual enhancement of overly bright scenes [10]. |

---

#### **Spatial Average Filter vs. Median Filter**

| Feature | Spatial Average (Box) Filter | Median Filter |
| :--- | :--- | :--- |
| **Mathematical Type** | Linear operator (weighted sum) | Non-linear operator (sorting-based) |
| **Primary Purpose** | Gaussian noise smoothing / general blurring | Salt and Pepper impulsive noise removal |
| **Edge Fidelity** | Blurs sharp edge boundaries noticeably | Preserves high-frequency edge transitions cleanly |

---

## 🏁 SYLLABUS & PPT COVERAGE CHECKLIST (`IVP UNIT 2.pptx`)

Every syllabus topic and practical homework calculation listed in the authoritative slide deck is documented and solved completely:

*   [x] **Topic 2.1: Digital Negative Transformation** — Handled in Section 2, Question 2a solved [117].
*   [x] **Topic 2.2: Contrast Stretching** — Handled in Section 2, complete piecewise slope equations and matrix mapping solved.
*   [x] **Topic 2.3: Global Thresholding** — Handled in Section 2, complete iterative algorithm and 3x3 matrix segmentation solved.
*   [x] **Topic 2.4: Intensity-Level Slicing** — Handled in Section 2, complete 3-bit range highlight calculations solved [255].
*   [x] **Topic 2.5: Logarithmic Transformation** — Handled in Section 2, dynamic multiplier calculations solved.
*   [x] **Topic 2.6: Power-Law Transformation** — Handled in Section 2, fractional root calculations solved.
*   [x] **Topic 2.7: Histogram Equalization Algorithm** — Handled in Section 3, manual probability CDF tracking solved [182].
*   [x] **Topic 2.8: Spatial Average / Weighted Filters** — Handled in Section 4, inner grid averaging mask operations solved [256].
*   [x] **Topic 2.9: Median / Laplacian Filtering** — Handled in Section 4, sorted list array median retrieval solved [308, 310].
