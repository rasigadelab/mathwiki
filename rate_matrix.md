# Properties of the transition-rate matrix of a continuous-time Markov process

The **transition rate matrix** (or **generator matrix**) of a **Continuous Time Markov Chain** (CTMC) governs the behavior of the system's transitions over time. The **eigenvalues** and **eigenvectors** of this matrix reveal critical properties about the system's long-term behavior, such as stability, convergence to equilibrium, and transient dynamics. Let’s explore the key properties of the eigenvalues and eigenvectors of the transition rate matrix of a CTMC.

### 1. **Transition Rate (Generator) Matrix Properties**

A **transition rate matrix** $Q = [q_{ij}]$ for a CTMC is a square matrix with the following properties:

- **Off-diagonal elements** ($q_{ij}$ for $i \neq j$) represent the rates of transition from state $i$ to state $j$, and are non-negative:
$$q_{ij} \geq 0 \text{ for } i \neq j$$
- **Diagonal elements** ($q_{ii}$) are the negative of the sum of the rates of leaving state $i$, i.e.,
$$q_{ii} = -\sum_{j \neq i} q_{ij}$$
- The **rows sum to zero**, i.e.,
$$\sum_{j} q_{ij} = 0 \text{ for all } i$$

### 2. **Eigenvalues of the Transition Rate Matrix**

The **eigenvalues** of the transition rate matrix $Q$ provide important information about the time dynamics of the CTMC.

- **Real-valued Eigenvalues**: The eigenvalues of $Q$ are real, because $Q$ is a **real matrix** and can often be seen as similar to a symmetric matrix (especially in reversible processes).
  
- **Negative or Zero Eigenvalues**: The eigenvalues of $Q$ are non-positive real numbers. That is, if $\lambda$ is an eigenvalue of $Q$, then:
$$\lambda \leq 0$$
  This is because the diagonal elements $q_{ii}$ are negative, and the off-diagonal elements $q_{ij} \geq 0$ ensure that the matrix does not have positive eigenvalues. The most negative eigenvalue governs the rate of decay of transient behaviors.

- **Zero Eigenvalue**: The matrix $Q$ always has at least one eigenvalue equal to zero:
$$\lambda_1 = 0$$
  The corresponding eigenvector to this zero eigenvalue corresponds to the **stationary distribution** $\pi$ of the Markov chain, which satisfies:
$$Q \pi = 0$$
  The stationary distribution represents the long-term steady-state probabilities of the states.

- **Non-zero Eigenvalues**: The non-zero eigenvalues correspond to the **rates of decay** of transient modes in the system. The closer the non-zero eigenvalue is to zero, the slower the corresponding mode decays. The magnitude of these eigenvalues controls how quickly the system approaches equilibrium.

### 3. **Eigenvectors of the Transition Rate Matrix**

The **eigenvectors** of $Q$ provide additional insight into the behavior of the CTMC, particularly in terms of how different states of the chain evolve over time.

- **Eigenvector Corresponding to Zero Eigenvalue**:
  - The **left eigenvector** corresponding to the eigenvalue $\lambda_1 = 0$ is the **stationary distribution** $\pi$, which satisfies:
$$\pi^T Q = 0$$

This left eigenvector represents the long-term probabilities that the CTMC will be found in each state once the system reaches equilibrium.
  
  - The **right eigenvector** corresponding to $\lambda_1 = 0$ is typically a **constant vector** (e.g., a vector of all ones), reflecting the fact that the total probability across all states remains constant over time.

- **Non-zero Eigenvalues**:
  - The **right eigenvectors** corresponding to non-zero eigenvalues describe **modes of transient behavior**. These modes capture how the system moves from its initial state distribution towards the stationary distribution over time.
  - The **left eigenvectors** corresponding to non-zero eigenvalues describe how these transient modes influence the overall dynamics when projected back onto the probability space.

### 4. **Decomposition of the Transition Matrix**

The transition rate matrix $Q$ can be decomposed using its eigenvalues and eigenvectors:

$$Q = V \Lambda V^{-1}$$
where:
- $\Lambda$ is a diagonal matrix of the eigenvalues of $Q$ (with at least one zero entry),
- $V$ is a matrix whose columns are the right eigenvectors of $Q$,
- $V^{-1}$ is the inverse of $V$.

This **spectral decomposition** allows us to express the evolution of the system’s state probabilities over time as:

