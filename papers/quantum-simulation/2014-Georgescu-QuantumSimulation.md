# Title: Quantum Simulation
Authors:  I.M.Georgescu, S.Ashhab, Franco Nori  
Year:  2014  
Institute: RIKEN; Qatar Environment and Energy Research Institute; University of Michigan  
Link: https://arxiv.org/pdf/1308.6253   


## One-sentence summary
This is a review that outlines the theoretical foundations and experimental progress of quantum simulation, arguing for its role as a primary computational tool in the transition toward full quantum advantage. 

*Definition*:   
Quantum simulation is using a controllable quantum system, involves the mapping between a target quantum system and the controllable laboratory device, to simulate/emulate the target's dynamics or properties.
*Revised*: Quantum simulation is the use of a controllable quantum system—often acting as a specialized "stepping stone" before universal quantum computers—to mimic and study the behavior of other complex systems that are too difficult for classical computers to handle.


## Problem - claim
Specialized quantum simulators offer a more immediate and feasible path to overcoming the exponential scaling limits of classical computation, compared to the development of fault-tolerant, universal (general-purposed) quantum computers.  

*Notes*:  
Computer memory needed to store the quantum state is huge. Number of operations increases exponentially with the size of the system. -- *Exponential Explosion* is unavoidable, even approximation methods have limits.   
Use quantum computer to run/store quantum states, because itself would have the capacity to deal with that without using exponentially large amount of physical resources. (Feynman)  


## Motivation
The motivation comes from the maturation of coherent control technologies, and the missing of a multi-disciplinary reference to provide a comprehensive introduction to quantum simulation across physics, chemistry and biology. 
More importantly, quantum simulation has a great potential to revolutionize research by providing a verifiable tool for exploring physical regimes that are currently inaccessible to both classical computation and direct experimentation. 


*Notes*:  
Quantum simulation gains attentions recently because of 2 reasons (twofold): potential applications of quantum simulation, and the technologies required for hte coherent control have matured enough for physical implementation of QS.   
Quantum Simulation can provide insights into new physical phenomena, help solve difficult quantum many-body problems, bring positive impact on the development of other fields other than just in quantum, and will provide a new tool for testing physical theories.


## Evidence - support the claim
Scientists have already simulate the quantum phase transition from a superfluid to a Mott insulator using a cold atomic gas in an optical lattice, and implement digital quantum simulation protocols using trapped-ion chains. (successful proof-of-principle experiments)

*Notes*:
- Physical realizations: (hardware evidence)
  -  Neutral atoms in an optical lattice is possible to perform quantum simulations with more than a few particles. (though individual control and readout is not yet available) - (VI, section F) 
     -  simulation of the quantum phase transition from a superfluid to a Mott insulator using a cold atomic gas in an optical lattice (Greiner et al., 2002).
     -  A theoretical review (Lewenstein et al., 2007) discusses in detail atoms in optical lattices as potential quantum simulators.
  - DQS has been realized with trapped ions. (though with no error correction, the fidelity of the DQS implementation was lower than for the AQS implementation.)
- Applications: (theoretical evidence)


## Questions - weaken
The claim is weakened by technical limitations, for instance the controllability and scalability of quantum simulators, and the problem rises about accuracy with scaling the system size, in other words, the precision in a given quantum simulation is another important question. 

*Notes*:  
(Experimental)  
- controllability and scalability of quantum simulators
- different approaches have each own pros and cons   
(Theoretical)  
- further studies of decoherence and control


## Notes-taken
Quantum simulation will provide a valuable tool for researchers in many fields:
e.g, condensed matter physics -- QS allow the study of many difficult problems like quantum phase transitions, quantum magnetism or high-Tc superconductivity.
Other potential areas: high-energy physics, quantum chemistry, cosmology, nuclear physics.
  
Latest advances in th coherent manipulation:
- atoms in optical lattices
- trapped ions
- nuclear spins
- superconducting circuits
- spins in semiconductors

3 types of simulation:
- Digital quantum simulation
- Analog quantum simulation
- Quantum-information-inspired algorithms for the classical simulation of quantum systems
  
Resource estimation and fault tolerance
- Resource estimation
- Decoherence and errors


Physical realizations: (hardware evidence)
  - Atoms and ions 
    - Neutral atoms in optical lattices for mimicking solid-state systems
    - optics lattices - tunable and defect-free
  - Nuclear and electronic spins
  - Superconducting circuits
  - Photons
  - Other systems 
    
Applications: (theoretical evidence)
  - Condensed-matter physics
    - Hubbard model
    - spin models
    - quantum phase transitions
    - disordered and frustrated systems
    - spin glasses
    - superconductivity
    - meta-materials
    - topological order
  - High-energy physics
  - Cosmology
  - Atomic physics
  - Quantum chemistry
  - Open quantum systems
  - Quantum chaos
  - Nuclear physics
  - Interferometry
  - Other applications


## Some related papers/ papers mentioned
adiabatic quantum computation(Farhi et al., 2001),   
measurement-based quantum computation (Raussendorf et al., 2003),   
topological quantum computation (Kitaev, 2003)   
the theory of quantum computation (Vollbrecht and Cirac, 2008)  

adiabatic quantum computation (Ashhabet al., 2006)  
planar Coulomb crystals (Taylor and Calarco,2008; Wunderlich, 2009) and atoms in optical lattices(Kay et al., 2006)   
entanglement in many-body systems and its relation with quantum phase transitions (Amico et al., 2008)  


proofof-principle experiments on quantum simulation:
Friedenauer et al., 2008;   
Gerritsma et al., 2010;   
Greiner et al., 2002;  
Kim et al.,2010;  
Lanyon et al., 2010;   
Leibfried et al., 2002;   
Neeleyet al., 2009

coherent manipulation of quantum systems:
Buluta et al., 2011;   
Ladd et al.,2010

## Interesting 
- This paper states that more than a few tens of qubits mark the point. -- whereas in 2026, we have >100 qubits ! 