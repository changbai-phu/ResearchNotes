# Classical Simulation Algorithms & The "Symbolic" Paper

#### What does "Classical Simulation" mean?

It means running a program on a classical computer (like a laptop or supercomputer) that **calculates the exact state or predicts the measurement outputs of a quantum system** without possessing an actual quantum chip.

Classical simulation acts as the moving goalpost for quantum advantage: before declaring "Quantum Advantage," researchers try to push classical simulation to its absolute physical limits to see if a classical computer can match the quantum output.

#### The Symbolic / Milestone Paper in Classical Simulation

The most famous "classical vs. quantum" tug-of-war paper is the **2019 Google Sycamore experiment vs. IBM's classical simulation response**:

* **Google (2019):** Claimed Quantum Supremacy using a 53-qubit chip running a random circuit in 200 seconds, stating Summit (the world's fastest supercomputer at the time) would take **10,000 years**.
* **IBM / Classical Counter-Paper (2019/2021):** IBM researchers published a classical simulation paper demonstrating that by utilizing secondary storage (hard drives) and tensor network slicing techniques on the Summit supercomputer, classical algorithms could simulate Google's exact task in **2.5 days** (and later reduced by Chinese academy teams using tensor networks to **a few dozen seconds**).

---

## Deconstructing the 3 Simulation Methods

You asked if Tensor Networks are Machine Learning—**no, Tensor Networks are not ML.** They originate from condensed matter physics and linear algebra. They are structured ways to store and compress massive multi-dimensional matrices.

| Method | What is it in simple terms? | Why is it used for classical simulation? |
| --- | --- | --- |
| **Tensor Networks** *(e.g., MPS, PEPS)* | A mathematical trick to **compress huge state vectors**. Instead of tracking $2^N$ numbers, you chop the state into a network of small, connected matrices (tensors) and throw away negligible entanglements. | **Low-entanglement simulation:** Shallow circuits or 1D chains have limited entanglement. Tensor networks simulate these systems exponentially faster than raw brute force. |
| **Clifford + T Decomposition** | A strategy that separates quantum gates into two types: **Clifford gates** (easy/cheap to simulate classically) and **T gates** (hard/expensive to simulate). | **Gottesman-Knill Theorem:** Circuits made *only* of Clifford gates can be perfectly simulated on a laptop in polynomial time. Simulator algorithms measure "how many T gates" exist and only pay the exponential cost for the T gates. |
| **Classical Shadows** | A measurement technique introduced by Huang, Kueng, and Preskill (2020). You apply random Clifford unitaries, take a few measurements, and build a **compact classical data sketch** of the quantum state. | **Efficient Property Estimation:** Instead of reconstructing the full $2^N$ state vector (quantum state tomography), classical shadows let you calculate physical properties (like energy or order parameters) using very few measurements. |

#### Are there other classical simulation methods?

* **Full State-Vector Simulation:** Brute-force tracking of all $2^N$ complex amplitudes in RAM (limited to ~45–50 qubits before running out of global RAM).
* **Matrix Product States (MPS):** A 1D variant of tensor networks widely used for low-depth local circuits.
* **Pauli / Stabilizer Frame Sampling:** Simulating noisy circuits by sampling Pauli error channels probabilistically.