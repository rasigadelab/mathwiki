## Generalized Time-Reversible model

The **Generalized Time-Reversible (GTR) model** is a widely used model in molecular evolution that describes the substitution rates between different states (such as nucleotides or amino acids) over time. The GTR model is a more flexible and general model than simpler models like the **Jukes-Cantor** or **Kimura models** because it allows for different rates of substitution between different states, while still maintaining a key property called **time reversibility**.

The GTR model can be generalized to an arbitrary number of states $K$, where $K$ could represent nucleotides, amino acids, or any set of discrete entities that evolve over time according to a **continuous-time Markov chain (CTMC)**.

### 1. **Key Features of the GTR Model**

- **Arbitrary Transition Rates**: Unlike simpler models, the GTR model allows different substitution rates between different pairs of states, so that the rate of substitution from state $i$ to state $j$ (denoted $q_{ij}$) is generally not the same as the rate from $j$ to $i$.
  
- **Time Reversibility**: The model assumes that the evolutionary process is **time-reversible**, meaning that the process looks the same whether we follow it forward or backward in time. Mathematically, this means that the product of the equilibrium frequencies and the substitution rates satisfies $\pi_i q_{ij} = \pi_j q_{ji}$, where $\pi_i$ is the equilibrium frequency of state $i$.

- **Stationary Distribution**: The GTR model assumes the existence of a **stationary distribution** $\pi$, meaning that over long periods of time, the probability of being in state $i$ reaches a constant value $\pi_i$. This stationary distribution represents the equilibrium frequencies of the different states.

### 2. **Rate Matrix (Q Matrix)**

The GTR model is defined by a **transition rate matrix** $Q$, also known as the **infinitesimal generator** of the CTMC. The rate matrix describes how quickly the system transitions between different states. For a process with $K$ states, the rate matrix is a $K \times K$ matrix $Q$, with the following properties:

1. **Off-diagonal elements** $q_{ij}$ (for $i \neq j$) represent the rate at which state $i$ transitions to state $j$.
2. **Diagonal elements** $q_{ii}$ are chosen so that the rows of the matrix sum to zero. This ensures that $Q$ defines a valid Markov process, where the total probability flow out of each state is balanced by the flow into other states.

The general form of $Q$ for the GTR model is:

$$Q =
\begin{pmatrix}
-q_1 & q_{12} & q_{13} & \dots & q_{1K} \\
q_{21} & -q_2 & q_{23} & \dots & q_{2K} \\
q_{31} & q_{32} & -q_3 & \dots & q_{3K} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
q_{K1} & q_{K2} & q_{K3} & \dots & -q_K
\end{pmatrix}$$

where:
- $q_{ij}$ (for $i \neq j$) is the rate of transitioning from state $i$ to state $j$,
- $q_i = \sum_{j \neq i} q_{ij}$, which ensures that each row sums to zero.

### 3. **Time-Reversibility Condition**

The defining characteristic of the GTR model is the **time-reversibility condition**:

$$\pi_i q_{ij} = \pi_j q_{ji}$$

This condition means that the process is symmetric in time. Intuitively, the number of transitions from state $i$ to state $j$ over long periods of time is the same as the number of transitions from state $j$ to state $i$, when weighted by the equilibrium frequencies $\pi_i$ and $\pi_j$.

### 4. **Parametrization of the GTR Model**

To satisfy the time-reversibility condition, the transition rate matrix $Q$ is often parametrized as follows:

$$q_{ij} = \pi_j r_{ij} \quad \text{for} \quad i \neq j$$

where:
- $\pi_j$ is the equilibrium frequency of state $j$,
- $r_{ij}$ is a symmetric **exchangeability rate**, meaning that $r_{ij} = r_{ji}$ for all $i, j$.

The off-diagonal elements of $Q$ are thus products of the equilibrium frequencies $\pi_j$ and the exchangeability rates $r_{ij}$.

The diagonal elements are determined by the condition that the rows must sum to zero:

$$q_{ii} = -\sum_{j \neq i} q_{ij} = -\sum_{j \neq i} \pi_j r_{ij}$$

### 5. **Stationary Distribution**

The stationary distribution $\pi = (\pi_1, \pi_2, \dots, \pi_K)$ represents the long-term equilibrium probabilities of each state. This distribution satisfies the following condition for each state $i$:

$$\sum_{j \neq i} \pi_i q_{ij} = \sum_{j \neq i} \pi_j q_{ji}$$

which ensures that, at equilibrium, the flow of probability into and out of each state is balanced.

### 6. **Transition Probability Matrix**

