# 🔢 NumPy Cheat Sheet

NumPy is a Python library for **numerical computing** and working with **arrays**.
It provides fast operations on large datasets using vectorized operations.

---

## **1. Import NumPy**

```python
import numpy as np
```

---

## **2. Creating Arrays**

### **From Python Lists**

```python
arr = np.array([1, 2, 3])
arr2d = np.array([[1, 2], [3, 4]])
```

---

### **Initial Placeholder Arrays**

| Function              | Description         | Example              |
| --------------------- | ------------------- | -------------------- |
| `np.zeros(shape)`     | Array of zeros      | `np.zeros((2, 3))`   |
| `np.ones(shape)`      | Array of ones       | `np.ones((3, 3))`    |
| `np.full(shape, val)` | Constant array      | `np.full((2, 4), 5)` |
| `np.eye(n)`           | Identity matrix     | `np.eye(3)`          |
| `np.empty(shape)`     | Uninitialized array | `np.empty((2, 2))`   |

---

### **Random Arrays**

| Function                              | Description              | Example                            |
| ------------------------------------- | ------------------------ | ---------------------------------- |
| `np.random.random(shape)`             | Random floats \[0,1)     | `np.random.random((2, 3))`         |
| `np.random.randint(low, high, shape)` | Random integers          | `np.random.randint(0, 10, (3, 3))` |
| `np.random.randn(n)`                  | Standard normal dist.    | `np.random.randn(5)`               |
| `np.random.seed(n)`                   | Seed for reproducibility | `np.random.seed(42)`               |

---

### **Evenly Spaced Values**

| Function                        | Description  | Example                |
| ------------------------------- | ------------ | ---------------------- |
| `np.arange(start, stop, step)`  | Range array  | `np.arange(0, 10, 2)`  |
| `np.linspace(start, stop, num)` | Even spacing | `np.linspace(0, 1, 5)` |

---

### **From Other Python Objects**

```python
l = [1, 2, 3]
arr = np.asarray(l)  # Converts list to NumPy array
```

---

## **3. Array Attributes**

| Attribute | Description          | Example     |
| --------- | -------------------- | ----------- |
| `.shape`  | Dimensions           | `arr.shape` |
| `.ndim`   | Number of dimensions | `arr.ndim`  |
| `.size`   | Number of elements   | `arr.size`  |
| `.dtype`  | Data type            | `arr.dtype` |
| `.T`      | Transpose            | `arr.T`     |

---

## **4. Reshaping & Flattening**

| Method           | Description    | Example             |
| ---------------- | -------------- | ------------------- |
| `.reshape(r, c)` | Reshape array  | `arr.reshape(2, 3)` |
| `.flatten()`     | Flatten to 1D  | `arr.flatten()`     |
| `.ravel()`       | Flatten (view) | `arr.ravel()`       |

---

## **5. Indexing & Slicing**

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

arr[0, 0]    # First element
arr[1, :]    # Second row
arr[:, 2]    # Third column
arr[0:2, 1:3]  # Slice rows & cols
```

---

## **6. Mathematical Operations**

| Function            | Description           | Example             |
| ------------------- | --------------------- | ------------------- |
| `np.add(a, b)`      | Element-wise addition | `np.add(a, b)`      |
| `np.subtract(a, b)` | Subtraction           | `np.subtract(a, b)` |
| `np.multiply(a, b)` | Multiplication        | `np.multiply(a, b)` |
| `np.divide(a, b)`   | Division              | `np.divide(a, b)`   |
| `np.power(a, b)`    | Power                 | `np.power(a, 2)`    |
| `np.mod(a, b)`      | Modulus               | `np.mod(a, 2)`      |

---

## **7. Aggregate Functions**

| Function     | Description        | Example        |
| ------------ | ------------------ | -------------- |
| `np.sum(a)`  | Sum                | `np.sum(arr)`  |
| `np.mean(a)` | Mean               | `np.mean(arr)` |
| `np.min(a)`  | Min value          | `np.min(arr)`  |
| `np.max(a)`  | Max value          | `np.max(arr)`  |
| `np.std(a)`  | Standard deviation | `np.std(arr)`  |
| `np.var(a)`  | Variance           | `np.var(arr)`  |

---

## **8. Linear Algebra**

| Function           | Description           | Example            |
| ------------------ | --------------------- | ------------------ |
| `np.dot(a, b)`     | Dot product           | `np.dot(a, b)`     |
| `np.matmul(a, b)`  | Matrix multiplication | `np.matmul(a, b)`  |
| `np.linalg.inv(a)` | Inverse               | `np.linalg.inv(m)` |
| `np.linalg.det(a)` | Determinant           | `np.linalg.det(m)` |
| `np.linalg.eig(a)` | Eigenvalues/vectors   | `np.linalg.eig(m)` |

---

## **9. Boolean Indexing**

```python
arr = np.array([1, 2, 3, 4, 5])
arr[arr > 3]         # [4, 5]
arr[(arr % 2) == 0]  # [2, 4]
```

---

## **10. Copying Arrays**

```python
a = np.array([1, 2, 3])
b = a.copy()  # Creates a separate copy
```

---

## **11. Broadcasting**

NumPy can perform operations between arrays of different shapes if they follow broadcasting rules.

```python
a = np.array([1, 2, 3])
b = 2
a * b  # [2, 4, 6]
```
