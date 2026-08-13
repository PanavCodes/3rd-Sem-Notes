# Unit 1: Image Fundamentals Study Notes
**Course:** Image and Video Processing (IVP)
**Level:** SVKM's NMIMS MPSTME, Semester V (B.Tech COMP/EXTC)
**Primary Source:** `IVP UNIT 1.pptx` (and official course syllabus)
**Focus:** Comprehensive, Exam-Oriented Study Guide

---

## 📖 Module 1.1: What is Digital Image Processing (DIP)?

### 1. Definition of an Image
*   **Mathematical Representation:** An image is defined as a two-dimensional continuous spatial function $f(x, y)$.
    *   **$x$ and $y$:** Spatial coordinates in a 2-D plane.
    *   **$f$ / Amplitude:** The value of the function $f$ at any pair of coordinates $(x, y)$ is called the **intensity** or **gray level** of the image at that specific point.
*   **Continuous vs. Digital Image:**
    *   A continuous (analog) image has infinite resolution in both coordinates $(x, y)$ and amplitude $f(x, y)$.
    *   When $x$, $y$, and the amplitude values of $f$ are all finite, discrete, and quantized quantities, the image is called a **digital image**.
*   **The Picture Element (Pixel):** A digital image is composed of a finite number of elements, each possessing a particular coordinate location and intensity value. These discrete elements are referred to as **picture elements, image elements, pels, or pixels**. "Pixel" is the most widely accepted term.

⭐ **Must Remember:** A computer cannot understand a continuous photograph directly; it views an image as a 2-D matrix of numbers where the smallest unit of information is a pixel representing light intensity or color.

### 2. Why are Images Represented as 2-D Functions?
*   **Spatial Location:** To uniquely identify any point or dot on a flat visual surface, we must specify its relative location along two orthogonal directional axes (horizontal and vertical).
*   **Coordinate Mapping:** Let $x$ denote the row/vertical axis and $y$ denote the column/horizontal axis. Since two spatial variables $(x, y)$ are required to index any point, the continuous mapping is expressed as $f: \mathbb{R}^2 \rightarrow \mathbb{R}$ (grayscale) or $f: \mathbb{R}^2 \rightarrow \mathbb{R}^3$ (RGB color).

🧠 **Must Understand:** In color images, $f(x, y)$ becomes a vector-valued function:
$$f(x, y) = \begin{bmatrix} r(x, y) \\ g(x, y) \\ b(x, y) \end{bmatrix}$$
where $r$, $g$, and $b$ represent the continuous intensities of the red, green, and blue primary color channels.

### 3. Digital Image Processing (DIP) Overview
*   **DIP Definition:** The field of digital image processing refers to the manipulation and analysis of digital images by means of a digital computer.
*   **Classification of Imaging Disciplines:** Course notes define three levels of computerized image handling:
    1.  **Low-Level Processing (Image Processing):** Both input and output are images. Typical operations include noise reduction, contrast enhancement, and image sharpening.
    2.  **Mid-Level Processing (Image Analysis):** Inputs are images, but outputs are extracted features/attributes (e.g., edge coordinates, object segment boundaries, or class labels). Typical tasks are segmentation and classification.
    3.  **High-Level Processing (Computer Vision):** Involves "making sense" of the scene, replicating human cognitive visual functions to perform scene reconstruction and autonomous decision-making.

---

## 📐 Module 1.2: Digital Image Representation

### 1. The 2-D Matrix Representation
A digital image is represented on a computer as a 2-D grid or an ordered rectangular matrix of discrete integers. Assuming an image is sampled into $M$ rows and $N$ columns:

$$f(x, y) = \begin{bmatrix}
f(0,0) & f(0,1) & f(0,2) & \dots & f(0,N-1) \\
f(1,0) & f(1,1) & f(1,2) & \dots & f(1,N-1) \\
f(2,0) & f(2,1) & f(2,2) & \dots & f(2,N-1) \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
f(M-1,0) & f(M-1,1) & f(M-1,2) & \dots & f(M-1,N-1)
\end{bmatrix}$$

