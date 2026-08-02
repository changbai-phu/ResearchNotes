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
- Previous approach to finding eigenvalues is QPE, which offers an exponential speedup over classical methods, and requires a number of quantum operations to obtain an estimate with certain precision, but it also requires ? 



## Evidence - support the claim


*Notes*:



## Questions - weaken


*Notes*:  



## Notes-taken



## Some related papers/ papers mentioned


### Related contents from other paper
According to [2025-Lanes](papers/quantum-computing/2025-Lanes-framework-for-quan-adv.md):
- VQE is a hybrid quantum-classical algorithm designed for the NISQ era, utilizing shallow circuits to approximate the ground-state energies of Hamiltonians. However, low-depth VQE is not good choice for large-scale chemistry systems yet, because it takes too many measurements to get a precise result. 
- It does not have convergence guarantees, not directly tied to the quality of the initial reference state. 


## Interesting 
