# Multidimensional-Arrays

## Introduction:

### Examples:

**2D Array:**

A conventional chessboard features 8 rows and 8 columns, making it a prime candidate for representation through an 8x8 two-dimensional array. This array structure allocates 8 rows, with each having the capacity to store 8 elements.

**3D Array:**

In computer vision and digital image processing, the RGB channels of a colored image are described by triplets of red, green, and blue values. By combining these pixel representations, a comprehensive 3D array is formed, capturing the complete color spectrum of the entire image.

### Declaring and Initializing Multidimensional Arrays:

In Python, we can use the "numpy" library for array operations and numerical computing.

- **Initializing a 2D numpy array (Matrix):**

```python
import numpy as np
arr2d = np.array([[1, 2, 3], [4, 5, 6]])  # Each inner list represents a row of the array, and the outer list contains all the rows
print(arr2d)
