# Reading 11 
> Jupyter
- JupyterLab is a next-generation web-based user interface for Project Jupyter. 

> NumPy 'Numerical Python'
- pip install numpy
- NumPy is a commonly used Python data analysis package. By using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem 

> Operations using NumPy 
- Mathematical and logical operations on arrays. 
- Fourier's transforms and routines for shape manipulation.
- Operations related to linear algebra. NumPy has in-built functions for linear algebra and random number generation
- **NumPy is often used along with packages like SciPy (Scientific Python) and Mat−plotlib (plotting library).**

> NumPy - Ndarray Object 
```
import numpy as np 
a = np.array([1,2,3]) 
print a
>>> [1, 2, 3]
```

> Data Type Objects (dtype) 
- Type of data (integer, float or Python object)
- Size of data
- Byte order (little-endian or big-endian)
- In case of structured type, the names of fields, data type of each field and part of the memory block taken by each field.
- If data type is a subarray, its shape and data type
- numpy.dtype(object, align, copy) 
  - Object − To be converted to data type object
  - Align − If true, adds padding to the field to make it similar to C-struct
  - Copy − Makes a new copy of dtype object. If false, the result is reference to builtin data type object
  
```
# using array-scalar type 
import numpy as np 
dt = np.dtype(np.int32) 
print dt
output will be 
>>> int32
```

> NumPy - Array Attributes 
- ndarray.shape
  - This array attribute returns a tuple consisting of array dimensions. It can also be used to resize the array.
- ndarray.ndim 
  - This array attribute returns the number of array dimensions.
- numpy.itemsize 
  - This array attribute returns the length of each element of array in bytes.
- numpy.flags 
  - The ndarray object has the following attributes. Its current values are returned by this function.


> The ndarray object has the following attributes. Its current values are returned by this function.
- numpy.empty
  - It creates an uninitialized array of specified shape and dtype. It uses the following constructor
- numpy.zeros
  - Returns a new array of specified size, filled with zeros.
- numpy.ones
  - Returns a new array of specified size and type, filled with ones.

    
> I/O with NumPy 
- numpy.save() 
  - The numpy.save() file stores the input array in a disk file with npy extension.
```
import numpy as np 
a = np.array([1,2,3,4,5]) 
np.save('outfile',a)

import numpy as np 
b = np.load('outfile.npy') 
print b 
It will produce the following output −

array([1, 2, 3, 4, 5])
```

- savetxt() 
  - The storage and retrieval of array data in simple text file format is done with savetxt() and loadtxt() function
```
import numpy as np 
a = np.array([1,2,3,4,5]) 
np.savetxt('out.txt',a) 
b = np.loadtxt('out.txt') 
print b 
It will produce the following output −

[ 1. 2. 3. 4. 5.]
```

> Resources
- https://www.tutorialspoint.com/numpy/numpy_useful_resources.htm 
- https://www.tutorialspoint.com/numpy/numpy_with_io.htm
- https://numpy.org/doc/stable/reference/ 