$$p(t) = e^{Qt} p(0) = V e^{\Lambda t} V^{-1} p(0)$$
where $p(0)$ is the initial state distribution and $p(t)$ is the distribution at time $t$. The matrix $e^{\Lambda t}$ involves exponentiating the eigenvalues, which reveals the decay of the transient modes as time progresses. Modes corresponding to non-zero eigenvalues decay exponentially over time.

### 5. **Convergence to Stationary Distribution**

- The **zero eigenvalue** corresponds to the stationary distribution, and as time goes to infinity ($t \to \infty$), the contribution of the non-zero eigenvalues decays to zero.
- As a result, the system's probability distribution converges to the stationary distribution $\pi$, assuming the chain is **ergodic** (i.e., irreducible and positive recurrent).

### 6. **Reversible Markov Chains**

For **reversible Markov chains**, the generator matrix $Q$ has additional properties:

- The eigenvalues of $Q$ are **real and non-positive** because reversible Markov chains are closely related to symmetric matrices. This symmetry simplifies the computation of eigenvalues and eigenvectors.
- In reversible chains, the matrix $Q$ is **similar to a symmetric matrix** (through diagonalization by the stationary distribution), and thus the eigenvectors are orthogonal.

### 7. **Interpretation of the Magnitude of Eigenvalues**

The magnitude of the non-zero eigenvalues of $Q$ gives insight into how quickly the Markov chain "forgets" its initial state:

- **Larger negative eigenvalues**: Correspond to **faster decay** of the corresponding mode, meaning that the system moves quickly to equilibrium along that direction.
- **Smaller negative eigenvalues** (closer to zero): Correspond to **slower decay** and longer-lasting transient behavior.

### 8. **Ergodicity and Irreducibility**

- If the CTMC is **irreducible** (i.e., it is possible to reach any state from any other state), there will be a unique eigenvalue $\lambda_1 = 0$, and all other eigenvalues will be negative. The system will converge to a unique stationary distribution.
- If the CTMC is **reducible**, there may be multiple zero eigenvalues corresponding to different invariant subspaces (i.e., multiple stationary distributions or absorbing states).

### Summary of Key Properties

1. **Eigenvalues**:
   - The matrix $Q$ has at least one eigenvalue equal to zero ($\lambda_1 = 0$).
   - All other eigenvalues are real and non-positive ($\lambda_i \leq 0$).
   - The eigenvalues represent rates of decay of transient modes, with larger negative values corresponding to faster convergence to equilibrium.

2. **Eigenvectors**:
   - The left eigenvector corresponding to $\lambda_1 = 0$ is the stationary distribution $\pi$.
   - The right eigenvector corresponding to $\lambda_1 = 0$ is typically a constant vector.
   - Eigenvectors corresponding to non-zero eigenvalues describe transient behaviors and how the system approaches equilibrium.

3. **Convergence**: The system converges to the stationary distribution over time, with the rate of convergence determined by the non-zero eigenvalues.

4. **Reversibility**: In reversible Markov chains, the eigenvalues and eigenvectors have additional symmetry properties, and the eigenvalues are real and non-positive.

These properties of the eigenvalues and eigenvectors of the transition rate matrix help us understand the dynamics, convergence, and steady-state behavior of continuous-time Markov chains.

## Constrained perturbation of eigenvalues and eigenvectors

**Inequality constraints** can be imposed on the perturbed eigenvalues and eigenvectors of a transition rate matrix to ensure that the **off-diagonal elements** of the transition rate matrix remain **non-negative**. Here’s how we can approach this:

### Key Constraints for Transition Rate Matrix:
1. **Off-diagonal elements non-negative**: For all $i \neq j$, $Q_{ij} \geq 0$.
2. **Rows sum to zero**: For each row $i$, $\sum_j Q_{ij} = 0$.

Perturbing the eigenvalues and eigenvectors can affect the structure of the matrix $Q$, so the goal is to impose constraints during this perturbation to ensure the resulting matrix is still a valid **generator matrix** with these properties.

### 1. Eigenvalue Constraints

The eigenvalues of a transition rate matrix have the following properties:
- There is always at least one eigenvalue equal to **zero** (this corresponds to the steady-state or equilibrium distribution).
- All other eigenvalues must have **non-positive real parts**: $\Re(\lambda_i) \leq 0$. This ensures that the system remains stable and all transient modes decay over time.

#### Constraint on Eigenvalue Perturbations:
When perturbing the eigenvalues $\lambda_i$ of the transition rate matrix $Q$, the following inequality constraints should be imposed:
- The zero eigenvalue must remain **exactly zero**:
$$\lambda_1 = 0$$
- For all other eigenvalues, their real parts must remain **non-positive**:
$$\Re(\lambda_i) \leq 0 \quad \text{for all} \ i \neq 1$$

