# Title: Variational quantum algorithms
Authors: M. Cerezo, Andrew Arrasmith, Ryan Babbush et al.  
Year:  2021     
Institute: Los Alamos National Laboratory, Google Quantum AI, and more  
Venue: Nature Reviews Physics  
Link:  https://arxiv.org/pdf/2012.09265    
Document: [2021_Cerezo_Review_arXiv](resources/papers_download/QO_2021_Cerezo_VQA_Review.pdf)  


## One-sentence summary
This paper provide an overview of the VQAs, discuss how to overcome challenges in VQAs, and highlight the future prospects of using VQA to obtain quantum advantage.

*Notes*:
- classical computers - high computational cost for simulate quantum systems or solve large-scale linear algebra problems. (Abstract)
- current quantum computers have constraints - limited number of qubits, noise processes that limit circuit depth. (Abstract)
- VQA - use a classical optimizer to train a parametrized quantum circuit - address the challenge of current quantum devices. (Abstract)
  - has challenges like trainability, accuracy, and efficiency of VQAs (Abstract)


## Problem - claim




## Motivation




## Evidence - support the claim



## Questions - weaken


*Notes*:  



## Notes-taken
Outlook section: 
- Better methods to analyze VQA scalability, including gradient scaling and other scaling aspects, such as the density of local minima and the shape of the cost landscape. 
- Better application specific ansatzes will enhance gradient magnitudes to improve trainability, and reduce the impact of noise on VQAs, include adaptive ansatz strategies. Hybrid quantum-classical models.
- New error mitigation strategies to improve accuracy. 
- Better quantum hardware - qubit count and noise levels. 
- VQAs are not only important during current NISQ era, can also be useful in the fault-tolerant era. Transitioning from estimating expectation values from Hamiltonian averaging to phase estimation. QAOA is a good candidate to find usage in the fault tolerant era. Strategies address challenges in NISQ (keep shallow circuit depth, avoid barren plateaus) can still be useful later on. 


## Some related papers/ papers mentioned



### Related contents from other paper



## Interesting 