#### Key Structural Conventions:
*   **The Origin $(0, 0)$:** By convention, the origin of a digital image matrix lies in the **upper-left corner**. Row indices increase downward $(x = 0 \text{ to } M-1)$, and column indices increase to the right $(y = 0 \text{ to } N-1)$. This aligns with TV scanline sweeping patterns and standard linear algebra matrix indexing.
*   **Pixel Values (Quantization Levels):** Each entry in the matrix $f(x, y)$ is a non-negative integer representing the quantized intensity or gray-level of that pixel.

### 2. Types of Images Based on Intensity Quantization (Bit Depth)

The information capacity of a pixel depends on its **bit depth ($k$)**. A pixel represented by $k$ bits can take on any of $L = 2^k$ distinct intensity levels.

| Image Type | Bit Depth ($k$) | Allowed Intensity Levels ($L$) | Intensity Range | Key Characteristics & PPT Examples |
| :--- | :---: | :---: | :---: | :--- |
| **Binary Image** (Bi-level) | 1-bit | $2^1 = 2$ | $\{0, 1\}$ or $\{0, 255\}$ | Contains only black (0) and white (1 or 255) pixels. Used for document archiving, fax encoding, and binary masks. |
| **Grayscale Image** (Monochromatic) | 8-bit | $2^8 = 256$ | $0 \text{ to } 255$ | $0$ represents pure black (minimum brightness). $255$ represents pure white (maximum brightness). Intermediate values represent shades of gray. Monochromatic; no color components. |
| **True Color Image** (RGB) | 24-bit | $2^{24} \approx 16.7 \times 10^6$ | Three channels: $0 \text{ to } 255$ each | Composed of 3 distinct spatial planes (Red, Green, Blue). Each color plane is quantized to 8 bits ($L=256$). A pixel is represented as a triplet $(R, G, B)$. Total colors: $256 \times 256 \times 256 = 16,777,216$. |

✍️ **Exam Focus (Numerical Trap):** Be careful when reading exam questions about "8-bit color images".
1. If the question implies **8 bits per channel (RGB)**, the total color depth is **24 bits** ($16.7$ million colors).
2. If the question implies an **indexed color image**, the total color depth is **8 bits** ($L = 256$ color palette). Always write down both interpretations to ensure full marks.

---

## 🔄 Module 1.3: Image Sampling and Quantization

To convert continuous analog visual scenes captured by sensor arrays into a digital format suitable for computers, **Analog-to-Digital (A/D) conversion** must take place. This process consists of two distinct, irreversible steps: **Sampling** and **Quantization**.

```
  Continuous Analog Image
           │
           ▼
   [ STEP 1: SAMPLING ]    ──► Discretizes spatial coordinates (x, y) ──► Determines Pixels
           │
           ▼
  [ STEP 2: QUANTIZATION ] ──► Discretizes amplitude f(x, y)          ──► Determines Grays/Tones
           │
           ▼
     Digital Image
```

### 1. Image Sampling (Discretizing Spatial Coordinates)
*   **Definition:** The discretization of continuous spatial coordinates $(x, y)$ of a continuous scene onto a structured grid of physical sensor elements.
*   **Physical Mechanism:** During image capture, the camera lens projects the continuous scene onto a 2-D sensor array (e.g., CCD or CMOS chip). The physical arrangement of these individual sensor elements divides the continuous image plane into a discrete grid of rectangular or square pixels.
*   **Result:** Sampling directly determines the **spatial resolution** (number of pixels, $M \times N$) of the digital image.

### 2. Image Quantization (Discretizing Amplitude)
*   **Definition:** The transformation of a continuous intensity/amplitude value $f(x, y)$ at a sampled coordinate into a finite, discrete integer value representing a specific shade of gray or color.
*   **Physical Mechanism:** Each sensor element measures light intensity and outputs an analog voltage proportional to the photon count. An Analog-to-Digital Converter (ADC) rounds this continuous voltage value to the nearest discrete integer level.
*   **Result:** Quantization directly determines the **intensity resolution** (number of gray levels or colors, $L = 2^k$).

### 3. Key Differences: Sampling vs. Quantization

