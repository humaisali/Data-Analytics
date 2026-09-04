
# NumPy Basics for Lab Tasks

---

# 1. What is NumPy?

**NumPy** stands for **Numerical Python**.

It is a Python library mainly used for:

- Working with arrays
- Mathematical calculations
- Matrix operations
- Data analysis
- Scientific computing

We normally import NumPy like this:

```python
import numpy as np
```

Here:

```python
numpy → actual library
np    → short name / alias
```

So instead of writing:

```python
numpy.array()
```

we write:

```python
np.array()
```

---

# 2. What is a NumPy Array?

A NumPy **array** is a collection of values stored together.

For example:

```python
import numpy as np

arr = np.array([10, 20, 30, 40])
```

The array contains:

```text
10 20 30 40
```

Unlike normal Python lists, NumPy arrays are designed specifically for fast numerical operations.

---

# 3. One-Dimensional Array

Example:

```python
arr = np.array([10, 20, 30, 40, 50])
```

Visually:

```text
[10 20 30 40 50]
```

This is a **1D array**.

Its dimension is:

```text
1
```

---

# 4. Two-Dimensional Array

A two-dimensional array contains rows and columns.

Example:

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```

Visually:

```text
1  2  3
4  5  6
```

It has:

- `2` rows
- `3` columns

Therefore its shape is:

```text
(2, 3)
```

---

# Lab Task 1

## Create a 2×2 Array Filled with Roll Number Using `full()`

First understand what **2×2** means.

A 2×2 array has:

```text
2 rows
2 columns
```

Example:

```text
282  282
282  282
```

NumPy provides a built-in function called:

```python
np.full()
```

Its job is:

> Create an array of a specified shape and fill every position with the same value.

---

## Syntax

```python
np.full(shape, value)
```

For example:

```python
np.full((2, 2), 282)
```

Here:

```text
(2, 2)
  ↓
2 rows and 2 columns

282
 ↓
Value placed in every position
```

Result:

```text
[[282 282]
 [282 282]]
```

So conceptually:

```python
np.full((2, 2), roll_number)
```

means:

> Create a 2-row, 2-column array and fill every location with my roll number.

---

# Your Lab Task 2

## Create a 5×5 Identity Matrix Using `np.eye()`

First understand an **identity matrix**.

An identity matrix is a square matrix where:

- Main diagonal contains `1`
- Every other position contains `0`

For example, a 3×3 identity matrix is:

```text
1  0  0
0  1  0
0  0  1
```

Notice the diagonal:

```text
1
   1
      1
```

---

## 5×5 Identity Matrix

It looks like:

```text
1 0 0 0 0
0 1 0 0 0
0 0 1 0 0
0 0 0 1 0
0 0 0 0 1
```

NumPy provides:

```python
np.eye()
```

Example:

```python
np.eye(5)
```

means:

> Create an identity matrix having 5 rows and 5 columns.

The default values are usually floating-point numbers:

```text
[[1. 0. 0. 0. 0.]
 [0. 1. 0. 0. 0.]
 [0. 0. 1. 0. 0.]
 [0. 0. 0. 1. 0.]
 [0. 0. 0. 0. 1.]]
