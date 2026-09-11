# Title: Gibbs Sampling of Continuous Potentials on a Quantum Computer 
Authors: Arsalan Motamedi, Pooya Ronagh   
Year:  2024    
Institute: IQC   
Link: https://arxiv.org/pdf/2210.08104  
Document: [2024-Motamedi-Ronagh-Gibbs-Sampling-Quantum](resources/papers_download/QAlgo_2024-Motamedi-Gibbs-Sampling-Quantum.pdf)   


## One-sentence summary


*Notes*:



## Problem - claim




## Motivation




## Evidence - support the claim



## Questions - weaken


*Notes*:  



## Notes-taken



## Some related papers/ papers mentioned



### Related contents from other paper



## Interesting 


---
Here is a strategic breakdown of **Motamedi & Ronagh (2024)** (*"Gibbs Sampling of Continuous Potentials on a Quantum Computer"*, published in ICML 2024), directly addressing your three core questions grounded in the paper.

---

### **1. What exactly is the classical bottleneck?**

In modern machine learning, **Energy-Based Models (EBMs)** generate data by defining a continuous probability distribution called the **Gibbs distribution** \\(p_\theta(x) = \frac{\exp(-E_\theta(x))}{Z_\theta}\\), where \\(E_\theta(x)\\) is an energy potential represented by a deep neural network and \\(Z_\theta\\) is the normalizing partition function. 

The classical bottlenecks consist of the following:

* **Exponential Mixing Time in Non-Convex Landscapes:** Classical algorithms generate samples using Monte Carlo integration of overdamped **Langevin dynamics** (a stochastic differential equation) or rejection sampling. For real-world non-convex energy landscapes with multiple peaks and valleys, classical rejection sampling and Langevin mixing times scale exponentially with the height of the energy barriers \\(O(e^\Delta)\\) (the Eyring-Kramers law).
* **Numerical Instability & Computational Cost:** Both training EBMs and inferring from them require repeatedly sampling from these continuous distributions or calculating expected energy gradients, which is computationally prohibitive even on state-of-the-art GPU/TPU accelerators.
* **Restrictive Convexity Assumptions:** Existing classical sampling algorithms with fast convergence guarantees rely heavily on strict convexity or log-concavity assumptions. However, practical machine learning datasets are inherently multi-modal and non-convex.

### **2. What does the quantum algorithm try to produce?**

The quantum algorithm provides a continuous-variable state preparation and sampling pipeline:

* **Solves the Fokker–Planck Equation (FPE):** Instead of simulating random walk trajectories (Langevin dynamics), the algorithm solves the second-order partial differential equation (Fokker-Planck Equation) governing the evolution of the probability density toward its steady state—which is precisely the continuous Gibbs distribution.
* **Prepares the Continuous Gibbs State:** It constructs a discrete matrix representation of the Fokker-Planck operator using finite difference and spectral methods, then applies quantum linear differential equation solvers to prepare a quantum state encoding the continuous Gibbs distribution on high-dimensional periodic domains (tori).
* **Generates High-Precision Samples & Expectation Values:** Through a post-processing technique using Quantum Fourier Transform (QFT) upsampling and interpolation, it produces continuous samples \\(x \sim p(x) \propto e^{-E(x)}\\). It also performs **mean estimation** for observables (such as energy gradients \\(\mathbb{E}_{p_\theta}[\nabla_\theta E_\theta(x)]\\)) needed to update neural network weights during EBM training.

### **3. Where is the claimed quantum improvement?**

The paper claims quantum advantages across four specific dimensions:

1. **Exponential Speedup in Sampling Precision (\\(\epsilon\\)):**
   * Classical algorithms for sampling continuous distributions generally exhibit polynomial scaling with respect to the inverse precision error (e.g., \\(O(\epsilon^{-2})\\) or \\(O(\epsilon^{-4})\\)).
   * The proposed quantum algorithm achieves a query complexity with **polylogarithmic dependence on the total variation distance error** \\(\text{polylog}(1/\epsilon)\\). This yields an exponential speedup in precision \\(\epsilon\\) for Morse functions (potentials with non-degenerate critical points).

