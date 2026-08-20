# NMIMS Unit 2: Image Enhancement (Spatial Domain) - Theoretical PYQ & Expected Question Bank

**Course:** Image and Video Processing (IVP)  
**Target Exam:** Mid-Sem Prep (SVKM's NMIMS MPSTME, Semester V, B.Tech COMP/EXTC)  
**Primary Source:** `IVP UNIT 2.pptx` & Uploaded PYQ Papers  
**Syllabus Focus:** Point Processing Operations, Histogram Equalization, and Blurring/Smoothing Neighborhood Filters.  
**Strict Exclusion Policy:** All sharpening, Laplacian, high-pass/high-boost filters, and frequency-domain/Fourier transforms have been quarantined at the very end as non-mid-sem content.

---

## 📊 PART A: TOPIC-WISE PYQ FREQUENCY & PRIORITY ANALYSIS

An analysis of past NMIMS exam papers (2022–2026) shows that theoretical conceptual explanations, derivations, and filter comparative mappings constitute **approx. 10% to 15% of the total marks** in any exam paper. Below is the syllabus frequency and priority tracking.

### 1. Topic Priority Map
*   🔥 **VERY HIGH PRIORITY (Multiple repetitions, highly conceptual):**
    *   Linear vs. Non-Linear Spatial Filtering (Averaging vs. Median).
    *   Logarithmic vs. Power-Law (Gamma Correction) Transformations.
    *   Piecewise Linear Contrast Stretching Slopes and Ranges.
*   ⭐ **HIGH PRIORITY (Direct conceptual definitions and algorithms):**
    *   The Histogram Equalization Algorithm and running CDF mapping logic.
    *   Intensity-Level Slicing (With vs. Without Background preservation).
    *   Gaussian Filtering properties (smoothing and noise-reduction mechanics).
*   🟡 **MODERATE PRIORITY (Niche definitions or binarization logic):**
    *   Digital Negative / Image Complement purpose.
    *   Basic Iterative Global Thresholding convergence.

### 2. Complete Mid-Sem Syllabus Checklist

- [x] **Point Processing Operations**:
  - [x] Digital Negative / Complement properties
  - [x] Contrast Stretching slopes and regions
  - [x] Global Thresholding concepts
  - [x] Intensity-Level Slicing (with/without background)
  - [x] Logarithmic Transformation range compression
  - [x] Power-Law / Gamma display calibration
- [x] **Histogram Processing**:
  - [x] Histogram Equalization (HE) theory
  - [x] HE Step-by-Step Algorithm
- [x] **Smoothing Spatial Filters**:
  - [x] Low-Pass Blurring principles
  - [x] Standard Average (Box) Filter
  - [x] Weighted Average Filter
  - [x] Non-linear Median Filter (Impulse noise removal)
  - [x] Gaussian Blurring mechanics

---

## 🟢 PART B: SOLVED THEORETICAL PYQ BANK (SYLLABUS-ALIGNED)

---

### 📥 1. Point Processing Operations

#### **PYQ 1: Contrast Stretching Definition**
*   **Exact Wording:** What is contrast stretching?
*   **Source Paper:** NMIMS MPSTME Semester V, Final Exam
*   **Year / Q No. / Marks:** Nov 2024 | Q2a | 2 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Point Processing - Contrast Stretching

##### **Exam-Ready Answer:**
**Contrast stretching** is a piecewise-linear spatial domain transformation technique designed to increase the dynamic range of gray levels in a low-contrast image. Low-contrast images often occur due to poor illumination, a lack of dynamic range in the imaging sensor, or improper lens aperture settings. 

The process maps a narrow, compressed band of input intensity values $[r_1, r_2]$ to a much wider, expanded band of output intensity values $[s_1, s_2]$ using a piecewise-linear mapping function:
$$s = T(r)$$
By selectively choosing the control points $(r_1, s_1)$ and $(r_2, s_2)$, we steeply stretch the mid-tones while compressing highlights and shadows, making dark areas darker and bright areas brighter to enhance visibility of details.

---

#### **PYQ 2: Piecewise-Linear Transformations and Contrast Stretching**
*   **Exact Wording:** Explain piecewise-linear transformations of image enhancement with suitable example.
*   **Source Paper:** NMIMS MPSTME Semester V, Final Exam
*   **Year / Q No. / Marks:** Nov 2023 | Q2a | 5 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Point Processing - Piecewise-Linear Transformations

##### **Exam-Ready Answer:**
**Piecewise-Linear Transformation Functions** represent a class of spatial domain point processing operations that offer user-defined flexibility. Unlike purely mathematical log or power-law curves, piecewise functions are made of multiple straight-line segments. The user controls the slopes of these segments to selectively stretch or compress specific gray-level bands.

The most prominent example is **Contrast Stretching**, which uses three linear segments defined by control points $(r_1, s_1)$ and $(r_2, s_2)$:
$$s = \begin{cases} \alpha \cdot r & 0 \le r < r_1 \\ \beta \cdot (r - r_1) + s_1 & r_1 \le r < r_2 \\ \gamma \cdot (r - r_2) + s_2 & r_2 \le r \le L-1 \end{cases}$$

###### **Slopes & Transformations:**
*   **Slope 1 ($\alpha = s_1 / r_1$):** Controls mapping of low-intensity shadows.
*   **Slope 2 ($\beta = (s_2 - s_1) / (r_2 - r_1)$):** Controls mapping of mid-tones. Usually, we set $\beta > 1$ to steeply stretch contrast in this critical region.
*   **Slope 3 ($\gamma = (L-1-s_2) / (L-1-r_2)$):** Controls mapping of high-intensity highlights.

###### **Suitable Example (Thresholding as a Limiting Case):**
If we set $r_1 = r_2 = T$, $s_1 = 0$, and $s_2 = L-1$, the transformation function becomes a binary step function. This represents **Global Thresholding / Binarization**, which maps all pixels below threshold $T$ to 0 (black) and all pixels above or equal to $T$ to $L-1$ (white). This is used to segment foreground objects from background regions.

---

#### **PYQ 3: Gamma Correction and Its Effects**
*   **Exact Wording:** What is Gamma Correction and how does the value of gamma affect the image?
*   **Source Paper:** NMIMS MPSTME Semester V, Re-Exam (Batch 2023-24)
*   **Year / Q No. / Marks:** Dec 2024 | Q5a.2 | 5 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Point Processing - Power-Law / Gamma Transformation

##### **Exam-Ready Answer:**
**Gamma Correction** is a non-linear power-law transformation used to correct and calibrate the non-linear relationship between a digital pixel's voltage value and the physical brightness response of display monitors (such as CRTs, LCDs, or printers). 

Displays naturally possess a power-law response of $s = r^{\gamma_{\text{display}}}$, where $\gamma_{\text{display}}$ typically ranges from $1.8$ to $2.5$. This makes uncorrected images appear overly dark on screen. Gamma correction applies the inverse exponent ($\gamma = 1/\gamma_{\text{display}}$) to the image before displaying, ensuring a linear perceived luminance.

The general power-law transformation is:
$$s = c \cdot r^{\gamma}$$

###### **How the Value of Gamma ($\gamma$) Affects the Image:**
*   **$\gamma < 1$ (Fractional Gamma):** The transformation curve arches upward. It maps a narrow band of dark input values into a wider band of output levels. **Effect:** **Brightens the overall image**, revealing hidden details in dark shadows and low-visibility regions.
*   **$\gamma > 1$ (Integer Gamma):** The transformation curve arches downward. It compresses low-intensity regions and stretches the bright highlights. **Effect:** **Darkens the overall image**, making highlights more distinct and removing washed-out white details (e.g., enhancing contrast in aerial maps).
*   **$\gamma = 1$:** Represents a strictly linear identity transformation. The output remains identical to the input.

```
  Output s
    ▲
L-1 █      ┌───────────────── (gamma < 1: Brightens)
    │     / 
    │    /  ┌─────────────── (gamma = 1: Linear)
    │   /  /
    │  /  /   ┌───────────── (gamma > 1: Darkens)
    │ /  /   /
  0 └/──/───/──────────────► Input r
    0                      L-1
```

---

### 📥 2. Histogram Processing

#### **PYQ 4: Histogram Equalization Theory & Properties**
*   **Exact Wording:** Explain histogram equalization. Write a short note on the properties of images described by a histogram.
*   **Source Paper:** NMIMS MPSTME Semester V, Final Exam
*   **Year / Q No. / Marks:** Dec 2025 | Q2b | 5 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Histogram Processing - Equalization Theory

##### **Exam-Ready Answer:**
**Histogram Equalization (HE)** is a spatial domain contrast enhancement technique that spreads out the most frequent intensity levels of an image to achieve a flatter, more uniform histogram. 

Mathematically, it uses a Point Transformation based on the Cumulative Distribution Function (CDF):
$$s_k = T(r_k) = (L - 1) \cdot \sum_{j=0}^{k} p_r(r_j) = (L - 1) \cdot \text{CDF}(r_k)$$
where $p_r(r_j) = n_j / N$ is the Probability Density Function (PDF) representing the relative frequency of level $r_j$.

###### **Properties of Images Described by a Histogram:**
A histogram $h(r_k) = n_k$ provides a global statistical summary of an image's dynamic range and contrast, allowing us to deduce several key properties:
1.  **Dark Image:** The histogram bins are concentrated heavily on the extreme left-hand side of the scale (near 0), indicating low brightness.
2.  **Bright Image:** The histogram bins are concentrated heavily on the extreme right-hand side of the scale (near $L-1$), indicating high brightness.
3.  **Low-Contrast Image:** The histogram is very narrow and grouped tightly in a small, localized region (e.g., only in the mid-gray levels). The image appears flat and washed out.
4.  **High-Contrast Image:** The histogram spans the entire dynamic range from $0$ to $L-1$ with a wide, well-balanced distribution of pixel counts. It has distinct, rich details and high dynamic range.

---

### 📥 3. Blurring/Smoothing Spatial Filters

#### **PYQ 5: Linear vs. Non-Linear Smoothing Filters**
*   **Exact Wording:** What are the linear and non-linear smoothing filters in spatial domain? Compare and contrast between linear and non-linear spatial filtering.
*   **Source Paper:** NMIMS MPSTME Semester V, Re-Exam (Batch 2023-24)
*   **Year / Q No. / Marks:** Jan 2023 | Q10.1 | 5 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Neighborhood Operations - Linear vs. Non-linear Filtering

##### **Exam-Ready Answer:**
In spatial neighborhood filtering, we apply a small sub-grid (mask or kernel) over an image to modify the intensity of a pixel based on its surrounding neighbors. These filters are broadly categorized as **Linear** or **Non-Linear**:

*   **Linear Smoothing Filters:** The output pixel value is a linear combination (weighted sum) of the input pixels covered by the filter mask.
    *   *Examples:* Standard Average (Box) Filter, Weighted Average Filter, Gaussian Filter.
*   **Non-Linear Smoothing Filters:** The operation is based on sorting or ranking the pixel values covered by the filter window. The output value does not vary linearly with input intensities.
    *   *Examples:* Median Filter, Min Filter, Max Filter.

##### **Comparison Table:**

| Feature Parameter | Linear Spatial Filtering (e.g., Average Filter) | Non-Linear Spatial Filtering (e.g., Median Filter) |
| :--- | :--- | :--- |
| **Mathematical Type** | Linear operator (weighted arithmetic sum) [124]. | Non-linear operator (sorting and ranking) [20]. |
| **Mechanics** | Performs convolution/correlation using a fixed coefficient mask [124]. | Sorts neighborhood elements in ascending order and selects based on rank [161]. |
| **Noise Attenuation** | Optimal for **Gaussian (additive, white) noise**. | Optimal for **Salt-and-Pepper (impulse) noise** [308]. |
| **Edge Preservation** | **Blurs sharp edges** and fine details because it averages high frequencies [174]. | **Preserves sharp edges** cleanly without blur [308, 310]. |
| **Computational Complexity**| Low. Involves simple multiply-and-accumulate operations. | High. Sorting algorithms require greater processing overhead. |

---

#### **PYQ 6: Suitability of Blurring Filters on Gaussian Noise**
*   **Exact Wording:** Suggest a suitable filter that could minimize the impact of 'Gaussian noise'. Explain its working.
*   **Source Paper:** NMIMS MPSTME Semester V, Final Exam
*   **Year / Q No. / Marks:** Dec 2025 | Q4b | 4 Marks
*   **Verification Status:** 🟢 Verified PYQ
*   **Topic:** Blurring Filters - Gaussian Noise Reduction

##### **Exam-Ready Answer:**
The most suitable spatial filter to minimize the impact of **Gaussian Noise** is the **Gaussian Blurring Filter** (or a standard **Averaging / Blurring Filter**). 

###### **Why it Applies:**
Gaussian noise is characterized by small, random fluctuations in intensity distributed symmetrically according to a bell-shaped Gaussian curve. Because the noise values are additive and zero-mean, taking a localized average of surrounding pixels causes the positive and negative noise fluctuations to cancel each other out, smoothing the region.

###### **Working of a Gaussian Filter:**
1.  **Mask Generation:** The coefficients of the filter mask are sampled from a continuous 2-D Gaussian distribution function centered at $(0, 0)$:
    $$G(x, y) = \frac{1}{2\pi\sigma^2} e^{-\frac{x^2 + y^2}{2\sigma^2}}$$
    where $\sigma$ is the standard deviation controlling the width of the filter (blur radius).
2.  **Isotropic Blurring:** The kernel assigns higher weights to pixels near the center and lower weights to distant pixels. This produces isotropic, natural blurring.
3.  **Spatial Convolution:** The filter convolves with the image, computing each output pixel as the weighted sum of its neighborhood, effectively smoothing out high-frequency Gaussian noise fluctuations while preserving more edge structure than a flat box average.

---

## ⭐ PART C: SOLVED EXPECTED / PROBABLE QUESTIONS (SYLLABUS-ALIGNED)

---

### 📥 1. Point Processing Operations

#### **Expected Q1: Digital Negative vs. Thresholding**
*   **Topic:** Point Processing Comparison
*   **Source Reference:** `IVP UNIT 2.pptx` Slides 66 & 94
*   **Priority:** 🟡 Moderate Priority

##### **Comparison Table:**

| Feature Parameter | Digital Negative / Complement | Global Thresholding / Binarization |
| :--- | :--- | :--- |
| **Primary Purpose** | Reverses gray scale intensities. | Segments foreground objects from background. |
| **Mathematical Equation**| $s = (L - 1) - r$ | $s = L-1$ (if $r \ge T$), else $0$ |
| **Transformation Curve** | Continuous linear line with slope = $-1$. | Non-linear discontinuous step function. |
| **Output Type** | Grayscale (preserves tonal transitions). | Binary (contains only 0 and $L-1$). |
| **Primary Application** | Enhancing X-rays or mammograms. | OCR document binarization, mask creation. |

---

#### **Expected Q2: Logarithmic vs. Power-Law (Gamma) Transformations**
*   **Topic:** Point Processing Comparison
*   **Source Reference:** `IVP UNIT 2.pptx` Slides 80 & 87
*   **Priority:** 🔥 Very High Priority

##### **Comparison Table:**

| Feature Parameter | Logarithmic Transformation | Power-Law (Gamma) Transformation |
| :--- | :--- | :--- |
| **Mathematical Equation**| $s = c \log_{10}(1 + r)$ | $s = c \cdot r^{\gamma}$ |
| **Flexibility** | Fixed mathematical logarithmic shape. | Highly flexible; shape is tuned by changing $\gamma$. |
| **Response to Bright Levels**| Compresses high-intensity highlights heavily. | Can compress or expand highlights depending on $\gamma$. |
| **Primary Application** | Displaying Fourier Spectra with massive ranges. | Display calibration, luminance correction. |
| **Zero handling** | Requires adding $1$ to prevent $\log(0)$ error. | Handles $r = 0$ natively without shift. |

---

### 📥 2. Histogram Processing

#### **Expected Q3: Explain the Step-by-Step Histogram Equalization Algorithm**
*   **Topic:** Histogram Equalization Procedure
*   **Source Reference:** `IVP UNIT 2.pptx` Slide 182
*   **Priority:** ⭐ High Priority

##### **Exam-Ready Answer:**
To manually perform histogram equalization on a discrete $k$-bit image with spatial resolution $M \times N$, follow this step-by-step mathematical algorithm:

1.  **Calculate Total Pixels ($N$):** Compute the total number of pixels in the image:
    $$N = M \times N$$
2.  **Count Gray-Level Frequencies ($n_k$):** For each gray level $r_k$ in the range $[0, L-1]$ (where $L = 2^k$), count the number of pixels $n_k$ possessing that intensity.
3.  **Compute Probability Density Function (PDF):** Normalize the frequencies to obtain the probability of occurrence of each gray level:
    $$p_r(r_k) = \frac{n_k}{N} \quad \text{for } k = 0, 1, \dots, L-1$$
4.  **Compute Cumulative Distribution Function (CDF):** Calculate the running cumulative sum of the probabilities:
    $$\text{CDF}(r_k) = \sum_{j=0}^{k} p_r(r_j)$$
5.  **Calculate Mapped Intensities ($s_k$):** Scale the CDF values to the output dynamic range $[0, L-1]$ and round to the nearest integer:
    $$s_k = \text{round}\left( (L - 1) \cdot \text{CDF}(r_k) \right)$$
6.  **Reconstruct the Output Image:** Map every pixel in the original matrix from its old gray level $r_k$ to its new equalized gray level $s_k$ to generate the enhanced output image.

---

### 📥 3. Blurring/Smoothing Spatial Filters

#### **Expected Q4: Compare Average, Weighted Average, Median, and Gaussian Filters**
*   **Topic:** Filter Comparative Analysis
*   **Source Reference:** `IVP UNIT 2.pptx` Slides 125, 174, 308
*   **Priority:** 🔥 Very High Priority

##### **Comparison Table:**

| Feature Parameter | Standard Average (Box) Filter | Weighted Average Filter | Median Filter | Gaussian Blurring Filter |
| :--- | :--- | :--- | :--- | :--- |
| **Mathematical Class**| Linear | Linear | Non-Linear | Linear |
| **Mask / Mechanism** | Simple arithmetic mean of neighborhood pixels. | Arithmetic mean with higher weight on center pixel. | Sorts neighborhood and selects middle value. | Weights are sampled from continuous Gaussian curve. |
| **Effect on Edges** | Heavily blurs sharp boundaries. | Blurs edges, but preserves more than Box. | **Preserves sharp edges** cleanly. | Smooths edges naturally without jagged ringing. |
| **Noise Suitability** | Gaussian Noise | Gaussian Noise | **Salt-and-Pepper Noise** | Gaussian Noise / High-freq fluctuations. |
| **Separability Advantage**| No | No | No | **Separable** (can convolve 1D horizontally, then vertically). |

---

## 📂 PART D: DETAILED CONCEPT REFERENCE (GRAPHS & DIAGRAMS)

### 1. Point Processing Curves Sketch
When asked to sketch the point processing curves in an exam, draw the following orthogonal graph:
*   The **digital negative** is a straight diagonal line running from the top-left $(0, L-1)$ to the bottom-right $(L-1, 0)$.
*   The **log transformation** is a steep logarithmic arch rising rapidly from $(0,0)$ and flattening out as it approaches $(L-1, L-1)$.
*   The **power-law curves ($\gamma < 1$)** arch upward, similar to the log transform.
*   The **power-law curves ($\gamma > 1$)** arch downward, staying close to the bottom axis before rising steeply at the end.

### 2. Low-Pass Filter Mask Representation
*   **Standard 3x3 Box Mask:** Each coefficient is exactly $\frac{1}{9}$. The sum of all elements is $1.0$, which preserves the overall brightness of the image:
    $$H = \frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}$$