| Parameter | Sampling | Quantization |
| :--- | :--- | :--- |
| **Domain Affected** | Spatial Coordinates ($x$, $y$ axes) | Amplitude / Intensity ($f(x, y)$) |
| **Determines** | The **number of pixels** ($M \times N$) | The **shades/tone of a pixel** ($L$ levels) |
| **Physical Component** | Sensor array grid density (DPI / PPI) | Analog-to-Digital Converter (ADC) precision |
| **Sequence** | Must be performed **prior to** Quantization | Performed **after** Sampling has isolated coordinates |
| **Limitation Artifact** | Insufficient sampling causes **checkerboard / pixelization** | Insufficient quantization causes **false contouring** |

🧠 **Must Understand:** Quantization is an **irreversible operation**. Once continuous voltage values are rounded to discrete levels, original analog precision is permanently discarded. This loss of information is called quantization noise.

---

## 🖥️ Module 1.4: Spatial and Intensity Resolution

### 1. Spatial Resolution
*   **Definition:** Spatial resolution is a quantitative measure of the smallest discernible physical detail present in a digital image.
*   **Measurement Metrics:**
    1.  **Line Pairs per Unit Distance:** Typically measured by constructing a chart of alternating black and white vertical lines of width $W$. A line pair consists of one black line and its adjacent white space (width $2W$). The spatial resolution is defined as the maximum number of discernible line pairs per millimeter ($\text{lp/mm}$).
    2.  **Dots / Pixels per Unit Distance:** Used extensively in the printing, publishing, and scanning industries, expressed in **DPI (Dots Per Inch)** or **PPI (Pixels Per Inch)**.
    3.  **Pixel Dimensions ($M \times N$):** Although widely used to state resolution in commercial cameras (e.g., 20 Megapixels), pixel dimensions alone are not mathematically meaningful unless the physical dimensions of the scene being imaged are specified.
*   **Resolution Modification Techniques:**
    *   **Down-Sampling (Sub-Sampling):** Reducing spatial resolution by discarding rows and columns according to a sampling frequency. This decreases both image resolution and file size.
    *   **Up-Sampling:** Increasing spatial resolution by interpolating new pixel values between existing coordinates.

### 2. Intensity (Gray-Level) Resolution
*   **Definition:** Intensity resolution refers to the number of discrete gray levels or intensity values utilized to represent each pixel.
*   **Bit Allocation:** It is directly dictated by the number of bits allocated to each pixel ($k$). For an 8-bit intensity resolution, there are $2^8 = 256$ gray levels.
*   **Perceptual Limitations:** While computer screens commonly use 8 bits, the human eye is typically only capable of distinguishing about $60 \text{ to } 80$ distinct shades of gray under normal viewing conditions.

### 3. Dimensional and Storage Calculations

$$N_{\text{bits}} = M \times N \times k \times P$$

Where:
*   $M$ = Number of rows (vertical resolution)
*   $N$ = Number of columns (horizontal resolution)
*   $k$ = Bit depth (intensity resolution in bits/pixel)
*   $P$ = Number of image planes (color bands; $P=1$ for grayscale, $P=3$ for RGB)

#### ✍️ Numerical Exam Example 1:
**Question:** Determine the exact storage requirement in bytes for an 8-bit color image of size $800 \times 600$ pixels.
*   **Interpretation A (Assuming 24-bit True Color RGB, where each color channel has 8 bits):**
    *   $M = 800$, $N = 600$, $k = 8$ bits, $P = 3$ planes
    *   $\text{Total Bits} = 800 \times 600 \times 8 \times 3 = 11,520,000 \text{ bits}$
    *   $\text{Total Bytes} = \frac{11,520,000}{8} = 1,440,000 \text{ bytes}$
    *   $\text{In Kilobytes (KB)} = \frac{1,440,000}{1024} = 1406.25 \text{ KB} \approx 1.37 \text{ MB}$

*   **Interpretation B (Assuming 8-bit Indexed Color, where total depth is 8 bits/pixel):**
    *   $M = 800$, $N = 600$, $k = 8$ bits, $P = 1$ index plane
    *   $\text{Total Bits} = 800 \times 600 \times 8 \times 1 = 3,840,000 \text{ bits}$
    *   $\text{Total Bytes} = \frac{3,840,000}{8} = 480,000 \text{ bytes}$
    *   $\text{In Kilobytes (KB)} = \frac{480,000}{1024} \approx 468.75 \text{ KB}$

### 4. Sampling & Quantization Artifacts

