# Questions 

## VQE 
VQE → parameterized circuit → measure → classical optimizer → solution  
But Berezo states that: beware barren plateaus, measurement cost, noise, trainability, accuracy and efficiency of VQAs.   


- Why does VQE require an optimizer in the first place?
- Why does VQE need repeated measurements?
- What information does the optimizer receive from the quantum computer?
- What role does the ansatz play?


- why does this procedure produce a barren plateau? 
- Why do I need so many measurements? 
- What exactly is being measured?
- What is SQD changing compared with VQE?
- Barren plateaus seem to be a significant obstacle to scaling VQAs. What current approaches actually do about it?


Near-term algorithms: VQE/QAOA/SQD  
Foundational algorithms: Shor/Grover/QPE  
Quantum communication: BB84/QKD  



## query model
- why query gates has to be unitary? 
- how to overcome the physical limitations to make an unitary gate?
  - query register
  - target register using bitwise XOR  -> permutation matrix