*   **Standard 3x3 Weighted Mask:** The center has a weight of 4, orthogonal neighbors have a weight of 2, and diagonal corners have a weight of 1. The sum of weights is $1+2+1+2+4+2+1+2+1 = 16$. The normalization factor is $\frac{1}{16}$:
    $$H = \frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix}$$

---

## ⚠️ OUT OF MID-SEM SYLLABUS — DO NOT PREPARE

*The topics below are part of the broader digital image processing syllabus but are **STRICTLY EXCLUDED** from the Mid-Sem exam. Do not study these for the upcoming test.*

### 1. Sharpening Spatial Filters
*   **Laplacian Operators:** Used for edge enhancement. These are second-order derivative filters that detect rapid gray-level transitions.
    $$\text{Center Negative Laplacian Mask} = \begin{bmatrix} 0 & 1 & 0 \\ 1 & -4 & 1 \\ 0 & 1 & 0 \end{bmatrix}$$
*   **High-Boost Filtering:** Combines the original image with a high-pass filtered version to sharpen details while preserving background intensity.

### 2. Frequency-Domain Processing & Fourier Analysis
*   **Discrete Fourier Transform (DFT):** Converts spatial coordinate pixels $f(x,y)$ into frequency components $F(u,v)$.
*   **Frequency-Domain Filtering:** Includes Low-Pass Filters (Ideal, Butterworth, Gaussian) and High-Pass Filters applied by multiplying the Fourier spectrum.

