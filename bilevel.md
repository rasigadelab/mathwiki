## Bilevel optimization: use cases

Bilevel optimization is a special class of optimization problems involving two levels of decision-making, where one optimization problem (the "upper-level problem") is nested within another (the "lower-level problem"). The solution of the upper-level problem depends on the solution of the lower-level problem. This hierarchical structure makes bilevel optimization suitable for scenarios where one decision-maker controls the upper level and another controls the lower level. Here are some common use cases:

### 1. **Pricing and Supply Chain Optimization**
   - **Use Case**: In supply chain management, a manufacturer (upper level) decides on pricing and production quantities, while a retailer (lower level) decides on order quantities based on the manufacturer's decisions.
   - **How Bilevel Optimization Helps**: The manufacturer's decisions are made with the knowledge that the retailer's response will be optimizing its own costs. Bilevel optimization captures this interaction to maximize overall profits.

### 2. **Energy Markets**
   - **Use Case**: In electricity markets, the independent system operator (ISO) may set market prices and generate schedules (upper level) while power generators respond to these prices by choosing generation levels (lower level).
   - **How Bilevel Optimization Helps**: The ISO seeks to minimize total operational costs, while generators aim to maximize their individual profits. Bilevel optimization models this competition between market regulators and participants.

### 3. **Environmental Policy and Regulation**
   - **Use Case**: Governments set environmental policies or taxes (upper level) aimed at reducing emissions, while companies (lower level) react by adjusting their production processes to minimize costs while complying with the regulations.
   - **How Bilevel Optimization Helps**: Governments must anticipate how companies will react to regulations, and bilevel optimization allows for modeling this interplay, finding policies that balance economic and environmental goals.

### 4. **Adversarial Machine Learning**
   - **Use Case**: In adversarial machine learning, an attacker (lower level) tries to fool a machine learning model by providing adversarial examples, while the defender (upper level) designs robust models that can resist such attacks.
   - **How Bilevel Optimization Helps**: The upper-level optimization aims to minimize the error of the model while considering the worst-case actions of the adversary, which are modeled in the lower-level optimization.

### 5. **Game Theory and Economics**
   - **Use Case**: In Stackelberg games, a leader (upper level) makes a decision first, and a follower (lower level) reacts to the leader's decision. This is common in economic settings such as pricing competition or market entry games.
   - **How Bilevel Optimization Helps**: The leader must anticipate the reaction of the follower and optimize accordingly, while the follower solves their own optimization problem based on the leader's decision.

### 6. **Hyperparameter Tuning in Machine Learning**
   - **Use Case**: Hyperparameter tuning is often formulated as a bilevel optimization problem, where the upper level seeks to find the best hyperparameters, and the lower level optimizes the model's parameters (e.g., weights) based on those hyperparameters.
   - **How Bilevel Optimization Helps**: By treating hyperparameter selection as a high-level decision problem and the learning process as a lower-level optimization problem, bilevel optimization frameworks enable more systematic tuning of machine learning models.

### 7. **Network Design and Traffic Management**
   - **Use Case**: In transportation networks, city planners (upper level) may optimize the design of roads or toll pricing, while drivers (lower level) optimize their routes to minimize travel time.
   - **How Bilevel Optimization Helps**: The upper-level decision-maker (planners) aims to reduce congestion or improve network efficiency, while the lower-level decision-makers (drivers) make selfish routing decisions. Bilevel optimization helps align these interests for better outcomes.

### 8. **Finance and Investment Strategies**
   - **Use Case**: In portfolio optimization, an investor (upper level) decides on investment strategies, while the market (lower level) reacts by changing asset prices based on supply and demand.
   - **How Bilevel Optimization Helps**: The investor needs to consider how the market will respond to their investment decisions. Bilevel optimization helps capture this interdependence and optimize accordingly.

### 9. **Biological Systems and Control**
   - **Use Case**: In biological systems, bilevel optimization can be used for metabolic engineering, where an engineer (upper level) designs genetic modifications, and the cell (lower level) optimizes its metabolic processes based on these changes.
   - **How Bilevel Optimization Helps**: The engineer needs to account for the cell's natural responses and biological constraints. Bilevel optimization helps to design interventions that lead to the desired outcome.

