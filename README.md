## Workflow of the Grayscale Histogram Script

1. **Import Required Libraries**

   ```python
   import cv2
   import numpy as np
   from matplotlib import pyplot as plt
   ```

   * **cv2**: OpenCV module for reading and displaying images.
   * **numpy**: Used here implicitly by OpenCV image arrays.
   * **matplotlib.pyplot**: For plotting the intensity histogram.

2. **Load Images in Grayscale**

   ```python
   img1 = cv2.imread(r'Histogram\1.jpg', cv2.IMREAD_GRAYSCALE)
   img2 = cv2.imread(r'Histogram\2.jpg', cv2.IMREAD_GRAYSCALE)
   img3 = cv2.imread(r'Histogram\3.jpg', cv2.IMREAD_GRAYSCALE)
   ```

   * Each call to `cv2.imread(..., cv2.IMREAD_GRAYSCALE)` returns a single-channel 2D array (values 0–255).

3. **Display Each Grayscale Image**

   ```python
   cv2.imshow('Grayscale1', img1)
   ```

   * Opens a window titled “Grayscale1” and shows the first image’s pixels.

4. **Compute & Plot the Histogram**

   ```python
   plt.hist(img1.ravel(), 256, [0, 256])
   plt.show()
   ```

   * **`img1.ravel()`** flattens the 2D image array into a 1D list of pixel values.
   * **`256`** is the number of bins (one for each possible intensity).
   * **`[0, 256]`** sets the range of values to cover 0 through 255.
   * `plt.show()` pops up the histogram plot.

5. **Repeat for the Other Images**

   ```python
   cv2.imshow('Grayscale2', img2)
   plt.hist(img2.ravel(), 256, [0, 256])
   plt.show()

   cv2.imshow('Grayscale3', img3)
   plt.hist(img3.ravel(), 256, [0, 256])
   plt.show()
   ```

   * Each image gets its own display window and histogram plot.

6. **Wait for Key Press & Cleanup**

   ```python
   cv2.waitKey(0)
   cv2.destroyAllWindows()
   ```

   * `cv2.waitKey(0)` pauses execution until you press any key inside an OpenCV window.
   * `cv2.destroyAllWindows()` closes all OpenCV windows opened by `imshow`.

---

### Full Example

```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# 1. Load in grayscale
img1 = cv2.imread(r'Histogram\1.jpg', cv2.IMREAD_GRAYSCALE)
img2 = cv2.imread(r'Histogram\2.jpg', cv2.IMREAD_GRAYSCALE)
img3 = cv2.imread(r'Histogram\3.jpg', cv2.IMREAD_GRAYSCALE)

# 2–5. Show each image and its histogram
for idx, img in enumerate([img1, img2, img3], start=1):
    cv2.imshow(f'Grayscale{idx}', img)
    plt.hist(img.ravel(), 256, [0, 256])
    plt.title(f'Histogram of Image {idx}')
    plt.xlabel('Pixel Intensity')
    plt.ylabel('Frequency')
    plt.show()

# 6. Wait and clean up
cv2.waitKey(0)
cv2.destroyAllWindows()
```
