## The generalized Jukes-Cantor model

The **generalized Jukes-Cantor model** extends the original **Jukes-Cantor (JC69) model** to handle an arbitrary number of states $K$. This model is used in evolutionary biology to describe the substitution of discrete characters (such as nucleotides or amino acids) over time in a **continuous-time Markov chain (CTMC)** framework. The original JC69 model applies to four nucleotides (A, C, G, T), assuming equal rates of substitution between all pairs of nucleotides. The generalized model extends this to $K$ states and assumes symmetric substitution rates between any two states.

### 1. **Generalized Jukes-Cantor Model Setup**

Let the number of possible states be $K$ (where $K$ could represent nucleotides, amino acids, or other discrete characters). In the generalized Jukes-Cantor model:
- Each state has an equal probability of transitioning to any other state.
- The substitution rate from one state to another is the same across all state pairs.

The substitution process is governed by a **transition rate matrix** $Q$, where:
- $q_{ij} = \beta$ for all $i \neq j$, representing the rate at which state $i$ transitions to state $j$.
- $q_{ii} = -(K-1)\beta$, which ensures that the rows of the rate matrix sum to zero. This reflects the total rate of leaving state $i$.

Thus, the transition rate matrix $Q$ for $K$ states can be written as:

$$Q_{\text{Generalized JC}} =
\begin{pmatrix}
-(K-1)\beta & \beta & \beta & \dots & \beta \\
\beta & -(K-1)\beta & \beta & \dots & \beta \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
\beta & \beta & \beta & \dots & -(K-1)\beta
\end{pmatrix}$$

This matrix describes the instantaneous rates of transitioning between states in the generalized Jukes-Cantor model.

### 2. **Solving for the Transition Probability Matrix**

The goal is to find the **transition probability matrix** $P(t)$, which gives the probability of transitioning from one state to another after time $t$. This matrix is the solution to the matrix differential equation:

$$\frac{dP(t)}{dt} = P(t) Q$$

The solution is given by the matrix exponential:

$$P(t) = e^{Qt}$$

For the generalized Jukes-Cantor model, since $Q$ has a symmetric structure, the matrix exponential can be computed in closed form.

### 3. **Eigenvalues and Eigenvectors of $Q$**

To compute the matrix exponential $e^{Qt}$, we first find the **eigenvalues** and **eigenvectors** of $Q$. The matrix $Q$ is symmetric, so it has a full set of real eigenvalues and orthogonal eigenvectors.

#### Eigenvalues

The eigenvalues of the matrix $Q$ are:
- One eigenvalue is 0, corresponding to the stationary distribution where all states have equal probability.
- The other $K-1$ eigenvalues are $-(K-1)\beta$.

#### Eigenvectors

The eigenvector corresponding to the eigenvalue 0 is the vector where all components are equal, representing the uniform stationary distribution. The eigenvectors corresponding to the eigenvalue $-(K-1)\beta$ are orthogonal to the uniform vector and represent the directions in which the process decays exponentially over time.

### 4. **Closed-Form Solution for Transition Probabilities**

Using the eigenvalue decomposition, we can derive the closed-form solution for the transition probabilities. The transition probability matrix $P(t)$ has the following structure:

$$P(t) = \frac{1}{K} \mathbf{1} \mathbf{1}^T + \left( I - \frac{1}{K} \mathbf{1} \mathbf{1}^T \right) e^{-(K-1)\beta t}$$

where:
- $\mathbf{1}$ is the column vector of ones (dimension $K \times 1$).
- $I$ is the identity matrix.
- $\frac{1}{K} \mathbf{1} \mathbf{1}^T$ represents the stationary distribution, where all states are equally probable.
- The term $e^{-(K-1)\beta t}$ represents the exponential decay in the probability of remaining in the same state.

This solution reflects two key behaviors:
1. **Stationary Distribution**: As $t \to \infty$, the process converges to the uniform stationary distribution, where each state has probability $\frac{1}{K}$.
2. **Exponential Decay**: Over time, the process moves away from the initial state and converges toward the stationary distribution at a rate proportional to $\beta$.

### 5. **Transition Probabilities Between States**

The specific probabilities of transitioning from state $i$ to state $j$ at time $t$ can be derived from the matrix $P(t)$. For the generalized Jukes-Cantor model, the probabilities are:

- **Probability of staying in the same state** $i$ after time $t$:

  $$P_{ii}(t) = \frac{1}{K} + \left( 1 - \frac{1}{K} \right) e^{-(K-1)\beta t}$$

  This formula shows that the probability of staying in the same state decreases over time, eventually approaching $\frac{1}{K}$, the probability that corresponds to the stationary distribution.

- **Probability of transitioning to a different state** $j \neq i$ after time $t$:

  $$P_{ij}(t) = \frac{1}{K} \left( 1 - e^{-(K-1)\beta t} \right)$$

  This formula shows that the probability of transitioning to any other state increases over time and converges to $\frac{1}{K}$, reflecting the uniform stationary distribution.

### 6. **Long-Term Behavior (Stationary Distribution)**

In the long run, as $t \to \infty$, the system reaches its **stationary distribution**, where the probability of being in any state is the same. The stationary distribution is:

$$\lim_{t \to \infty} P(t) = \frac{1}{K} \mathbf{1} \mathbf{1}^T$$

This reflects the fact that in the generalized Jukes-Cantor model, all states are equally probable at equilibrium.

### 7. **Example: Generalized JC Model for $K = 4$ (Nucleotides)**

For $K = 4$ (the case of nucleotides A, C, G, T), the generalized Jukes-Cantor model reduces to the original **JC69 model**. In this case:
- The substitution rate between any two nucleotides is $\beta = \alpha/3$, where $\alpha$ is the overall rate of substitution.
- The transition probabilities have the form:

$$P_{ii}(t) = \frac{1}{4} + \frac{3}{4} e^{-\alpha t}$$

$$P_{ij}(t) = \frac{1}{4} \left( 1 - e^{-\alpha t} \right)$$

This is the familiar result from the JC69 model, which describes how the probability of remaining in the same nucleotide decays over time, while the probability of transitioning to a different nucleotide increases.

### 8. **Applications of the Generalized JC Model**

The generalized Jukes-Cantor model is used in various fields, including:
- **Molecular Evolution**: To model the substitution of nucleotides, amino acids, or other molecular sequences over evolutionary time.
- **Phylogenetic Inference**: To estimate the evolutionary distances between species based on genetic data.
- **Markov Chain Models**: In broader applications, to model systems with $K$ discrete states that transition between states over time.

### Summary

- The **generalized Jukes-Cantor model** extends the original JC69 model to $K$ states, assuming symmetric substitution rates between all pairs of states.
- The **transition rate matrix** $Q$ describes the rates of transitioning between states, with equal off-diagonal elements $\beta$ and diagonal elements $-(K-1)\beta$.
- The **transition probability matrix** $P(t)$ can be computed in closed form using the matrix exponential, with probabilities that describe how the system evolves over time.
- As $t \to \infty$, the system converges to a **uniform stationary distribution**, where all states are equally probable.
- The model has applications in molecular evolution, phylogenetics, and any context where transitions between discrete states are modeled using Markov chains.