#### A. Checkerboard Effect (Pixelization Error)
*   **Cause:** Caused by **insufficient spatial sampling** (low number of pixels $M \times N$) while keeping the quantization level $L$ high.
*   **Visual Appearance:** The fine structural details of the image are lost, and individual pixels become enlarged, visible squares. The image appears blocky or "pixelated".

#### B. False Contouring (Contour Banding)
*   **Cause:** Caused by **insufficient intensity quantization** (low bit depth $k \le 4$, $L \le 16$ gray levels) while keeping the spatial resolution $M \times N$ constant.
*   **Visual Appearance:** Smooth, continuous grayscale gradients are replaced by harsh, distinct, visible boundaries or ridges that resemble topographical elevation lines on a map. This is because there are not enough discrete levels to represent the gradual transitions smoothly.

---

## 🔗 Module 1.5: Basic Relationships Between Pixels

Let $p$ be a pixel located at coordinates $(x, y)$ in a digital image.

### 1. Pixel Neighborhoods
There are three fundamental neighborhood types defined on a 2-D spatial grid:

#### A. 4-Neighbors: $N_4(p)$
The set of four immediate horizontal and vertical pixels adjacent to $p$.
$$N_4(p) = \{(x+1, y), (x-1, y), (x, y+1), (x, y-1)\}$$

```
      [ (x-1, y) ]
[ (x, y-1) ]   p(x, y)   [ (x, y+1) ]
      [ (x+1, y) ]
```
*Each of these pixels is exactly 1 unit of physical distance away from $p$.*

#### B. Diagonal Neighbors: $N_D(p)$
The set of four diagonally touching pixels adjacent to $p$.
$$N_D(p) = \{(x+1, y+1), (x+1, y-1), (x-1, y+1), (x-1, y-1)\}$$

```
[ (x-1, y-1) ]           [ (x-1, y+1) ]
                p(x,y)
[ (x+1, y-1) ]           [ (x+1, y+1) ]
```
*Each of these pixels is exactly $\sqrt{2} \approx 1.414$ units of distance away from $p$.*

#### C. 8-Neighbors: $N_8(p)$
The complete union of both the 4-neighbors and the diagonal neighbors.
$$N_8(p) = N_4(p) \cup N_D(p)$$

```
[ (x-1, y-1) ] [ (x-1, y) ] [ (x-1, y+1) ]
[ (x, y-1)   ]   p(x, y)    [ (x, y+1)   ]
[ (x+1, y-1) ] [ (x+1, y) ] [ (x+1, y+1) ]
```

---

### 2. Pixel Adjacency
Let $V$ represent the **set of intensity values** used to establish a criterion of similarity or membership.
*   In a binary image, $V = \{1\}$ if we are referring to the adjacency of white pixels.
*   In a grayscale image, $V$ contains a subset of intensity levels, such as $V = \{180, 181, \dots, 200\}$.

#### A. 4-Adjacency
Two pixels $p$ and $q$ with intensity values from the set $V$ are **4-adjacent** if $q$ belongs to the set of 4-neighbors of $p$, i.e., $q \in N_4(p)$.

#### B. 8-Adjacency
Two pixels $p$ and $q$ with intensity values from the set $V$ are **8-adjacent** if $q$ belongs to the set of 8-neighbors of $p$, i.e., $q \in N_8(p)$.

#### C. m-Adjacency (Mixed Adjacency)
Two pixels $p$ and $q$ with intensity values from the set $V$ are **m-adjacent** if:
1.  $q \in N_4(p)$, **OR**
2.  $q \in N_D(p)$ **AND** the intersection set $N_4(p) \cap N_4(q)$ contains **no pixels** whose intensity values are from the set $V$.

🧠 **Must Understand (Mixed Adjacency Concept):** m-adjacency is a highly specialized, restricted modification of 8-adjacency. It was introduced to **eliminate the path ambiguities** that frequently arise when 8-adjacency is used. By restricting diagonal connections, m-adjacency ensures that only **one unique path** exists between adjacent pixels.

#### Step-by-Step Ambiguity Elimination Example:
Consider the following binary pixel grid with $V = \{1\}$:

```
   (a) Pixel Grid         (b) 8-Adjacency Path       (c) m-Adjacency Path
     0   1   1               0 ── 1 ── 1                0 ── 1 ── 1
     0   1   0               │  / │                       /  │
     0   0   1               0 ── 1   0                0     1   0
                             │  /                              \
                             0   0 ── 1                0   0 ── 1
```
*   **In Fig (b) (8-Adjacency):** Multiple redundant paths exist between the center pixel $(1,1)$ and the top-right pixel $(0,2)$. We can go diagonally directly $(1,1) \to (0,2)$ or horizontally/vertically via $(1,1) \to (0,1) \to (0,2)$. This creates mathematical loops and ambiguity.
*   **In Fig (c) (m-Adjacency):** Since the top-center pixel $(0,1)$ has a value of `1` (which is in $V$), the intersection of 4-neighbors of the center $(1,1)$ and top-right $(0,2)$ contains a pixel from $V$. Thus, the diagonal path $(1,1) \to (0,2)$ is **blocked/eliminated** under m-adjacency. Only the unambiguous horizontal-vertical path remains.

---

### 3. Digital Paths and Curves
*   **Definition:** A digital path (or curve) from pixel $p$ with coordinates $(x, y)$ to pixel $q$ with coordinates $(s, t)$ is a sequence of distinct pixels with coordinates:
    $$(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)$$
    where $(x_0, y_0) = (x, y)$ and $(x_n, y_n) = (s, t)$, and pixels $(x_i, y_i)$ and $(x_{i-1}, y_{i-1})$ are adjacent for all $1 \le i \le n$.
*   **Path Length ($n$):** The length of the digital path is defined as the number of pixel-to-pixel transitions ($n$). If the start and end coordinates are identical, $(x_0, y_0) = (x_n, y_n)$, the path is a **closed path**.
*   **Path Types:** Paths are classified as **4-paths**, **8-paths**, or **m-paths** depending on the specific type of adjacency criteria enforced.

---

### 4. Connectivity, Regions, and Boundaries

#### A. Connectivity
*   **Connected in S:** Let $S$ represent a subset of pixels in an image. Two pixels $p$ and $q$ are said to be connected in $S$ if there exists a digital path between them consisting entirely of pixels belonging to $S$.
*   **Connected Component:** For any pixel $p$ in $S$, the set of all pixels that are connected to it within $S$ is called a connected component of $S$.
*   **Connected Set:** If $S$ contains only one connected component, then $S$ is called a connected set.

#### B. Region ($R$)
*   **Definition:** A subset of pixels $R$ in an image is called a **region** if $R$ is a connected set.
*   **Adjacent Regions:** Two regions $R_i$ and $R_j$ are said to be adjacent if their union $R_i \cup R_j$ forms a connected set. If they are not adjacent, they are considered **disjoint regions**.

#### C. Boundary (Border / Contour)
*   **Definition:** The boundary (also called border, contour, or inner boundary) of a region $R$ is the set of pixels in the region that have one or more neighbors that do **not** belong to $R$.
*   **Boundary Distinction:** If a region $R$ consists of the entire image, its boundary is defined as the pixels in the first and last rows and columns of the matrix.

---

## 📏 Module 1.6: Distance Measures

For any arbitrary pixels $p, q$, and $z$ with coordinates $(x, y)$, $(s, t)$, and $(v, w)$ respectively, a function $D$ is a **valid distance metric** if it satisfies the following three fundamental metric properties:

1.  **Non-Negativity / Positive Definiteness:**
    *   $D(p, q) \ge 0$
    *   $D(p, q) = 0 \text{ if and only if } p = q$
2.  **Symmetry:**
    *   $D(p, q) = D(q, p)$
3.  **Triangle Inequality:**
    *   $D(p, z) \le D(p, q) + D(q, z)$

---

### The Three Principal Distance Metrics

#### 1. Euclidean Distance ($D_e$)
The Euclidean distance (also known as the $L_2$ norm or straight-line distance) is defined as:
$$D_e(p, q) = \sqrt{(x - s)^2 + (y - t)^2}$$

*   **Geometric Contour:** Constant distance contours form a **circular disk** centered at the origin pixel.
*   **Physical Meaning:** Represents the shortest physical straight-line path between two points in continuous Euclidean space.

#### 2. City-Block Distance ($D_4$)
The City-Block distance (also known as the $L_1$ norm or Manhattan distance) is defined as:
$$D_4(p, q) = |x - s| + |y - t|$$