In all these cases, bilevel optimization provides a powerful framework to model hierarchical decision-making processes where the outcomes at one level depend on the optimized responses at another level. It is widely applicable in economics, engineering, operations research, and machine learning.

## Bilevel optimization: an overview

In mathematical terms, bilevel optimization involves two nested optimization problems: an **upper-level problem** and a **lower-level problem**. The decision variable of the upper-level problem influences the lower-level problem, and the optimal solution to the lower-level problem is a function of the upper-level decision variable.

### General Formulation

A bilevel optimization problem can be written as:

$$\min_{x \in X} \ F(x, y)$$
subject to:
$$y \in \arg\min_{y \in Y(x)} \ f(x, y)$$

- $x \in \mathbb{R}^n$ is the decision variable of the upper-level problem.
- $y \in \mathbb{R}^m$ is the decision variable of the lower-level problem.
- $F(x, y)$ is the upper-level objective function.
- $f(x, y)$ is the lower-level objective function.
- $Y(x)$ denotes the feasible set for $y$, which can depend on $x$.

Here, the upper-level problem is constrained by the optimal solution $y(x)$ of the lower-level problem. This creates a nested structure: to solve the upper-level problem, we must solve the lower-level problem for a given $x$, and the solution to the lower-level problem defines the constraints of the upper-level problem.

### Gradient Descent in Bilevel Optimization

When using gradient descent methods to solve bilevel optimization problems, the challenge is to compute the gradients of the upper-level objective $F(x, y(x))$, where $y(x)$ is implicitly defined by the lower-level problem. The key challenge is handling this implicit dependency of $y$ on $x$.

#### 1. **Lower-Level Problem Solution via Gradient Descent**

For a given $x$, we can solve the lower-level problem $\min_{y \in Y(x)} f(x, y)$ using a standard gradient descent method. If $y^+(x)$ is the optimal solution to the lower-level problem, we want to update $y$ iteratively using:

$$y_{k+1} = y_k - \eta_y \nabla_y f(x, y_k)$$

where $\eta_y$ is the step size, and $\nabla_y f(x, y_k)$ is the gradient of the lower-level objective function with respect to $y$.

Once we have converged to an approximate optimal solution $y^+(x)$ for a fixed $x$, we can proceed to update $x$.

#### 2. **Upper-Level Gradient Computation**

The upper-level problem involves optimizing $F(x, y(x))$, where $y(x)$ is the optimal solution to the lower-level problem for a given $x$. The total gradient of the upper-level objective with respect to $x$ is given by the **chain rule**:

$$\nabla_x F(x, y(x)) = \frac{\partial F(x, y)}{\partial x} + \frac{\partial F(x, y)}{\partial y} \cdot \frac{\partial y(x)}{\partial x}$$

The key difficulty lies in computing $\frac{\partial y(x)}{\partial x}$, the derivative of the lower-level solution $y(x)$ with respect to $x$.

##### **Implicit Differentiation Approach**

If the lower-level problem is solved optimally, we can use the **optimality conditions** of the lower-level problem (assuming $y^+(x)$ satisfies the first-order optimality condition) to compute the derivative of $y(x)$ with respect to $x$. For example, if $f(x, y)$ is smooth, the optimality condition is:

$$\nabla_y f(x, y^+(x)) = 0$$

Taking the total derivative with respect to $x$ on both sides gives:

$$\nabla_{xy}^2 f(x, y^+(x)) + \nabla_{yy}^2 f(x, y^+(x)) \cdot \frac{\partial y(x)}{\partial x} = 0$$

Solving for $\frac{\partial y(x)}{\partial x}$:

$$\frac{\partial y(x)}{\partial x} = - \left( \nabla_{yy}^2 f(x, y^+(x)) \right)^{-1} \nabla_{xy}^2 f(x, y^+(x))$$

- $\nabla_{xy}^2 f(x, y)$ is the mixed second-order partial derivative of $f$ with respect to $x$ and $y$.
- $\nabla_{yy}^2 f(x, y)$ is the Hessian of $f$ with respect to $y$.

Using this, we can compute the upper-level gradient:

$$\nabla_x F(x, y(x)) = \frac{\partial F(x, y)}{\partial x} + \frac{\partial F(x, y)}{\partial y} \cdot \left( - \left( \nabla_{yy}^2 f(x, y^+(x)) \right)^{-1} \nabla_{xy}^2 f(x, y^+(x)) \right)$$

