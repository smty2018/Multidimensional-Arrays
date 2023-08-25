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
```

Output:

```python
[[1 2 3]
 [4 5 6]]
```
- **Initializing a 3D numpy array (Matrix):**

```python
arr3D = np.array([    # The outermost list represents different "layers"
                         # Each layer is a 2D array (matrix)
    [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]],

    [[10, 11, 12],
     [13, 14, 15],
     [16, 17, 18]],

    [[19, 20, 21],
     [22, 23, 24],
     [25, 26, 27]]
])
```

## Memory Allocation in NumPy Arrays

- **Contiguous Memory Layout:** NumPy arrays are designed to have a **contiguous memory layout**. This means that the elements of the array are stored in a continuous block of memory.

- **Row-Major and Column-Major Formats:** There are two ways to store multi-dimensional arrays:

    - **Row-major format:** In this format, elements along the rows are stored together in memory. It is used in languages like C.
    
    - **Column-major format:** In this format, elements along the columns are stored together. It is used in languages like Fortran.

NumPy arrays can adopt either format using the keyword arguments `order='C'` for row-major (default) or `order='F'` for column-major.

- **Strides and Memory Offset:** Each dimension in a NumPy array is associated with a **"stride,"** which represents the number of bytes to move to the next element along that dimension. The `ndarray.strides` attribute in NumPy defines these strides as a tuple with a length equal to the number of dimensions. The values within the strides tuple act as multipliers for each axis index. This determines the memory offset in bytes when calculating index expressions.

    For example, if you have a NumPy array `arr` with strides `(stride_dim1, stride_dim2, ...)`, accessing `arr[i, j]` involves moving `i * stride_dim1 + j * stride_dim2` bytes from the start of the array to reach the desired element.



