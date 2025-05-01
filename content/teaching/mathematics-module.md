---
title: "Mathematics for Data Analysis"
date: 2023-01-15
draft: false
tags: ["mathematics", "statistics", "linear-algebra"]
summary: "Essential mathematical concepts for data analysis and machine learning"
semester: "Spring 2023"
level: "Graduate"
---

# Mathematics for Data Analysis

This module covers essential mathematical concepts that form the foundation of modern data analysis, statistics, and machine learning.

## Learning Objectives

By the end of this module, students will be able to:

- Apply linear algebra concepts to data analysis problems
- Understand fundamental concepts in probability theory
- Apply calculus techniques for optimization problems
- Implement numerical methods for data analysis

## Linear Algebra Review

### Vector Spaces

A vector space $V$ over a field $F$ consists of a set of vectors and two operations: vector addition and scalar multiplication, satisfying certain axioms.

For data analysis, we typically work with the vector space $\mathbb{R}^n$, which consists of all $n$-dimensional vectors with real entries.

### Matrix Operations

For matrices $A \in \mathbb{R}^{m \times n}$ and $B \in \mathbb{R}^{n \times p}$, the matrix product $C = AB$ is defined as:

$$C_{ij} = \sum_{k=1}^{n} A_{ik} B_{kj}$$

### Eigenvalues and Eigenvectors

For a square matrix $A \in \mathbb{R}^{n \times n}$, a scalar $\lambda$ and a non-zero vector $v \in \mathbb{R}^n$ are called an eigenvalue and eigenvector of $A$ if:

$$Av = \lambda v$$

Finding eigenvalues and eigenvectors is crucial for dimensionality reduction techniques like PCA.

## Probability Theory

### Random Variables

A random variable $X$ is a function that maps outcomes from a sample space to real numbers. The probability distribution of $X$ describes the likelihood of different values.

### Expected Value and Variance

For a discrete random variable $X$ with probability mass function $p(x)$, the expected value is:

$$E[X] = \sum_{x} x \cdot p(x)$$

The variance is:

$$\text{Var}(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$$

### Bayes' Theorem

Bayes' theorem relates conditional probabilities:

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

This forms the foundation of many machine learning algorithms.

## Calculus for Optimization

### Gradients

The gradient of a function $f: \mathbb{R}^n \rightarrow \mathbb{R}$ is the vector of partial derivatives:

$$\nabla f(x) = \left( \frac{\partial f}{\partial x_1}, \frac{\partial f}{\partial x_2}, \ldots, \frac{\partial f}{\partial x_n} \right)$$

### Optimization

Finding the minimum of a function $f$ often involves setting the gradient to zero:

$$\nabla f(x) = 0$$

This is the basis for many machine learning algorithms like gradient descent:

$$x_{t+1} = x_t - \alpha \nabla f(x_t)$$

where $\alpha$ is the learning rate.

## Code Example: Principal Component Analysis

Here's a Python implementation of PCA using eigenvalue decomposition:

```python
import numpy as np
import matplotlib.pyplot as plt

def pca(X, num_components):
    """
    Perform PCA on dataset X
    
    Parameters:
    X: Dataset, shape (n_samples, n_features)
    num_components: Number of principal components to keep
    
    Returns:
    X_pca: Data transformed into principal components
    components: Principal components
    explained_variance: Explained variance of each component
    """
    # Center the data
    X_centered = X - np.mean(X, axis=0)
    
    # Compute covariance matrix
    cov_matrix = np.cov(X_centered, rowvar=False)
    
    # Eigenvalue decomposition
    eigenvalues, eigenvectors = np.linalg.eigh(cov_matrix)
    
    # Sort eigenvalues and corresponding eigenvectors in descending order
    idx = np.argsort(eigenvalues)[::-1]
    eigenvalues = eigenvalues[idx]
    eigenvectors = eigenvectors[:, idx]
    
    # Select top k eigenvectors
    components = eigenvectors[:, :num_components]
    
    # Compute explained variance
    explained_variance = eigenvalues[:num_components] / np.sum(eigenvalues)
    
    # Project data onto principal components
    X_pca = np.dot(X_centered, components)
    
    return X_pca, components, explained_variance

# Example usage
if __name__ == "__main__":
    # Generate random data
    np.random.seed(42)
    X = np.random.randn(100, 5)
    
    # Apply PCA
    X_pca, components, explained_variance = pca(X, num_components=2)
    
    # Print results
    print(f"Explained variance: {explained_variance}")
    print(f"Principal components shape: {components.shape}")
    
    # Plot results
    plt.figure(figsize=(8, 6))
    plt.scatter(X_pca[:, 0], X_pca[:, 1])
    plt.xlabel("First Principal Component")
    plt.ylabel("Second Principal Component")
    plt.title("PCA Example")
    plt.grid(True)
    plt.show()
```

## Assignment

Implement the following algorithms using the mathematical concepts covered in this module:

1. Linear regression using normal equations: $\hat{\beta} = (X^T X)^{-1} X^T y$
2. k-means clustering
3. Naive Bayes classifier using Bayes' theorem

## Resources

- Textbook: "Mathematics for Machine Learning" by Deisenroth, Faisal, and Ong
- Online course: MIT OpenCourseWare 18.06 Linear Algebra
- Python libraries: NumPy, SciPy, scikit-learn 