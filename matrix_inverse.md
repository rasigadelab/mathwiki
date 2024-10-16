## Explicit inverses of small matrices

The inverse of a square matrix $A$ exists only if the matrix is invertible (i.e., its determinant is non-zero). Here are the analytical expressions for the inverses of $2 \times 2$, $3 \times 3$, and $4 \times 4$ square matrices:

### 1. **Inverse of a $2 \times 2$ Matrix**  
Let $A$ be a $2 \times 2$ matrix:

$$A = \begin{pmatrix} a & b \\ 
c & d \end{pmatrix}$$

The inverse of $A$, if $\det(A) = ad - bc \neq 0$, is given by:

$$A^{-1} = \frac{1}{\det(A)} \begin{pmatrix} d & -b \\
-c & a \end{pmatrix}$$

Thus:

$$A^{-1} = \frac{1}{ad - bc} \begin{pmatrix} d & -b \\
-c & a \end{pmatrix}$$

### 2. **Inverse of a $3 \times 3$ Matrix**  
Let $A$ be a $3 \times 3$ matrix:
$$A = \begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i \end{pmatrix}$$
The inverse of $A$, if $\det(A) \neq 0$, can be written as:
$$A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$$
Where $\text{adj}(A)$ is the adjugate (transpose of the cofactor matrix). The cofactor matrix for $A$ is:
$$\text{cof}(A) = \begin{pmatrix}
ei - fh & ch - bi & bf - ce \\
fg - di & ai - cg & cd - af \\
dh - eg & bg - ah & ae - bd
\end{pmatrix}$$
So the inverse is:
$$A^{-1} = \frac{1}{\det(A)} \begin{pmatrix}
ei - fh & ch - bi & bf - ce \\
fg - di & ai - cg & cd - af \\
dh - eg & bg - ah & ae - bd
\end{pmatrix}$$
Where $\det(A) = a(ei - fh) - b(di - fg) + c(dh - eg)$.

### 3. **Inverse of a $4 \times 4$ Matrix**  
Let $A$ be a $4 \times 4$ matrix:
$$A = \begin{pmatrix}
a & b & c & d \\
e & f & g & h \\
i & j & k & l \\
m & n & o & p
\end{pmatrix}$$
The inverse of $A$, if $\det(A) \neq 0$, is also expressed as:
$$A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$$
Where $\text{adj}(A)$ is the adjugate matrix. The adjugate is the transpose of the cofactor matrix, and each cofactor is a $3 \times 3$ determinant (as minors) of the original matrix. The cofactor matrix for $A$ is given by:

$$\text{cof}(A) = \begin{pmatrix}
\det(A_{11}) & -\det(A_{12}) & \det(A_{13}) & -\det(A_{14}) \\
-\det(A_{21}) & \det(A_{22}) & -\det(A_{23}) & \det(A_{24}) \\
\det(A_{31}) & -\det(A_{32}) & \det(A_{33}) & -\det(A_{34}) \\
-\det(A_{41}) & \det(A_{42}) & -\det(A_{43}) & \det(A_{44})
\end{pmatrix}$$
Where $\det(A_{ij})$ is the determinant of the $3 \times 3$ minor matrix formed by deleting the $i$-th row and $j$-th column of $A$.

Thus:
$$A^{-1} = \frac{1}{\det(A)} \begin{pmatrix}
\det(A_{11}) & -\det(A_{12}) & \det(A_{13}) & -\det(A_{14}) \\
-\det(A_{21}) & \det(A_{22}) & -\det(A_{23}) & \det(A_{24}) \\
\det(A_{31}) & -\det(A_{32}) & \det(A_{33}) & -\det(A_{34}) \\
-\det(A_{41}) & \det(A_{42}) & -\det(A_{43}) & \det(A_{44})
\end{pmatrix}$$
Where $\det(A)$ is the determinant of the full $4 \times 4$ matrix.

### General Procedure for Inversion of Larger Matrices
For any $n \times n$ matrix, the inverse is computed using:
$$A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$$
Where:
- $\det(A)$ is the determinant of the matrix.
- $\text{adj}(A)$ is the adjugate matrix (the transpose of the cofactor matrix).

The cofactor matrix involves calculating the determinants of smaller minors, and the process becomes more complex as the matrix size increases. However, the principles of determinant and adjugate calculation remain the same across dimensions.