```

The dot in:

```text
1.
0.
```

means they are floating-point numbers.

---

# Your Lab Task 3

## Create an Integer Array of 5 Elements and Find Its Properties

Suppose:

```python
arr = np.array([10, 20, 30, 40, 50])
```

Now we want to understand several properties.

---

# 1. Shape — `.shape`

Shape tells us:

> How many elements exist along each dimension?

For:

```python
[10, 20, 30, 40, 50]
```

there are `5` elements.

Therefore:

```python
arr.shape
```

returns:

```text
(5,)
```

The comma indicates that this is a **one-dimensional array** containing 5 elements.

---

# 2. Size — `.size`

The `size` property tells us:

> Total number of elements present in the array.

Example:

```python
arr.size
```

For:

```text
[10 20 30 40 50]
```

the answer is:

```text
5
```

Because there are five values.

---

# 3. Dimension — `.ndim`

The `ndim` property tells us:

> How many dimensions does the array have?

Example:

```python
arr.ndim
```

For:

```text
[10 20 30 40 50]
```

the result is:

```text
1
```

Because it is a one-dimensional array.

---

## Example with 2D

```python
arr = np.array([
    [1, 2],
    [3, 4]
])
```

Here:

```python
arr.ndim
```

returns:

```text
2
```

---

# 4. Data Type — `.dtype`

The `dtype` property tells us:

> What type of data is being stored inside the NumPy array?

Example:

```python
arr.dtype
```

You might get something like:

```text
int64
```

or:

```text
int32
```

depending on your system.

Meaning:

```text
int → integer
64  → 64 bits
```

---

# 5. Total Bytes Consumed — `.nbytes`

The `nbytes` property tells us:

> Total memory consumed by all elements of the array.

Example:

```python
arr.nbytes
```

Suppose the array contains:

```text
5 elements
```

and each integer consumes:

```text
8 bytes
```

Then:

```text
5 × 8 = 40 bytes
```

So:

```python
arr.nbytes
```

would return:

```text
40
```

This can differ depending on the array's data type.

---

# 6. Size of One Element — `.itemsize`

The `itemsize` property tells us:

> How many bytes are required to store one element?

Example:

```python
arr.itemsize
```

If the data type is:

```text
int64
```

one element usually consumes:

```text
8 bytes
```

Therefore:

```text
arr.itemsize = 8
```

---

# Important Difference: `size`, `itemsize`, and `nbytes`

These three names can initially be confusing.

Suppose:

```python
arr = np.array([10, 20, 30, 40, 50])
```

and each element takes `8 bytes`.

| Property      | Meaning                   | Example |
| ------------- | ------------------------- | ------: |
| `.size`     | Number of elements        |   `5` |
| `.itemsize` | Bytes used by one element |   `8` |
| `.nbytes`   | Total bytes used          |  `40` |

And:

```text
nbytes = size × itemsize
```

Therefore:

```text
40 = 5 × 8
```

---

# Your Lab Task 4

## Create a Two-Dimensional Array and Find Dimension, Shape, and Elements

Consider:

```python
arr = np.array([
    [10, 20, 30],
    [40, 50, 60]
])
```

It looks like:

```text
10  20  30
40  50  60
```

---

## Dimension

Using:

```python
arr.ndim
```

we get:

```text
2
```

Why?

Because the array has:

```text
Rows + Columns structure
```

It is therefore two-dimensional.

---

# Shape

Using:

```python
arr.shape
```

we get:

```text
(2, 3)
```

Meaning:

```text
2 rows
3 columns
```

Always remember:

```text
shape = (rows, columns)
```

So:

```text
(2, 3)
```

means:

```text
Rows    = 2
Columns = 3
```

---

# Accessing Elements in NumPy

Suppose:

```python
arr = np.array([
    [10, 20, 30],
    [40, 50, 60]
])
```

Array positions start from **0**.

So:

```text
        Column
        0   1   2

Row 0   10  20  30
Row 1   40  50  60
```

To access an element:

```python
arr[row, column]
```

For example:

```python
arr[0, 0]
```

gives:

```text
10
```

And:

```python
arr[0, 1]
```

gives:

```text
20
```

While:

```python
arr[1, 2]
```

gives:

```text
60
```

---

# NumPy Indexing Mental Model

For:

```python
arr = np.array([
    [10, 20, 30],
    [40, 50, 60]
])
```

Think:

```text
arr[0,0] = 10
arr[0,1] = 20
arr[0,2] = 30

arr[1,0] = 40
arr[1,1] = 50
arr[1,2] = 60
```

The first number identifies the **row**.

The second identifies the **column**.

---

# All Important NumPy Properties from This Lab

| NumPy Concept  | Purpose                                |
| -------------- | -------------------------------------- |
| `np.array()` | Creates an array                       |
| `np.full()`  | Creates an array filled with one value |
| `np.eye()`   | Creates an identity matrix             |
| `.shape`     | Gives array shape                      |
| `.size`      | Gives total number of elements         |
| `.ndim`      | Gives number of dimensions             |
| `.dtype`     | Gives data type                        |
| `.nbytes`    | Gives total memory consumed            |
| `.itemsize`  | Gives memory used by one element       |

---

# Very Important Visualization

Consider:

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```

### `.ndim`

```text
2
```

Because it is 2D.

### `.shape`

```text
(2, 3)
```

Because:

```text
2 rows
3 columns
```

### `.size`

```text
6
```

Because:

```text
2 × 3 = 6 elements
```

---

# Your Four Lab Tasks in Simple Words

### Task 1 — `full()`

Create:

```text
RollNo RollNo
RollNo RollNo
```

using:

```python
np.full()
```

---

### Task 2 — `eye()`

Create:

```text
1 0 0 0 0
0 1 0 0 0
0 0 1 0 0
0 0 0 1 0
0 0 0 0 1
```

using:

```python
np.eye()
```

---

### Task 3 — Array Properties

Create:

```text
[10 20 30 40 50]
```

and check:

```python
.shape
.size
.ndim
.dtype
.nbytes
.itemsize
```

---

### Task 4 — 2D Array

Create something like:

```text
10 20 30
40 50 60
```

and understand:

```python
.ndim
.shape
```

along with accessing its elements.

---

## Key Things to Remember for Lab/Viva

**NumPy** is a Python library used for numerical and array operations.

**`np.full()`** creates an array where every element contains the same value.

**`np.eye()`** creates an identity matrix.

**`.ndim`** tells the number of dimensions.

**`.shape`** tells the number of rows/columns or elements along each dimension.

**`.size`** tells the total number of elements.

**`.dtype`** tells the data type.

**`.itemsize`** tells the memory consumed by one element.

**`.nbytes`** tells the total memory consumed by the whole array.

The important memory relationship is:

```text
nbytes = size × itemsize
```
