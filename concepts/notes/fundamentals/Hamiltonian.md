Here is the breakdown of the physics, machine learning, and quantum mechanics concepts from your questions.

---

### 1. Quantum Hamiltonians & Optimization Encoding

#### What is a Hamiltonian?

In physics, a **Hamiltonian** ($H$) is an operator representing the total energy of a system.

* **Classical Hamiltonian:** A mathematical function $H(x, p)$ where $x$ represents position/state and $p$ represents momentum/energy.
* **Quantum Hamiltonian:** A matrix (operator) whose eigenvalues correspond to the possible energy levels of a quantum system.

#### How do we use Hamiltonians to solve Optimization Problems?

In combinatorial optimization, we seek a combination of variables $x \in \{0,1\}^n$ that minimizes a cost function $C(x)$.

1. **The Core Trick:** Map the cost function $C(x)$ directly to a Hamiltonian $H$ such that the lowest energy state (the **ground state**) of $H$ corresponds exactly to the global minimum of $C(x)$.
2. **Finding the Answer:** Evolve a quantum system into its lowest energy state (via Quantum Annealing or QAOA); reading the final qubit states reveals the optimal solution.

#### What are the specific Encoding Techniques?

| Encoding Technique | How it Works | Common Applications |
| --- | --- | --- |
| **Ising Model** | Maps classical binary variables $x_i \in \{0,1\}$ to quantum spins $s_i \in \{-1, +1\}$ using Pauli-$Z$ matrices ($s_i \to Z_i$). | Magnetic spin simulations, Max-Cut graph problem. |
| **QUBO** *(Quadratic Unconstrained Binary Optimization)* | Formulates quadratic cost terms $x_i Q_{ij} x_j$ directly into qubit-qubit interactions. Easily converted to an Ising Hamiltonian via $x_i = \frac{I - Z_i}{2}$. | Financial portfolio optimization, Logistics, Traveling Salesperson. |
| **Continuous Function Encoding** | Encodes a continuous variable $x \in [a, b]$ into an $n$-qubit register using binary fixed-point grid discretization: $\Vert{}x\rangle = \Vert{}b_{n-1} \dots b_0\rangle$. | Continuous potential energy sampling, PDE solvers. |

