# Lab 5: Spatial Filtering & Image Sharpening

This laboratory assignment explores the mechanics of neighborhood-based spatial filtering, focusing on spatial domain convolution, linear smoothing, non-linear noise reduction, and edge-based image sharpening techniques.

## Implemented Operations & Key Observations

1. **Unsharp Masking**
   * **Method:** Subtracted a blurred (Gaussian) version of the astronaut image from its original to isolate high-frequency spatial details (the mask), then added this weighted mask back to the original image.
   * **Observation:** Effectively amplified high-frequency structural elements like edges and fine lines. By tuning the `sigma` and `amount` parameters, micro-contrast was significantly enhanced without introducing severe overshoot or halo artifacts.

2. **Box Filter (7×7)**
   * **Method:** Constructed a manual \(7 \times 7\) averaging kernel where all 49 entries were uniformly set to \(1/49\) to preserve absolute global brightness, then convolved it over the target profile using `cv2.filter2D`.
   * **Observation:** Performed an even, non-weighted local spatial averaging that suppressed random noise. However, it noticeably degraded fine edge definitions and introduced blocky geometric artifacts around high-contrast boundaries due to its uniform spatial distribution.

3. **Gaussian Filters (5×5 vs. 21×21)**
   * **Method:** Applied 2D Gaussian bell-curve smoothing operators using `cv2.GaussianBlur` across varying window sizes to assign higher weights to closer neighboring pixels.
   * **Observation:** Produced a highly natural, smooth blur that bypassed the blocky artifacts characteristic of box filters. Small kernels (\(5 \times 5\)) achieved clean, subtle noise reduction, whereas large configurations (\(21 \times 21\)) completely washed out high-frequency spatial components.

4. **3×3 Laplacian Sharpening**
   * **Method:** Extracted a second-order isotropic derivative edge map using `cv2.Laplacian` and subtracted this map directly from the normalized floating-point original framework.
   * **Observation:** Sharply accentuated rapid intensity transitions from all spatial directions simultaneously. This discrete differentiation process caused fine physical structures to pop dramatically while keeping uniform background regions intact.

5. **Box Filter Scaling Comparison (3×3, 9×9, 15×15)**
   * **Method:** Iterated over scalar increases in uniform box kernel dimensions, evaluating the correlation between window size and spatial frequency degradation.
   * **Observation:** Explicitly confirmed that larger kernel boundaries correspond directly to stronger blur effects and increased structural information loss, shifting the image contents from subtle smoothing to total loss of fine detail.

6. **Median Filter vs. Gaussian Blur (Salt-and-Pepper Noise)**
   * **Method:** Generated random impulsive salt-and-pepper noise profiles and comparatively evaluated the restorative performance of `cv2.medianBlur` against standard Gaussian smoothing.
   * **Observation:** The median filter completely rejected extreme intensity outliers by selecting the statistical median of the neighborhood, cleanly erasing the noise specks. Conversely, the Gaussian filter smeared the noise across adjacent pixels, resulting in an artifact-ridden, cloudy output.

7. **Bilateral Filter (Edge-Preserving Blur)**
   * **Method:** Configured `cv2.bilateralFilter` to perform localized smoothing based on a dual-metric framework evaluating both geometric closeness (spatial domain) and photometric similarity (intensity/color domain).
   * **Observation:** Successfully smoothed out flat textural regions and surface variations while leaving high-contrast structural borders crisp and completely intact. This verified its superiority over standard blind Gaussian filters for applications like digital beauty filtering and smart denoising.

## Dependencies

The following Python libraries are required to run this lab:

* opencv-python
* scikit-image
* matplotlib
* numpy

## File Index

* [Lab5_Spatial_Filtering.ipynb](Lab5_Spatial_Filtering-2.ipynb) — Complete Jupyter execution notebook containing image processing pipelines, neighborhood convolutions, noise injection/filtering scripts, and side-by-side comparative visualizations.