This ensures that the perturbed matrix remains a valid transition rate matrix, where eigenvalues still correspond to decay rates or stationary behavior.

### 2. Eigenvector Constraints

The eigenvectors of the matrix $Q$ represent the directions in which the matrix evolves. The key eigenvector to consider is the one associated with the **zero eigenvalue**. This eigenvector corresponds to the **steady-state distribution**, which must satisfy:
- The steady-state vector $\pi$ must have **non-negative components**: $\pi_i \geq 0$.
- Typically, $\pi$ is normalized so that $\sum_i \pi_i = 1$.

#### Constraint on Eigenvector Perturbations:
When perturbing the eigenvector $\pi$ associated with the zero eigenvalue, the following inequality constraints should be imposed:
- The perturbed steady-state vector $\pi'$ must still be **non-negative**:
$$\pi'_i \geq 0 \quad \text{for all} \ i$$
- The normalization condition must still hold:
$$\sum_i \pi'_i = 1$$
For the other eigenvectors (corresponding to transient modes), the constraints are less strict, but any perturbation should ensure that the matrix $Q$ still produces a valid generator matrix after reconstruction.

### 3. Reconstruction of the Perturbed Matrix

Once the eigenvalues and eigenvectors are perturbed, the matrix $Q'$ is reconstructed as:
$$Q' = V' \Lambda' V'^{-1}$$
Where:
- $V'$ is the perturbed eigenvector matrix,
- $\Lambda'$ is the perturbed diagonal eigenvalue matrix.

To ensure that the off-diagonal elements of $Q'$ are non-negative, **additional inequality constraints** should be imposed on the reconstructed matrix.

#### Constraint on Off-diagonal Elements:
For all $i \neq j$, we impose the following condition:
$$Q'_{ij} \geq 0 \quad \text{for all} \ i \neq j$$

These constraints can be imposed during the perturbation process or as a post-processing step to adjust any perturbed values that violate the non-negativity condition.

### 4. Practical Approach: Quadratic Programming or Constrained Optimization

To handle perturbations while ensuring these constraints are satisfied, we can use **constrained optimization** techniques. This can be formulated as a **quadratic programming** (QP) or **nonlinear programming** (NLP) problem, where:

- The **objective function** is to minimize the deviation of the perturbed eigenvalues and eigenvectors from their original values (this could be formulated as minimizing the Frobenius norm of the difference between $Q$ and $Q'$, for example).
  
- The **constraints** are:
  1. The zero eigenvalue remains unchanged, $\lambda_1 = 0$, and all other eigenvalues have non-positive real parts, $\Re(\lambda_i) \leq 0$.
  2. The perturbed steady-state eigenvector remains non-negative, $\pi'_i \geq 0$, and normalized, $\sum_i \pi'_i = 1$.
  3. The off-diagonal elements of the matrix remain non-negative, $Q'_{ij} \geq 0$.

In practice, algorithms such as **gradient descent** with constraints, **interior point methods**, or **active set methods** can be used to solve this optimization problem while ensuring all the constraints are satisfied.

### Example Formulation for Perturbation with Constraints

Let’s assume we have a small perturbation $\Delta Q$ to the original matrix $Q$. The goal is to perturb $Q$ while satisfying the constraints:

1. **Objective**: Minimize $\|\Delta Q\|_F$, the Frobenius norm of the perturbation.
2. **Constraints**:
   - $\lambda_1 = 0$, $\Re(\lambda_i) \leq 0$ for $i \neq 1$,
   - $\pi'_i \geq 0$ and $\sum_i \pi'_i = 1$,
   - $Q'_{ij} \geq 0$ for $i \neq j$.

The problem can be solved using a numerical optimization solver that supports quadratic or nonlinear constraints.

### Conclusion

We can impose **inequality constraints** on the perturbed eigenvalues and eigenvectors to ensure that the off-diagonal elements of the perturbed transition rate matrix remain non-negative. This can be formulated as a constrained optimization problem where the constraints ensure:
- The zero eigenvalue is preserved,
- The real parts of all other eigenvalues are non-positive,
- The eigenvector associated with the zero eigenvalue is non-negative and normalized,
- The off-diagonal elements of the reconstructed matrix are non-negative.

By carefully constructing these constraints, we ensure that the perturbations result in a matrix that still satisfies the properties of a valid transition rate matrix.