*   **Geometric Contour:** Constant distance contours form a **diamond-shaped** boundary centered at $(x, y)$.
*   **Physical Meaning:** Measures distance restricted to horizontal and vertical steps only (matching a grid system, similar to streets in a city).
*   **Adjacency Connection:** Pixels having a $D_4$ distance equal to $1$ are the immediate **4-neighbors** of $p$.

#### 3. Chessboard Distance ($D_8$)
The Chessboard distance (also known as the $L_{\infty}$ norm or Chebyshev distance) is defined as:
$$D_8(p, q) = \max(|x - s|, |y - t|)$$

*   **Geometric Contour:** Constant distance contours form a **square-shaped** boundary centered at $(x, y)$.
*   **Physical Meaning:** Measures movement where diagonal moves are permitted and cost the same as horizontal or vertical moves (matching king movement in chess).
*   **Adjacency Connection:** Pixels having a $D_8$ distance equal to $1$ are the immediate **8-neighbors** of $p$.

---

### Step-by-Step Contour Visualizations (Radius $r \le 2$)

#### City-Block ($D_4 \le 2$) Contour Diamond:
```
      2
    2 1 2
  2 1 0 1 2
    2 1 2
      2
```

#### Chessboard ($D_8 \le 2$) Contour Square:
```
  2 2 2 2 2
  2 1 1 1 2
  2 1 0 1 2
  2 1 1 1 2
  2 2 2 2 2
```

---

### ✍️ Numerical Exam Example 2:
**Question:** Calculate the Euclidean distance ($D_e$), City-Block distance ($D_4$), and Chessboard distance ($D_8$) between two pixels $p(0, 4)$ and $q(6, 1)$ on a discrete grid.

*   **Identify Coordinates:** $(x, y) = (0, 4)$ and $(s, t) = (6, 1)$.
*   **1. Euclidean Distance ($D_e$):**
    $$D_e(p, q) = \sqrt{(0 - 6)^2 + (4 - 1)^2} = \sqrt{(-6)^2 + (3)^2}$$
    $$D_e(p, q) = \sqrt{36 + 9} = \sqrt{45} \approx \mathbf{6.71 \text{ units}}$$
*   **2. City-Block Distance ($D_4$):**
    $$D_4(p, q) = |0 - 6| + |4 - 1| = |-6| + |3|$$
    $$D_4(p, q) = 6 + 3 = \mathbf{9 \text{ units}}$$
*   **3. Chessboard Distance ($D_8$):**
    $$D_8(p, q) = \max(|0 - 6|, |4 - 1|) = \max(|-6|, |3|)$$
    $$D_8(p, q) = \max(6, 3) = \mathbf{6 \text{ units}}$$

---

## 📁 Module 1.7: Image File Formats

Digital images must be compressed and formatted cleanly to be stored and transmitted efficiently.

### 1. TIFF (Tagged Image File Format)
*   **Compression Type:** Lossless compression (often utilizing LZW algorithm) or completely uncompressed.
*   **Maximum Color Support:** Extremely versatile, supporting up to 48-bit true color and multi-page configurations.
*   **Transparency Support:** Yes (supports alpha channel transparency and multi-layered editing).
*   **Primary Usage & Advantages:** Used heavily in professional photography, printing, desktop publishing, and archival document storage. It preserves maximum original detail without compression artifacts.
*   **Major Disadvantages:** Extremely large file sizes, making it entirely unsuitable for standard web sharing.

