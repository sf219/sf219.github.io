---
layout: post
title: "Cauchy matrices and the symmetric eigenvalue problem"
description: "An introduction to Cauchy matrices, with emphasis on their connection to the symmetric eigenvalue problem"
comments: true
tags: [mathematics, signal_processing, matrices]
---


<style>
  .post-content {
    text-align: justify;
    text-justify: inter-word;
  }
</style>

## Introduction to Cauchy matrices

Cauchy matrices are a special class of structured matrices whose entries are the ratio of differences of two sequences. This structure makes them useful in signal processing: I've used them to derive fast matrix-vector product algorithms (in signal processing terms, like the FFT for the DFT) for graph-based transforms [1].

<br/> <br/>

While there are some great papers on Cauchy matrices [2], I believe they are relatively less known than other structured matrices, such as Vandermonde or Hadamard matrices. The main goal of this post is to show how Cauchy matrices appear when computing the eigenvectors of rank-one updates of a symmetric matrix. In doing so, we will present some of their key properties and illustrate their practical applications.

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

Remarkably, there are analytic expressions for the inverse and the determinant of a Cauchy matrix.

## Rank-one updates of a symmetric matrix



## References

[1] S. Fernández-Menduiña, E. Pavez, and A. Ortega, "Fast DCT+: A Family of Fast Transforms Based on Rank-One Updates of the Path Graph," *2025 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*, pp. 1-5, 2025.

[2] Fasino, Dario. "Orthogonal Cauchy-like matrices." *Numerical Algorithms* 92.1 (2023): 619-637.