This gradient can then be used to update $x$ using gradient descent:

$$x_{k+1} = x_k - \eta_x \nabla_x F(x_k, y^+(x_k))$$

where $\eta_x$ is the step size for updating $x$.

#### 3. **Bilevel Optimization via Gradient Descent**

In practice, bilevel optimization is often solved by iterating between the two levels:

1. **Solve the lower-level problem** to find the optimal $y^+(x_k)$ for the current $x_k$ using gradient descent.
2. **Compute the upper-level gradient** $\nabla_x F(x_k, y^+(x_k))$ using the chain rule and implicit differentiation.
3. **Update $x_k$** using gradient descent on the upper-level objective function.
4. **Repeat** until convergence.

This iterative approach combines gradient descent on both the lower- and upper-level problems, with implicit differentiation used to account for the dependency of $y(x)$ on $x$.

### Challenges

- **Computation of the inverse Hessian** $\left( \nabla_{yy}^2 f(x, y) \right)^{-1}$ can be computationally expensive, especially when the dimension of $y$ is large.
- **Non-convexity**: Both the upper-level and lower-level problems may be non-convex, leading to local minima and making convergence challenging.
- **Approximate Solutions**: In practice, we may only compute an approximate solution to the lower-level problem, which introduces approximation errors into the upper-level gradient.

Nonetheless, bilevel optimization with gradient descent and implicit differentiation provides a powerful framework for solving hierarchical problems with interdependent decision-making.

## Second-order bilevel optimization

When applying the **Newton method** to solve bilevel optimization problems, the approach focuses on using second-order information (Hessian matrices) rather than just first-order gradients, as is the case with gradient descent. This allows for faster convergence, especially for smooth, well-behaved functions, though it comes at the cost of more computational complexity due to the need to compute and invert Hessians.

### General Formulation of Bilevel Optimization

A bilevel optimization problem can be expressed mathematically as:

$$\min_{x \in X} F(x, y(x))$$
subject to:
$$y(x) \in \arg\min_{y \in Y(x)} f(x, y)$$

- $x \in \mathbb{R}^n$ is the decision variable of the upper-level problem.
- $y \in \mathbb{R}^m$ is the decision variable of the lower-level problem.
- $F(x, y)$ is the objective function of the upper-level problem.
- $f(x, y)$ is the objective function of the lower-level problem.
- $y(x)$ is the optimal solution to the lower-level problem, which is itself dependent on $x$.

### Newton Method for Bilevel Optimization

Newton's method is used to solve optimization problems by taking into account both the gradient and the Hessian of the objective function. It is especially useful when the objective functions are twice differentiable and reasonably smooth.

#### 1. **Lower-Level Problem: Newton's Method**

For the lower-level problem $\min_{y} f(x, y)$, given a fixed $x$, we use Newton's method to solve for $y(x)$. Newton's update rule for the lower-level problem is:

$$y_{k+1} = y_k - H_y^{-1}(x, y_k) \nabla_y f(x, y_k)$$

where:
- $H_y(x, y_k) = \nabla^2_y f(x, y_k)$ is the Hessian of the lower-level objective $f(x, y)$ with respect to $y$.
- $\nabla_y f(x, y_k)$ is the gradient of $f(x, y)$ with respect to $y$.

Newton's method converges quadratically if the Hessian is well-conditioned (i.e., positive definite). This allows for rapid convergence to the solution $y^+(x)$ for a fixed $x$.

#### 2. **Upper-Level Gradient and Hessian Calculation**

The goal at the upper level is to minimize $F(x, y(x))$, where $y(x)$ is the optimal solution of the lower-level problem. To apply Newton's method at the upper level, we need to compute both the **gradient** and **Hessian** of the upper-level objective $F(x, y(x))$.

##### **Gradient Calculation**

The gradient of the upper-level objective $F(x, y(x))$ can be written using the chain rule:

$$\nabla_x F(x, y(x)) = \frac{\partial F(x, y)}{\partial x} + \frac{\partial F(x, y)}{\partial y} \cdot \frac{\partial y(x)}{\partial x}$$

Here, the key term to compute is $\frac{\partial y(x)}{\partial x}$, which can be derived using **implicit differentiation** based on the lower-level problem's optimality condition.

