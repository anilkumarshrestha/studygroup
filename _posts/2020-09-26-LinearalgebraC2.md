---
layout: post
mathjax: true
title:  "Chapter 2: Solving Linear Equation"
crawlertitle: "All about vectors"
summary: "Just a sumary about vectors"
date:   2020-09-26
categories: ['Linear Algebra']
tags: linear-algebra
author: unknown
bg: "african-penguins.jpg"
---


## Summary | Chapter 2 (Part B) 
# Elimination Using Matrices
The ultimate purpose of elimination is to knock out variables from other equations and hence find the solution of x in $$Ax = b$$. 
 
## Matrices times Vectors and $$Ax = b$$
Ax = b represents both row and column form.
$$Ax = a_{i1} x_1 + .. + a_{in} x_n  =\sum\limits_{j=1}^n a_{ij}x_j $$

where, x = $$\begin{bmatrix}
    x_1 \\
    x_2 \\
    x_3 \\
    . \\
    . \\
    . 
\end{bmatrix}$$
$$A = \begin{bmatrix}
    a_{1,1} & a_{1,2} & ... \\
    . &  & \\
     . & & 
\end{bmatrix}
$$


## Matrix Form of One Elimination Step
Elimination matrix has the extra non-zero entry $$-l$$ in the $$i,j$$ position in an identity matrix and hence subtracts $$l$$ times row $$j$$ from row $$i$$. Inverse of an elimination matrix reverses the action. If $$E$$ multiplied by $$l$$ and subtracted then $$E^{-1}$$ multiplies and adds the rows.
Example of elimination matrix:<br>
$$
\begin{bmatrix}
1 & 0 & 0\\
0 & 1 & 0 \\
-l & 0 & 1
\end{bmatrix}
$$

With this we can create 0 at any desired position in the matrix and also makes computation efficient.

# Matrix Multiplication

- Associative so $$A(BC) = (AB)C$$
- NOT commutative so $$AB \neq BA$$.
- Commutative $$A + B = B + A$$
- Distributive $$c(A + B) = cA + cB$$
- Associative $$A + (B + C) = (A + B) + C$$


## Matrix $$P_{ij}$$ for Row Exchange
When zero is pivot, we might have to exchange rows as zero cannot be a pivot. For this we use permutation matrix $$P_{ij}$$ which exchanges ith row and jth row.
example: <br>
$$P_{ij} = \begin{bmatrix}
                1 & 0 & 0\\
                0 & 0 & 1 \\
                0 & 1 & 0
                \end{bmatrix}$$
<br>
The above permutation matrix says: take $$A_{C1}$$ to $$B_{C1}$$; take $$A_{C3}$$ to $$B_{C2}$$ and $$A_{C2}$$ to $$B_{C3}$$

# Matrix multiplication
## First way
For a matrix multiplication AB to create C the number columns of A must equal the number of rows of B.
<br>
$$AB = C $$
<br>
$$(m * n) (n * p) = m * p$$
<br>

So here we get the result matrix as $$m * p$$.

-  If A and B are n * n then AB is n * n
-  Also each dot product needs n multiplication so computation of AB needs $$n^3$$ separate multiplication which is the cost of calculation of AB.


## Second and Third way: Column and Row picture
Column picture gives: Matrix A times (every column of B) i.e 
<br>
$$A [b_1, b_2, ... , b_p] = [Ab_1, ... , Ab_p]$$. 
<br>

Similarly Row picture Every row of A times 
(Matrix B) i.e 
<br>
[row of A] . $$\begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6\\7 & 8 & 9 \end{bmatrix}$$

## Fourth way: column multiply row
Here we multiply column 1 to n of A with 1 to n rows of B and add them.
<br>
$$\begin{bmatrix}
    1 & 2 & 3\\
    . & . & . \\
    . & . & .
    \end{bmatrix}
\begin{bmatrix}
    4 & . & .\\
    5 & . & . \\
    6 & . & .
    \end{bmatrix}
    = (1*4) + (2*5) + (3*6) 
$$

## Block Multiplication

-  Matrix can be divided into blocks which can give a better picture for complex matrices
-  We can use block multiplication to eliminate multiple elements with single matrix


# Inverse Matrix
The matrix $$A^{-1}$$ is the inverse of A if $$A^{-1}A = I$$ and  $$AA^{-1} = I$$. 
## Testing Inverse

- If matrix is diagonally dominant, it has inverse. 
- $$A^{-1}$$ exists iff elimination produces $$n$$ pivot points. That is no diagonal element should be zero.
-  Matrix A can not have two different inverse which means x = $$A^{-1}B$$ has one and only solution.
-  If $$Ax = 0$$, we cannot divide by 0 to create $$A^{-1}$$.
-  $$A^{-1}$$ exists if determinant of $$A \neq 0$$.


