# Title: A Quantum Approximate Optimization Algorithm
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
- The independent sets: is a group of vertices on a graph where no two points are connected by an edge. So the goal is to find the largest possible group of these points. (Section VII)

## Problem - claim
The primary claim is that the authors have developed a general hybrid quantum algorithm capable of providing approximate solutions to combinatorial optimization problem, with performance is guaranteed to improve as the algorithm's depth p increases.

*Notes*:
- evaluate the algorithm's performance in MaxCut, and propose an alternate algorithm to find a large independent set of vertices of a graph. 
- The Quantum Approximate Optimization Algorithm (QAOA) is fundamentally a hybrid quantum-classical approach. In this framework, a classical computer performs the heavy lifting of finding the optimal "tuning knobs"—specifically the angles (γ,β)—which are then "fed" into the quantum processor to prepare a state that approximates the solution to a hard math problem.


## Motivation
The motivation is rooted in the computational intractability of NP-hard combinatorial optimization problems. The authors created QAOA that can potentially exceed the classical algorithm when solving specific problems like scheduling.

*Notes*:
- We hope that either p fixed or growing slowly with n will be enough to have this quantum algorithm be of use in finding solutions to combinatorial search problems beyond what classical algorithms can achieve.


## Evidence - support the claim
To prove the algorithm works, the authors tested it on the MaxCut problem for regular graphs, proving a worst-case approximation ratio of 0.6924 for p=1 on 3-regular graphs. 

*Notes*:
- THe authors study the algorithm as applied to MaxCut, and analyzed its performance on 2-regular and 3-regular graphs for fixed p. For p=1 on 3-regular graphs, the proposed algorithm finds a cat that is at least 0.6924 times the size of the optimal cut. 


## Questions - weaken
A major weakness is the challenge of finding the best set of angles (classically) that need to feed into quantum part, which can be memory-intensive as the p grows. 
Furthermore, for p=1, existing classical algorithm still perform better than this quantum alternative. 

*Notes*:  
- Running the algorithm requires a strategy for picking a sequence of sets of angles with the goal of making Fp as big as possible.
- In this case there is an efficient classical algorithm that determines the
best set of angles which is then fed to the quantum computer. Here the quantum computer is run with only the best set of angles. Note that the “efficient” classical algorithm which evaluates (25) using (24) could require space doubly exponential in p.An alternative to using a classical preprocessor to find the best angles is to make repeated calls to the quantum computer with different sets of angles.
- The authors admit that this p = 1 result on 3-regular graphs is not as good as known classical algorithms. 


## Notes-taken



## Some related papers/ papers mentioned
[1] Eran Halperin, Dror Livnat, Uri Zwick.
MAX CUT in cubic graphs, 2004.
Journal of Algorithms, Volume 53 Issue 2, Pages 169-185.  
[2] Edward Farhi, Jeffrey Goldstone, Sam Gutmann, Michael Sipser.
Quantum computation by adiabatic evolution, 2000.
arXiv:quant-ph/0001106.  
[3] Edward Farhi, Jeffrey Goldstone, Sam Gutmann.
Quantum Adiabatic Evolution Algorithms versus Simulated Annealing, 2002.
arXiv:quant-ph/0201031.  
[4] Elizabeth Crosson, Edward Farhi, Cedric Yen-Yu Lin, Han-Hsuan Lin, Peter Shor.
Different strategies for optimization with the quantum adiabatic algorithm, 2014.
arXiv:1401.7320 [quant-ph].  
[5] Edward Farhi, Sam Gutmann.
Quantum Computation and Decision Trees, 1997.
Phys. Rev. A 58, 915 arXiv:quant-ph/9706062.  


### Related contents from other paper



## Interesting 
