# 🧠 Multi-Method Image Completion and Object Removal  
_Using Template Matching, Texture Synthesis, and PatchMatch_

This project implements advanced image processing techniques for object detection, texture synthesis, and image inpainting — all without deep learning. It combines **classical computer vision** methods with **GPU-accelerated texture synthesis** and **PatchMatch**-based image completion to remove and restore objects in images seamlessly.

---

## 📂 Project Overview

### 🔹 Section 1: Object Detection via Template Matching
Finds instances of a given template (`template.png`) within a target image (`input.jpg`) using correlation-based template matching methods:
- Cross Correlation
- Zero-Mean Cross Correlation
- Sum of Squared Differences (SSD)
- Normalized Cross Correlation (default)

Detected objects are outlined (or masked) and saved as `output1.jpg`.

---

### 🔹 Section 2: Image Completion Methods

#### **1. Texture Synthesis**
Implements Efros & Freeman’s **Image Quilting** approach to generate larger texture maps from small samples.  
Reference: [Image Quilting for Texture Synthesis and Transfer](https://people.eecs.berkeley.edu/~efros/research/quilting/quilting.pdf)

- Generates high-resolution synthetic textures (`2400x2400`) from small inputs.
- GPU acceleration using **PyTorch**.
- Adaptive patch blending with **minimum error boundary cuts**.

#### **2. PatchMatch**
Implements the **PatchMatch algorithm** for fast image inpainting and texture transfer.  
Reference: [Barnes et al., PatchMatch: A Randomized Correspondence Algorithm for Structural Image Editing](https://gfx.cs.princeton.edu/pubs/Barnes_2009_PAR/patchmatch.pdf)

Used to:
- Fill missing or masked areas.
- Remove unwanted objects (e.g., boats) and reconstruct the background naturally.

---

### 🔹 Section 3: Object Removal & Completion
Combines template matching (from Section 1) and inpainting (from Section 2) to:
1. Detect target objects.
2. Mask them out.
3. Fill the removed regions using **PatchMatch** or **Texture Synthesis**.

Final result saved as `output-complete.jpg`.

---

## 🧰 Tech Stack

| Library | Purpose |
|----------|----------|
| **OpenCV** | Image I/O, template matching, drawing, and inpainting |
| **NumPy** | Array operations and numerical processing |
| **Matplotlib** | Visualization and result display |
| **PIL (Pillow)** | Image cropping and manipulation |
| **tqdm** | Progress bars for iterative synthesis |
| **PyTorch** | GPU acceleration for texture synthesis |
| **Numba** | Just-In-Time compilation for optimized loops |