### 2. PNG (Portable Network Graphics)
*   **Compression Type:** Lossless compression (utilizing the DEFLATE algorithm, combining Huffman and LZ77).
*   **Maximum Color Support:** Supports up to 48-bit true color and 16-bit grayscale.
*   **Transparency Support:** Superior transparency support with a dedicated 8-bit alpha channel (smooth gradient alpha channels, unlike GIF's binary transparency).
*   **Primary Usage & Advantages:** Standard for web graphics, logos, icons, screenshots, and images containing text. It maintains perfect, crisp details on sharp boundaries.
*   **Major Disadvantages:** File sizes are noticeably larger than JPEG for highly complex, continuous-tone photographic scenes.

### 3. JPEG (Joint Photographic Experts Group)
*   **Compression Type:** Lossy compression (utilizing Discrete Cosine Transform (DCT) quantization and Huffman entropy encoding).
*   **Maximum Color Support:** Supports up to 24-bit RGB true color (8 bits per channel).
*   **Transparency Support:** No (does not support transparency).
*   **Primary Usage & Advantages:** The dominant standard for sharing digital photographs over the internet, websites, and cameras. It provides highly adjustable, massive compression ratios, drastically reducing file sizes with minimal perceptually noticeable quality degradation.
*   **Major Disadvantages:** Lossy nature means it permanently discards image detail during saving. Repeatedly editing and saving a JPEG image causes generational loss and introduces visible "blocky DCT artifacts" along $8 \times 8$ pixel boundaries.

---

## 🛠️ Unit 1 Study Toolkit

### 1. Important Definitions

*   **Digital Image:** A continuous 2-D light intensity function $f(x, y)$ that has been sampled in spatial coordinates and quantized in amplitude to form a discrete matrix of integer entries.
*   **Pixel (Pel):** The smallest individual element or point sample of a digital image possessing a unique coordinate location and intensity value.
*   **Sampling:** The process of converting a continuous spatial coordinate into a discrete, digital grid coordinate.
*   **Quantization:** The process of mapping a continuous intensity value to a discrete integer representing a specific gray scale level.
*   **False Contouring:** A visual artifact causing ridges to appear in smooth areas of an image, caused by using an insufficient number of gray levels (quantization bits).
*   **Checkerboard Effect:** A blocky, pixelated visual artifact that occurs when spatial sampling is too coarse (insufficient number of pixels).
*   **Bit Depth ($k$):** The number of binary bits allocated to store the intensity information of a single pixel.
*   **m-Adjacency:** A restricted type of pixel adjacency designed to prevent path ambiguity by blocking diagonal connections when a parallel horizontal or vertical connection is available.
*   **Euclidean Distance:** The straight-line distance between two points measured in Euclidean space.
*   **City-Block Distance:** The path distance between two pixels restricted entirely to horizontal and vertical movements.
*   **Chessboard Distance:** The path distance between two pixels where horizontal, vertical, and diagonal movements are all allowed and weighted equally.

---

### 2. Core Formula Sheet

#### Image Size & Storage (Bits):
$$\text{Storage (bits)} = M \times N \times k \times P$$
*(where $M=$ rows, $N=$ columns, $k=$ bit depth, $P=$ color planes)*

#### Dynamic Range of Intensity Levels ($L$):
$$L = 2^k$$
*Allowable gray levels range from $0 \text{ to } L-1$.*

#### Distance Equations:
*   **Euclidean Distance ($D_e$):**
    $$D_e(p, q) = \sqrt{(x-s)^2 + (y-t)^2}$$
*   **City-Block Distance ($D_4$):**
    $$D_4(p, q) = |x-s| + |y-t|$$
*   **Chessboard Distance ($D_8$):**
    $$D_8(p, q) = \max(|x-s|, |y-t|)$$

---

### 3. Quick Comparison Tables

#### Sampling vs. Quantization
| Metric | Sampling | Quantization |
| :--- | :--- | :--- |
| **Domain** | Space coordinates ($x$, $y$) | Amplitude/Intensity ($f(x, y)$) |
| **Determines** | Grid density (Pixel dimension) | Grayscale/Color tone depth |
| **Artifact** | Checkerboard / Blockiness | False contouring / Ridges |

#### Spatial vs. Intensity Resolution
| Metric | Spatial Resolution | Intensity Resolution |
| :--- | :--- | :--- |
| **Focus** | Fine spatial detail | Grayscale shade detail |
| **Metric** | DPI, PPI, lp/mm, Pixel dimension | Bits per pixel ($k$), Grayscale levels ($L$) |
| **Control** | Sub-sampling / Down-sampling | Quantization levels |

#### Image Formats Quick-Reference
| Format | Compression | Transparency | Main Use Case | Max Bit-Depth |
| :--- | :--- | :---: | :--- | :---: |
| **TIFF** | Lossless / None | Yes | Professional printing, archiving | 48-bit |
| **PNG** | Lossless | Yes | Web design, logos, screenshots | 48-bit |
| **JPEG** | Lossy | No | Web photographs, camera storage | 24-bit |

---

### 4. Important Diagrams to Study
1.  **Continuous to Digital Transformation:** Study how a continuous waveform $F(x, y)$ is sampled along a grid and quantized into steps to yield discrete integer values in a matrix.
2.  **Pixel Neighborhood Grid Patterns:** Practice drawing the 4-neighbors ($N_4$), Diagonal neighbors ($N_D$), and 8-neighbors ($N_8$) around a center pixel $p(x, y)$.
3.  **Ambiguity in 8-Adjacency vs. m-Adjacency:** Practice drawing the standard "corner-loop" diagram where a diagonal connection under 8-adjacency is blocked by m-adjacency because a common horizontal or vertical neighbor is present in $V$.
4.  **Distance Contours:** Be prepared to sketch the diamond contour of constant distance for the City-block ($D_4$) metric, and the square contour for the Chessboard ($D_8$) metric.

---

### 5. Past Exam Practice Questions

#### Section A: Conceptual & Theory (L2 - Understanding)
1.  **Explain the phenomenon of false contouring.** Why does it happen, what does it look like, and how can it be avoided?
2.  **Define and differentiate between sampling and quantization.** Which process determines the spatial resolution of an image, and which determines its tonal characteristics?
3.  **Why is m-adjacency introduced in digital image processing?** Provide a step-by-step example where 8-adjacency causes path ambiguity and show how m-adjacency resolves it.
4.  **Compare and contrast PNG, JPEG, and TIFF image formats.** Evaluate their performance based on compression types, transparency support, and typical industrial usage.

#### Section B: Analytical & Numerical (L3 - Applying)
1.  **Calculate the Euclidean, City-block, and Chessboard distances** between two pixels located at $(1, 5)$ and $(9, 2)$ on a standard grid.
2.  **Determine the storage requirement** in Kilobytes (KB) for a 16-bit grayscale image of size $1024 \times 1024$ pixels.
3.  **Consider the following $5 \times 5$ binary image region with $V = \{1\}$:**
    ```
    1   1   0   0   0
    0   1   1   0   0
    0   0   1   1   0
    0   0   0   1   1
    0   0   0   0   1
    ```
    Determine the length of the shortest 4-path, 8-path, and m-path between the top-left pixel at $(0,0)$ and the bottom-right pixel at $(4,4)$. If a path does not exist, explain why.

---

## 📋 `IVP UNIT 1.pptx` Coverage Checklist

This checklist confirms that every meaningful section of the official Unit 1 presentation has been fully mapped and covered in these study notes:

- [x] **Slide 1-5:** Introduction to Digital Image Processing & Definition of an Image (Covered in Module 1.1)
- [x] **Slide 6-10:** Why images are 2-D functions & Image representations (Covered in Module 1.1 & 1.2)
- [x] **Slide 11-15:** Picture elements, pels, pixels & Continuous vs. Digital forms (Covered in Module 1.1 & 1.2)
- [x] **Slide 16-20:** Discrete representation of images as matrices (Covered in Module 1.2)
- [x] **Slide 21-25:** Types of Images: Binary, Grayscale, and True Color RGB (Covered in Module 1.2)
- [x] **Slide 26-30:** Analog-to-Digital Conversion: Sampling & Quantization (Covered in Module 1.3)
- [x] **Slide 31-35:** Spatial and Intensity Resolutions & Dimensional Calculations (Covered in Module 1.4)
- [x] **Slide 36-40:** Up-sampling and Down-sampling/Sub-sampling operations (Covered in Module 1.4)
- [x] **Slide 41-45:** Image display artifacts: False contouring & Checkerboard effects (Covered in Module 1.4)
- [x] **Slide 46-50:** Basic pixel relationships: 4, diagonal, and 8 pixel neighborhoods (Covered in Module 1.5)
- [x] **Slide 51-55:** Adjacency, connectivity, region definition, and boundaries (Covered in Module 1.5)
- [x] **Slide 56-60:** Adjacency ambiguity: 8-adjacency vs. m-adjacency path resolution (Covered in Module 1.5)
- [x] **Slide 61-63:** Distance measures: Euclidean, City-block ($D_4$), and Chessboard ($D_8$) (Covered in Module 1.6)
