# Title: A variational eigenvalue solver on a quantum processor
Authors: Alberto Peruzzo, Jarrod McClean, Peter Shadbolt et al.  
Year:  2014    
Institute: University of Bristol, Harvard University, Tsinghua University, Haverford College   
Venue: Nature Communications  
Link: https://arxiv.org/pdf/1308.6253     
Document: [2014_Peruzzo_VQE_arXiv](resources/papers_download/QO_2014_Peruzzo_VQE_arxiv.pdf) 
[2014_Peruzzo_VQE_nature](resources/papers_download/QO_2014_Peruzzo_VQE_nature.pdf)


## One-sentence summary
The paper introduces a hybrid quantum-classical algorithm VQE, that use a variational approach to state preparation, which greatly reduces the requirements for coherent evolution that is required by QPE. 

*Notes*:
- A new approach to find the eigenvalues:
  - Reduce coherence time requirements
  - Implemented by combining a reconfigurable photonic quantum processor with a conventional computer
  - demonstrate the feasibility of the approach with calculating the ground-state molecular energy in quantum chemistry. 
- The quantum phase estimation algorithm finds the eigenvalue but requires the full coherent evolution.


## Problem - claim
The previous best way to find the eigenvalues is QPE but requires fully coherent evolution, but today's quantum computers can't stay stable long enough to meet that requirement. The new proposed approach (VQE) provides a viable, near-term alternative to QPE by drastically reducing the coherence time needed, allowing to perform chemical calculations on current hardware. 



## Motivation
As the dimension of the problem space grows exponentially, finding eigenvalues is a fundamental challenge, meanwhile the applications of solving it have a wide range. It is crucial to propose a new approach that can unlock practical applications like drug discovery using limited near-term quantum resources. 

*Notes*:  
- solution of large eigenvalue problems have applications ranging from determining the results of internet search engines to designing new materials and drugs.
- Previous approach to finding eigenvalues is QPE, which offers an exponential speedup over classical methods, and requires a number of quantum operations to obtain an estimate with certain precision, but it also requires full coherent evolution.
- By using a variational algorithm, can reduce the requirement for coherent evolution of the quantum state, making more efficient use of quantum resources, and may offer an alternative route to practical quantum-enhanced computation.



## Evidence - support the claim
The authors provide validation by using the new approach to calculate the ground-state molecular energy for He-H+, and achieve results that are within the threshold of chemical accuracy (precision). 

*Notes*:
- Demonstrate the feasibility of the new approach with an example from quantum chemistry -- calculating the ground-state molecular energy for He–H+.
- The problem from quantum chemistry: determining the bond dissociation curve of the molecule He-H+ in a minimal basis. 
- more than 96% of the experimental data are within chemical theoretical accuracy. 


## Questions - weaken
While the proof-of-concept is successful, the study is limited to a small-scale specialized photonic architecture, without addressing the challenges of scaling regards to large-scale systems.  

And actually, according to [2025 Lanes](papers/quantum-computing/2025-Lanes-framework-for-quan-adv.md), to get a useful precision for large chemistry systems, the number of measurements needed becomes so massive that the quantum computer would also take years to solve, which in other words, 'prohibitive' as mentioned in that paper. And plus, 'VQE answers come with uncertainty related to the statistical nature of the energy estimation', which means the result might accidentally look lower thant he true energy level because of a statistical error, so it is hard to trust if a new low score is a better discovery. 

*Notes*:  
- tests on a small-scale photonic quantum processor with a conventional computer. 
- (2025 Lanes) quality metrics like V-score may help, but low-depth VQE is not good for large-scale system.
- (extra) VQE Measurement Scaling: as a molecule gets bigger, the number of measurements needed can grow by the power of 4 or even 6 ($N^4$ or $N^6$) -- (ref 35, 36 mentioned in 2025 Lanes)


## Notes-taken
Algorithms used:
- Algorithm 1: Quantum expectation estimation - compute the expectation value of a given Hamiltonian for an input state. 
  - quantum hardware can store a global quantum state with exponentially fewer resources than required by classical hardware, and as a result the N-representability problem does not arise.
  - **Reduce the coherence time requirement while maintaining an exponential advantage over the classical case, by adding a polynomial number of repetitions w.r.t QPE.**
- Algorithm 2: Quantum variational eigensolver
  -  Both QPE and Algorithm 1 require a good approximation to the ground state wavefunction to compute the ground state eigenvalue.
  -  Previous approaches using adiabatic evolution or quantum metropolis algorithm require long cohere evolution. 
  -  Algorithm 2 is a variational method to prepare the eigenstate and, by exploiting Algorithm 1, requires short coherent evolution

QPE requires a large number of n-qubit quantum controlled operations to be performed in series. (demands on the number of components and coherence time)


## Some related papers/ papers mentioned
- （ref 35 in 2025 Lanes） D. Wecker, M. B. Hastings, and M. Troyer, "Progress towards practical quantum computing: Towards 100 qubits", Phys. Rev. A 92, 042303 (2015)  
- （ref 36 in 2025 Lanes) Y. Zhang et al., "Variational quantum algorithms: A survey of theoretical and practical aspects", Wiley Interdisciplinary Reviews: Computational Molecular Science 15, e70020 (2025)


### Related contents from other paper
According to [2025-Lanes](papers/quantum-computing/2025-Lanes-framework-for-quan-adv.md):
- VQE is a hybrid quantum-classical algorithm designed for the NISQ era, utilizing shallow circuits to approximate the ground-state energies of Hamiltonians. However, low-depth VQE is not good choice for large-scale chemistry systems yet, because it takes too many measurements to get a precise result. 
- It does not have convergence guarantees, not directly tied to the quality of the initial reference state. 


## Interesting 