The **transition probability matrix** $P(t)$ gives the probability of transitioning from one state to another after time $t$. It is obtained by solving the differential equation:

$$\frac{dP(t)}{dt} = P(t) Q$$

with the initial condition $P(0) = I$ (the identity matrix). The solution is given by the **matrix exponential** of $Q$:

$$P(t) = e^{Qt}$$

where $e^{Qt}$ is the matrix exponential of $Qt$, defined by the series:

$$e^{Qt} = I + Qt + \frac{(Qt)^2}{2!} + \frac{(Qt)^3}{3!} + \cdots$$

Computing the matrix exponential in closed form can be difficult for large matrices, but efficient numerical methods exist for this purpose.

### 7. **Special Cases of the GTR Model**

The GTR model encompasses several simpler models as special cases:

- **JC69 (Jukes-Cantor 1969 Model)**: The JC69 model assumes equal substitution rates between all pairs of nucleotides and equal equilibrium frequencies. This corresponds to the case where $\pi_i = \frac{1}{4}$ for all states (nucleotides) and $r_{ij}$ is the same for all $i \neq j$.
  
- **K80 (Kimura 2-Parameter Model)**: The K80 model assumes different rates for transitions (changes between purines or pyrimidines) and transversions (changes between purines and pyrimidines). This can be viewed as a special case of the GTR model with specific values for $r_{ij}$ and equal equilibrium frequencies $\pi_i$.

- **HKY (Hasegawa-Kishino-Yano Model)**: The HKY model allows for different equilibrium frequencies for each nucleotide and different rates for transitions and transversions. This is a more flexible model than JC69 or K80, but still simpler than the full GTR model.

### 8. **Number of Free Parameters**

In the GTR model, the number of free parameters depends on:
- The number of states $K$.
- The equilibrium frequencies $\pi = (\pi_1, \pi_2, \dots, \pi_K)$, which sum to 1, so there are $K-1$ free parameters for the equilibrium frequencies.
- The **exchangeability rates** $r_{ij}$ for $i \neq j$, which are symmetric, so there are $\frac{K(K-1)}{2}$ independent exchangeability rates.

Thus, the total number of free parameters in the GTR model is $\frac{K(K-1)}{2}$ (exchangeability rates) plus $K-1$ (equilibrium frequencies), which gives:

$$\frac{K(K-1)}{2} + (K-1) = \frac{K(K-1)}{2} + K - 1$$

For example, for $K = 4$ (nucleotides), the GTR model has:

$$\frac{4(4-1)}{2} + 4 - 1 = 6 + 3 = 9$$

free parameters, which include 6 exchangeability rates and 3 independent equilibrium frequencies (since the frequencies must sum to 1).

### 9. **Applications of the GTR Model**

The GTR model is widely used in **molecular evolution** to model nucleotide or amino acid substitution processes over time. Some of its key applications include:

- **Phy

logenetic Inference**: The GTR model is often used to estimate evolutionary trees (phylogenies) from DNA or protein sequence data, as it allows for realistic modeling of substitution processes.
  
- **Substitution Rate Estimation**: The GTR model can be used to estimate substitution rates between different nucleotides or amino acids, allowing researchers to quantify how fast different types of mutations occur.

- **Likelihood-Based Inference**: In maximum likelihood and Bayesian methods for phylogenetic inference, the GTR model is frequently used to compute the likelihood of observed sequence data given a proposed evolutionary tree.

### 10. **Advantages and Limitations of the GTR Model**

#### Advantages:
- **Flexibility**: The GTR model allows for different substitution rates between different pairs of states and accommodates different equilibrium frequencies, making it highly flexible.
- **Time Reversibility**: Time reversibility simplifies both the mathematical analysis and computational implementation of the model, as it allows for efficient algorithms to compute likelihoods.
  
#### Limitations:
- **Complexity**: The GTR model has many free parameters, especially for larger $K$, which can lead to overfitting or computational challenges, particularly for large datasets or when estimating many parameters simultaneously.
- **Stationary Assumption**: The assumption of a stationary process (equilibrium frequencies are constant over time) may not always be realistic, particularly if the evolutionary process is changing over time.

### Summary

The **Generalized Time-Reversible (GTR) model** is a highly flexible and commonly used model in molecular evolution that allows for different substitution rates between different states while maintaining time-reversibility. The model is defined by a rate matrix $Q$, with off-diagonal elements that depend on equilibrium frequencies and exchangeability rates. The GTR model generalizes simpler models like JC69 and K80, providing a more realistic framework for modeling substitution processes, especially when the substitution rates are non-uniform across different states. It plays a critical role in phylogenetic analysis, evolutionary rate estimation, and other applications in molecular biology.