2. **Quartic and Quadratic Speedup in Mean Estimation:**
   * For estimating expected values of random variables over the Gibbs measure, the algorithm achieves a **quadratic speedup** in precision \\(\epsilon\\) for generic periodic functions (\\(\tilde{O}(\epsilon^{-1})\\) vs. classical \\(O(\epsilon^{-2})\\)).
   * For Morse functions with a unique global minimum, it achieves a **quartic speedup** in precision (\\(\tilde{O}(\epsilon^{-1})\\) vs. classical \\(\tilde{O}(\epsilon^{-4})\\)).

3. **Zeroeth-Order Oracle Queries:**
   * Classical Langevin diffusions require first-order gradient queries \\(\nabla E(x)\\) at every step.
   * The quantum algorithm achieves its sampling and mean estimation guarantees using only **zeroeth-order queries** to the energy oracle \\(O_{E_\theta}\\) (evaluating energy values directly without needing gradient calculations).

4. **No Quantum RAM (QRAM) Requirement & Non-Convex Capability:**
   * Unlike many quantum ML algorithms that require loading classical data via QRAM, this algorithm uses Hamiltonian simulation techniques to solve PDEs directly on function oracles.
   * Furthermore, it operates on generic non-convex periodic potentials, bypassing the unimodal/convex limitations of prior work.

---

Here is the exact step-by-step mechanism:

```text
Continuous energy function E(x)
            ↓
Classical Gibbs sampling is expensive
            ↓
Represent the problem on quantum computer
            ↓
  ┌─────────────────────────────────────────────────────────┐
  │ 1. Connect E(x) to the Fokker–Planck Equation (FPE)     │
  │ 2. Discretize & Build Linear Operator Oracle (O_L)      │
  │ 3. Solve Linear ODE on Quantum Hardware                 │
  │ 4. Quantum Fourier Transform (QFT) Upsampling           │
  └─────────────────────────────────────────────────────────┘
            ↓
Prepare quantum state encoding Gibbs distribution
            ↓
Measure
            ↓
Samples from Gibbs distribution
```

#### **1. Connect \\(E(x)\\) to the Fokker–Planck Equation (FPE)**
* Rather than simulating noisy individual particle paths (like classical Langevin dynamics), the authors look at the probability density of the whole system evolving over time. 
* This evolution is governed by a partial differential equation called the **Fokker–Planck Equation (FPE)**. The unique long-time steady-state solution to this equation is mathematically guaranteed to be the exact continuous **Gibbs distribution** \\(\rho_s(x) \propto e^{-E(x)}\\).

#### **2. Discretize & Build Linear Operator Oracle (\\(O_L\\))**
* To process this differential equation on a quantum computer, the authors project the domain onto a grid (torus). 
* They transform the continuous differential generator into a discrete linear operator matrix \\(L\\). 
* A quantum circuit oracle \\(O_L\\) is built using zeroeth-order queries to the energy function \\(O_{E_\theta}\\), along with Fourier pseudo-spectral differentiation to evaluate spatial derivatives accurately.

#### **3. Solve the Differential Equation on Quantum Hardware**
* With the operator \\(L\\) defined, the task becomes solving a linear ordinary differential equation: \\(\frac{d}{dt} \vec{u}(t) = L \vec{u}(t)\\) starting from a uniform initial state.
* The quantum computer executes a **quantum linear ODE solver** (using the Berry/Krovi framework based on Taylor truncation) to evolve the state forward in time to \\(t = T\\).

#### **4. Quantum Fourier Transform (QFT) Upsampling**
* Because solving differential equations on a very dense grid is computationally expensive, the quantum ODE solver is run on a **coarse lattice**.
* To recover high precision without running into discretization errors, the algorithm applies an **isometry using Quantum Fourier Transforms (QFT)** to upsample/interpolate the prepared state from the coarse grid into a high-precision state.