From the first-order optimality condition of the lower-level problem:

$$\nabla_y f(x, y^+(x)) = 0$$

Taking the total derivative with respect to $x$:

$$\nabla_{xy}^2 f(x, y^+(x)) + \nabla_{yy}^2 f(x, y^+(x)) \cdot \frac{\partial y(x)}{\partial x} = 0$$

Solving for $\frac{\partial y(x)}{\partial x}$:

$$\frac{\partial y(x)}{\partial x} = - \left( \nabla_{yy}^2 f(x, y^+(x)) \right)^{-1} \nabla_{xy}^2 f(x, y^+(x))$$

Thus, the gradient of the upper-level problem is:

$$\nabla_x F(x, y(x)) = \frac{\partial F(x, y)}{\partial x} - \frac{\partial F(x, y)}{\partial y} \cdot \left( \nabla_{yy}^2 f(x, y^+(x)) \right)^{-1} \nabla_{xy}^2 f(x, y^+(x))$$

##### **Hessian Calculation**

For Newton's method, we also need to compute the Hessian of the upper-level objective $F(x, y(x))$, which involves second-order derivatives. The total derivative of the gradient $\nabla_x F(x, y(x))$ gives us the Hessian of $F$ with respect to $x$.

The Hessian consists of several terms:

1. **Hessian of the upper-level objective**: $\nabla_{xx}^2 F(x, y)$, which can be computed directly if $F$ is known.
2. **Interaction terms**: Involving derivatives of $\nabla_x y(x)$, which includes higher-order derivatives from the lower-level problem.

Using implicit differentiation again, we find that the full Hessian $H_x$ is:

$$H_x = \nabla_{xx}^2 F(x, y) - \nabla_{xy}^2 F(x, y) \left( \nabla_{yy}^2 f(x, y^+(x)) \right)^{-1} \nabla_{xy}^2 f(x, y^+(x))$$

The second term accounts for the effect of the lower-level solution's dependence on $x$.

#### 3. **Newton's Method for the Upper-Level Problem**

Once we have the gradient $\nabla_x F(x, y(x))$ and the Hessian $H_x$, we can apply Newton's method to update $x$ as follows:

$$x_{k+1} = x_k - H_x^{-1} \nabla_x F(x_k, y^+(x_k))$$

This update rule incorporates second-order information and is expected to converge quadratically, provided that the Hessian is well-conditioned.

#### 4. **Overall Algorithm: Bilevel Optimization with Newton's Method**

The overall bilevel optimization process using Newton's method can be summarized in the following steps:

1. **Lower-Level Optimization**:
   - For a given $x_k$, solve the lower-level problem $\min_y f(x_k, y)$ using Newton's method to find $y^+(x_k)$.
   
2. **Upper-Level Gradient and Hessian**:
   - Compute the upper-level gradient $\nabla_x F(x_k, y^+(x_k))$ using implicit differentiation.
   - Compute the upper-level Hessian $H_x$ using second-order derivatives and implicit differentiation.

3. **Upper-Level Newton Update**:
   - Update $x_k$ using the Newton step:
$$x_{k+1} = x_k - H_x^{-1} \nabla_x F(x_k, y^+(x_k))$$

4. **Repeat** until convergence, where both the upper-level and lower-level solutions stabilize.

### Challenges and Considerations

- **Hessian Computation and Inversion**: Newton's method requires computing and inverting Hessians at both the upper and lower levels, which can be computationally expensive, especially if the dimensions of $x$ and $y$ are large.
  
- **Non-convexity**: If either the upper-level or lower-level problem is non-convex, Newton's method may converge to a local minimum rather than a global one. In such cases, regularization or trust-region methods may be needed.

- **Feasibility and Convergence**: The convergence of Newton's method is sensitive to the conditioning of the Hessian matrices. Poorly conditioned Hessians can lead to slow convergence or even divergence.

### Conclusion

Newton's method, when applied to bilevel optimization, leverages second-order information to achieve faster convergence, especially near optimal points. However, the computational cost of evaluating and inverting Hessians, especially when combined with the nested structure of bilevel problems, can be significant. Nonetheless, in cases where efficiency and precision are crucial, the Newton approach provides an effective framework for bilevel optimization.