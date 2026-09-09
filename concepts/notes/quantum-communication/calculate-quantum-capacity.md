> How to calculate channel capacity? I mean more specifically, I know it is counting how many quantum coherent information received by Bob. But based on Smith2025 paper on additivity on non-degradable channal, it seems more complicate than expected. Need to ensure coherent information, tractable? math, control the channel setting to be weaker than degradable but not fully non-degradable for it to be provable and computable? 

Calculating the quantum capacity $Q(\mathcal{N})$ of a quantum channel is tricky because of **superadditivity**.

### 1. The Core Equation (LSD Theorem)

The quantum capacity is defined by the **Lloyd-Shor-Devetak (LSD) theorem**:

$$Q(\mathcal{N}) = \lim_{n \to \infty} \frac{1}{n} Q^{(1)}\left(\mathcal{N}^{\otimes n}\right)$$

where $Q^{(1)}(\mathcal{N})$ is the **single-letter coherent information**:

$$Q^{(1)}(\mathcal{N}) = \max_{\rho_A} I(A \rangle B) = \max_{\rho_A} \left[ S(\mathcal{N}(\rho_A)) - S\left((\mathcal{N} \otimes I)(\vert{}\psi_{AB}\rangle\langle\psi_{AB}\vert{})\right) \right]$$

Here, $S(\rho) = -\text{Tr}(\rho \log \rho)$ is the von Neumann entropy.

* **The Problem:** $I(A \rangle B) = S(\text{Bob}) - S(\text{Environment})$. For general channels, sending entangled states across $n$ parallel uses yields *more* output per use than sending them one by one ($Q^{(1)}(\mathcal{N}^{\otimes n}) > n \cdot Q^{(1)}(\mathcal{N})$).
* **The Result:** To calculate $Q(\mathcal{N})$, you must evaluate an infinite-dimensional limit ($n \to \infty$), which is numerically and analytically **intractable**.


### 2. Why Smith & Wu (2025) Make It Tractable

Graeme Smith and Peixue Wu (*IEEE Trans. Inf. Theory*, 2025) tackle how to eliminate the $\lim_{n \to \infty}$ requirement **without** forcing the channel into the restrictive "degradable" box.

```
[ Degradable Channels ] ──> [ Outperforming / Convex Combinations ] ──> [ Arbitrary Channels ]
     (Strictly Additive)        (Weaker Structural Constraints;          (Superadditive;
                                 STILL ADDITIVE & TRACTABLE)              INTRACATABLE)

```

To make the math provable and computable, they design specific mathematical constraints:

* **Weakening Degradability ("Outperforming the Environment"):**
Instead of requiring Eve's system to be a direct degraded copy of Bob's ($\mathcal{N}_E = \mathcal{D} \circ \mathcal{N}_B$), they weaken the condition to cases where Bob's output simply preserves better quantum correlations than Eve's. A primary example is taking **probabilistic convex mixtures of degradable and anti-degradable channels**:

$$\mathcal{N} = p \mathcal{N}_{\text{deg}} + (1-p) \mathcal{N}_{\text{anti}}$$


While $\mathcal{N}$ as a whole is **non-degradable**, its mathematical structure still guarantees that entangled block inputs offer no advantage over single-shot inputs.
* **Additivity Holds ($Q^{(1)}(\mathcal{N}^{\otimes n}) = n Q^{(1)}(\mathcal{N})$):**
Because superadditivity is mathematically suppressed by these relaxed conditions, the regularization limit drops out:

$$Q(\mathcal{N}) = Q^{(1)}(\mathcal{N})$$


* **How to Compute It in Practice:**
Once the limit is gone, calculating capacity reduces to a finite-dimensional optimization problem over a single input state $\rho_A$:
1. Parameterize input state $\rho_A$.
2. Compute $S(\rho_B)$ and $S(\rho_E)$ analytically or using standard matrix logarithm routines.
3. Perform a convex optimization to find $\max_{\rho_A} [S(\rho_B) - S(\rho_E)]$.


### Summary

To calculate quantum capacity without running into the infinite-dimension wall ($n \to \infty$), you must find structural properties that **force single-letter additivity**. Smith & Wu show that you can relax strict degradability into weaker "outperforming" or probabilistic mixture conditions, keeping the single-letter coherent information $Q^{(1)}(\mathcal{N})$ equal to the true channel capacity $Q(\mathcal{N})$.



---
> but why superadditivity make calculating quantum capa hard?

Superadditivity makes calculating quantum capacity hard because it forces you to solve an **infinite-dimensional optimization problem** rather than a single math problem.


### The Fundamental Math Problem: "Single-Shot" vs. "Infinite-Use"

In classical communications (like Wi-Fi or 5G), channel capacity is **additive**. Calculating the capacity of a classical cable requires evaluating what happens during a **single use** of the channel (a single-shot calculation). If 1 use gives you 10 Mbps, 2 uses give 20 Mbps, and $n$ uses give $10n$ Mbps.

In quantum mechanics, **superadditivity** means sending an entangled quantum state across $n$ channel uses at the same time gives you *more* information than sending states one by one:

$$Q^{(1)}\left(\mathcal{N}^{\otimes n}\right) > n \cdot Q^{(1)}(\mathcal{N})$$

Because of this, the true quantum capacity $Q(\mathcal{N})$ is defined by a mathematical limit that goes to infinity:

$$Q(\mathcal{N}) = \lim_{n \to \infty} \frac{1}{n} Q^{(1)}\left(\mathcal{N}^{\otimes n}\right)$$


### Why a Limit to Infinity Breaks Computability

1. **Infinite Search Space:** To find $Q^{(1)}(\mathcal{N})$, a computer only needs to optimize a matrix for **1 particle**. But if the channel is superadditive, calculating $Q^{(1)}(\mathcal{N}^{\otimes 2})$ requires optimizing over entangled pairs across **2 particles**, $Q^{(1)}(\mathcal{N}^{\otimes 3})$ across **3 particles**, and so on.
2. **Exponential Matrix Growth:** The dimension of a quantum state matrix grows exponentially ($2^n \times 2^n$ for $n$ qubits).
3. **No Stopping Rule:** You can never know if block length $n = 100$ or $n = 100,000$ will suddenly unlock a new, massive jump in capacity due to a clever entanglement scheme. Because you cannot check all $n$ up to infinity, **you cannot compute the true capacity**.


### The Analogy

Imagine a delivery truck:

* **Additive Channel (Easy):** 1 truck carries 10 boxes. 2 trucks carry 20 boxes. 100 trucks carry 1,000 boxes. You only need to count 1 truck to know the capacity forever.
* **Superadditive Channel (Hard):** 1 truck carries 10 boxes. But if you chain 2 trucks together, a trick allows them to carry 25 boxes. If you chain 1,000 trucks together, an unknown stacking trick might let them carry 50,000 boxes.

Because you don't know the ultimate "stacking limit" for an infinite chain of trucks, **you cannot calculate the true capacity per truck until you find a mathematical proof that stops the superadditivity**.


### Why "Degradable" or "Additivity" Proofs are the Holy Grail

When researchers like Smith & Wu (2025) prove that a non-degradable channel has **additive** coherent information, they are proving that **chaining particles together gives zero bonus** ($Q^{(1)}(\mathcal{N}^{\otimes n}) = n \cdot Q^{(1)}(\mathcal{N})$).

The $\lim_{n \to \infty}$ disappears, $n$ becomes 1, and the capacity becomes immediately computable on a computer.


---
> so basically until today, calculating channel capacity for quantum channels especially in superadditivity is still an on-going progress? researchers are trying to find a workaround of it since it is impossible to mathematically calculate the capacity in a fully non-degradability channel which is what the real physical channel is?


**Yes, exactly.** You have arrived at the central, defining paradox of Quantum Information Theory.

Determining the exact capacity for arbitrary physical quantum channels remains an active, open area of research. Calculating this capacity directly using brute-force mechanics is not merely difficult—in many cases, it is mathematically impossible.


### Why Exact Capacity Calculation Is Impossible

1. **Unbounded Superadditivity:** In 2015, Toby Cubitt and colleagues proved that for any arbitrarily large integer $n$, there exist channels whose quantum capacity remains hidden ($Q^{(n)} = 0$) until you test $n + 1$ entangled channel uses in parallel. Because you can never know how far out the "jump" in capacity will occur, you can never stop testing higher block lengths.
2. **Computational Undecidability:** Building on this, researchers demonstrated that computing general quantum channel capacities is **algorithmically undecidable** (similar to Turing's Halting Problem) and **QMA-hard** (the quantum equivalent of NP-hard). There is no general algorithm that can take an arbitrary channel matrix and output its exact quantum capacity.


### How Researchers Handle Real Physical Channels

Since computing the exact limit $\lim_{n \to \infty} \frac{1}{n} Q^{(1)}(\mathcal{N}^{\otimes n})$ for general channels cannot be done directly, research focuses on strategic alternatives:

```
                  ┌──> 1. Find Structural Additivity (Smith & Wu) ──> Exact Capacity Q(N) = Q⁽¹⁾(N)
                  │
Physical Channel ─┼──> 2. Prove Tight Upper Bounds (PLOB Bound)   ──> Guaranteed Cap: Q(N) ≤ Upper Bound
                  │
                  └──> 3. Flagger / Convex Extensions             ──> Approximate Bounds via De-noising

```

* **Expanding Additivity Classes (The Smith & Wu Approach):** Researchers identify conditions broader than degradability—such as probabilistic mixtures or "outperforming" environment states—where superadditivity is provably suppressed. If a real noise process falls into these classes, the limit disappears, rendering single-letter calculations exact ($Q = Q^{(1)}$).
* **Proving Upper Bounds (The PLOB Approach):** When exact capacity cannot be computed, researchers establish tight mathematical ceilings (like the PLOB bound for optical fiber loss). While this does not yield an exact value for every noise model, it provides an unassailable performance ceiling for physical systems.
* **Numerical Approximations & De-noising:** For arbitrary channels that resist exact solution, researchers construct artificial "degradable extensions" that closely approximate the real channel from above and below, yielding tight numerical bounds.


### The Fundamental Difference: Classical vs. Quantum Engineering

| Domain | Channel Capacity Problem | Operational Reality |
| --- | --- | --- |
| **Classical Communications** | Solved by Claude Shannon (1948). Single-shot formula $C = \max I(X;Y)$ works for virtually all channels. | Engineers design systems knowing the exact theoretical capacity limits. |
| **Quantum Communications** | Generally non-additive, QMA-hard, and undecidable for arbitrary channels. | Researchers rely on specialized additivity proofs, single-letter lower bounds, and universal upper bounds to guide network design. |