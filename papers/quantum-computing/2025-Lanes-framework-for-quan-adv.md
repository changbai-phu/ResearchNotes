# Title: A framework for quantum advantage
Authors:  O. Lanes, M. Beji et al   
Year:  2025  
Institute: IBM Quantum, PASQAL SAS  
Link:  https://arxiv.org/html/2506.20658v2#S2   
Document: [2025_Lanes_QuanAdvantageFramework](resources/papers_download/QC_2025_Lanes_QuanAdvantageFramework.pdf)


## One-sentence summary
This paper provides a framework for quantum advantage which has two criteria, **validation** and **quantum separation**, to create a **verifiable** and **platform-agnostic**(platform-independent) standard. 

## Problem
The term "quantum advantage" is currently blurred and lacks a functional, verifiable definition. 

## Motivation
To provide a rigorous benchmark of quantum technological progress and identify real-world applications with near-term impact. 

## Evidence
The authors support their framework by identifying **3 key families of computational problems** and current hardware progresses.
- The 3 families of problems: sampling algorithms, variational principle, and expectation values of observables.
- Hardware readiness: Modern superconducting and neutral-atom architectures have reached a critical scale (>100 qubits) that allows for the execution of circuits beyond the reach of brute-force classical simulation. 
- Furthermore, quantum-centric supercomputing (QCSC) is the hybrid approach that can be evidence of near-term advantage. 


## Questions
Because quantum advantage is a dynamic, iterative process, and classical algorithms are keep improving that may supersede a quantum advantage claim, this is a on-going process instead of a stable fixed standard for quantum advantage, where claims must be treated as falsifiable hypotheses.   
Current random tests like RCS (Random circuit sampling) as a benchmark is limited by its lack of a scalable verification protocol, which failing the "validation" criterion of the proposed framework. 



## Notes-taken
Two criteria for Quantum Advantage:
1. Validation
   1. Three main ways to address: 
      1. Error bars and error bounds
      2. Problems with efficient classical verification
      3. Variational problems 
2. Quantum separation: a quantum computer solves a problem faster, cheaper, or more accurately than classical computers, but because classical methods keep getting better and we lack absolute mathematical proofs, that lead must be continuously tested and proven over time.
  
Three key problem families:
1. sampling problems - generate probability distributions (e.g, Shor's algorithm, QAOA)
2. variational principle problems - find ground states
3. expectation values of observables - measure physical properties of quantum systems
  
Elements for advantage:
1. Accurate circuits
   1. Error correction
   2. Error mitigation
   3. Error detection
2. QCSC (Quantum-centric supercomputing)
3. Performant quantum processors
   1. Superconducting qubits
   2. Neutral atoms
  
Real world deployment:
- HPC centers like GENCI and Jülich