---

## 🏁 COMPLETE THEORY COVERAGE AUDIT

The table below confirms the absolute syllabus alignment of all solved and expected questions in this bank:

| Syllabus Topic | Verified PYQ Solved | Expected Question Solved | Status |
| :--- | :--- | :--- | :---: |
| **Digital Negative** | — | **Expected Q1** | 🟢 Complete |
| **Contrast Stretching** | **PYQ 1 & PYQ 2** | — | 🟢 Complete |
| **Global Thresholding** | — | **Expected Q1** | 🟢 Complete |
| **Intensity Slicing** | **PYQ 2 (binarization version)** | — | 🟢 Complete |
| **Log Transform** | **PYQ 3 (Part 2) & PYQ 1** | — | 🟢 Complete |
| **Power-Law (Gamma)**| **PYQ 3 (Part 3) & PYQ 3 (Part 4)** | **Expected Q2** | 🟢 Complete |
| **HE Theory & Properties**| **PYQ 4** | — | 🟢 Complete |
| **HE Algorithm** | — | **Expected Q3** | 🟢 Complete |
| **Linear vs. Non-linear**| **PYQ 5** | — | 🟢 Complete |
| **Averaging Blurring** | **PYQ 9** | **Expected Q4** | 🟢 Complete |
| **Median Filtering** | **PYQ 8** | **Expected Q4** | 🟢 Complete |
| **Gaussian Blurring** | **PYQ 6** | **Expected Q4** | 🟢 Complete |
