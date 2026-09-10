The battle between Google’s Sycamore processor and classical supercomputers over **Random Circuit Sampling (RCS)** is one of the most famous tug-of-war sagas in modern computer science. It redefined the practical boundary of "Quantum Advantage" and spurred massive innovation in classical tensor network contraction algorithms.

---

* October 2019: Google Claims Quantum Supremacy
Google published a landmark paper in *Nature* using its **53-qubit Sycamore processor**.

  * **The Task:** Sample bitstrings from a 20-cycle random quantum circuit.
  * **The Result:** Sycamore performed the sampling task in **200 seconds** with a fidelity of $0.2\%$.
  * **The Claim:** Google estimated that generating the same 1 million uncorrelated bitstring samples on **Summit** (the world's most powerful classical supercomputer at the time) using standard Schrödinger-Feynman state-vector simulation algorithms would take **10,000 years**.


* Late October 2019: IBM Strikes Back (The Memory Optimization)
Just days after Google's announcement, IBM researchers published a paper challenging the 10,000-year estimate without running code, using pure classical architecture design.

  * **The Insight:** Google assumed the classical supercomputer would be constrained by RAM limits. IBM showed that by utilizing **secondary disk storage** (petabytes of hard drives) on Summit alongside RAM, a supercomputer could store the entire state vector.
  * **The Counter-Claim:** IBM argued Summit could perform an exact classical simulation in **2.5 days** (a $1,400,000\times$ speedup over Google's estimate) with higher fidelity.


* May 2020: Alibaba Drops to 20 Days (Tensor Network Slicing)
Alibaba Quantum Laboratory introduced advanced **Tensor Network Contraction** techniques (the ACQDP framework) to replace brute-force state-vector simulation.

  * **The Innovation:** Instead of evolving the entire $2^{53}$-dimensional Hilbert space over time, they mapped the quantum circuit to a 3D grid of matrices (tensors) and used **tensor slicing/cutting** to divide the contraction graph into independent parallel tasks.
  * **The Result:** Reduced the estimated classical simulation time on Summit down to **less than 20 days**.


* November 2021: Pan Lab / CAS Achieves 15 Hours on GPUs
A team at the Chinese Academy of Sciences (CAS) led by Feng Pan and Pan Zhang shifted the target from full state-vector simulation to **imperfect / approximate sampling**.

  * **The Breakthrough:** They realized Sycamore's actual fidelity was only $0.2\%$ due to physical noise. A classical simulator didn't need to generate perfect amplitudes—it only needed to match Sycamore's low linear Cross-Entropy Benchmarking (XEB) score.
  * **The Result:** Using a 512-GPU cluster running a specialized tensor network slicing algorithm, they generated 1 million uncorrelated samples in **15 hours**, dramatically closing the gap to 200 seconds.


* March 2022: SWAGGER & CAS Crush Sycamore in Seconds
The Chinese Academy of Sciences team optimized their GPU tensor network contractor (using the Sunway supercomputer) to evaluate millions of bitstring amplitudes simultaneously via tensor slicing.

  * **The Final Blow to 2019 Supremacy:** They executed the full classical simulation of Google's exact 20-cycle 53-qubit Sycamore circuit in **just 15 seconds** on the Sunway supercomputer—beating Sycamore's 200-second hardware runtime while achieving higher fidelity.


* July 2023 - Present: The Goalpost Moves: Sycamore 2.0 (70 Qubits)
Recognizing that classical tensor networks had overtaken their 2019 benchmark, Google published a new study using a upgraded **70-qubit Sycamore chip**.

  * **The Escalation:** Increasing the chip size from 53 to 70 qubits increased the Hilbert space size by a factor of $2^{17}$ ($\sim 131,072\times$).
  * **New Benchmark:** Google estimated that simulating the 70-qubit, 24-cycle noisy circuit with state-of-the-art classical tensor networks on the Frontier supercomputer would take **over 47 years**, pushing the goalpost back into quantum territory for the time being.


---

### What Made Tensor Networks So Effective?

Classical simulators bypassed the exponential wall by changing the mathematical approach:

1. **State-Vector (Old Way):** Stores all $2^{53} \approx 9 \times 10^{15}$ complex numbers in memory and updates them gate-by-gate. Highly memory-bound.
2. **Tensor Network Contraction (New Way):** Treats the entire spacetime grid of the quantum circuit as a single large network of small matrices.
3. **Tensor Slicing / Sashing:** By "cutting" a few key physical entanglement edges in the network, the massive calculation splits into millions of small, independent tensor contractions that fit inside standard GPU memory and run in parallel without inter-node communication delays.