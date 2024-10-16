## The expectation of a function of a random variable with unknown distribution

When approximating the **expectation of a function of a vector-valued random variable** with an unknown multivariable distribution, using a **Taylor expansion around the distribution mode**, the process is an extension of the univariate case. However, because we now deal with vector-valued variables, the Taylor expansion and the integrals will involve **gradients** (first derivatives) and **Hessians** (second-order derivatives with respect to the vector components). The mode of the distribution serves as the expansion point.

Here’s how we approach the problem step by step.

### Problem Setup

Let $\mathbf{X} \in \mathbb{R}^n$ be a random vector with an **unknown multivariable probability density function** $p(\mathbf{x})$, and let $g(\mathbf{X})$ be a smooth function of $\mathbf{X}$. The objective is to approximate the expectation $\mathbb{E}[g(\mathbf{X})]$, i.e.,

$$\mathbb{E}[g(\mathbf{X})] = \int_{\mathbb{R}^n} g(\mathbf{x}) p(\mathbf{x}) \, d\mathbf{x}$$

Assume the following:
- $p(\mathbf{x})$ is smooth and unimodal with mode $\mathbf{x}_0$, meaning $\nabla p(\mathbf{x}_0) = 0$ (the gradient is zero at the mode), and $p(\mathbf{x}_0)$ is a local maximum.
- $g(\mathbf{x})$ is a sufficiently smooth function, allowing for a Taylor expansion around the mode $\mathbf{x}_0$.

### Step 1: Taylor Expansion of the Function $g(\mathbf{x})$ Around the Mode

We start by expanding the function $g(\mathbf{x})$ using a second-order Taylor series around the mode $\mathbf{x}_0$:

$$g(\mathbf{x}) \approx g(\mathbf{x}_0) + (\mathbf{x} - \mathbf{x}_0)^T \nabla g(\mathbf{x}_0) + \frac{1}{2} (\mathbf{x} - \mathbf{x}_0)^T H_g(\mathbf{x}_0) (\mathbf{x} - \mathbf{x}_0)$$

where:
- $\nabla g(\mathbf{x}_0)$ is the **gradient** of $g(\mathbf{x})$ at $\mathbf{x}_0$ (a vector of first partial derivatives).
- $H_g(\mathbf{x}_0)$ is the **Hessian matrix** of $g(\mathbf{x})$ at $\mathbf{x}_0$ (a matrix of second partial derivatives).

### Step 2: Approximation of the Multivariable Probability Density Function $p(\mathbf{x})$

Next, we approximate the multivariable PDF $p(\mathbf{x})$ around the mode $\mathbf{x}_0$ using a second-order Taylor expansion:

$$p(\mathbf{x}) \approx p(\mathbf{x}_0) + \frac{1}{2} (\mathbf{x} - \mathbf{x}_0)^T H_p(\mathbf{x}_0) (\mathbf{x} - \mathbf{x}_0)$$

where $H_p(\mathbf{x}_0)$ is the Hessian matrix of $p(\mathbf{x})$ at the mode $\mathbf{x}_0$. Since $\mathbf{x}_0$ is the mode, the gradient of $p(\mathbf{x})$ vanishes at $\mathbf{x}_0$, i.e., $\nabla p(\mathbf{x}_0) = 0$, which simplifies the expansion.

Alternatively, in many cases (and to make computations tractable), we assume that the distribution $p(\mathbf{x})$ behaves like a **multivariate normal distribution** near the mode. In this case, the PDF around the mode can be approximated by:

$$p(\mathbf{x}) \approx \frac{1}{(2\pi)^{n/2} |\Sigma|^{1/2}} \exp \left( -\frac{1}{2} (\mathbf{x} - \mathbf{x}_0)^T \Sigma^{-1} (\mathbf{x} - \mathbf{x}_0) \right)$$

where $\Sigma$ is the **covariance matrix** of the distribution, and $|\Sigma|$ denotes the determinant of the covariance matrix. This is a reasonable approximation when the distribution is unimodal and concentrated around $\mathbf{x}_0$.

### Step 3: Approximation of the Expectation $\mathbb{E}[g(\mathbf{X})]$

Now, we can approximate the expectation $\mathbb{E}[g(\mathbf{X})]$ using the Taylor expansion of $g(\mathbf{x})$. Substituting the Taylor-expanded $g(\mathbf{x})$ into the expectation gives:

$$\mathbb{E}[g(\mathbf{X})] = \int_{\mathbb{R}^n} \left( g(\mathbf{x}_0) + (\mathbf{x} - \mathbf{x}_0)^T \nabla g(\mathbf{x}_0) + \frac{1}{2} (\mathbf{x} - \mathbf{x}_0)^T H_g(\mathbf{x}_0) (\mathbf{x} - \mathbf{x}_0) \right) p(\mathbf{x}) \, d\mathbf{x}$$

We compute the expectation term by term:

#### Term 1: $g(\mathbf{x}_0)$

The first term is:

$$g(\mathbf{x}_0) \int_{\mathbb{R}^n} p(\mathbf{x}) \, d\mathbf{x} = g(\mathbf{x}_0)$$

Since the integral of the PDF $p(\mathbf{x})$ over its domain is 1, this term contributes $g(\mathbf{x}_0)$, which is simply the value of the function at the mode.

#### Term 2: $(\mathbf{x} - \mathbf{x}_0)^T \nabla g(\mathbf{x}_0)$

The second term is:

$$\nabla g(\mathbf{x}_0)^T \int_{\mathbb{R}^n} (\mathbf{x} - \mathbf{x}_0) p(\mathbf{x}) \, d\mathbf{x}$$

Because $p(\mathbf{x})$ is symmetric around $\mathbf{x}_0$, the mean $\mathbb{E}[\mathbf{x}] = \mathbf{x}_0$, so:

$$\int_{\mathbb{R}^n} (\mathbf{x} - \mathbf{x}_0) p(\mathbf{x}) \, d\mathbf{x} = 0$$

Thus, this term vanishes, contributing nothing to the expectation.

#### Term 3: $\frac{1}{2} (\mathbf{x} - \mathbf{x}_0)^T H_g(\mathbf{x}_0) (\mathbf{x} - \mathbf{x}_0)$

The third term is:

$$\frac{1}{2} \int_{\mathbb{R}^n} (\mathbf{x} - \mathbf{x}_0)^T H_g(\mathbf{x}_0) (\mathbf{x} - \mathbf{x}_0) p(\mathbf{x}) \, d\mathbf{x}$$

This integral represents the **quadratic term** and depends on the covariance structure of $\mathbf{X}$. It is proportional to the **trace** of the product of the Hessian $H_g(\mathbf{x}_0)$ and the covariance matrix $\Sigma$ of the distribution:

$$\frac{1}{2} \, \text{Tr}\left( H_g(\mathbf{x}_0) \Sigma \right)$$

Here, $\Sigma$ is the covariance matrix of the distribution $p(\mathbf{x})$. For a Gaussian approximation of $p(\mathbf{x})$, $\Sigma$ is the covariance matrix of the multivariate normal distribution.

### Step 4: Final Approximation

Putting everything together, the approximation for $\mathbb{E}[g(\mathbf{X})]$ is:

$$\mathbb{E}[g(\mathbf{X})] \approx g(\mathbf{x}_0) + \frac{1}{2} \, \text{Tr}\left( H_g(\mathbf{x}_0) \Sigma \right)$$

Where:
- $g(\mathbf{x}_0)$ is the value of the function at the mode of the distribution.
- $H_g(\mathbf{x}_0)$ is the Hessian of $g(\mathbf{x})$ at the mode.
- $\Sigma$ is the covariance matrix of the distribution (or the Hessian of $p(\mathbf{x})$ at $\mathbf{x}_0$).

### Interpretation

- **$g(\mathbf{x}_0)$**: The leading term is simply the value of the function at the mode $\mathbf{x}_0$. This is the dominant term, especially when the distribution is tightly concentrated around the mode.
- **$\frac{1}{2} \, \text{Tr}(H_g(\mathbf{x}_0) \Sigma)$**: This term accounts for the curvature of the function $g(\mathbf{x})$ near the mode and the covariance (spread) of the distribution. It provides a correction based on how the function changes

 in the neighborhood of the mode and how spread out the distribution is.

### Summary

The Taylor expansion approximation for the expectation of a function $g(\mathbf{X})$ of a vector-valued random variable $\mathbf{X}$ with an unknown multivariable distribution is:

$$\mathbb{E}[g(\mathbf{X})] \approx g(\mathbf{x}_0) + \frac{1}{2} \, \text{Tr}(H_g(\mathbf{x}_0) \Sigma)$$

This approach is useful when:
- The distribution $p(\mathbf{x})$ is unimodal and concentrated around the mode $\mathbf{x}_0$.
- The function $g(\mathbf{x})$ is smooth, allowing for a Taylor expansion.
- The covariance matrix $\Sigma$ (or an approximation of it) is available or can be approximated.

This approximation works well for distributions that are approximately normal or close to unimodal distributions. For highly skewed or multimodal distributions, this method may need further refinement.