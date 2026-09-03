# Programming Assignment 2: Numerical Python (NumPy)

#### NAME: Sen Airish B. Bravo

#### 2ECE-C

## Objectives:

1. create and reshape NumPy arrays using appropriate NumPy functions;
2. perform vectorized numerical operations on an ndarray;
3. compute array statistics and use Boolean conditions to select elements; and
4. save computed NumPy arrays as `.npy` files.

---

## A. Reproducible Normalization Problem

Create a reproducible random 5 × 5 integer ndarray named `X`. The array is generated using NumPy's random functions with a specified seed.

The complete array is then normalized using the formula:

**Z = (X - x̄) / σ**

where:

* `x̄` is the mean of all 25 elements.
* `σ` is the population standard deviation of the array.

### NumPy Functions and Concepts Used

* `np.random.seed(2112)` - sets the random seed so that the same random numbers are generated every time the code is run. This makes the result reproducible.

* `np.random.randint(10, 101, size=(5, 5))` - generates random integers from 10 up to 100 and creates them in a 5 × 5 array.

* `np.mean(X)` - calculates the mean or average of all elements in the array.

* `np.std(X)` - calculates the standard deviation of the elements in the array. NumPy's default `std()` calculates the population standard deviation.

* `(X - x) / o` - performs vectorized arithmetic on the entire array without needing a loop. Each element is subtracted by the mean and divided by the standard deviation.

* `np.save()` - saves a NumPy array into a `.npy` file.

### Code

```python
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
X
```

```python
x = np.mean(X)
x
```

```python
o = np.std(X)
o
```

```python
Z = (X - x) / o
Z
```

```python
X_normalized = Z
X_normalized
```

```python
X
```

```python
xn = np.mean(Z)
xn
```

```python
xstd = np.std(Z)
xstd
```

The normalized array has a mean of approximately `0` and a standard deviation of approximately `1`.

```python
np.save('X_normalized.npy', X_normalized)
```

---

## B. Cubes Divisible by 4 Problem

Create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named `C`.

A Boolean condition is then used to select only the cubed values that are divisible by 4.

### NumPy Functions and Concepts Used

* `np.arange(1, 101)` - creates an array containing the integers from 1 to 100.

* `n ** 3` - raises every element of the array to the third power, producing the cubes of the numbers.

* `.reshape(10, 10)` - changes the shape of the one-dimensional array into a 10 × 10 array while maintaining the original row-major order.

* `C % 4 == 0` - uses the modulo operator to check which elements have a remainder of `0` when divided by 4. These are the values divisible by 4.

* `C[C % 4 == 0]` - uses Boolean indexing to select only the elements that satisfy the condition.

* `.size` - returns the total number of elements in the selected array.

* `np.save()` - saves the selected NumPy array as a `.npy` file.

### Code

```python
n = np.arange(1, 101)
cubed = n ** 3
C = cubed.reshape(10, 10)
C
```

```python
print("Shape of C: ", C.shape)
```

```python
div_by_4 = C[C % 4 == 0]
div_by_4
```

```python
print("number of selected elements:", div_by_4.size)
```

The result contains **50 selected elements**, with the first value being `8` and the last value being `1000000`.

```python
np.save('div_by_4.npy', div_by_4)
```

---

## C. Above-Mean Squares Problem

Create a 6 × 6 ndarray named `S` containing the squares of the first 36 positive integers.

The mean of all the elements in `S` is then calculated. Boolean filtering is used to select only the elements that are **strictly greater than the mean**.

### NumPy Functions and Concepts Used

* `np.arange(1, 37)` - creates an array containing the integers from 1 to 36.

* `n ** 2` - raises every element to the second power, producing the squares of the numbers.

* `.reshape(6, 6)` - changes the one-dimensional array into a 6 × 6 array while preserving the order of the elements.

* `np.mean(S)` - calculates the mean of all elements in the array.

* `S > S_mean` - creates a Boolean condition that identifies elements greater than the calculated mean.

* `S[S > S_mean]` - uses Boolean indexing to select only the elements that satisfy the condition.

* `.size` - determines the number of elements selected by the Boolean condition.

* `np.save()` - saves the resulting NumPy array into a `.npy` file.

### Code

```python
n = np.arange(1, 37)
n
```

```python
s = n ** 2
s
```

```python
S = s.reshape(6, 6)
S
```

```python
S_mean = np.mean(S)
S_mean
```

```python
above_mean = S[S > S_mean]
above_mean
```

```python
print('Number of selected elements:', above_mean.size)
```

The result contains **15 selected elements**, with the first value being `484` and the last value being `1296`.

```python
np.save('above_mean.npy', above_mean)
```

---

## README File Version History
03/09/2026

**September 3, 2026** - Initial README output uploaded.
