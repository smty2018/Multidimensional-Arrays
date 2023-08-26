# Multidimensional-Arrays

## Introduction:

A multidimensional array, often denoted as `A[i, j, k, ...]`, is a structured data arrangement within a grid-like construct spanning multiple dimensions. Elements within this structure are pinpointed by an array of indices `(i, j, k, ...)` that define their unique positions within the array. 

The generic form of a multidimensional array with dimensions `d1, d2, ..., dn` can be expressed as:
```python
A[i1, i2, ..., in]
```

Here, the constraints  `0 ≤ i1 < d1, 0 ≤ i2 < d2, ..., 0 ≤ in < dn ` dictate the valid range for each index. The symbol `di` signifies the size of the i-th dimension, while the indices  `i1, i2, ...,` in dictate the exact element's location within each dimension.

#### Examples:

**2D Array:**

A conventional chessboard features 8 rows and 8 columns, making it a prime candidate for representation through an 8x8 two-dimensional array. This array structure allocates 8 rows, with each having the capacity to store 8 elements.
![Screenshot 2023-08-25 231524](https://github.com/smty2018/Multidimensional-Arrays/assets/74114936/a332e7ca-7098-4192-9960-b311268e8f85)

**3D Array:**

In computer vision and digital image processing, the RGB channels of a colored image are described by triplets of red, green, and blue values. By combining these pixel representations, a comprehensive 3D array is formed, capturing the complete color spectrum of the entire image.
![image-2](https://github.com/smty2018/Multidimensional-Arrays/assets/74114936/284e6507-7297-4474-ac81-7a950dfe8ba6)


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

    - **Row-major format:** Used in C.![Screenshot 2023-08-25 224129](https://github.com/smty2018/Multidimensional-Arrays/assets/74114936/be399197-2459-4176-b884-9039600bbc56)

    - **Column-major format:** Used in languages like Fortran.![Screenshot 2023-08-25 224232](https://github.com/smty2018/Multidimensional-Arrays/assets/74114936/4b4d72be-3532-4c1c-a7c7-f39748a8fa01)

NumPy arrays can adopt either format using the keyword arguments `order='C'` for row-major (default) or `order='F'` for column-major.

- **Strides and Memory Offset:** Each dimension in a NumPy array is associated with a **"stride,"** which represents the number of bytes to move to the next element along that dimension. The `ndarray.strides` attribute in NumPy defines these strides as a tuple with a length equal to the number of dimensions. The values within the strides tuple act as multipliers for each axis index. 

    For example, if you have a NumPy array `arr` with strides `(stride_dim1, stride_dim2, ...)`, accessing `arr[i, j]` involves moving `i * stride_dim1 + j * stride_dim2` bytes from the start of the array to reach the desired element.
   <br> 

  ```python
  >>>import numpy as np
  array_3d = np.array([
    [[1, 2, 3],
     [4, 5, 6]],
    [[7, 8, 9],
     [10, 11, 12]]
   ])
  array_3d_strides = array_3d.strides

  print("3D Array Strides:", array_3d_strides)
  ```


  Output:

  <br>

  ```python
  >>>3D Array Strides: (48, 24, 8) #tuple representing the memory steps (in bytes) needed to move along each dimension of the array.
  ```

- **Views**: Slicing or indexing an array doesn't create a new array but  rather a `view` into the original array's data. This view shares the same memory with the original array, making it memory-efficient

  <br>

   ```python
      import numpy as np
      original_array = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
      array_view = original_array[1:, 1:]
      array_view[0, 0] = 10

      print("Original Array:\n", original_array)
      print("View Array:\n", array_view)
   ```


   Output:

   ```python
      Original Array:
      [[ 1  2  3]
      [ 4 10  6]
      [ 7  8  9]]
      View Array:
      [[10  6]
      [ 8  9]]
  ```
  <br>
- **Memory overhead**:

   Numpy arrays are memory-efficient but might have overhead compared to raw Python lists due to stored information like data type and shape.
<br>

   ```python
   import numpy as np
   numpy_array = np.array([[1, 2, 3], [4, 5, 6]])
   python_list = [[1, 2, 3], [4, 5, 6]]
   print("2D NumPy Array Memory Usage:", numpy_array.nbytes)
   print("Nested Python List Memory Usage:", python_list.__sizeof__())
   ```


  Output:

  ```python
   2D NumPy Array Memory Usage: 48
   Nested Python List Memory Usage: 56
   ```

## Accessing Elements in Multidimensional Arrays

Accessing elements in multidimensional arrays involves using indices to locate values within the array. Each dimension has its index. For example, in a 2D array, `array[i][j]` gets the element at row `i`, column `j`. In NumPy, you can use `array[i, j]` for the same purpose. Indices start at 0.



- **3D Array**

   ```python


   import numpy as np
   array_3d = np.array([
       [[1, 2, 3], [4, 5, 6]],
       [[7, 8, 9], [10, 11, 12]]
   ])

   access_3d = lambda i, j, k: array_3d[i, j, k]

   element_3d = access_3d(1, 0, 2)
   print("3D Array - Element at (1, 0, 2):", element_3d)
  ```

  Output:

  ```python
   3D Array - Element at (1, 0, 2): 9
  ```

- **N-dimensional Arrays**

   ```python
   import numpy as np

   n_dim = np.arange(24).reshape(2, 3, 4) 

   access_n_dim = lambda indices: n_dim[tuple(indices)]

   element_n_dim = access_n_dim([1, 2, 3])
   print("n-Dimensional Array - Element at (1, 2, 3):", element_n_dim)
  ```

  Output:

   ```python
   n-Dimensional Array - Element at (1, 2, 3): 23
   ```
<br>

## Indexing and Slicing Multidimensional Arrays:

Slicing is a way to access and modify multiple elements within a multidimensional array simultaneously. The notation `arr[i:j, k:l]` allows us to work with a subarray spanning rows `i` to `j-1` and columns `k` to `l-1`.
<br>
```python
import numpy as np

data = np.array([[0, 1, 2, 3],
                 [4, 5, 6, 7],
                 [8, 9, 10, 11],
                 [12, 13, 14, 15]])

upper_half_diag = data[:3, :3]
print("Upper Half Diagonal Block Matrix:\n", upper_half_diag)
```

Output:
```python
Upper Half Diagonal Block Matrix:
 [[ 0  1  2]
 [ 4  5  6]
 [ 8  9 10]]
```


## Operations on Multidimensional Arrays:



| Function/Method      | Description with Examples                                         |
|----------------------|--------------------------------------------------------------------|
| `np.transpose()`     | Transposes the array, swapping rows with columns.                  |
|                      | `np.transpose(array)`                                              |
| `array.flatten()`    | Flattens the array into a 1D array.                                |
|                      | `flattened = array.flatten()`                                      |
| `array.ravel()`      | Flattens the array into a 1D array, returns a view if possible.   |
|                      | `raveled = array.ravel()`                                         |
| `np.vstack()`        | Stacks arrays vertically (along rows).                            |
|                      | `stacked = np.vstack((array1, array2))`                           |
| `np.hstack()`        | Stacks arrays horizontally (along columns).                       |
|                      | `stacked = np.hstack((array1, array2))`                           |
| `np.concatenate()`   | Concatenates arrays along a specified axis.                        |
|                      | `concatenated = np.concatenate((array1, array2), axis=0)`         |
| `np.split()`         | Splits an array into multiple sub-arrays along a specified axis.   |
|                      | `sub_arrays = np.split(array, 3, axis=0)`                         |
| `array.mean()`       | Computes the mean along a specified axis.                         |
|                      | `mean_value = array.mean(axis=0)`                                 |

## Summary

These multidimensional arrays are pivotal in mathematics, computer science, and scientific computing, offering a means to manage and manipulate data involving multiple dimensions and enables efficient computation in fields like image processing, offering insights through data selection, manipulation, and analysis.

