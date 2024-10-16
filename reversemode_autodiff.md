# Reverse mode in automatic differentiation

Reverse mode automatic differentiation is a method used to efficiently compute derivatives, especially when dealing with functions that have many inputs and a single output. It's particularly useful in fields like machine learning, where calculating gradients for optimization (e.g., during backpropagation in neural networks) is a common task.

### How Reverse Mode Works

Let’s say we have a function $f : \mathbb{R}^n \to \mathbb{R}$, meaning a function that takes $n$ inputs and produces a single output.

#### Forward Mode vs. Reverse Mode

- **Forward Mode** calculates derivatives for each intermediate variable as the function is evaluated. This is efficient when the number of inputs is small and the number of outputs is large.
- **Reverse Mode**, on the other hand, works backwards from the output. It computes the derivatives of the output with respect to each input efficiently, making it especially useful when the number of inputs is large and the number of outputs is small (e.g., machine learning models).

### Reverse Mode Step-by-Step:

1. **Forward Pass**: During the forward pass, the function is evaluated from inputs to output. Each intermediate variable is stored as the function progresses.

2. **Backward Pass**: Once the function has been fully evaluated and the output is known, the reverse mode goes backward to compute the derivatives (also known as adjoints or sensitivities) of the output with respect to each intermediate variable and, eventually, with respect to the original inputs.

3. **Chain Rule**: Reverse mode uses the chain rule of calculus to propagate derivatives from the output to the inputs. The derivative of the output with respect to an intermediate variable is multiplied by the derivative of that intermediate variable with respect to the inputs, and this process is repeated backward through the computational graph.

### Key Features:

- **Efficient for Many Inputs**: In cases where there are many inputs and one output, reverse mode is computationally efficient because it computes the gradient in a single backward pass.
  
- **Backpropagation**: In machine learning, reverse mode automatic differentiation is used during backpropagation, where the loss function (a scalar) is differentiated with respect to the parameters of the model (typically many parameters, like weights in a neural network).

### Example:

Consider a simple function $f(x, y, z) = x \cdot y + z$.

- **Forward Pass**: First, we compute the output:

$$f(x, y, z) = x \cdot y + z$$

- **Backward Pass**: Now, we compute the derivatives $\frac{\partial f}{\partial x}$, $\frac{\partial f}{\partial y}$, and $\frac{\partial f}{\partial z}$. Using reverse mode, we start from the output and propagate the derivatives back:
$$\frac{\partial f}{\partial x} = y, \quad \frac{\partial f}{\partial y} = x, \quad \frac{\partial f}{\partial z} = 1$$

In reverse mode, the computation is efficient, as all partial derivatives with respect to inputs are computed in one backward pass. 

This efficiency is what makes reverse mode automatic differentiation a core technique in optimizing functions with many parameters, like neural networks.