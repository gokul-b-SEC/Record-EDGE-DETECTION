# EXNO.6 – Edge Detection

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm

1. Import all the necessary modules for the program.
2. Load an image using `cv2.imread()`.
3. Convert the image to grayscale.
4. Apply the **Sobel Operator** using OpenCV to detect edges.
5. Apply the **Prewitt Operator** using custom kernels.
6. Apply the **Roberts Operator** using custom kernels.
7. Apply the **Laplacian Operator** using OpenCV.
8. Apply the **Canny Edge Detector** using OpenCV.
9. Display all edge-detected images for comparison.

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
image = cv2.imread('zebra.jpg')

# Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

# 1. Sobel Edge Detection
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)

# Combine both directions
sobel_combined = cv2.magnitude(sobel_x, sobel_y)

plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')

# 2. Laplacian Edge Detection
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()

# 3. Canny Edge Detection
canny_edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

## Output

The following screenshots show the original image and the results obtained using different edge detection techniques.

### 1. Original Image

<img width="515" height="370" alt="image" src="https://github.com/user-attachments/assets/8082b23b-33c0-4c1e-8790-b1c92796fd62" />


### 2. Sobel Edge Detection

<img width="515" height="370" alt="image" src="https://github.com/user-attachments/assets/f0a25426-4584-46ed-a548-96365d5c1187" />


### 3. Laplacian Edge Detection

<img width="515" height="370" alt="image" src="https://github.com/user-attachments/assets/91b80d0d-f361-46dc-8856-8a1e5c4d5421" />


### 4. Canny Edge Detection

<img width="515" height="370" alt="image" src="https://github.com/user-attachments/assets/e640bf11-5aff-442c-9caf-7872edb037e7" />


## Result

Thus, edge detection was implemented using Sobel, Laplacian, and Canny operators in OpenCV. These techniques identify boundaries and intensity changes in an image, helping in image analysis and feature extraction.
