---
layout: post
title: "Cauchy matrices and the symmetric eigenvalue problem"
description: "An introduction to Cauchy matrices, with emphasis on their connection to the symmetric eigenvalue problem"
comments: true
tags: [mathematics, signal_processing, matrices]
---

## Introduction to Cauchy matrices

Cauchy matrices are a special class of structured matrices whose entries are the ratio of differences of two sequences. This structure makes them useful in signal processing: I've used them to derive fast matrix-vector product algorithms (in signal processing terms, like the FFT for the DFT) for graph-based transforms [1].

<br/> <br/>

While there are some great papers on Cauchy matrices [2], I believe they are relatively less known than other structured matrices, such as Vandermonde or Hadamard matrices. The main goal of this post is to show how Cauchy matrices appear when computing the eigenvectors of a rank-one update of a symmetric matrix. In doing so, we will present some of their key properties.

<br/> <br/>

## Definition

A Cauchy matrix is an $m \times n$ matrix $\mathbf{C}(\mathbf{x}, \mathbf{y})$ parametrized by two vectors $\mathbf{x} \in \mathbb{R}^m$ and $\mathbf{y} \in \mathbb{R}^n$ with entries given by:

$$ C_{i,j} = \frac{1}{x_i - y_j} $$

where $\mathbf{x} = [x_1, x_2, \ldots, x_m]$ and $\mathbf{y} = [y_1, y_2, \ldots, y_n]$ are two vectors such that $x_i \neq y_j$ for all $i,j$. We also require that $x_i \neq x_j$ for all $i,j$ and $y_i \neq y_j$ for all $i,j$.

<br/> <br/>

## Key properties

Cauchy matrices satisfy multiple properties. Most of them can be found online, such as in the [Wikipedia article](https://en.wikipedia.org/wiki/Cauchy_matrix). Just to name a few:

1. **Nonsingularity**: All square Cauchy matrices are invertible.
2. **Structured Rank**: Cauchy matrices have low displacement rank, making them computationally efficient.
3. Every submatrix of a Cauchy matrix is also a Cauchy matrix.

<br/> <br/>

Remarkably, there exists analytic expressions for the inverse and the determinant of a Cauchy matrix.

## Example: Constructing a Cauchy Matrix

Here's a simple Python function to create a Cauchy matrix:

```python
import numpy as np

def cauchy_matrix(x, y):
    """
    Create a Cauchy matrix from vectors x and y.
    x, y: 1D arrays or lists
    Returns: 2D numpy array
    """
    x = np.array(x).reshape(-1, 1)  # Convert to column vector
    return 1 / (x - y)  # Broadcasting does the rest

# Example usage
x = [1, 2, 3, 4]
y = [5, 6, 7]
C = cauchy_matrix(x, y)
print("Cauchy matrix:")
print(C)
```

## Connection to Vandermonde Matrices

Cauchy matrices are closely related to Vandermonde matrices. In fact, a Cauchy matrix can be expressed as:

$$ C = \frac{1}{V(x)V(-y)^T} $$

where $V(x)$ is a Vandermonde matrix and the division is element-wise.

## Conclusion

Cauchy matrices provide a powerful tool in various areas of signal processing and coding theory. Their special structure enables efficient computations and their properties make them invaluable in error correction and interpolation problems. Understanding these matrices can provide deeper insights into many signal processing algorithms and coding schemes.

## References

[1] S. Fernández-Menduiña, E. Pavez, and A. Ortega, "Fast DCT+: A Family of Fast Transforms Based on Rank-One Updates of the Path Graph," *2025 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*, pp. 1-5, 2025.

[2] Fasino, Dario. "Orthogonal Cauchy-like matrices." *Numerical Algorithms* 92.1 (2023): 619-637.

## Further Reading

1. Golub, G. H., & Van Loan, C. F. (2013). Matrix computations. JHU press.
2. Davis, P. J. (1979). Circulant matrices. John Wiley & Sons.
3. Blahut, R. E. (2003). Algebraic codes for data transmission. Cambridge university press.
