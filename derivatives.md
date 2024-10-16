## Derivatives of elementary functions

These are the first and second derivatives for common elementary functions, covering power, exponential, logarithmic, trigonometric, and hyperbolic functions.

### 1. **Constant Function**:  
   - $f(x) = c$, where $c$ is a constant.
     - First derivative: $f'(x) = 0$
     - Second derivative: $f''(x) = 0$

### 2. **Power Function**:  
   - $f(x) = x^n$, where $n$ is a constant.
     - First derivative: $f'(x) = n \cdot x^{n-1}$
     - Second derivative: $f''(x) = n(n-1) \cdot x^{n-2}$

### 3. **Exponential Function**:  
   - $f(x) = e^x$
     - First derivative: $f'(x) = e^x$
     - Second derivative: $f''(x) = e^x$

   - $f(x) = a^x$, where $a > 0$ is a constant.
     - First derivative: $f'(x) = a^x \cdot \ln(a)$
     - Second derivative: $f''(x) = a^x \cdot (\ln(a))^2$

### 4. **Natural Logarithm Function**:  
   - $f(x) = \ln(x)$
     - First derivative: $f'(x) = \frac{1}{x}$
     - Second derivative: $f''(x) = -\frac{1}{x^2}$

### 5. **General Logarithm Function**:  
   - $f(x) = \log_a(x)$, where $a > 0$ is a constant.
     - First derivative: $f'(x) = \frac{1}{x \ln(a)}$
     - Second derivative: $f''(x) = -\frac{1}{x^2 \ln(a)}$

### 6. **Sine Function**:  
   - $f(x) = \sin(x)$
     - First derivative: $f'(x) = \cos(x)$
     - Second derivative: $f''(x) = -\sin(x)$

### 7. **Cosine Function**:  
   - $f(x) = \cos(x)$
     - First derivative: $f'(x) = -\sin(x)$
     - Second derivative: $f''(x) = -\cos(x)$

### 8. **Tangent Function**:  
   - $f(x) = \tan(x)$
     - First derivative: $f'(x) = \sec^2(x)$
     - Second derivative: $f''(x) = 2\sec^2(x)\tan(x)$

### 9. **Cotangent Function**:  
   - $f(x) = \cot(x)$
     - First derivative: $f'(x) = -\csc^2(x)$
     - Second derivative: $f''(x) = 2\csc^2(x)\cot(x)$

### 10. **Secant Function**:  
   - $f(x) = \sec(x)$
     - First derivative: $f'(x) = \sec(x) \tan(x)$
     - Second derivative: $f''(x) = \sec(x)\left(\tan^2(x) + \sec^2(x)\right)$

### 11. **Cosecant Function**:  
   - $f(x) = \csc(x)$
     - First derivative: $f'(x) = -\csc(x) \cot(x)$
     - Second derivative: $f''(x) = -\csc(x)\left(\cot^2(x) + \csc^2(x)\right)$

### 12. **Hyperbolic Sine Function**:  
   - $f(x) = \sinh(x)$
     - First derivative: $f'(x) = \cosh(x)$
     - Second derivative: $f''(x) = \sinh(x)$

### 13. **Hyperbolic Cosine Function**:  
   - $f(x) = \cosh(x)$
     - First derivative: $f'(x) = \sinh(x)$
     - Second derivative: $f''(x) = \cosh(x)$

### 14. **Hyperbolic Tangent Function**:  
   - $f(x) = \tanh(x)$
     - First derivative: $f'(x) = \text{sech}^2(x)$
     - Second derivative: $f''(x) = -2\tanh(x)\text{sech}^2(x)$

### 15. **Inverse Sine (Arcsine) Function**:  
   - $f(x) = \arcsin(x)$
     - First derivative: $f'(x) = \frac{1}{\sqrt{1 - x^2}}$
     - Second derivative: $f''(x) = \frac{x}{(1 - x^2)^{3/2}}$

### 16. **Inverse Cosine (Arccosine) Function**:  
   - $f(x) = \arccos(x)$
     - First derivative: $f'(x) = -\frac{1}{\sqrt{1 - x^2}}$
     - Second derivative: $f''(x) = \frac{x}{(1 - x^2)^{3/2}}$

### 17. **Inverse Tangent (Arctangent) Function**:  
   - $f(x) = \arctan(x)$
     - First derivative: $f'(x) = \frac{1}{1 + x^2}$
     - Second derivative: $f''(x) = -\frac{2x}{(1 + x^2)^2}$

## Derivatives of linear algebra operations

These are key matrix and vector derivatives commonly encountered in linear algebra, optimization, and machine learning applications. Eigenvalue and eigenvector derivatives are particularly important in sensitivity analysis and perturbation theory, although they require careful handling due to dependencies on the full eigendecomposition of the matrix.

### 1. **Derivative of a Matrix-Vector Product**  
   If $A$ is a matrix and $x$ is a vector:
   - $f(x) = A x$
     - First derivative: $\frac{d}{dx}(Ax) = A$
     - Second derivative: $\frac{d^2}{dx^2}(Ax) = 0$ (constant matrix)

### 2. **Derivative of a Scalar Quadratic Form**  
   If $f(x) = x^T A x$, where $A$ is a symmetric matrix:
   - First derivative: $\frac{d}{dx}(x^T A x) = 2 A x$
   - Second derivative: $\frac{d^2}{dx^2}(x^T A x) = 2 A$

