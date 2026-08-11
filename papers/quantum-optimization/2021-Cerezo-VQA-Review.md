# Title: Variational quantum algorithms
Authors: M. Cerezo, Andrew Arrasmith, Ryan Babbush et al.  
Year:  2021     
Institute: Los Alamos National Laboratory, Google Quantum AI, and more  
Venue: Nature Reviews Physics  
Link:  https://arxiv.org/pdf/2012.09265    
Document: [2021_Cerezo_Review_arXiv](resources/papers_download/QO_2021_Cerezo_VQA_Review.pdf)  


## One-sentence summary
This paper provide an overview of the VQAs(Variational Quantum Algorithms), explaining how they works, identifying challenges in VQAs, and evaluating the potential of VQA to obtain quantum advantage.

*Notes*:
- classical computers - high computational cost for simulate quantum systems or solve large-scale linear algebra problems. (Abstract)
- current quantum computers have constraints - limited number of qubits, noise processes that limit circuit depth. (Abstract)
- VQA - use a classical optimizer to train a parametrized quantum circuit - address the challenge of current quantum devices. (Abstract)
  - has challenges like trainability, accuracy, and efficiency of VQAs (Abstract)


## Problem - claim
Current quantum devices are small and noisy, VQA's hybrid approach that combines with a classical optimizers is now the best solution on NISQ devices.

*Notes*:
-  with an exponential speedup over classical methods, quantum algorithms could factor numbers, simulate quantum systems, or solve linear systems of equations. (Intro)
- Constraints: limited numbers of qubits, limited connectivity of the qubits, and coherent
and incoherent errors that limit quantum circuit depth.(Intro)
- VQAs leverage the toolbox of classical optimization, since VQAs use **parametrized quantum circuits** to be run on the quantum computer, and then outsource the parameter optimization to a **classical optimizer**. This approach has the added advantage of keeping the quantum circuit depth **shallow** and hence mitigating noise, in contrast to quantum algorithms developed for the fault-tolerant era. (Intro)


## Motivation
Many important scientific problems are too expensive for even the best supercomputers to solve. Since fault-tolerant quantum devices are still years away, it is vital to maximize the utility of current NISQ resources for practical applications.

*Notes*:   
- Classical computers have high computational cost to solve large-scale problem or simulate quantum systems. Due to the limitations of current NISQ devices, VQAs that can make use of shallow quantum circuit and mitigate noise, becomes a promising solution before fault-tolerant quantum devices.
- Nevertheless, the true promise of quantum computers, speedup for practical applications, which is often called quantum advantage, has yet to be realized. Moreover, the availability of fault-tolerant quantum computers appears to still be many years... The key technological question is therefore how to make best use of today’s NISQ devices to achieve quantum advantage. Any such strategy must account for: limited numbers of qubits, limited connectivity of the qubits, and coherent and incoherent errors that limit quantum circuit depth. (Intro)



## Evidence - support the claim
- One of the evidences is using VQE to estimate eigenstate and eigenvalues of a given Hamiltonian. Unlike previous adiabatic state preparation and quantum phase estimation quantum algorithms that require hardware beyond current reach, the variational quantum eigensolver (VQE) provides a near-term solution. 
- The other evidence is using VQE to simulate the dynamical evolution of a quantum system. Conventional approach like Trotter-Suzuki product formation, the circuit depth grows polynomially with the system size, VQAs only use a shallow circuit depth.  
- The QAOA is the another evidence, that applying VQAs to solve combinatorial problems, which has probale performance guarantees at p=1.

*Notes*:
-  Current state-of-the-art device size ranges from 50 to 100 qubits which allows one to achieve ‘quantum supremacy’: outperforming the best classical supercomputer, for certain contrived mathematical tasks. (Intro)
-  There are many different applications of VQAs: error correction, compilation, machine learning, new frontiers like quantum info, quantum metrology, combinatorial optimization, dynamical simulations, finding ground states in quan chemistry and condensed matter, mathematical applications like factoring, systems of equations etc. (Figure 3)
-  Previous quantum algorithms to find the ground state of a given Hamiltonian H were based on adiabatic state preparation and quantum phase estimation subroutines [104, 105], both of which have circuit depth requirements beyond those available in the NISQ era. Hence, the first proposed VQA, the Variational Quantum Eigensolver (VQE), was developed to provide a near-term solution to this task. (Applications)
-  Apart from static eigenstate problems, VQAs can also be applied to simulate the dynamical evolution of a quantum system. Conventional quantum Hamiltonian simulation algorithms, such as the Trotter-Suzuki product formula [117], generally discretize time into small time steps and simulate each time evolution with a quantum circuit. Therefore, the circuit depth generally increases polynomially with the system size and simulated time. Given the noise inherent in NISQ devices, the accumulated hardware errors for such deep quantum circuits can prove prohibitive. To address this, VQAs for dynamical quantum simulation only use a shallow depth circuit, significantly reducing the impact of hardware noise. (Applications)
- The most famous VQA for quantum-enhanced optimization is the QAOA [23], originally introduced to approximately solve combinatorial problems such as Constraint-Satisfaction (SAT) [127] and Max-Cut problems [128]. (Applications)
- Applying Quantum Approximate Optimization Algorithm (QAOA) to classical optimization problems is widely considered to be one of the leading candidates for achieving quantum advantage on NISQ devices [131]. There are several reasons for this optimism. QAOA has provable performance guarantees [23, 282] for p = 1. In general, even p = 1 QAOA ansatz cannot be efficiently simulated on any classical device [283]. At the same time, QAOA performance can only improve by increasing p. (Opportunities)


