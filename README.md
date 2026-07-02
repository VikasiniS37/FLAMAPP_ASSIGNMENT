# FlamApp AI - Research & Development Assignment

## Candidate Details

**Name:** Vikasini S

**Course:** B.Tech Computer Science and Engineering (Artificial Intelligence)

**College:** Amrita Vishwa Vidyapeetham, Ettimadai

---

# Problem Statement

The objective of this assignment is to estimate the unknown parameters of the given parametric curve using the provided dataset of 1500 two-dimensional points.

The parametric equations are

\[
x = t\cos(\theta)-e^{M|t|}\sin(0.3t)\sin(\theta)+X
\]

\[
y = 42+t\sin(\theta)+e^{M|t|}\sin(0.3t)\cos(\theta)
\]

Unknown variables:

- θ
- M
- X

Known range:

- 0° < θ < 50°
- -0.05 < M < 0.05
- 0 < X < 100
- 6 ≤ t ≤ 60

---

# Objective

Estimate the values of

- θ
- M
- X

such that the generated parametric curve closely matches the given dataset.

---

# Methodology

The solution was developed in multiple stages.

## Step 1

Loaded the provided CSV dataset using Pandas.

---

## Step 2

Performed exploratory data analysis.

The following checks were performed:

- Dataset shape
- Missing values
- Data types
- Statistical summary

---

## Step 3

Visualized the given data using scatter plots.

This helped understand the overall geometry of the curve.

---

## Step 4

Implemented the given parametric equations in Python.

The equations were implemented exactly as provided in the assignment.

---

## Step 5

Generated uniformly sampled values of parameter **t**

```
6 ≤ t ≤ 60
```

using

```
numpy.linspace()
```

---

## Step 6

Generated an initial curve using trial parameter values to verify the correctness of the mathematical implementation.

---

## Step 7

Compared the generated curve with the observed dataset.

Initially a point-wise comparison was considered.

However, further analysis showed that the dataset points were **not ordered according to parameter t**.

This was verified by visualizing the point indices using a color map.

---

## Step 8

Since the observed points were unordered, point-to-point comparison would produce incorrect error values.

Therefore, a nearest-neighbor matching strategy was adopted.

A KDTree was constructed from the predicted curve.

Each observed point was matched with its nearest predicted point.

The assignment evaluation metric specifies the use of L1 distance, therefore the optimization objective minimizes the mean Manhattan distance between corresponding nearest neighbors.

---

## Step 9

The unknown parameters

- θ
- M
- X

were estimated using Differential Evolution.

Differential Evolution was selected because

- nonlinear objective
- multiple local minima
- only three unknown parameters
- bounded search space

---

# Final Estimated Parameters

| Parameter | Estimated Value |
|-----------|----------------:|
| θ (degrees) | 29.999565 |
| θ (radians) | 0.523591 |
| M | 0.030001 |
| X | 54.998962 |

---

# Final Error

Mean L1 Distance

```
0.01336226
```

---

# Final Parametric Equation

```
(
t*cos(0.523591)
-
e^(0.030001*abs(t))
*
sin(0.3*t)
*
sin(0.523591)
+
54.998962,

42
+
t*sin(0.523591)
+
e^(0.030001*abs(t))
*
sin(0.3*t)
*
cos(0.523591)
)
```

Domain

```
6 ≤ t ≤ 60
```

---

# Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- SciPy
- cKDTree

---

# Repository Structure

```
FLAMAPP_ASSIGNMENT/

│── data/

│── outputs/

│── src/

│── README.md

│── requirements.txt
```

---

# References

NumPy Documentation

https://numpy.org/doc/

Pandas Documentation

https://pandas.pydata.org/docs/

SciPy Documentation

https://docs.scipy.org/doc/scipy/

Matplotlib Documentation

https://matplotlib.org/stable/

KDTree Documentation

https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.cKDTree.html

---

