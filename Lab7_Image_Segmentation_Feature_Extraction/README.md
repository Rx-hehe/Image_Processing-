# Lab 7: Image Segmentation & Feature Extraction

This laboratory assignment explores edge detection, corner detection, and automatic image thresholding using OpenCV. The exercises demonstrate how intensity changes can be used to identify image boundaries, distinctive feature points, and foreground regions.

## Implemented Operations & Key Observations

### 1. Canny Edge Detection
* **Method:** Loaded the grayscale `camera` image from `skimage.data` and applied `cv2.Canny(img, 100, 200)` to detect edges. Canny uses Gaussian smoothing, gradient estimation, non-maximum suppression, double thresholding, and hysteresis.
* **Observation:** The resulting binary edge map highlights sharp intensity transitions while suppressing much of the smooth background. The lower and upper thresholds help distinguish weak from strong edge candidates.

### 2. Harris Corner Detection
* **Method:** Loaded a checkerboard image, converted it to BGR, resized it to 400×400 pixels, and calculated the Harris response with `cv2.cornerHarris(gray, blockSize=2, ksize=3, k=0.04)`. Selected responses above 1% of the maximum and marked the detected locations with filled red circles.
* **Observation:** Strong corner responses appear around intersections where intensity changes in two directions. These points are useful as distinctive image features, unlike flat regions or single-direction edges.

### 3. Otsu's Automatic Thresholding (Assessment Task)
* **Method:** Applied `cv2.threshold(img, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)` to select a grayscale threshold automatically. Displayed the original image, its 256-bin intensity histogram with the selected threshold marked, and the resulting binary image.
* **Observation:** Otsu's method separates pixels into two intensity classes without requiring a manually chosen threshold. It is most effective when the image histogram contains reasonably distinct foreground and background intensity groups.

## Key Concepts

* **Edges** correspond to rapid brightness changes and are detected by the Canny pipeline.
* **Corners** exhibit intensity variation in two directions and can be located using the Harris response.
* **Otsu's thresholding** chooses a threshold by maximizing between-class variance.
* OpenCV uses **BGR** channel ordering for color images, so `(0, 0, 255)` draws red markers.

## Dependencies

The following Python libraries are required to run this lab:

* `opencv-python`
* `numpy`
* `matplotlib`
* `scikit-image`

## File Index

* [Lab7_Image_Segmentation_Feature_Extraction.ipynb](Lab7_Image_Segmentation_Feature_Extraction.ipynb) — Jupyter notebook covering Canny edge detection, Harris corner detection, and Otsu's automatic thresholding assessment.
