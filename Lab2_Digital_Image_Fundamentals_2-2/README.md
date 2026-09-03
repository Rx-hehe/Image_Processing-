# Lab 2: Image Sampling, Quantization & Arithmetic

This laboratory assignment explores the fundamental mechanics of digital image representation, focusing on grid downsampling, gray-level intensity reduction, and element-wise pixel arrays.

## Implemented Operations & Key Observations

### 1. Spatial Resolution (Sampling Factor)
* **Function:** `sample_image(image, factor)`
* **Method:** Downsampled images using `cv2.INTER_NEAREST` to isolate the pixel grid without blending values.
* **Observation:** Increasing the sampling factor drops high-frequency fine details, introducing visible **aliasing** and square blockiness ("jaggies").

### 2. Intensity Resolution (Quantization Levels)
* **Function:** `quantize_image(image, levels)`
* **Method:** Scaled down continuous grayscale values into localized discrete brightness brackets.
* **Observation:** Dropping quantization levels down to small values (like 3) removes smooth lighting gradients, resulting in harsh, visible bands known as **false contouring**.

### 3. Image Arithmetic & Saturated Shifting
* **Method:** Used OpenCV operations (`cv2.add`, `cv2.subtract`) instead of raw native Python matrix operations.
* **Observation:** Standard operators perform modulo wrapping that creates severe visual corruption. OpenCV safely applies **saturated arithmetic**, pinning overflows cleanly at `255` (pure white) and underflows at `0` (pure black).

### 4. Grayscale Set Operations (Bitwise Logic)
* **Intersection (`&`):** Maps shared high-intensity bits, darkening the image.
* **Set Difference (`& ~B`):** Isolates pixel bit values unique to Image A relative to Image B.
* **Symmetric Difference (`^`):** Lights up boundaries where patterns vary, turning shared patterns black.
* **Union (`|`):** Merges high-bit structures together, producing a bright combined matrix.

##  File Index
* `Lab2_Sampling_and_Arithmetic.ipynb` — Complete Jupyter execution notebook containing output plots and visualizations.

