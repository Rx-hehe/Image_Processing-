
# Lab 4: Intensity Transformations & Histogram Enhancement

This laboratory assignment explores the mechanics of point-based intensity domain processing, focusing on percentile-based contrast stretching, global histogram equalization, and multi-channel histogram specification (matching).

## Implemented Operations & Key Observations

### 1. Percentile-Based Intensity Rescaling
* **Method:** Calculated the statutory 3rd and 80th intensity percentiles of the `moon` image data and linearly re-mapped that specific window to occupy the full dynamic range (0 to 255).
* **Observation:** Effectively clipped extreme outlier values while maximizing structural micro-contrast within the selected band. The resulting histogram stretched outward, making under-exposed structural details highly visible across the surface terrain.

### 2. Histogram Equalization (Flattening)
* **Method:** Applied global non-linear mapping using the `exposure.equalize_hist` algorithm to redistribute intensity distributions across a uniform probability density function.
* **Observation:** Linearized the cumulative distribution function (CDF), producing a flattened, spread-out histogram profile. While it vastly improved global visibility and contrast, it introduced minor quantization artifacts and noise amplification in uniform regions.

### 3. Histogram Specification & Matching
* **Method:** Evaluated the cumulative distribution functions of the 3-channel RGB `chelsea` (source) and `rocket` (reference) images, translating the color profiles of the source to align with the geometric contrast properties of the template.
* **Observation:** Successfully forced the source profile to adapt to the target's lighting characteristics. The matched image adopted the distinct color cast and ambient tone of the reference profile while perfectly maintaining its original spatial features and structures.

## Dependencies

The following Python libraries are required to run this lab:
* `opencv-python`
* `scikit-image`
* `matplotlib`
* `numpy`

## File Index

* [Lab4_Intensity_Transformation.ipynb](Lab4_Intensity_Transformations_&Filtering_Spatial_Domain.ipynb) — Complete Jupyter execution notebook containing image processing pipelines, intensity transformations, and comparative side-by-side histogram visualizations.
