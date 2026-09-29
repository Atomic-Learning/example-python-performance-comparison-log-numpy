This page compares the performance of calculating logarithms using Python's `math` module versus NumPy's `np.log()` function for both single scalar values and arrays of values.

# Scalar Logarithm Comparison

In this section, we will repeatedly calculate the logarithm of a single scalar value using both Python's `math.log()` and NumPy's `np.log()` to compare their performance.

## Native Python Implementation

```py-cell
import time
import math

repetitions = 1000000

start_time = time.time()
for i in range(repetitions):
  c = math.log(2)
## print('Non-NumPy single log:', time.time() - start_time)
```

## NumPy Implementation

```py-cell
import time
import numpy as np

repetitions = 1000000

start_time = time.time()
for i in range(repetitions):
  c = np.log(2)
print('NumPy single log:', time.time() - start_time)
```

## Discussion

For a single scalar value, the `math.log()` function is typically faster than `np.log()`. This is because `np.log()` is designed to handle arrays and includes additional overhead as a result, which is unnecessary for a single value. This overhead is not present when using `math.log()`.

# Array Logarithm Comparison

In this section, we will repeatedly calculate the logarithm of an array of values using both Python's `math.log()` applied element-wise and NumPy's `np.log()` to compare their performance.

## Native Python Implementation

```py-cell
import time
import math

a = list(range(1, 10000))

repetitions = 1000

start_time = time.time()
for i in range(repetitions):
  c = list(map(math.log, a))
print('Non-NumPy log of list:', time.time() - start_time)
```

## NumPy Implementation

```py-cell
import time
import numpy as np

b = np.arange(1, 10000)
repetitions = 1000

start_time = time.time()
for i in range(repetitions):
  c = np.log(b)
print('NumPy log of array:', time.time() - start_time)
```

## Discussion

For an array of values, `np.log()` is significantly faster than applying `math.log()` to each element individually. This is because `np.log()` is vectorised: it performs the logarithm calculation on all elements at once using optimised compiled code.

# Choosing the Right Function

If you are working exclusively with single scalar values, it is generally better to use Python's `math.log()` for simplicity and performance.

However, if you are working with arrays of values, it is generally better to use NumPy's `np.log()` for improved performance due to its vectorised operations.