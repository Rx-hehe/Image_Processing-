# Lab 8: Morphological Image Processing

This laboratory assignment explores binary morphological image processing using erosion, dilation, opening, and closing. The experiments compare the effects of square and circular structuring elements on filled shapes, thin outlines, and salt noise.

## Implemented Operations & Key Observations

### 1. Binary Image with Shapes and Noise
* **Method:** Created a 200×600 black binary image using NumPy, then drew a filled circle, filled rectangle, hollow circle, and hollow rectangle using OpenCV. Added 1,000 randomly positioned white pixels with `np.random.seed(0)` to produce reproducible salt noise.
* **Observation:** The synthetic image provides both solid and thin-outlined objects, making it possible to compare shape preservation, boundary changes, and noise removal across morphological operations.

### 2. Morphological Operations with a 5×5 Square Kernel
* **Method:** Constructed a 5×5 square structuring element using `np.ones((5, 5), np.uint8)`. Applied erosion with `cv2.erode`, dilation with `cv2.dilate`, opening with `cv2.morphologyEx(..., cv2.MORPH_OPEN, ...)`, and closing with `cv2.morphologyEx(..., cv2.MORPH_CLOSE, ...)`.
* **Observation:** Erosion shrinks foreground objects and removes isolated noise, while dilation expands foreground regions and also enlarges noise. Opening removes small white noise but can eliminate thin outlines; closing fills small gaps and connects nearby white regions.

### 3. Morphological Operations with a Circular Kernel
* **Method:** Created a custom circular structuring element by drawing a filled circle of radius 5 into an 11×11 binary kernel. Repeated erosion, dilation, opening, and closing on the original synthetic image using this circular kernel.
* **Observation:** The larger circular kernel generally produces stronger changes than the 5×5 square kernel. Erosion reduces objects more substantially, dilation expands them with rounder boundaries, opening removes larger small-scale details, and closing can bridge larger gaps.

### 4. Comparison of Square and Circular Structuring Elements
* **Method:** Compared the results of the four operations using the 5×5 square kernel and the radius-5 circular kernel.
* **Observation:** The square kernel produces less aggressive changes and tends to retain more of the original detail. The circular kernel produces smoother, more rounded effects, but it is also larger (11×11 versus 5×5). Differences therefore reflect **both kernel shape and kernel size**, not shape alone.

## Key Morphological Concepts

* **Erosion:** Shrinks white foreground objects by removing boundary pixels.
* **Dilation:** Expands white foreground objects by adding pixels around their boundaries.
* **Opening:** Erosion followed by dilation; useful for removing small foreground noise.
* **Closing:** Dilation followed by erosion; useful for filling small background gaps and holes.
* **Structuring element:** Defines the neighborhood and geometry used by each morphological operation.

## Dependencies

The following Python libraries are required to run this lab:

* `opencv-python`
* `numpy`
* `matplotlib`

## File Index

* [Lab8_Morphological.ipynb](Lab8_Morphological.ipynb) — Jupyter notebook for generating the binary test image, applying four morphological operations with square and circular kernels, and comparing their effects.
