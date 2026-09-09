
# Lab 3: Spatial Filtering & Image Enhancement

This laboratory assignment explores the mechanics of neighborhood-based spatial domain processing, focusing on local convolution masks, noise reduction filters, and directional edge-detection operators.

## Implemented Operations & Key Observations

### 1. Linear Smoothing Filters
* **Operators**: Mean (Box) Filter, Gaussian Filter.
* **Method**: Applied spatial convolution using localized kernels to blend adjacent pixel intensities.
* **Observation**: Increasing kernel dimensions introduces localized blurring that attenuates high-frequency details. While both filters smooth noise, the Gaussian filter preserves edge structures far better than the unweighted Box filter.

### 2. Non-Linear Smoothing Filters
* **Operator**: Median Filter.
* **Method**: Replaced central pixels with the statistical median value of their neighboring window matrix.
* **Observation**: Proved exceptionally robust against high-frequency impulse noise ("salt-and-pepper") by completely discarding extreme outlier values without degrading structural border crispness like linear blurs do.

### 3. High-Pass & Edge-Detection Filters
* **Operators**: Sobel Gradient, Laplacian Operator, Canny Edge Detector.
* **Method**: Calculated localized discrete derivatives to capture high-rate spatial intensity transitions.
* **Observation**: First-derivative Sobel filters isolate directional horizontal and vertical gradients. Second-derivative Laplacians highlight isotropic omnidirectional transitions but are highly sensitive to noise. The Canny pipeline delivers optimal clean single-pixel boundaries by applying non-maximum suppression and hysteresis thresholding.

### 4. High-Boost Filtering & Sharpening
* **Method**: Subtracted a low-pass blurred component from the original image to isolate a high-frequency "unsharp mask," then scaled and re-added it back to the original matrix.
* **Observation**: Amplifies subtle micro-contrasts and structural transitions, vastly improving visual sharpness and making faint fine details highly discernible.

## File Index

* [Lab3_Image_Mnupilatioins.ipynb](Lab3_Image_Mnupilatioins.ipynb) — Complete Jupyter execution notebook containing output convolution matrices, filtering pipelines, and comparative visualizations.
