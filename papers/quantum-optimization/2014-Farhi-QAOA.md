# Title: 
Authors: Edward Farhi and Jeffrey Goldstone  
Year:  2014    
Institute: MIT  
Link: https://arxiv.org/pdf/1411.4028   
Document: [2014_Farhi_arXiv](resources/papers_download/QO_2014_Farhi_QAOA.pdf)  


## One-sentence summary
The paper introduce a quantum algorithm (QAOA) for approximate combinatorial search problem which depends on an integer parameter p, that the performance get better when the more steps p take. 
The algorithm is tested on MaxCut, proving it can reach at least approximation ratio of 0.6924 at the simplest level p=1. And a specialized version of finding independent sets is also introduced. 

*Notes*:
- QAOA: Quantum approximate optimization algorithm
- The paper introduce a quantum algorithm that produces approximate solutions for combinatorial optimization problems. The depth of the circuit grows linearly with p*the number of constraints. The algorithm is tested by applying to MaxCut, and analyzed its performance on 2-regular and 3-regular graphs for fixed p. 
- If p is fixed, that is, independent of the input size, the algorithm makes use of efficient classical pre-processing. If p grows with the input size a different strategy is proposed. 
- Running the algorithm requires a strategy for picking a sequence of sets of angles with the goal of making Fp as big as possible --- an efficient classical algorithm is used to determine the best set of angles that is then fed to the quantum computer, but this could require space doubly exponential in p. And alternative is making repeated calls to the quantum computer with different sets of angles. 


## Problem - claim
The primary claim is that the authors have developed a general hybrid quantum algorithm capable of providing approximate solutions to combinatorial optimization problem, with performance is guaranteed to improve as the algorithm's depth p increases.

*Notes*:
- evaluate the algorithm's performance in MaxCut, and propose an alternate algorithm to find a large independent set of vertices of a graph. 
- The Quantum Approximate Optimization Algorithm (QAOA) is fundamentally a hybrid quantum-classical approach. In this framework, a classical computer performs the heavy lifting of finding the optimal "tuning knobs"—specifically the angles (γ,β)—which are then "fed" into the quantum processor to prepare a state that approximates the solution to a hard math problem.


## Motivation




## Evidence - support the claim



## Questions - weaken


*Notes*:  



## Notes-taken



## Some related papers/ papers mentioned



### Related contents from other paper



## Interesting 
