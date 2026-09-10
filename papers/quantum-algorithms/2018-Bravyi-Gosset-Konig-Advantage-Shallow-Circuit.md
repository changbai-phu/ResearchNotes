# Title: Quantum advantage with shallow circuits
Authors: Sergey Bravyi, David Gosset, Robert Konig   
Year:  2018    
Institute: IBM T.J. Watson Research Center, Technical University of Munich  
Link: https://arxiv.org/pdf/1704.00690 
Document: [2018-Bravyi-Gosset-Konig-Advantage-Shallow-Circuit](resources/papers_download/QAlgo_2018-Bravyi-Gosset-Konig-Quantum-Advantage-Shallow-Circuit.pdf)   


## One-sentence summary
Prove mathematically that a shallow (very short/fast) quantum circuit can beat any shallow classical circuit, without using any black-box shortcuts in a problem of 2D HLF which is an explicit inspired by the structure of Bernstein-Vazirani problem.


*Notes*:
- The Problem (2D HLF): You are given a specific mathematical formula (a quadratic equation mapping $n$-bit strings to integers mod 4). The goal is to find a hidden linear rule hidden inside that formula.
- The Classical Result (The Bottleneck): Any standard classical computer using basic logic gates (AND, OR, NOT with limited inputs) must get taller/deeper as the input size $n$ grows. Specifically, it needs a circuit depth that scales logarithmically with $n$ ($\text{depth} \propto \log n$) to pass information across the network.
- The Quantum Result (The Advantage): A quantum computer can solve this exact problem 100% of the time with a constant depth ($\text{depth} = O(1)$), meaning the execution time stays completely flat no matter how large $n$ gets.
- The Physical Twist: The quantum circuit only needs simple 1-qubit and 2-qubit gates connected to their immediate neighbors on a 2D grid (matching real-world superconducting chip layouts).


## Problem - claim




## Motivation




## Evidence - support the claim



## Questions - weaken
- Question 1 (Classical Counterattack): What if we give the classical computer "super-gates" that can take an unlimited number of inputs at once (a model called $\text{AC}^0$)? Can quantum circuits still beat that stronger classical model?
- Question 2 (Tightening the Math Bounds): In their proof, they showed that classical circuits fail if they try to get a success rate above $7/8$ ($87.5\%$). Can someone tighten the math to prove classical circuits fail even worse (i.e., their success rate drops near $0\%$ as the problem size grows)?
- Question 3 (Deeper Speedups via Recursion): In basic oracle theory, nesting the Bernstein-Vazirani problem inside itself over and over (recursion) creates massive, exponential speedups. Can we nest the 2D HLF problem inside itself to create an even stronger quantum advantage?
- Question 4 (Sampling vs. Finding Exact Answers): Their paper was about finding one exact answer. But what about sampling (generating random outputs according to a quantum probability pattern)? Can shallow classical circuits generate those same probability patterns, or is quantum sampling fundamentally harder to copy?

*Notes*:  



## Notes-taken



## Some related papers/ papers mentioned
David Gosset and his collaborators tackled their open questions by pursuing two main research directions: **handling real-world noise/imperfections** and **developing classical algorithms** to simulate near-term shallow circuits.  

##### 1. Robustness to Noise & Experimental Advantage

* **The Open Question:** The original 2D HLF result assumed perfect, noise-free quantum circuits. Does shallow quantum advantage survive when real-world hardware noise is introduced?
* **How Gosset Addressed It:** In *Quantum advantage with noisy shallow circuits* (Bravyi, Gosset, Koenig, Tomamichel, 2020), the authors extended the theoretical proof to 3D grid architectures under realistic, uncorrected noise. They proved that even in the presence of noise, shallow quantum circuits maintain an unconditional computational separation over classical bounded-depth circuits.

##### 2. Classical Algorithms for Estimating Observables & Sampling

* **The Open Question:** How hard is it classically to sample from or calculate expectation values of shallow quantum output states?
* **How Gosset Addressed It:**
* **Classical Algorithms for Quantum Mean Values (Nature Physics, 2021):** Gosset, Bravyi, and Movassagh proved that calculating expectation values (like energy or cost functions in VQE/QAOA) for output states of constant-depth circuits can actually be computed on classical computers in polynomial/quasi-polynomial time for single-qubit local observables.
* This established an important boundary: while shallow circuits can beat classical computers at *exact global searches* (like 2D HLF), classical simulation algorithms can efficiently estimate *local physical observables*.


##### 3. Pushing Classical Simulation Bounds (Stabilizers & Peaked Circuits)

* **The Open Question:** How can we build scalable classical simulation tools for non-Clifford shallow circuits and shallow-circuit sampling?
* **How Gosset Addressed It:**
* **Low-Rank Stabilizer Decompositions (2019):** Gosset co-developed classical algorithms based on *stabilizer rank*, allowing classical computers to simulate circuits dominated by Clifford gates + $T$ gates by decomposing non-Clifford states into low-rank stabilizer combinations.
* **Simulation of Peaked Shallow Circuits (2023–2024):** Gosset and collaborators designed sparse, classical sampling algorithms specifically for "peaked" shallow quantum circuits (circuits whose probability distributions concentrate on a small subset of bitstrings), showing how classical tools can approximate output probability distributions without full state-vector tracking.

##### Summary of Impact

Instead of remaining purely in theoretical complexity, Gosset used those open questions to build **a two-sided framework**:

1. **Lower Bounds (Hardness):** Proving where shallow quantum hardware holds a true, noise-tolerant quantum advantage.
2. **Upper Bounds (Software):** Writing classical simulation tools and algorithms (tensor networks, stabilizer rank, local observable estimators) to establish the exact computational frontier classical computers can reach.


### Related contents from other paper



## Interesting 