## Questions - weaken
- Barren Plateau: when try to solve bigger problems, it becomes harder to find the best settings. A huge number of measurements will be required. This cancel out the quantum advantage. 
- Measurement efficiency: To get a useful result, the quantum computer must be run large number of times, which means the total time needed becomes a roadblock to practical use. 
- Noise in hardware: hardware noise don't just cause wrong answers, they also make the problem look like random noise, making it impossible to train the algorithm or be optimized.

*Notes*:  
- challenges remain including the trainability, accuracy, and efficiency of VQAs. (Abstract)
- When a given cost function C(θ) exhibits a BP, the magnitude of its partial derivatives will be, on average, exponentially vanishing with the system size [194]...in a BP one needs an exponentially large precision to resolve against finite sampling noise and determine a cost-minimizing direction, with this being valid independently of using a gradient-based [84] or gradient-free optimization method [195].  (Challenges)
- Recently, it was shown in Ref. [202] that noise can induce barren plateaus, regardless of the ansatz employed. Here, the presence of noise acting throughout the circuit progressively corrupts the state towards the fixed point of the noise model, usually the maximally mixed state [203]. Such a phenomenon was shown to arise when the circuit depth needs to be linear (or larger) with the system size, meaning that it will affect many widely-used ansatzes. (Challenges)
- Another requirement that must be met for VQAs to provide a quantum advantage is having an efficient way to estimate expectation values (and more general cost functions). The existence of BPs can exponentially increase the precision requirements needed for the optimization portion of VQAs, as discussed in the section on BPs, but even in the absence of such BPs these expectation value estimations are not guaranteed to be efficient. (Challenges)
- In practice, it is typical to observe that noise slows down the training. For example, it was heuristically observed that the noise-free cost achieves lower values with noise-free training than with noisy training [96, 223, 229]. As discussed in the section on BPs, the intuition behind this slowing down is that the cost landscape is flattened, and hence gradient magnitudes are reduced, by the presence of incoherent noise [202, 230, 231]. More-over, gradients decay exponentially with the algorithm’s depth, meaning that the deeper the circuit, the more it will be affected. This can be further understood from the fact that cost functions are typically extremized by pure states, and since incoherent noise reduces state purity, one expects this noise to erode the extremal points of the landscape [203]. (Challenges)
- Effect of noise on cost evaluation. In Refs. [202, 203] it was also shown that in the presence of local Pauli noise, the cost landscape concentrated exponentially with the depth of the ansatz around the value of the cost associated with the maximally mixed state.(Challenges)



## Notes-taken
![2021-Cerezo-VQAs_Figure_1](2021-Cerezo-VQAs_Figure_1.png)
  
Basic concepts and tools & Applications:  
- The trademark of VQAs is that they use a quantum computer to estimate the cost function C(θ) (or its gradient) while leveraging the power of classical optimizers to train the parameters θ.
- Main advantage of VQAs: 
  - provide a **general framework** that can be used to solve a variety of problems.
    - Building blocks of VQAs:
      - Define a cost/loss function that encodes the solution to the problem.
      - Propose an ansatz, that is, a quantum operation depending on a set of continuous or discrete parameters that can be optimized. 
      - Train the ansatz in a hybrid quantum-classical loop to solve the optimization task.
  - Allows for **task-oriented programming**.  
- Applications:
  - Finding ground and excited states
    - Variational quantum eigensolver
    - Orthogonality constrained VQE
    - Subspace expansion method
    - Subspace VQE
    - Multistate contracted VQE
    - Adiabatically assisted VQE
    - Accelerated VQE
  - Dynamical quantum simulation
    - Iterative approach
    - SUbspace approach
    - Variational fast forwarding
    - Simulating open systems
  - Optimization
    - QAOA
  - Mathematical applications
    - Linear systems
    - Matrix-vector multiplication
    - Non-linear equations
    - Factoring
    - Principal Component Analysis
  - Compilation and unsampling
    - Full unitary matrix compiling (FUMC)
    - Fixed input state compiling (FISC)
  - Error correction
  - ML and data science
    - classifier
    - autoencoders
    - generative models
    - variational quantum generators
    - quantum neural network architectures
  - New frontiers
    - quantum foundations
    - quantum information theory
    - entanglement spectroscopy
    - quantum metrology

Challenges and potential solutions:  
- Trainability
  - Barren plateaus (BP)
  - Ansatz and initialization strategies 
    - 2 approaches to prevent BPs:
      - Parameter initialization
      - Ansatz strategies
- Efficiency
  - commuting sets of operators
  - optimized sampling
  - classical shadows
  - neural network tomography
- Accuracy
  - impact of hardware noise
    - effect on noise on training
    - on cost evaluation
  - noise resilience
  - error mitigation

Outlook section:   
- Better methods to analyze VQA scalability, including gradient scaling and other scaling aspects, such as the density of local minima and the shape of the cost landscape. 
- Better application specific ansatzes will enhance gradient magnitudes to improve trainability, and reduce the impact of noise on VQAs, include adaptive ansatz strategies. Hybrid quantum-classical models.
- New error mitigation strategies to improve accuracy. 
- Better quantum hardware - qubit count and noise levels. 
- VQAs are not only important during current NISQ era, can also be useful in the fault-tolerant era. Transitioning from estimating expectation values from Hamiltonian averaging to phase estimation. QAOA is a good candidate to find usage in the fault tolerant era. Strategies address challenges in NISQ (keep shallow circuit depth, avoid barren plateaus) can still be useful later on. 


## Some related papers/ papers mentioned



### Related contents from other paper



## Interesting 
QAOA and VQE work great on small scales and have optimal theoretical roots, but as soon as scale them up to solve "real" problems,we will hit the **Barren Plateau** (can't find the answer) and the **Measurement Wall** (it takes too many repetitions to see the answer). That's why SQD (sample-based quantum diagonalization) comes to play.