## Inverse of A+B and AB

Even if A and B are invertible separately, it does not guarantee that $$A+B$$ will be invertible. For example if $$A + B$$ adds to $$0$$; no inverse exists. However, the product of A and B has inverse and takes the form: $$(AB)^{-1} = B^{-1}A^{-1}$$ so $$(AB) (B^{-1}A^{-1}) = I$$

## Diagonally Dominant Matrix
The matrices whose diagonal element is greater than the sum of it other element in a row. We can easily determine if a matrix has inverse by checking if it is diagonally dominant. Mathematically,
<br>
$$|a_{ij}| > \sum\limits_{j \neq i} |a_{ij}|$$

Example:

\begin{bmatrix}
    5 & 1 & 3\\
    1 & 7 & 3\\
    2 & 1 & 8 
    \end{bmatrix}
$$

## Calculating Inverse with Gaussian Jordan Elimination

Here we solve all n equations together to find inverse of A. First form an augmented matrix $$[A I]$$, then unlike Gaussian continue elimination to reduced echelon form $$R = I$$ which finally converts to $$[I A^{-1}]$$.

# Factorization: A=LU

Here we try to eliminate without exchanging rows. L is the lower triangular matrix which is the combination of inverse of elimination matrices. U is upper triangular matrix with pivot on its diagonal.
<br>
$$E_{21}A = U $$
<br>
$$
\begin{bmatrix}
    1 & 0 \\
    -4 & 1 \\
    \end{bmatrix}
\begin{bmatrix}
    2 & 1 \\
    8 & 7 \\
    \end{bmatrix}
    =
\begin{bmatrix}
    2 & 1 \\
    0 & 3 \\
    \end{bmatrix}
$$
<br>
$$
A = L U 
$$
<br>
$$
\begin{bmatrix}
2 & 1 \\
8 & 7 \\
\end{bmatrix}
    =
\begin{bmatrix}
1 & 0 \\
4 & 1 \\
\end{bmatrix}
\begin{bmatrix}
    2 & 1 \\
    0 & 3 \\
\end{bmatrix}
$$
<br>
Here L = $$E_{21}^{-1}$$ . Similarly for three dimensional matrix we have $$E_{32}E_{31}E_{21}A = U$$ and $$ L = E_{21}^{-1}E_{31}^{-1}E_{32}^{-1}$$

# Transpose of a Matrix
If $$A_{ij}$$ is a matrix then its transpose $$(A^T)_{ij} = A_{ji}$$  
For example:
<br>
$$A = \begin{bmatrix}
    4 & 1 & 2\\
    5 & 7 & 1 \\
    \end{bmatrix}
A^T= \begin{bmatrix}
    4 & 5\\
    1 & 7\\
    2 & 1 
    \end{bmatrix}
$$
<br>

Note: $$AA^T$$ gives a square matrix, which can be used to find inverse of a matrix. 

$$
\begin{bmatrix}
    1 & 3\\
    2 & 3\\
    4 & 1 
    \end{bmatrix}
$$
$$\begin{bmatrix}
    1 & 2 & 4\\
    3 & 3 & 1
    \end{bmatrix}
$$ 
= $$\begin{bmatrix}
    10 & 11 & 7\\
    11 & 13 & 11\\
    7 & 11 & 17 
    \end{bmatrix}
$$ 

$$(R^TR)^T = R^TR^{TT} = R^TR$$
Hence symmetric.

### Symmetric matrix
If a matrix A = $$A^T$$, then A is symmetric.

# Permutations
Permutation matrices have rows of identity in any order.
Example: Permutation matrices of 3 * 3 matrix.
<br>
$$
\begin{bmatrix}
    1 & & \\
     & 1 & \\
     & & 1
\end{bmatrix}
\begin{bmatrix}
     & 1 & \\
     1 &  & \\
     & & 1
\end{bmatrix}
\begin{bmatrix}
     & & 1 \\
     & 1 & \\
     1& & 
\end{bmatrix}
\begin{bmatrix}
    1 & & \\
     &  & 1\\
     & 1 & 
\end{bmatrix}
\begin{bmatrix}
     & & 1\\
    1 &  & \\
     1 & & 
\end{bmatrix}
\begin{bmatrix}
     & & 1\\
     1 &  & \\
     & 1 & 
\end{bmatrix}
$$
<br>

-  $$P^{-1} = P^T$$
-  for $$n*n$$ matrix there are $$n!$$ permutations.