### 3. **Derivative of the Matrix Trace**  
   If $f(A) = \text{tr}(A)$, where $A$ is a matrix:
   - First derivative: $\frac{d}{dA}\text{tr}(A) = I$, where $I$ is the identity matrix.
   - Second derivative: $\frac{d^2}{dA^2}\text{tr}(A) = 0$ (since trace is linear).

### 4. **Derivative of the Determinant**  
   If $f(A) = \det(A)$, where $A$ is a square matrix:
   - First derivative: $\frac{d}{dA}\det(A) = \det(A) A^{-1}$
   - Second derivative: $\frac{d^2}{dA^2}\det(A) = \det(A) A^{-1} \otimes A^{-1}$, where $\otimes$ denotes the Kronecker product.

### 5. **Derivative of the Inverse of a Matrix**  
   If $f(A) = A^{-1}$, where $A$ is an invertible matrix:
   - First derivative: $\frac{d}{dA}A^{-1} = -A^{-1} \otimes A^{-1}$
   - Second derivative: This would involve higher-order tensor calculus and is typically expressed using Kronecker products and higher-dimensional objects.

### 6. **Derivative of the Eigenvalue of a Matrix**  
   Let $A$ be a matrix with an eigenvalue $\lambda$ and corresponding eigenvector $v$, such that $A v = \lambda v$:
   - **First Derivative**:  
     For a smooth function $A(\theta)$ parameterized by $\theta$:
     - $\frac{d}{d\theta}\lambda(\theta) = v^T \frac{dA}{d\theta} v$, where $v$ is the eigenvector of $A$.
   - **Second Derivative**:  
     The second derivative of the eigenvalue can be expressed as:
     - $\frac{d^2}{d\theta^2}\lambda(\theta) = v^T \frac{d^2A}{d\theta^2} v + 2 \frac{d v^T}{d\theta} \frac{dA}{d\theta} v$, where additional terms involving derivatives of the eigenvector need to be considered.

### 7. **Derivative of an Eigenvector**  
   If $A(\theta) v(\theta) = \lambda(\theta) v(\theta)$, where both $A$ and $v$ depend on $\theta$:
   - **First Derivative**:  
     The derivative of an eigenvector $v$ with respect to a parameter $\theta$ is more complex and involves the other eigenvectors and eigenvalues:
     - $\frac{dv}{d\theta} = \sum_{j \neq i} \frac{v_j^T \frac{dA}{d\theta} v_i}{\lambda_i - \lambda_j} v_j$, where $\lambda_i$ and $\lambda_j$ are eigenvalues and $v_j$ are the eigenvectors of $A$, and the sum is over $j \neq i$.
   - **Second Derivative**:  
     The second derivative of the eigenvector involves further cross-eigenvalue and eigenvector terms, and is often written in terms of higher-order perturbation theory.

### 8. **Gradient of a Vector Norm**  
   If $f(x) = \|x\|_2 = \sqrt{x^T x}$:
   - First derivative: $\frac{d}{dx} \|x\|_2 = \frac{x}{\|x\|_2}$
   - Second derivative: The Hessian is $\frac{d^2}{dx^2} \|x\|_2 = \frac{I}{\|x\|_2} - \frac{x x^T}{\|x\|_2^3}$

### 9. **Derivative of the Frobenius Norm**  
   If $f(A) = \|A\|_F = \sqrt{\text{tr}(A^T A)}$:
   - First derivative: $\frac{d}{dA} \|A\|_F = \frac{A}{\|A\|_F}$
   - Second derivative: More complex, but involves similar structure to the second derivative of the vector norm.

### 10. **Derivative of Matrix Exponential**  
   If $f(A) = \exp(A)$, where $A$ is a square matrix:
   - First derivative: $\frac{d}{dA}\exp(A) = \exp(A)$
   - Second derivative: Higher-order derivatives involve recursion using series expansions of matrix exponentials.

### 11. **Derivative of the Singular Value Decomposition (SVD)**  
   Given $A = U \Sigma V^T$, where $\Sigma$ contains the singular values:
   - **First Derivative**:  
     The derivative of the singular values $\sigma_i$ with respect to $A$ is:
     - $\frac{d\sigma_i}{dA} = u_i v_i^T$, where $u_i$ and $v_i$ are the corresponding left and right singular vectors.
   - **Second Derivative**:  
     The second derivative involves complex tensor calculus and is not typically expressed in simple form.

### 12. **Derivative of a Matrix-Scalar Product**  
   If $f(A) = cA$, where $c$ is a scalar constant and $A$ is a matrix:
   - First derivative: $\frac{d}{dA} (cA) = c$
   - Second derivative: $\frac{d^2}{dA^2} (cA) = 0$ (since the derivative of a constant times a matrix is a constant).

### 13. **Kronecker Product**  
   If $f(A, B) = A \otimes B$ where $\otimes$ is the Kronecker product:
   - First derivative: $\frac{d}{dA}(A \otimes B) = I_B \otimes A$ (where $I_B$ is the identity matrix of dimension corresponding to $B$).
   - Second derivative: Similar extensions exist but depend on the structure of $A$ and $B$.

