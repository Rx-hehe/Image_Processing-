# Image Processing Coursework

Welcome to my repository for the Image Processing curriculum. This space contains all of my laboratory assignments, source code, and practical image-manipulation pipelines.

## 🛠️ Environment & Core Tools

* **Language:** Python 3
* **Libraries:** OpenCV (`cv2`), NumPy, Pillow (`PIL`), Scikit-Image (`skimage`), Matplotlib

## 📂 Course Directory

* **Lab 1:** Submitted directly to course portal.
* **Lab 2: Image Sampling, Quantization & Arithmetic**
  * Analyzed spatial and intensity resolutions.
  * Implemented pixel-level saturated arithmetic and grayscale bitwise set operations.
* **Lab 3: Spatial Filtering & Image Enhancement**
  * Explored linear smoothing filters (Mean and Gaussian) along with non-linear Median filters to analyze noise reduction trade-offs.
  * Implemented first-derivative Sobel gradients, isotropic Laplacian operators, and the Canny edge-detection pipeline.
  * Executed high-boost filtering using an unsharp mask to amplify subtle micro-contrasts and structural details.
* **Lab 4: Intensity Transformations & Histogram Enhancement**
  * Applied percentile-based intensity rescaling between the 3rd and 80th percentiles to stretch image contrast.
  * Implemented global histogram equalization to flatten intensity profiles and linearize cumulative distribution functions.
  * Executed multi-channel histogram specification to match color profiles between source and reference templates.
* **Lab 5: Spatial Filtering & Image Sharpening**
  * Constructed manual 7×7 box averaging kernels alongside automated 5×5 and 21×21 Gaussian bell-curve smoothing operations.
  * Implemented discrete second-order isotropic Laplacian derivative filters and high-frequency unsharp masking pipelines.
  * Evaluated non-linear spatial restorations using structural median filtering against salt-and-pepper noise alongside edge-preserving photometric bilateral smoothing.
* **Lab 6: Frequency Domain Filtering**
  * Explored two-dimensional Fourier-domain image processing and the relationship between spatial convolution and frequency-domain multiplication.
  * Implemented Laplacian filtering directly in the frequency domain to emphasize high-frequency intensity transitions and edge structure.
  * Converted horizontal and vertical Sobel kernels into frequency responses and combined their inverse-transformed outputs to generate a full edge-magnitude image.
* **Lab 7: Image Segmentation & Feature Extraction**
  * Applied Canny edge detection with double thresholding and hysteresis to identify sharp image boundaries.
  * Detected Harris corners on a checkerboard image and visualized strong corner responses with red markers.
  * Used Otsu's automatic thresholding to segment a grayscale image and compared the original, intensity histogram, and binary result.
