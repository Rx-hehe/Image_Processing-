# Lab 6: Frequency Domain Filtering

This laboratory assignment explores image filtering in the frequency domain using the two-dimensional Fourier Transform, focusing on frequency-based Laplacian filtering and implementing Sobel edge detection through frequency-domain multiplication.

## Implemented Operations & Key Observations

### 1. Laplacian Filtering in the Frequency Domain
* **Method:** Loaded and resized the grayscale `camera` image to 256×256 pixels, generated a two-dimensional frequency grid using `np.fft.fftfreq`, and constructed the Laplacian frequency response using \(H(u,v) = -4\pi^2(u^2 + v^2)\). The image was transformed with `fft2`, multiplied pointwise by the Laplacian filter, and reconstructed using `ifft2`.
* **Observation:** The Laplacian suppressed low-frequency image content while emphasizing high-frequency components associated with rapid intensity changes. The reconstructed spatial output therefore behaved as an edge map, with flat regions close to zero and strong transitions clearly highlighted.

### 2. Sobel Filtering in the Frequency Domain
* **Method:** Defined the standard 3×3 horizontal and vertical Sobel kernels and embedded each kernel into a zero-padded array matching the image dimensions. The centered kernels were moved to the FFT origin using `ifftshift`, transformed into their frequency responses with `fft2`, and multiplied by the image spectrum. After inverse transformation, the horizontal and vertical responses were combined using \(\sqrt{G_x^2 + G_y^2}\).
* **Observation:** Combining the two directional Sobel responses produced a clear edge-detection result containing intensity transitions from both orientations. This demonstrated how a small spatial-domain convolution kernel can be converted into a frequency-domain filter while preserving its edge-detection behavior.

## Key Frequency-Domain Concepts

* **Low frequencies** represent gradual intensity variations, smooth regions, and overall image brightness.
* **High frequencies** represent rapid intensity changes such as edges, fine texture, and noise.
* Spatial-domain convolution corresponds to pointwise multiplication in the frequency domain.
* `fft2` transforms an image into the frequency domain, while `ifft2` reconstructs the spatial-domain result.
* `fftshift` is useful for displaying the spectrum with zero frequency at the center, while `ifftshift` restores the ordering required for FFT-based computation.

## Dependencies

The following Python libraries are required to run this lab:

* `numpy`
* `matplotlib`
* `scikit-image`

## File Index

* [Lab6_Frequency_Domain-2.ipynb](Lab6_Frequency_Domain-2.ipynb) — Complete Jupyter execution notebook containing frequency-domain theory, Laplacian filtering, Sobel frequency-response construction, FFT-based filtering, inverse transformations, and comparative visualizations.
